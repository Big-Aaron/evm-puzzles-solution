# puzzle_10 题解

## 题目

```json
{
  "code": "36600310600957FDFD5B343602600814601457FD5B00",
  "askForValue": true,
  "askForData": true
}
```

### 操作码

```
#############
# Puzzle 10 #
#############

00      38          CODESIZE
01      34          CALLVALUE
02      90          SWAP1
03      11          GT
04      6008        PUSH1 08
06      57          JUMPI
07      FD          REVERT
08      5B          JUMPDEST
09      36          CALLDATASIZE
0A      610003      PUSH2 0003
0D      90          SWAP1
0E      06          MOD
0F      15          ISZERO
10      34          CALLVALUE
11      600A        PUSH1 0A
13      01          ADD
14      57          JUMPI
15      FD          REVERT
16      FD          REVERT
17      FD          REVERT
18      FD          REVERT
19      5B          JUMPDEST
1A      00          STOP
```

### 要求

```
? Enter the value to send: 
? Enter the calldata:
```

## 题解

SWAP1 交换栈顶元素和第3个栈中元素

ISZERO 判断当前栈顶元素是否为0，为0则返回1，否则返回0

ADD 从栈中取两个值a,b（a在栈顶）,返回a+b的值

MOD 从栈中取两个值a,b（a在栈顶）,返回a%b的值



程序需要跳转两次，第一次需要GT返回1，CODESIZE为27，所以CALLVALUE需要小于27。第二次需要MOD返回0，即CALLDATASIZE需要为3的倍数，并且CALLVALUE在加上0x0a后需要等于0x19，即25-10=15。所以CALLVALUE=15，CALLDATASIZE为3。

## 解题

```
? Enter the value to send: 15
? Enter the calldata: 0x000000

Puzzle solved!

Run it in evm.codes: https://www.evm.codes/playground?callValue=15&unit=Wei&callData=0x000000&codeType=Bytecode&code='38349011600857FD5B3661000390061534600A0157FDFDFDFD5B00'_
```

