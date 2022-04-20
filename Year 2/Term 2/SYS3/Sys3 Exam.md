# Sys3 Open Assessment

## Part A

### (i)

| Hazard Type | 1st Instruction | 2nd Instruction |
| ----------- | --------------- | --------------- |
| RAW         | (1, 6, WB.3)      | (2, 5, RR.3)    |
| WAW         | (2, 8, WB.5)    | (3, 7, WB.5)    |
| WAW         | (4, 9, WB.2)    | (5, 8, WB.2)    |
| Structural  | (2, 8, WB.5)    | (5, 8, WB.2)    |
| Memory      | (2, 4, OF)      | (4, 4, IF)      |

### (ii)

| Hazard Type | 1st Instruction | 2nd Instruction | 3rd Instruction |
| ----------- | --------------- | --------------- | --------------- |
| Memory      | (1, 3, OF)      | (3, 3, IF)      |                 |
| Memory      | (2, 4, OF)      | (4, 4, IF)      |                 |
| Structural  | (1, 7, IALU)    | (3, 7, IALU)    | (4, 7, IALU)    |
| Structural  | (3, 8, WB.5)    | (4, 8, WB.2)                |                 |

- If a register reads and writes to the same register in the same cycle, is it a RAW / WAR?
	- (1, 5, RR.3)    (3, 5, WB.3)
- Which hazard???
- **simulate on practical**

### (iii)

| Hazard Type | 1st Instruction | 2nd Instruction | 3rd Instruction |
| ----------- | --------------- | --------------- | --------------- |
| Structural  | (2, 4, RR.3)    | (3, 4, RR.5)    | (4, 4, RR.7)    |
| Structural  | (1, 6, IALU)    | (2, 6, IALU)    | (4, 6, IALU)    |
| Structural  | (3, 6, FALU)    | (6, 6, FALU)    |                 |
| Structural  | (2, 8, WB.4)    | (6, 8, WB.12)   |                 |
| Memory      | (1, 7, DS)      | (2, 7, DF)      | (5, 7, OF)                |

- Is final memory hazard valid???


## Part B

### (i)


| Instr. |     |     |     |      |      |      |      |      |      |      |      |                     |
| ------ | --- | --- | --- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ------------------- |
| 1      | IF  | ID  | OF  | RR.2 | RR.3 | IALU | IALU | DS   |      |      |      |                     |
| 2      |     | IF  | ID  | OF   | ---  | WB.3 |      |      |      |      |      |                     |
| 3      |     |     | --- | ---  | IF   | ID   | RR.4 | IALU | IALU | WB.5 |      |                     |
| 4      |     |     |     | ---  | ---  | IF   | ID   | RR.2 | IALU | ---  | WB.2 |                     |
|        | 1   | 2   | 3   | 4    | 5    | 6    | 7    | 8    | 9    | 10   | 11   | $\leftarrow$ cycle |


### (ii)

| Instr. |     |     |     |      |      |      |      |      |      |      |      |                    |
| ------ | --- | --- | --- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ------------------ |
| 1      | IF  | ID  | OF  | RR.2 | RR.3 | IALU | IALU | DS   |      |      |      |                    |
| 2      |     | NOP |     |      |      |      |      |      |      |      |      |                    |
| 3      |     |     | NOP |      |      |      |      |      |      |      |      |                    |
| 4      |     |     |     | IF   | ID   | OF   | WB.3 |      |      |      |      |                    |
| 5      |     |     |     |      | IF   | ID   | RR.4 | IALU | IALU | WB.5 |      |                    |
| 6      |     |     |     |      |      | NOP  |      |      |      |      |      |                    |
| 7      |     |     |     |      |      |      | IF   | ID   | RR.2 | IALU | WB.2 |                    |
|        | 1   | 2   | 3   | 4    | 5    | 6    | 7    | 8    | 9    | 10   | 11   | $\leftarrow$ cycle |


### (iii)

