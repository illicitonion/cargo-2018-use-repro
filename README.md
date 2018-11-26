```
$ git clone https://github.com/illicitonion/cargo-2018-use-repro.git
$ rustc +nightly --version
rustc 1.32.0-nightly (6acbb5b65 2018-11-25)
$ cargo +nightly --version
cargo 1.32.0-nightly (b3d0b2e54 2018-11-15)
$ RUST_BACKTRACE=1 cargo +nightly build --verbose
       Fresh indexmap v1.0.2
   Compiling rust-use-repro v0.0.1 (/home/dwh/tmp/rustplay)
     Running `rustc --edition=2018 --crate-name rust_use_repro src/main.rs --color always --crate-type bin --emit=dep-info,link -C debuginfo=2 -C metadata=0e6cedb7e581324a -C extra-filename=-0e6cedb7e581324a --out-dir /home/dwh/tmp/rustplay/target/debug/deps -C incremental=/home/dwh/tmp/rustplay/target/debug/incremental -L dependency=/home/dwh/tmp/rustplay/target/debug/deps --extern indexmap=/home/dwh/tmp/rustplay/target/debug/deps/libindexmap-4f9d100201616fe2.rlib`
thread 'main' panicked at 'src/librustc_resolve/lib.rs:3027: unexpected definition for an identifier in pattern: Mod(DefId(8/0:0))', src/librustc/util/bug.rs:47:26
stack backtrace:
   0: std::sys::unix::backtrace::tracing::imp::unwind_backtrace
             at src/libstd/sys/unix/backtrace/tracing/gcc_s.rs:49
   1: std::sys_common::backtrace::_print
             at src/libstd/sys_common/backtrace.rs:71
   2: std::panicking::default_hook::{{closure}}
             at src/libstd/sys_common/backtrace.rs:59
             at src/libstd/panicking.rs:211
   3: std::panicking::default_hook
             at src/libstd/panicking.rs:227
   4: rustc::util::common::panic_hook
   5: std::panicking::rust_panic_with_hook
             at src/libstd/panicking.rs:480
   6: std::panicking::begin_panic
   7: rustc::util::bug::opt_span_bug_fmt::{{closure}}
   8: rustc::ty::context::tls::with_opt::{{closure}}
   9: rustc::ty::context::tls::with_context_opt
  10: rustc::ty::context::tls::with_opt
  11: rustc::util::bug::opt_span_bug_fmt
  12: rustc::util::bug::span_bug_fmt
  13: syntax::ast::Pat::walk
  14: <rustc_resolve::Resolver<'a, 'cl> as syntax::visit::Visitor<'tcx>>::visit_local
  15: <rustc_resolve::Resolver<'a, 'cl> as syntax::visit::Visitor<'tcx>>::visit_block
  16: <rustc_resolve::Resolver<'a, 'cl> as syntax::visit::Visitor<'tcx>>::visit_fn
  17: syntax::visit::walk_item
  18: rustc_resolve::Resolver::resolve_item
  19: rustc_resolve::Resolver::resolve_crate
  20: rustc::util::common::time
  21: rustc_driver::driver::phase_2_configure_and_expand
  22: rustc_driver::driver::compile_input
  23: rustc_driver::run_compiler_with_pool
  24: <scoped_tls::ScopedKey<T>>::set
  25: rustc_driver::run_compiler
  26: syntax::with_globals
  27: __rust_maybe_catch_panic
             at src/libpanic_unwind/lib.rs:102
  28: rustc_driver::run
  29: rustc_driver::main
  30: std::rt::lang_start::{{closure}}
  31: std::panicking::try::do_call
             at src/libstd/rt.rs:59
             at src/libstd/panicking.rs:310
  32: __rust_maybe_catch_panic
             at src/libpanic_unwind/lib.rs:102
  33: std::rt::lang_start_internal
             at src/libstd/panicking.rs:289
             at src/libstd/panic.rs:398
             at src/libstd/rt.rs:58
  34: main
  35: __libc_start_main
  36: <unknown>
query stack during panic:
end of query stack

error: internal compiler error: unexpected panic

note: the compiler unexpectedly panicked. this is a bug.

note: we would appreciate a bug report: https://github.com/rust-lang/rust/blob/master/CONTRIBUTING.md#bug-reports

note: rustc 1.32.0-nightly (6acbb5b65 2018-11-25) running on x86_64-unknown-linux-gnu

note: compiler flags: -C debuginfo=2 -C incremental --crate-type bin

note: some of the compiler flags provided by cargo are hidden

error: Could not compile `rust-use-repro`.

Caused by:
  process didn't exit successfully: `rustc --edition=2018 --crate-name rust_use_repro src/main.rs --color always --crate-type bin --emit=dep-info,link -C debuginfo=2 -C metadata=0e6cedb7e581324a -C extra-filename=-0e6cedb7e581324a --out-dir /home/dwh/tmp/rustplay/target/debug/deps -C incremental=/home/dwh/tmp/rustplay/target/debug/incremental -L dependency=/home/dwh/tmp/rustplay/target/debug/deps --extern indexmap=/home/dwh/tmp/rustplay/target/debug/deps/libindexmap-4f9d100201616fe2.rlib` (exit code: 101)
$ rustc +beta --version
rustc 1.31.0-beta.17 (1a4f1f398 2018-11-25)
$ cargo +beta --version
cargo 1.31.0-beta (339d9f9c8 2018-11-16)
$ RUST_BACKTRACE=1 cargo +beta build --verbose
       Fresh indexmap v1.0.2
   Compiling rust-use-repro v0.0.1 (/home/dwh/tmp/rustplay)
     Running `rustc --edition=2018 --crate-name rust_use_repro src/main.rs --color never --crate-type bin --emit=dep-info,link -C debuginfo=2 -C metadata=1a2648f79db53d47 -C extra-filename=-1a2648f79db53d47 --out-dir /home/dwh/tmp/rustplay/target/debug/deps -C incremental=/home/dwh/tmp/rustplay/target/debug/incremental -L dependency=/home/dwh/tmp/rustplay/target/debug/deps --extern indexmap=/home/dwh/tmp/rustplay/target/debug/deps/libindexmap-c878d9476bc933e5.rlib`
thread 'main' panicked at 'librustc_resolve/lib.rs:3032: unexpected definition for an identifier in pattern: Mod(DefId(10/0:0))', librustc/util/bug.rs:47:26
stack backtrace:
   0: std::sys::unix::backtrace::tracing::imp::unwind_backtrace
             at libstd/sys/unix/backtrace/tracing/gcc_s.rs:49
   1: std::sys_common::backtrace::print
             at libstd/sys_common/backtrace.rs:71
             at libstd/sys_common/backtrace.rs:59
   2: std::panicking::default_hook::{{closure}}
             at libstd/panicking.rs:211
   3: std::panicking::default_hook
             at libstd/panicking.rs:227
   4: rustc::util::common::panic_hook
   5: std::panicking::rust_panic_with_hook
             at libstd/panicking.rs:480
   6: std::panicking::begin_panic
   7: rustc::util::bug::opt_span_bug_fmt::{{closure}}
   8: rustc::ty::context::tls::with_opt::{{closure}}
   9: rustc::ty::context::tls::with_context_opt
  10: rustc::ty::context::tls::with_opt
  11: rustc::util::bug::opt_span_bug_fmt
  12: rustc::util::bug::span_bug_fmt
  13: syntax::ast::Pat::walk
  14: <rustc_resolve::Resolver<'a, 'cl> as syntax::visit::Visitor<'tcx>>::visit_local
  15: <rustc_resolve::Resolver<'a, 'cl> as syntax::visit::Visitor<'tcx>>::visit_block
  16: <rustc_resolve::Resolver<'a, 'cl> as syntax::visit::Visitor<'tcx>>::visit_fn
  17: syntax::visit::walk_item
  18: rustc_resolve::Resolver::resolve_item
  19: rustc_resolve::Resolver::resolve_crate
  20: rustc::util::common::time
  21: rustc_driver::driver::phase_2_configure_and_expand
  22: rustc_driver::driver::compile_input
  23: rustc_driver::run_compiler_with_pool
  24: rustc_driver::driver::spawn_thread_pool
  25: rustc_driver::run_compiler
  26: <scoped_tls::ScopedKey<T>>::set
  27: <std::panic::AssertUnwindSafe<F> as core::ops::function::FnOnce<()>>::call_once
  28: __rust_maybe_catch_panic
             at libpanic_unwind/lib.rs:102
  29: rustc_driver::run
  30: rustc_driver::main
  31: std::rt::lang_start::{{closure}}
  32: std::panicking::try::do_call
             at libstd/rt.rs:59
             at libstd/panicking.rs:310
  33: __rust_maybe_catch_panic
             at libpanic_unwind/lib.rs:102
  34: std::rt::lang_start_internal
             at libstd/panicking.rs:289
             at libstd/panic.rs:392
             at libstd/rt.rs:58
  35: main
  36: __libc_start_main
  37: <unknown>
query stack during panic:
end of query stack

error: internal compiler error: unexpected panic

note: the compiler unexpectedly panicked. this is a bug.

note: we would appreciate a bug report: https://github.com/rust-lang/rust/blob/master/CONTRIBUTING.md#bug-reports

note: rustc 1.31.0-beta.17 (1a4f1f398 2018-11-25) running on x86_64-unknown-linux-gnu

note: compiler flags: -C debuginfo=2 -C incremental --crate-type bin

note: some of the compiler flags provided by cargo are hidden

error: Could not compile `rust-use-repro`.

Caused by:
  process didn't exit successfully: `rustc --edition=2018 --crate-name rust_use_repro src/main.rs --color never --crate-type bin --emit=dep-info,link -C debuginfo=2 -C metadata=1a2648f79db53d47 -C extra-filename=-1a2648f79db53d47 --out-dir /home/dwh/tmp/rustplay/target/debug/deps -C incremental=/home/dwh/tmp/rustplay/target/debug/incremental -L dependency=/home/dwh/tmp/rustplay/target/debug/deps --extern indexmap=/home/dwh/tmp/rustplay/target/debug/deps/libindexmap-c878d9476bc933e5.rlib` (exit code: 101)
```
