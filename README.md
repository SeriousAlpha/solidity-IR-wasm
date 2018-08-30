# solidity-IR-wasm


使用wasm编译成C

Tutorial: .wat -> .wasm -> .c
Let's look at a simple example of a factorial function.
```
(func (export "fac") (param $x i32) (result i32)
  (if (result i32) (i32.eq (get_local $x) (i32.const 0))
    (then (i32.const 1))
    (else
      (i32.mul (get_local $x) (call 0 (i32.sub (get_local $x) (i32.const 1))))
    )
  )
)
```

Save this to **fac.wat**. We can convert this to a .wasm file by using the wat2wasm tool:

**$ wat2wasm fac.wat -o fac.wasm**

We can then convert it to a C source and header by using the wasm2c tool:

**$ wasm2c fac.wasm -o fac.c**

This generates two files, fac.c and fac.h. We'll take a closer look at these files below, but first let's show a simple example of how to use these files.
