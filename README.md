# Args

A C++11 API that makes it simple to parse command line arguments and assign them to C++ variables.

For example, to parse arguments for a Factorial program that takes one argument:
```
unsigned int n = (unsigned int)-1;
bcArgs args[] = {
    { n }
};
bcParseArgs(argc, argv, args);
if (n != (unsigned int)-1)
    PrintFactorial(n);
```

A program that performs a math operation on 2 or more numbers could be implemented with:
```
const char* operation;      // Must be "Add", "Sub", "Mul" or "Div"
double operand0;            // First operand (required)
double operand1;            // Second operand (required)
double operands[998];       // Additional operands (optional)
size_t operandsCount = 0;   // Number of additional operands assigned in `operands`

bcArg args[] = {
    { operation, bcArg::Required, "Operation to perform: Add, Sub, Mul or Div", "operation" },
    { operand0,  bcArg::Required, "First operand",                              "number"    },
    { operand1,  bcArg::Required, "Second operand",                             "number"    },
    { operands,  operandsCount,   "Additional operand",                         "number"    },
};

bcArgResult result = bcParseArgs(argc, argv, args);
if (result)
    PerformOperation(operation, operand0, operand1, operands, operandsCount);
```
