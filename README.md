# Simple gRPC Client and Server using Rust

### A simple project implementation grpc in Rust using [tonic](https://github.com/hyperium/tonic) and [prost](https://github.com/tokio-rs/prost), based on Let's Get Rusty [tutorial](https://www.youtube.com/watch?v=JkSa-qA2jnY).

* Project setup
  
  ```toml
  [package]
  name = "grpc-sample"
  version = "0.1.0"
  edition = "2021"
  
  # See more keys and their definitions at https://doc.rust-lang.org/cargo/reference/manifest.html
  
  [[bin]]
  name = "client"
  path = "src/client.rs"
  
  [[bin]]
  name = "server"
  path = "src/server.rs"
  
  [dependencies]
  tonic = "*"
  prost = "*"
  tokio = {version = "*", features = ["macros", "rt-multi-thread"]}
  
  [build-dependencies]
  tonic-build = "*"
  ```

* Tonic build automation
  
  ```rust
  fn main() -> Result<(), Box<dyn std::error::Error>> {
      tonic_build::compile_protos("proto/payments.proto")?;
      Ok(())
  }
  ```

* Execute server
  
  ```
   $ cargo run --bin server
  ```

* Execute client
  
  ```
  $ cargo run --bin client
  response Response { metadata: MetadataMap { headers: {"content-type": "application/grpc", "date": "Thu, 03 Nov 2022 13:27:53 GMT", "grpc-status": "0"} }, message: BtcPaymentResponse { successful: true, message: "Sent 22BTC to 654321" }, extensions: Extensions }
  ```
  
  








































