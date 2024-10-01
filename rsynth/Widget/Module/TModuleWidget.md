---
tags:
  - TModuleWidget_Driver
  - TModuleWidget_Event
---

```rust
trait TModuleWidget {
	type Driver: TModuleDriver;
	type Event;

	fn input_order(&self) -> &[usize];
	fn output_order(&self) -> &[usize];

	fn inputs(&self) -> &[<Self::Driver as TModuleDriver>::ProcessInput];
	fn outputs(&self) -> &[<Self::Driver as TModuleDriver>::ProcessOutput];
}
```
# Links
1. 