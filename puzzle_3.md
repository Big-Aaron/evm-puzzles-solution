# puzzle_3 题解

## 题目

```json
{
  "code": "3656FDFD5B00",
  "askForValue": false,
  "askForData": true
}
```

### 操作码

```
############
# Puzzle 3 #
############

00      36      CALLDATASIZE
01      56      JUMP
02      FD      REVERT
03      FD      REVERT
04      5B      JUMPDEST
05      00      STOP
```

### 要求

```
? Enter the calldata:
```

## 题解

CALLDATASIZE calldata的大小所占字节数，存放在栈顶



程序需要跳转到0x04，才能成功结束。所以calldata大小需要为4bytes

## 解题

```
? Enter the calldata: 0x00000000

Puzzle solved!

Run it in evm.codes: https://www.evm.codes/playground?callValue=0&unit=Wei&callData=0x00000000&codeType=Bytecode&code='3656FDFD5B00'_
```

