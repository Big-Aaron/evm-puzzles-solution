# puzzle_8 题解

## 题目

```json
{
  "code": "36600080373660006000F0600080808080945AF1600014601B57FD5B00",
  "askForValue": false,
  "askForData": true
}
```

### 操作码

```
############
# Puzzle 8 #
############

00      36        CALLDATASIZE
01      6000      PUSH1 00
03      80        DUP1
04      37        CALLDATACOPY
05      36        CALLDATASIZE
06      6000      PUSH1 00
08      6000      PUSH1 00
0A      F0        CREATE
0B      6000      PUSH1 00
0D      80        DUP1
0E      80        DUP1
0F      80        DUP1
10      80        DUP1
11      94        SWAP5
12      5A        GAS
13      F1        CALL
14      6000      PUSH1 00
16      14        EQ
17      601B      PUSH1 1B
19      57        JUMPI
1A      FD        REVERT
1B      5B        JUMPDEST
1C      00        STOP
```

### 要求

```
? Enter the calldata:
```

## 题解

CALL 从栈顶取7个元素，`success`: return 0 if the sub [context](https://www.evm.codes/about) [reverted](https://www.evm.codes/#FD), 1 otherwise.

- gas：amount of gas to send to the sub [context](https://www.evm.codes/about) to execute. The gas that is not used by the sub context is returned to this one.
- address：the account which [context](https://www.evm.codes/about) to execute.
- value：[value](https://www.evm.codes/#34) in [wei](https://www.investopedia.com/terms/w/wei.asp) to send to the account.
- argsOffset: byte offset in the [memory](https://www.evm.codes/about) in bytes, the [calldata](https://www.evm.codes/about) of the sub [context](https://www.evm.codes/about).
- argsSize：byte size to copy (size of the [calldata](https://www.evm.codes/about)).
- retOffset： byte offset in the [memory](https://www.evm.codes/about) in bytes, where to store the [return data](https://www.evm.codes/about) of the sub [context](https://www.evm.codes/about).
- retSize：byte size to copy (size of the [return data](https://www.evm.codes/about)).



程序需要跳转到0x1B，则EQ存放在栈顶的值不为0，即CALL指令存放在栈顶的元素为0，即调用合约时需要reverted，即被调用合约需要返回REVERT操作码（FD）  所以新合约的runtime代码中只能有一个操作码，即return回的runtime只能有一个字节，即FD。所以

```
[00]	60 00	PUSH1	FD	//	REVERT操作码
[02]	60 00	PUSH1	00	//	MSTORE8存放在memory中的偏移量
[04]	53		MSTORE8		//  将STOP操作码存放在memory的0字节处
[05]	60 01 	PUSH1	01	// 	RETURN需要返回的数据存放在memory中的大小
[07]	60 00	PUSH1	00	// 	RETURN需要返回的数据存放在memory中的偏移量
[09]	F3		RETURN		//  返回STOP操作码
```



## 解题

```
? Enter the calldata: 0x60FD60005360016000F3

Puzzle solved!

Run it in evm.codes: https://www.evm.codes/playground?callValue=0&unit=Wei&callData=0x60FD60005360016000F3&codeType=Bytecode&code='36600080373660006000F0600080808080945AF1600014601B57FD5B00'_
```

