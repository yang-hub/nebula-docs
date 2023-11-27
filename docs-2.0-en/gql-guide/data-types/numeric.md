# Numeric types

GQL supports integer types and floating-point types. Integer types can be signed or unsigned, while floating-point types are always signed.

## Signed integer

Signed integer is either non-negative (positive or zero) or negative.

The following table lists the signed interger types and their value ranges.

| Type | Declared keywords | Range |
|-|-|-|
| INT64 | `INT64` | -9,223,372,036,854,775,808 ~ 9,223,372,036,854,775,807 |
| INT32 | `INT32` | -2,147,483,648 ~ 2,147,483,647 |
| INT16 | `INT16` | -32,768 ~ 32,767 |
| INT8 | `INT8` | -128 ~ 127 |
| INT | `INT` | ? |
| SMALLINT | `SMALLINT` | ? |
| BIGINT | `BIGINT` | ? |

implmentation-defined的类型，取值范围谁来提供？

## Unsigned integer

Unsigned integer is always non-negative.

The following table lists the unsigned interger types and their value ranges.

| Type | Declared keywords | Range |
|-|-|-|
| UINT64 | `UINT64` | 0 ~ 9,223,372,036,854,775,807 |
| UINT32 | `UINT32` | 0 ~ 2,147,483,647 |
| UINT16 | `UINT16` | 0 ~ 32,767 |
| UINT8 | `UINT8` | 0 ~ 127 |
| UINT | `UINT` | ? |
| USMALLINT | `USMALLINT` | ? |
| UBIGINT | `UBIGINT` | ? |

implmentation-defined的类型，取值范围谁来提供？

## Floating-point

Both single-precision floating-point format (FLOAT) and double-precision floating-point format (DOUBLE) are supported.
是否还区分单双精度的？

| Type | Declared keywords | Range | Precision |
|-|-|-|-|
| FLOAT32 | `FLOAT32` | 3.4E +/- 38 | 6~7 bits |
| FLOAT64 | `FLOAT64` | ? | ? |

implmentation-defined的类型，取值范围谁来提供？

Scientific notation is also supported, such as `1e2`, `1.1e2`, `.3e4`, `1.e4`, and `-1234E-10`.
为啥要提科学记数法？是否还支持？