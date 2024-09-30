---
tags:
  - TModuleDriver_Config
  - TModuleDriver_InitReq
  - TModuleDriver_InitOutput
  - TModuleDriver_RefreshReq
  - TModuleDriver_RefreshOutput
---
```rust
trait TModuleDriver {
	type Config: TModuleDriverConfig;
	type InitReq;
	type InitOutput;
	type RefreshReq;
	type RefreshOutput;

	fn new(config: ModuleDriverConfig<Self::Config>) 
		-> miette::Result<Arc<Mutex<Self>>> 
	{
		Self::new_impl(config).tokio_mutex().arc()
	}
	
	fn new_impl(config: ModuleDriverConfig<Self::Config>) 
		-> miette::Result<Self>;
	
	async fn init(
		module: Arc<Mutex<Self>>, 
		req: Self::InitReq
	) -> miette::Result<Self::InitOutput>;

	async fn refresh(
		module: Arc<Mutex<Self>>, 
		req: Self::RefreshReq
	) -> miette::Result<(
		Arc<Mutex<Self>>, 
		Self::RefreshOutput
	)>;
}
```
# Links
1. #TModuleDriver_Config -> [[TModuleDriverConfig]]

# Deps
1. [[ModuleDriverConfig]]