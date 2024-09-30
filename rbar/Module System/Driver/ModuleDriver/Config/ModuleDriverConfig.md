```rust
#[derive(Serialize, Deserialize)]
struct ModuleDriverConfig<MDC> where MDC: TModuleDriverConfig {
	timeout_ms: u64,
	...,
	#[serde(flatten)]
	module_config: MDC,
}
```
# Links
1. MDC -> [[TModuleDriverConfig]]