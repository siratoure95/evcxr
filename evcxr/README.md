# Evcxr library

[![Latest Version](https://img.shields.io/crates/v/evcxr.svg)](https://crates.io/crates/evcxr)

An implementation of eval() for Rust.

The main struct in this crate is ```EvalContext```. You create one, then ask it
to eval bits of code. Any defined functions, variables etc are local to that
context.

```rust
let mut context = EvalContext::new();
context.eval("let s = String::new();")?;
context.eval(r#"s.push_str("Hello ");"#)?;
context.eval(r#"s.push_str("World");"#)?;
context.eval(r#"println!("{}", s);"#)?;
```

You must call ```evcxr::runtime_hook()``` at the top of main, otherwise the
library becomes a fork-bomb.

I'll not go into too much detail here, since the purpose of this library is
really to provide functionality to evcxr\_jupyter and evcxr\_repl. If you'd like
to try using this crate for something else, drop me an email, or file an issue
on the repository and we can figure out your use case.

## MSRV

See .github/workflows/ci.yml for the current minimum supported rust version.
Generally rare that we support much older versions than the latest stable, since
- mostly because our upstream dependencies make use of new rust features pretty
quickly after they stabalize.

## How it works

See [how it works](HOW_IT_WORKS.md)

## Release notes

See [release notes](RELEASE_NOTES.md)
