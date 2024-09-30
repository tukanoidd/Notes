```rust
trait TModuleWidgetEvent {
	type Driver: TModuleDriver;

	fn refresh(input: <Self::Driver as TModuleDriver>::RefreshOutput) -> Self;
}
```
# Deps
1. [[TModuleDriver]]