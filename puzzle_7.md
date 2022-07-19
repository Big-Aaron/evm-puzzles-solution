# puzzle_7 题解

## 题目

```json
{
  "code": "36600080373660006000F03B600114601357FD5B00",
  "askForValue": false,
  "askForData": true
}
```

### 操作码

```
############
# Puzzle 7 #
############

00      36        CALLDATASIZE
01      6000      PUSH1 00
03      80        DUP1
04      37        CALLDATACOPY
05      36        CALLDATASIZE
06      6000      PUSH1 00
08      6000      PUSH1 00
0A      F0        CREATE
0B      3B        EXTCODESIZE
0C      6001      PUSH1 01
0E      14        EQ
0F      6013      PUSH1 13
11      57        JUMPI
12      FD        REVERT
13      5B        JUMPDEST
14      00        STOP
```

### 要求

```
? Enter the calldata:
```

## 题解

CREATE 从栈中取3个数a,b,c（a在栈顶），其中a=发送到新合约的ETH（wei为单位），b=memory中的偏移量，c=取memory中多少字节，将新合约的地址放在栈顶

EXTCODESIZE 取当前栈顶元素（20个字节的地址），计算该地址下的合约大小



程序需要跳转到0x13，则EQ存放在栈顶的值不为0，即EXTCODESIZE 的大小为0x1（1bytes），所以新合约的runtime代码中只能有一个操作码，即return回的runtime只能有一个字节，即00。所以

```
[00]	60 00	PUSH1	00	//	STOP操作码
[02]	60 00	PUSH1	00	//	MSTORE8存放在memory中的偏移量
[04]	53		MSTORE8		//  将STOP操作码存放在memory的0字节处
[05]	60 01 	PUSH1	01	// 	RETURN需要返回的数据存放在memory中的大小
[07]	60 00	PUSH1	00	// 	RETURN需要返回的数据存放在memory中的偏移量
[09]	F3		RETURN		//  返回STOP操作码
```



## 解题

```
? Enter the calldata: 0x600060005360016000F3

Puzzle solved!

Run it in evm.codes: https://www.evm.codes/playground?callValue=0&unit=Wei&callData=0x600060005360016000F3&codeType=Bytecode&code='36600080373660006000F03B600114601357FD5B00'_
```

