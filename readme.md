# 6502 LUT Multiplication

This was a method discovered during a code analysis project. This would work in any 6502 app that needs 8 bit * 8 bit multiplication to get a 16 bit result.

## What it's doing

Using a LUT, the routine is effectively doing steps which translate into:

```c
int multiplyTwo8BitNumbers (n1 int, n2 int) {
  int oddFix = n1 & n2 & 1; //Will correct for 2 odd numbers
  int val1 = (n1*n1) / 2;
  int val2 = (n2*n2) / 2;
  int val3 = ((n1-n2)*(n1-n2)) / 2;
  return oddFix + val1 + val2 - val3;
}
```
