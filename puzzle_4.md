# puzzle_4 题解

## 题目

```json
{
  "code": "34381856FDFDFDFDFDFD5B00",
  "askForValue": true,
  "askForData": false
}
```

### 操作码

```
############
# Puzzle 4 #
############

00      34      CALLVALUE
01      38      CODESIZE
02      18      XOR
03      56      JUMP
04      FD      REVERT
05      FD      REVERT
06      FD      REVERT
07      FD      REVERT
08      FD      REVERT
09      FD      REVERT
0A      5B      JUMPDEST
0B      00      STOP
```

### 要求

```
? Enter the value to send:
```

## 题解

XOR 两数进行异或运算，结果存放在栈顶



程序需要跳转到0x0A，所以异或运算结果需要为0x0A（10、0x1010），CODESIZE为0x1100（12）。所以CALLVALUE需要为0x0110（6）

## 解题

```
? Enter the value to send: 6

Puzzle solved!

Run it in evm.codes: https://www.evm.codes/playground?callValue=6&unit=Wei&callData=&codeType=Bytecode&code='34381856FDFDFDFDFDFD5B00'_
```

