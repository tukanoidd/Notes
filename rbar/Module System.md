# Module
```rust
trait Module {
  type Config;
  type InitReq;
  type Init: TryInto<Self::State, Error = Report>;
  type State;

  fn id(&self) -> Uuid;
  fn new(config: Self::Config) -> miette::Result<Self>;
  async fn init(req: Self::InitReq) -> miette::Result<Self::Init>;
}

struct Noconfig;
struct NoInitReq;
struct NoInit;
struct NoState;
```

# Widget
```rust
trait ModuleWidget: Module {
  type Event: Into<AppMsg>;
  
  fn view(&self, state: Self::State) -> Element<'_, AppMsg, Theme, Rendered> {
    self.view_impl(state).into()
  }

  fn view_impl(&self, state: Self::State) -> impl Into<Element<'_.  AppMsg, Theme, Render>>;
  fn update(&mut self, state: &mut Self::State) -> Option<ModuleEvent>;
}

trait ModuleEvent {
  fn id(&self) -> Uuid;
}

enum EModuleEvent {
  Name(NameModuleEvent), 
  ... 
}

enum EModule {
  Name(NameModule), 
  ... 
}
```

# Group
```rust
struct ModuleGroup {
  modules: Vec<EModule>
}

struct ModuleRows {
  left: ModuleGroup, 
  center: ModuleGroup, 
  right: ModuleGroup
}
```