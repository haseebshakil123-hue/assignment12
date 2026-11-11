| Location | Problem | Evidence / command | Proposed decision | Reason |
|---|---|---|---|---|
| Index 5 | Missing `price` | `df.isna().sum()` and `df.loc[5]` | Flag; retain missing value | No source evidence gives the correct price. Do not invent or impute it. |
| Index 17 | Price stored as `1,250` text | Inspect raw price values; numeric conversion with comma removal | Correct representation only; retain value as 1250 and flag for review | The comma appears to be a thousands separator. Conversion changes representation, not the numeric amount. Because 1250 is far above most values, it should still be investigated. |
| Index 30 | Price `9999` | Numeric `describe()` and row inspection | Flag / investigate; do not delete automatically | It is an extreme value, but an unusual value is not automatically an error. Source confirmation is needed. |
| Index 40 | Item label `oil b` | `df['item'].value_counts()` and row inspection | Flag / investigate; retain original label | It may be a casing typo, but the price and same-date records make the correct product identity uncertain. |
| Index 96 | Exact duplicate of index 8 | `df.duplicated(keep=False)` | Exclude one copy after confirming exact equality | Both rows have the same values in all six columns. Keeping both would double-count one record. |
| All six columns | Initially `object` type | `df.info()` | Convert date and price to suitable types | Dates should be datetime values and prices should be numeric for analysis. Text category columns can remain strings/objects. |
