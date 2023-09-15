<center>异常</center>

当涉及到Java编程中的异常时，通常可以将异常分为两类：运行时异常（Runtime Exceptions）和非运行时异常

ConstraintViolationException

1. 运行时异常： 运行时异常是指那些继承自`RuntimeException`类的异常，它们在代码中通常不需要被显式地捕获或声明。这些异常通常是由程序的逻辑错误引起的，比如空指针异常（NullPointerException）、数组索引越界异常（ArrayIndexOutOfBoundsException）等。由于这些异常是在运行时才会被抛出，编译器不会强制要求你在代码中处理它们。
2. 非运行时异常： 非运行时异常是指继承自`Exception`类但不是`RuntimeException`的异常，它们在代码中需要被显式地捕获或声明。这些异常通常是由外部因素引起的，比如文件不存在异常（FileNotFoundException）、输入输出异常（IOException）等。因为这些异常可能在代码中产生，编译器会强制要求你在代码中使用`try-catch`块或者在方法签名中使用`throws`声明来处理这些异常。

总结：

- 运行时异常是由程序逻辑错误引起的，不需要强制处理

- 非运行时异常通常是由外部因素引起的，需要在代码中进行处理

  