```rust
trait TModuleDriver {
	type Config: ModuleDriverConfig*;
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