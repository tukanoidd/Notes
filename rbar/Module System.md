# Registry
```rust
struct Registry {
	map: HashMap<Uuid, Module*>
}
```
[*]  [[#Module]]

# Module
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
}
```
[*]  [[#Module Config]]

# Module Config
```rust
#[derive(Serialize, Deserialize)]
struct ModuleConfig<MC, WC> where MC: TModuleConfig + TModuleWidgetConfig {
	timeout_ms: u64,
	... (shared fields),
	#[serde(flatten)]
	module_config: MC,
	#[serde(flatten)]
	widget_config: WC,
}

trait TModuleConfig: Serialize + Deserialize {}
trait TModuleWidgetConfig: Serialize + Deserialize {}
```