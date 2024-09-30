---
tags:
  - TModuleWidget_Driver
  - TModuleWidget_Config
  - TModuleWidget_Event
---
```rust
trait TModuleWidget {
	type Driver: TModuleDriver;
	type Config: TModuleWidgetConfig;
	type Event: TModuleWidgetEvent;
	
	fn new(config: ModuleWidgetConfig<Self::Config>) -> Self;
	fn view(&self, id: Uuid) -> Element<'_, Self::Event, Theme, Renderer>;
	fn update(&mut self, id: Uuid, event: Self::Evet, driver: Arc<Mutex<Self::Driver>>) 
		-> Option<AppMsg>;
}
```
# Links
1. #TModuleWidget_Driver -> [[TModuleDriver]]
2. #TModuleWidget_Config -> [[TModuleWidgetConfig]]
3. #TModuleWidget_Event -> [[TModuleWidgetEvent]]

# Deps
1. [[ModuleWidgetConfig]]