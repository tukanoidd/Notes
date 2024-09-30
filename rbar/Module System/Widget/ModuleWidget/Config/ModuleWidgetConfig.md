```rust
#[derive(Serialize, Deserialize)]
struct ModuleWidgetConfig<MWC> where MWC: TModuleWidgetConfig {
	borders: Option<Borders>,
	background_color: Option<Color>,
	...,
	#[serde(flatten)]
	widget_config: MWC,
}
```
# Links
1. MWC -> [[TModuleWidgetConfig]]