# puzzle_2 题解

## 题目

```json
{
  "code": "34380356FDFD5B00FDFD",
  "askForValue": true,
  "askForData": false
}
```

### 操作码

```
############
# Puzzle 2 #
############

00      34      CALLVALUE
01      38      CODESIZE
02      03      SUB
03      56      JUMP
04      FD      REVERT
05      FD      REVERT
06      5B      JUMPDEST
07      00      STOP
08      FD      REVERT
09      FD      REVERT
```

### 要求

```
? Enter the value to send:
```

## 题解

CALLVALUE 读取我们发送的value值（以wei为单位），存放在栈顶

CODESIZE 读取当前程序共有多少字节

SUB 从栈中取出两个操作数a,b（a在栈顶），a - b的结果存在栈顶

JUMP 跳转到栈顶数据所指向的栈指针且该栈指针中内容必须为JUMPDEST（5B）

STOP 程序结束



此程序中CODESIZE为0xa（10bytes）,CODESIZE - CALLVALUE需要等于0x6，才能跳转成功。所以CALLVALUE需要为4.

## 解题

```
? Enter the value to send: 4

Puzzle solved!

Run it in evm.codes: https://www.evm.codes/playground?callValue=4&unit=Wei&callData=&codeType=Bytecode&code='34380356FDFD5B00FDFD'_
```

