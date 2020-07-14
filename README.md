# Args

A C++11 API that makes it simple to parse command line arguments and assign them to C++ variables.

For example, to parse the arguments for a Factorial program that takes one argument:
```
> Factorial.exe 5
5! = 120
```
could be implemented with:
```
unsigned int n = (unsigned int)-1;
bcArgs args[] = {
    { n }
};
bcParseArgs(argc, argv, args);
```

