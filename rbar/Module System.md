# Registry
```rust
struct Registry {
	map: HashMap<Uuid, Module*>
}
```
\* [[#Enum|Module]]

# Module
## Trait
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
\* [[#Confg|TModuleConfig]]
## Enum
```rust
enum Module {
	Name(ModuleType),
	...
}
```

## Config
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

trait TModuleConfig: Serialize + Deserialize {}
```

## Widget
### Trait
```rust
trait TModuleWidget {
	type Module: TModule*;
	type Config: TModuleWidgetConfig*;
}
```
\* [[#Trait|TModule]]
\** [[#|TModuleWidgetConfig]]
### Enum 
```rust
enum ModuleWidget {
	Name(ModuleWidgetType),
	...
}
```
### Config
```rust
trait TModuleWidgetConfig: Serialize + Deserialize {}
```