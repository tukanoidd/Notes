---
tags:
  - TModuleWidgetEvent_Driver
---
```rust
trait TModuleWidgetEvent {
	type Driver: TModuleDriver;

	fn refresh(input: (
		Arc<Mutex<Self>>, 
		<Self::Driver as TModuleDriver>::RefreshOutput
	)) -> Self;
}
```
# Deps
1. [[TModuleDriver]]