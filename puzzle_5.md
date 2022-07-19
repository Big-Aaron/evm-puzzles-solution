# puzzle_5 题解

## 题目

```json
{
  "code": "34800261010014600C57FDFD5B00FDFD",
  "askForValue": true,
  "askForData": false
}
```

### 操作码

```
############
# Puzzle 5 #
############

00      34          CALLVALUE
01      80          DUP1
02      02          MUL
03      610100      PUSH2 0100
06      14          EQ
07      600C        PUSH1 0C
09      57          JUMPI
0A      FD          REVERT
0B      FD          REVERT
0C      5B          JUMPDEST
0D      00          STOP
0E      FD          REVERT
0F      FD          REVERT
```

### 要求

```
? Enter the value to send:
```

## 题解

DUP1 复制栈顶元素，复制完的值存放在栈顶

MUL 从栈中取两个数啊a、b（a在栈顶），a * b的值存放在栈顶

EQ 从栈中取两个数啊a、b（a在栈顶），a == b的值（0 or 1）存放在栈顶

PUSH1 存放一个字节的数据在栈顶

PUSH2 存放二个字节的数据在栈顶

JUMPI 从栈中取两个数a、b（a在栈顶），a为要跳转的栈地址，b不为0时进行跳转



程序需要成功跳转到0x0c，所以EQ的结果不能为0，所以MUL的结果需要等于0x0100，所以CALLVALUE * CALLVALUE需要等于0x0100（256 = 16 * 16）.所以CALLVALUE需要等于16.

## 解题

```
? Enter the value to send: 16

Puzzle solved!

Run it in evm.codes: https://www.evm.codes/playground?callValue=16&unit=Wei&callData=&codeType=Bytecode&code='34800261010014600C57FDFD5B00FDFD'_
```

