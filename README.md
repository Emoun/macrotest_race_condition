
This repository exhibits a bug with the `macrotest` crate (v1.0.2).
If multiple tests run expansion tests (using `macrotest::expand_without_refresh`) they somehow interfere with each other and fail with the following error:

```
---- test_set_2 stdout ----
Running 1 macro expansion tests
Expansion error:
error: no bin target named `set_2`
        Did you mean `set_1`?
```

This error is spurious and might sometimes be the other way around (set_1 not found).

If you look at the `set_2` expansion, it should fail. This is to highlight a different error,
where if one test is failing, the diff message might be contaminated by other succeeding tests running at the same time.

