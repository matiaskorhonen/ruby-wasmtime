# Ruby Wasmtime

Proof of concept for [Wasmtime]() × [ruby.wasm]() integration.

## Notes

### `my-ruby-app.wasm`

Produced using `wasi-vfs` using these instructions ([cribbed from the ruby.wasm repo](https://github.com/ruby/ruby.wasm#quick-example-how-to-package-your-ruby-application-as-a-wasi-application)):

```sh
# Download a prebuilt Ruby release
$ curl -LO https://github.com/ruby/ruby.wasm/releases/latest/download/ruby-3_2-wasm32-unknown-wasi-full.tar.gz
$ tar xfz ruby-3_2-wasm32-unknown-wasi-full.tar.gz

# Extract ruby binary not to pack itself
$ mv 3_2-wasm32-unknown-wasi-full/usr/local/bin/ruby ruby.wasm

# Put your app code
$ mkdir src
$ echo "puts 'Hello'" > src/my_app.rb

# Pack the whole directory under /usr and your app dir
$ wasi-vfs pack ruby.wasm --mapdir /src::./src --mapdir /usr::./3_2-wasm32-unknown-wasi-full/usr -o my-ruby-app.wasm
```

### Run the embedded Ruby script

```sh
cargo run -r
```
