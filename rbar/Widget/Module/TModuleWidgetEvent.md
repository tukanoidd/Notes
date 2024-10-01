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
# Links
1. #TModuleWidgetEvent_Driver -> [[TModuleDriver]]
2. input -> #TModuleDriver_RefreshOutput 

# Deps
1. [[TModuleDriver]]