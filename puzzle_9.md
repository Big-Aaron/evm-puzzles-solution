# puzzle_9 题解

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
############
# Puzzle 9 #
############

00      36        CALLDATASIZE
01      6003      PUSH1 03
03      10        LT
04      6009      PUSH1 09
06      57        JUMPI
07      FD        REVERT
08      FD        REVERT
09      5B        JUMPDEST
0A      34        CALLVALUE
0B      36        CALLDATASIZE
0C      02        MUL
0D      6008      PUSH1 08
0F      14        EQ
10      6014      PUSH1 14
12      57        JUMPI
13      FD        REVERT
14      5B        JUMPDEST
15      00        STOP
```

### 要求

```
? Enter the value to send: 
? Enter the calldata:
```

## 题解

LT 在栈中取两数a，b（a在栈顶），a < b 为1，否则为0



程序需要跳转两次，第一次需要CALLDATASIZE大于3，第二次CALLVALUE*CALLDATASIZE =8，所以需要CALLDATASIZE为4，CALLVALUE为2.

## 解题

```
? Enter the value to send: 2
? Enter the calldata: 0x00000000

Puzzle solved!

Run it in evm.codes: https://www.evm.codes/playground?callValue=2&unit=Wei&callData=0x00000000&codeType=Bytecode&code='36600310600957FDFD5B343602600814601457FD5B00'_
```

