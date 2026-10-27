---
name: babylonjs-3d
description: "Production 3D WebGL/WebGPU interactive scenes: PBR materials, ArcRotateCamera, GLTF/GLB loading, and scroll-bound 3D product viewports."
---

# Babylon.js 3D (`/babylonjs-3d`)

Стандарт интерактивной 3D-графики WebGL и WebGPU для продуктовых витрин, scrollytelling-лендингов и презентаций.

## Преимущества перед Three.js:
- Встроенный PBR (Physically Based Rendering) из коробки.
- Полная поддержка WebGPU без костылей.
- Встроенные инспекторы сцены и оптимизация памяти при скролле.

## Базовый скролл-вьюпорт (TypeScript):
```typescript
import { Engine, Scene, ArcRotateCamera, Vector3, HemisphericLight, SceneLoader } from '@babylonjs/core';
import '@babylonjs/loaders/glTF';

export function init3DProductViewer(canvas: HTMLCanvasElement, modelUrl: string) {
  const engine = new Engine(canvas, true, { preserveDrawingBuffer: true, stencil: true });
  const scene = new Scene(engine);

  const camera = new ArcRotateCamera("camera", -Math.PI / 2, Math.PI / 2.5, 3, new Vector3(0, 0, 0), scene);
  camera.attachControl(canvas, true);

  new HemisphericLight("light", new Vector3(0, 1, 0), scene);

  SceneLoader.Append("", modelUrl, scene, () => {
    engine.runRenderLoop(() => scene.render());
  });

  window.addEventListener("resize", () => engine.resize());
  return { engine, scene, camera };
}
```
