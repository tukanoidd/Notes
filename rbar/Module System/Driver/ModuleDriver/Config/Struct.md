```rust
#[derive(Serialize, Deserialize)]
struct ModuleDriverConfig where MC: TModuleDriverConfig {
	timeout_ms: u64,
	... (shared fields),
	#[serde(flatten)]
	module_config: MC,
}
```