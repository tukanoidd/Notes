---
tags:
  - TModuleWidgetEvent_Driver
---
```rust
trait TModuleWidgetEvent {
	type Driver: TModuleDriver;

	fn refresh(input: (
		Arc<Mutex<Self>>, 
		<Self::Driver as TModuleDriver>::ProcessOutput
	)) -> Self;
}
```
# Links
1. #TModuleWidgetEvent_Driver -> [[TModuleDriver]]
2. input -> #TModuleDriver_ProcessOutput  

# Deps
1. [[TModuleDriver]]