```rust
#[derive(Serialize, Deserialize)]
struct ModuleDriverConfig<MDC> where MDC: TModuleDriverConfig {
	...,
	#[serde(flatten)]
	module_config: MDC,
}
```
# Links
1. MDC -> [[TModuleDriverConfig]]