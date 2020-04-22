# 问题

1. 这里对于+，-为一目运算符的情况下，似乎需要考虑上下文，还是说在语法分析的时候考虑，而不在这里体现？
2. 对于三目运算符该如何写？

> 尝试自己去看文档来解决

```text
<DecimalNumber>::=/^-?(0|[1-9][0-9]*)(\.[0-9]*)?$/

<PrimaryExpression>::=<DecimalNumber>|
    "("<LogicalExpress>")"

<SignExpression>::=<PrimaryExpression>|
    "!"<PrimaryExpression>|
    "-"<PrimaryExpression>|
    "+"<PrimaryExpression>

<MultiplicativeExpression>::=<SignExpression>|
    <MultiplicativeExpression>"*"<SignExpression>
    <MultiplicativeExpression>"/"<SignExpression>

<AddtiveExpression>::=<MultiplicativeExpression>|
    <AddtiveExpression>"+"<MultiplicativeExpression>
    <AddtiveExpression>"-"<MultiplicativeExpression>

<LogicalExpress>::=<AddtiveExpression>|
    <LogicalExpress>"||"<AddtiveExpression>|
    <LogicalExpress>"&&"<AddtiveExpression>|
```
