```rust
trait TModuleWidget {
	type Driver: TModuleDriver;
	type Event;

	fn input_order(&self) -> &[usize];
	fn output_order(&self) -> &[usize];

	fn inputs(&self) -> 
}
```