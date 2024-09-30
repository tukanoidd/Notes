# Registry
```rust
struct Registry {
	map: HashMap<Uuid, Module*>
}
```
## Deps
1. [[#Module]] 

# TModule
```rust
trait TModule {
	type Config: TModuleConfig*;
	type InitReq;
	type InitOutput;
	type RefreshReq;
	type RefreshOutput;

	fn new(config: Self::Config) -> miette::Result<Arc<Mutex<Self>>> {
		Self::new_impl(config).tokio_mutex().arc()
	}
	
	fn new_impl(config: Self::Config) -> miette::Result<Self>;
	
	async fn init(module: Arc<Mutex<Self>>, req: Self::InitReq) 
		-> miette::Result<Self::InitOutput>;

	async fn refresh(module: Arc<Mutex<Self>>, req: Self::RefreshReq) 
		-> miette::Result<Self::RefreshOutput>;
}
```
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
