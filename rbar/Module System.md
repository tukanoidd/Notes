# Registry

## Deps
1. [[#Module]] 

# TModule

## Deps
1. [[#TModuleConfig]]

# Module
```rust
enum Module {
	Name(ModuleType),
	...
}
```

# ModuleConfig
```rust
#[derive(Serialize, Deserialize)]
struct ModuleConfig {
	timeout_ms: u64,
	... (shared fields),
	#[serde(flatten)]
	module_config: MC,
	#[serde(flatten)]
	widget_config: WC,
}
```

# TModuleConfig
```rust
trait TModuleConfig: Serialize + Deserialize {}
```

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
