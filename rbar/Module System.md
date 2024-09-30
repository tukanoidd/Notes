
# ModuleConfig
```rust

```

# TModuleConfig


# TModuleWidget
```rust
trait TModuleWidget {
	type Module: TModule*;
	type Config: TModuleWidgetConfig*;
}
```
## Deps
1. [[#TModule]]
2. [[#TModuleWidgetConfig]]

# ModuleWidget 
```rust
enum ModuleWidget {
	Name(ModuleWidgetType),
	...
}
```

# TModuleWidgetConfig 
```rust
trait TModuleWidgetConfig: Serialize + Deserialize {}
```
