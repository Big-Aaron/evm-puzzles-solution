# puzzle_1 题解

## 题目

```json
{
  "code": "3456FDFDFDFDFDFD5B00",
  "askForValue": true,
  "askForData": false
}
```

### 操作码

```
############
# Puzzle 1 #
############

00      34      CALLVALUE
01      56      JUMP
02      FD      REVERT
03      FD      REVERT
04      FD      REVERT
05      FD      REVERT
06      FD      REVERT
07      FD      REVERT
08      5B      JUMPDEST
09      00      STOP
```

### 要求

```
? Enter the value to send:
```

## 题解

CALLVALUE 读取我们发送的value值（以wei为单位），存放在栈顶

JUMP 跳转到栈顶数据所指向的栈指针，且该栈指针中内容必须为JUMPDEST（5B）

STOP 程序结束

## 解题

```
? Enter the value to send: 8

Puzzle solved!

Run it in evm.codes: https://www.evm.codes/playground?callValue=8&unit=Wei&callData=&codeType=Bytecode&code='3456FDFDFDFDFDFD5B00'_
```

