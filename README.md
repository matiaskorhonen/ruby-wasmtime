# Ruby Wasmtime

Proof of concept for [Wasmtime]() × [ruby.wasm]() integration.

## Notes

## `src/ruby-vfs.wasm`

Produced using `wasi-vfs`:

```sh
wasi-vfs pack ruby.wasm --mapdir /usr::./3_2-wasm32-unknown-wasi-full/usr -o ruby-vfs.wasm
```

See the [wasi.vfs](https://github.com/ruby/ruby.wasm#quick-example-how-to-package-your-ruby-application-as-a-wasi-application) example from the ruby.wasm README for detailed steps.

## Run a line of Ruby code:

```sh
cargo run -r -- -e "puts 'Ruby.wasm <3 Wasmtime'"
```