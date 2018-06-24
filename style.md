# Overview
* K & R
* UTF-8 encoding
* UNIX line ending
* Tab to 4 spaces
* Trailing whitespace

# C++
```cpp
// game_app.h

#ifndef GAME_APP_H_
#define GAME_APP_H_

#include "game_world.h"
#include <memory>

class GameApp {
  public:
    void Init() {
        m_GameWorld = std::make_shared<GameWorld>();
        m_GameWorld->Init();
    }

    void Shutdown() {
        m_GameWorld->Shutdown();
    }

  privte:
    std::shared_prt<GameWorld> m_GameWorld;
};

#endif
```

# C#
```csharp
// GameApp.cs

public class GameApp {
    GameWorld m_GameWorld;

    public void Init() {
        m_GameWorld = new GameWorld();
        m_GameWorld.Init();
    }

    public void Shutdown() {
        m_GameWorld.Shutdown();
    }
}
```

# Lua
```lua
-- GameApp.lua

local GameApp = {}

function GameApp.Init()
    local world = World.New()
    world.Init()
    GameApp.world = world
end

function GameApp.Shutdown()
    GameApp.world.Shutdown()
end

return GameApp
```

# Swift
```swift
// GameApp.swift

class GameApp {
    var m_World: World

    func Init() {
        m_World = World()
        m_World.Init()
    }

    func Shutdown() {
        m_World.Shutdown()
    }
}
```

# Go
```go
// game_app.go

package main

type GameApp struct {
    world World
}

func (g GameApp) Init() {
    g.world := World()
    g.world.Init()
}

func (g GameApp) Shutdown() {
    g.world.Shutdown()
}
```
