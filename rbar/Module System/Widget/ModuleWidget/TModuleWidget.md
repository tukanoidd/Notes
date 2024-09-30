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

	fn view(&self, id: Uuid) -> Element<'_, Self::Event, Theme, Renderer>;
	fn update(&mut self, id: Uuid, event: Self::Evet, driver: Arc<Mutex<Self::Driver>>) 
		-> Option<AppMsg>;
}
```
# Deps
1. [[TModuleDriver]]
2. [[TModuleWidgetConfig]]
3. [[TModuleWidgetEvent]]