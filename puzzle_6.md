# puzzle_6 题解

## 题目

```json
{
  "code": "60003556FDFDFDFDFDFD5B00",
  "askForValue": false,
  "askForData": true
}
```

### 操作码

```
############
# Puzzle 6 #
############

00      6000      PUSH1 00
02      35        CALLDATALOAD
03      56        JUMP
04      FD        REVERT
05      FD        REVERT
06      FD        REVERT
07      FD        REVERT
08      FD        REVERT
09      FD        REVERT
0A      5B        JUMPDEST
0B      00        STOP
```

### 要求

```
? Enter the calldata:
```

## 题解

CALLDATALOAD 从栈顶中读取一个字节数a（小于等于32），从calldata中截取a之后的数据（32bytes）缺位补0（大端模式）



程序需要跳转到0x0A,所以CALLDATALOAD 存放在栈顶的元素需要为0x0A，程序取的是calldata的0字节开始的32字节，所以calldata为bytes32(0x000000000000000000000000000000000000000000000000000000000000000a)

## 解题

```
? Enter the calldata: 0x000000000000000000000000000000000000000000000000000000000000000a

Puzzle solved!

Run it in evm.codes: https://www.evm.codes/playground?callValue=0&unit=Wei&callData=0x000000000000000000000000000000000000000000000000000000000000000a&codeType=Bytecode&code='60003556FDFDFDFDFDFD5B00'_
```

