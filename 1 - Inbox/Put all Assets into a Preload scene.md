---
created: 2024-04-11 2024-04-11T02:46:13+02:00
tags:
  - code/web
  - code/gamedev
---

We load all assets in a central **assets** loading scene, decoupling it from the other game logic.

```js
import Phaser from "Phaser";

export default class Preloader extends Phaser.Scene {
  constructor() {
    super("Preloader");
  }

  preload() {
    // here we load all assets
  }

  create() {
    // then we switch to our first scene
    this.scene.start("Start");
  }
}
```

---

[[Tutorials]]
