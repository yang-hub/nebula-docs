# Numeric types

GQL supports integer types and floating-point types. Integer types can be signed or unsigned, while floating-point types are always signed.

问题：
- value range
  - out of range的行为？ To QA

## Signed integer

Signed integer is either non-negative (positive or zero) or negative.

The following table lists the signed interger types and their value ranges.

| Type | Declared keywords | Range |
|-|-|-|
| INT64 | `INT64`, `INT` | -9,223,372,036,854,775,808 ~ 9,223,372,036,854,775,807 |
| INT32 | `INT32` | -2,147,483,648 ~ 2,147,483,647 |
| INT16 | `INT16` | -32,768 ~ 32,767 |
| INT8 | `INT8` | -128 ~ 127 |


## Unsigned integer

Unsigned integer is always non-negative.

The following table lists the unsigned interger types and their value ranges.

| Type | Declared keywords | Range |
|-|-|-|
| UINT64 | `UINT64` | 0 ~ 18,446,744,073,709,551,615 |
| UINT32 | `UINT32` | 0 ~ 4,294,967,295 |
| UINT16 | `UINT16` | 0 ~ 65,535 |
| UINT8 | `UINT8` | 0 ~ 255 |
| UINT | `UINT` | ? |
| USMALLINT | `USMALLINT` | ? |
| UBIGINT | `UBIGINT` | ? |

## Floating-point

Both single-precision floating-point format (FLOAT) and double-precision floating-point format (DOUBLE) are supported.

| Type | Declared keywords | Range  |
|-|-|-|
| FLOAT32 | `FLOAT32`, `FLOAT` | 3.4E +/- 38 | 
| FLOAT64 | `FLOAT64`, `DOUBLE` | 1.7E +/- 308 |


Scientific notation is also supported, such as `1e2`, `1.1e2`, `.3e4`, `1.e4`, and `-1234E-10`.
是否支持科学记数法？ To QA