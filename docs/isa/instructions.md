# 基本指令

## 数据传输指令

### 加载指令

| 指令 | 格式 | 描述 | 操作 |
|------|------|------|------|
| LD   | LD Rd, offset(Rs1) | 加载字 | Rd = Mem[Rs1 + offset] |
| LDH  | LDH Rd, offset(Rs1) | 加载半字 | Rd = SignExt(Mem[Rs1 + offset][15:0]) |
| LDU  | LDU Rd, offset(Rs1) | 加载无符号半字 | Rd = ZeroExt(Mem[Rs1 + offset][15:0]) |
| LDB  | LDB Rd, offset(Rs1) | 加载字节 | Rd = SignExt(Mem[Rs1 + offset][7:0]) |
| LDBU | LDBU Rd, offset(Rs1) | 加载无符号字节 | Rd = ZeroExt(Mem[Rs1 + offset][7:0]) |

### 存储指令

| 指令 | 格式 | 描述 | 操作 |
|------|------|------|------|
| ST   | ST Rs2, offset(Rs1) | 存储字 | Mem[Rs1 + offset] = Rs2 |
| STH  | STH Rs2, offset(Rs1) | 存储半字 | Mem[Rs1 + offset][15:0] = Rs2[15:0] |
| STB  | STB Rs2, offset(Rs1) | 存储字节 | Mem[Rs1 + offset][7:0] = Rs2[7:0] |

### 寄存器传输指令

| 指令 | 格式 | 描述 | 操作 |
|------|------|------|------|
| MOV  | MOV Rd, Rs1 | 寄存器间传输 | Rd = Rs1 |
| LI   | LI Rd, imm | 加载立即数 | Rd = SignExt(imm) |
| LUI  | LUI Rd, imm | 加载上立即数 | Rd = imm << 16 |

## 算术指令

### 整数算术指令

| 指令 | 格式 | 描述 | 操作 |
|------|------|------|------|
| ADD  | ADD Rd, Rs1, Rs2 | 加法 | Rd = Rs1 + Rs2 |
| ADDI | ADDI Rd, Rs1, imm | 加立即数 | Rd = Rs1 + SignExt(imm) |
| SUB  | SUB Rd, Rs1, Rs2 | 减法 | Rd = Rs1 - Rs2 |
| SUBI | SUBI Rd, Rs1, imm | 减立即数 | Rd = Rs1 - SignExt(imm) |
| NEG  | NEG Rd, Rs1 | 取负 | Rd = -Rs1 |

### 比较指令

| 指令 | 格式 | 描述 | 操作 |
|------|------|------|------|
| CMP  | CMP Rs1, Rs2 | 比较 | SR = FLAGS(Rs1 - Rs2) |
| CMPI | CMPI Rs1, imm | 与立即数比较 | SR = FLAGS(Rs1 - SignExt(imm)) |

## 逻辑指令

### 基本逻辑操作

| 指令 | 格式 | 描述 | 操作 |
|------|------|------|------|
| AND  | AND Rd, Rs1, Rs2 | 按位与 | Rd = Rs1 & Rs2 |
| ANDI | ANDI Rd, Rs1, imm | 按位与立即数 | Rd = Rs1 & ZeroExt(imm) |
| OR   | OR Rd, Rs1, Rs2 | 按位或 | Rd = Rs1 \| Rs2 |
| ORI  | ORI Rd, Rs1, imm | 按位或立即数 | Rd = Rs1 \| ZeroExt(imm) |
| XOR  | XOR Rd, Rs1, Rs2 | 按位异或 | Rd = Rs1 ^ Rs2 |
| XORI | XORI Rd, Rs1, imm | 按位异或立即数 | Rd = Rs1 ^ ZeroExt(imm) |
| NOT  | NOT Rd, Rs1 | 按位取反 | Rd = ~Rs1 |

## 移位指令

| 指令 | 格式 | 描述 | 操作 |
|------|------|------|------|
| SLL  | SLL Rd, Rs1, Rs2 | 逻辑左移 | Rd = Rs1 << Rs2[4:0] |
| SLLI | SLLI Rd, Rs1, imm | 逻辑左移立即数 | Rd = Rs1 << imm[4:0] |
| SRL  | SRL Rd, Rs1, Rs2 | 逻辑右移 | Rd = Rs1 >> Rs2[4:0] |
| SRLI | SRLI Rd, Rs1, imm | 逻辑右移立即数 | Rd = Rs1 >> imm[4:0] |
| SRA  | SRA Rd, Rs1, Rs2 | 算术右移 | Rd = Rs1 >>> Rs2[4:0] |
| SRAI | SRAI Rd, Rs1, imm | 算术右移立即数 | Rd = Rs1 >>> imm[4:0] |

## 控制流指令

### 分支指令

| 指令 | 格式 | 描述 | 操作 |
|------|------|------|------|
| BEQ  | BEQ Rs1, Rs2, offset | 相等时分支 | if (Rs1 == Rs2) PC = PC + offset |
| BNE  | BNE Rs1, Rs2, offset | 不等时分支 | if (Rs1 != Rs2) PC = PC + offset |
| BLT  | BLT Rs1, Rs2, offset | 小于时分支 | if (Rs1 < Rs2) PC = PC + offset |
| BGE  | BGE Rs1, Rs2, offset | 大于等于时分支 | if (Rs1 >= Rs2) PC = PC + offset |
| BLTU | BLTU Rs1, Rs2, offset | 无符号小于时分支 | if (Rs1 <u Rs2) PC = PC + offset |
| BGEU | BGEU Rs1, Rs2, offset | 无符号大于等于时分支 | if (Rs1 >=u Rs2) PC = PC + offset |

### 跳转指令

| 指令 | 格式 | 描述 | 操作 |
|------|------|------|------|
| J    | J offset | 无条件跳转 | PC = PC + offset |
| JR   | JR Rs1 | 寄存器跳转 | PC = Rs1 |
| JAL  | JAL Rd, offset | 跳转并链接 | Rd = PC + 4; PC = PC + offset |
| JALR | JALR Rd, Rs1 | 寄存器跳转并链接 | Rd = PC + 4; PC = Rs1 |

## 系统指令

| 指令 | 格式 | 描述 | 操作 |
|------|------|------|------|
| SYS  | SYS imm | 系统调用 | 触发系统调用异常 |
| BREAK| BREAK | 断点 | 触发断点异常 |
| NOP  | NOP | 空操作 | 无操作 |
| HALT | HALT | 停机 | 处理器停止执行 |

## 条件执行指令

| 指令 | 格式 | 描述 | 操作 |
|------|------|------|------|
| MOVEQ | MOVEQ Rd, Rs1 | 相等时移动 | if (Z == 1) Rd = Rs1 |
| MOVNE | MOVNE Rd, Rs1 | 不等时移动 | if (Z == 0) Rd = Rs1 |
| MOVLT | MOVLT Rd, Rs1 | 小于时移动 | if (N != V) Rd = Rs1 |
| MOVGE | MOVGE Rd, Rs1 | 大于等于时移动 | if (N == V) Rd = Rs1 |

## 指令编码示例

以下是一些常见指令的二进制编码示例：

### ADD 指令（R 型）

```
操作码   Rs1    Rs2    Rd    功能码   保留位
000000  00001  00010  00011  000001  00000
  6位    5位    5位    5位     6位     5位
```

这表示 `ADD R3, R1, R2`（R3 = R1 + R2）。

### ADDI 指令（I 型）

```
操作码   Rs1    Rd           立即数
000001  00001  00011      0000000000001010
  6位    5位    5位            16位
```

这表示 `ADDI R3, R1, 10`（R3 = R1 + 10）。

### BEQ 指令（B 型）

```
操作码   Rs1    Rs2           偏移量
000100  00001  00010      0000000000000100
  6位    5位    5位            16位
```

这表示 `BEQ R1, R2, 4`（如果 R1 == R2，则 PC = PC + 4）。

### JAL 指令（J 型）

```
操作码   Rd                 跳转偏移量
001000  00001        000000000000000001000
  6位    5位                   21位
```

这表示 `JAL R1, 8`（R1 = PC + 4; PC = PC + 8）。 