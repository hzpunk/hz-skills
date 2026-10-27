---
name: hz-scrollytelling
description: "Стандарт и реализация интерактивного скроллителлинга для премиальных веб-лендингов: Scrollytelling, Scroll-bound/Scrubbing (1:1 привязка к скроллу), Scroll-triggered (stagger), Image Sequences (Canvas 360/разборка как у Apple), Sticky-scroll (fixed pinned sections), многослойный Parallax, Reveal-эффекты (шторки/маски). Включает готовые паттерны GSAP + ScrollTrigger, CSS Scroll-driven animations и Lottie scrubbing."
---

# HZ Scrollytelling & Interactive Motion Guide

Этот навык устанавливает стандарты и готовые шаблоны для проектирования интерактивных, кинематографичных лендингов уровня Awwwards и Apple. 

---

## 1. Фундаментальные инварианты производительности (60/120 FPS)

1. **Композитинг только на GPU:**
   - Анимировать **строго** `transform: translate3d/scale/rotate` и `opacity`.
   - **Категорически запрещено** анимировать `top`, `left`, `width`, `height`, `margin`, `padding` — они вызывают перерасчет геометрии (Layout Reflow) и дергают FPS.
2. **Сглаживание скраббинга (Smooth Scrub):**
   - Для плавной кинематики колесика мыши всегда использовать задержку инерции: `scrub: 1` или `scrub: 1.5` в GSAP ScrollTrigger.
3. **Управление слоями (`will-change`):**
   - Навешивать `will-change: transform, opacity` на активные слои в момент входа во viewport и сбрасывать после завершения.
4. **Доступность (`prefers-reduced-motion`):**
   - Если у пользователя включен режим пониженной подвижности, скролл-анимации обязаны мгновенно принимать финальное состояние без блокировки контента:
   ```css
   @media (prefers-reduced-motion: reduce) {
     * {
       animation-duration: 0.01ms !important;
       transition-duration: 0.01ms !important;
       scroll-behavior: auto !important;
     }
   }
   ```
5. **Очистка ресурсов (Memory Leak Prevention):**
   - В React/Next.js компонентах всегда очищать триггеры через `gsap.context()` или `@gsap/react` `useGSAP()` с авто-ревертом (`ctx.revert()`).

---

## 2. Три типа управления и взаимодействия

### А. Скроллителлинг (Scrollytelling)
Интерактивный сторителлинг: прокрутка страницы плавно переключает смысловые сцены, графики, слои данных или угол обзора 3D-модели.
- **Архитектура:** Фиксированный презентационный вьюпорт (`height: 100vh; position: sticky; top: 0`) + вертикальная дорожка шагов со сценарными триггерами.

### Б. Таймлайн-анимация (Scroll-bound / Scrub-animation)
Анимация жестко привязана к движению колесика мыши:
- Крутим вниз — прогресс идет вперед (0.0 → 1.0).
- Крутим вверх — анимация откручивается назад (1.0 → 0.0).
- Скорость воспроизведения прямо пропорциональна скорости вращения колесика.

### В. Поэтапное появление (Scroll-triggered)
Элементы взлетают, меняют прозрачность или выстраиваются «лесенкой» (stagger) при входе в заданную зону экрана, после чего фиксируются.
- Запуск однократный (`once: true`), чтобы не раздражать пользователя при повторном скролле.

---

## 3. Четыре ключевых визуальных приема

### 1. Секвенция кадров (Image Sequence Canvas — эффект Apple)
Анимация на базе последовательности из 60–180 кадров (WebP / AVIF), отрисовываемых в HTML5 `<canvas>`.
- **Преимущество:** Плавный фотореалистичный 3D-обзор продукта со всех сторон без тяжелых 3D-файлов.
- **Правило памяти:** Не создавать 100 элементов `<img>`. Загружать изображения в буфер памяти и рисовать текущий фрейм через `ctx.drawImage` по формуле:
  `const frameIndex = Math.min(frameCount - 1, Math.floor(progress * frameCount));`

### 2. Пошаговая фиксация (Sticky-скролл / Fixed Pinned Sections)
Экран или объект (смартфон, ноутбук, диаграмма) прилипает к центру экрана (`pin: true`), пока скроллится лента шагов (Шаг 1 → Шаг 2 → Шаг 3), синхронно меняя подсветку, графику или внутренний экран.

### 3. Параллакс (Parallax Effect)
Разделение слоев по глубине (Z-depth) с разными коэффициентами смещения:
- Задний план (пейзаж / градиентные сферы): смещение на 15–25% скорости скролла.
- Средний план (основной контент): 100% (естественная скорость).
- Передний план (парящие бейджи, частицы, карточки): смещение на 130–160%.

### 4. Эффект раскрытия (Reveal Effect)
Смена экранов через «снятие шторки» или маску:
- Использование `clip-path: inset(0 0 0 0)` расширяющегося из центра или сверху вниз.
- Идеально для демонстрации «До / После» или перехода между контрастными секциями лендинга.

---

## 4. Эталонные реализации (Production Code)

### Рецепт 1: GSAP + ScrollTrigger (React / Next.js с хуком useGSAP)

```tsx
"use client";

import React, { useRef } from "react";
import gsap from "gsap";
import { ScrollTrigger } from "gsap/ScrollTrigger";
import { useGSAP } from "@gsap/react";

if (typeof window !== "undefined") {
  gsap.registerPlugin(ScrollTrigger);
}

export function PinnedScrollytellingSection() {
  const containerRef = useRef<HTMLDivElement>(null);
  const visualRef = useRef<HTMLDivElement>(null);

  useGSAP(
    () => {
      // 1. Фиксация центрального визуального блока
      ScrollTrigger.create({
        trigger: containerRef.current,
        start: "top top",
        end: "+=2000",
        pin: visualRef.current,
        pinSpacing: true,
        anticipatePin: 1,
      });

      // 2. Скраббинг переключения шагов и трансформации визуала
      const tl = gsap.timeline({
        scrollTrigger: {
          trigger: containerRef.current,
          start: "top top",
          end: "+=2000",
          scrub: 1, // Плавная инерция в 1 секунду
        },
      });

      tl.to(visualRef.current, { scale: 1.15, rotate: 5, ease: "none" })
        .to(visualRef.current, { borderRadius: "48px", ease: "none" }, 0.5)
        .to(visualRef.current, { scale: 1.0, rotate: 0, ease: "none" }, 1.0);
    },
    { scope: containerRef }
  );

  return (
    <div ref={containerRef} className="relative w-full bg-background min-h-screen">
      <div
        ref={visualRef}
        className="w-[90vw] max-w-4xl h-[60vh] mx-auto rounded-3xl bg-gradient-to-tr from-primary/20 via-card to-primary/10 border border-border shadow-2xl flex items-center justify-center p-8 will-change-transform"
      >
        <span className="text-2xl font-semibold text-foreground">Интерактивный Центр</span>
      </div>
      <div className="h-[2000px]" /> {/* Скролл-дорожка */}
    </div>
  );
}
```

---

### Рецепт 2: Высокопроизводительная секвенция на Canvas (Image Sequence Scrub)

```tsx
"use client";

import React, { useRef, useEffect } from "react";
import gsap from "gsap";
import { ScrollTrigger } from "gsap/ScrollTrigger";

gsap.registerPlugin(ScrollTrigger);

interface ImageSequenceProps {
  frameCount: number;
  frameUrlTemplate: (index: number) => string; // e.g. (i) => `/frames/frame_${String(i).padStart(4, "0")}.webp`
  width: number;
  height: number;
}

export function CanvasImageSequenceScrub({ frameCount, frameUrlTemplate, width, height }: ImageSequenceProps) {
  const canvasRef = useRef<HTMLCanvasElement>(null);
  const containerRef = useRef<HTMLDivElement>(null);

  useEffect(() => {
    const canvas = canvasRef.current;
    if (!canvas) return;
    const ctx = canvas.getContext("2d");
    if (!ctx) return;

    // Кэш предзагруженных изображений
    const images: HTMLImageElement[] = [];
    const airpods = { frame: 0 };

    for (let i = 0; i < frameCount; i++) {
      const img = new Image();
      img.src = frameUrlTemplate(i);
      images.push(img);
    }

    const render = () => {
      const img = images[airpods.frame];
      if (img && img.complete) {
        ctx.clearRect(0, 0, width, height);
        ctx.drawImage(img, 0, 0, width, height);
      }
    };

    images[0].onload = render;

    const trigger = ScrollTrigger.create({
      trigger: containerRef.current,
      start: "top top",
      end: "+=2500",
      pin: canvas,
      scrub: 0.5,
      onUpdate: (self) => {
        const frameIndex = Math.min(frameCount - 1, Math.floor(self.progress * (frameCount - 1)));
        if (airpods.frame !== frameIndex) {
          airpods.frame = frameIndex;
          render();
        }
      },
    });

    return () => {
      trigger.kill();
    };
  }, [frameCount, frameUrlTemplate, width, height]);

  return (
    <div ref={containerRef} className="relative w-full h-[3000px] bg-background">
      <canvas
        ref={canvasRef}
        width={width}
        height={height}
        className="mx-auto sticky top-10 max-w-full h-auto will-change-contents"
      />
    </div>
  );
}
```

---

### Рецепт 3: Современный нативный CSS Scroll-Driven Animations (Zero JS)

```css
/* Прогресс-бар чтения и параллакс без сторонних JS-библиотек */

@keyframes scaleProgress {
  from { transform: scaleX(0); }
  to { transform: scaleX(1); }
}

.scroll-progress-bar {
  position: fixed;
  top: 0;
  left: 0;
  height: 4px;
  width: 100%;
  background: var(--primary);
  transform-origin: left;
  animation: scaleProgress auto linear;
  animation-timeline: scroll();
}

/* Появление карточки при входе в область видимости */
@keyframes fadeInUpReveal {
  from {
    opacity: 0;
    transform: translateY(40px) scale(0.96);
  }
  to {
    opacity: 1;
    transform: translateY(0) scale(1);
  }
}

.reveal-card {
  animation: fadeInUpReveal auto ease-out both;
  animation-timeline: view();
  animation-range: entry 15% cover 40%;
}
```

---

### Рецепт 4: Скраббинг Lottie-анимации через ScrollTrigger

```tsx
import lottie, { AnimationItem } from "lottie-web";
import { useEffect, useRef } from "react";
import gsap from "gsap";
import { ScrollTrigger } from "gsap/ScrollTrigger";

gsap.registerPlugin(ScrollTrigger);

export function LottieScrollScrub({ animationData }: { animationData: any }) {
  const containerRef = useRef<HTMLDivElement>(null);

  useEffect(() => {
    if (!containerRef.current) return;

    const anim: AnimationItem = lottie.loadAnimation({
      container: containerRef.current,
      renderer: "svg",
      loop: false,
      autoplay: false,
      animationData,
    });

    anim.addEventListener("DOMLoaded", () => {
      ScrollTrigger.create({
        trigger: containerRef.current,
        start: "top center",
        end: "bottom center",
        scrub: 1,
        onUpdate: (self) => {
          const totalFrames = anim.totalFrames;
          anim.goToAndStop(self.progress * totalFrames, true);
        },
      });
    });

    return () => {
      anim.destroy();
      ScrollTrigger.getAll().forEach((t) => t.kill());
    };
  }, [animationData]);

  return <div ref={containerRef} className="w-64 h-64 mx-auto" />;
}
```

---

### Рецепт 5: Интерактивный 3D-просмотр на Babylon.js с привязкой к скроллу

```tsx
"use client";

import React, { useEffect, useRef } from "react";
import { Engine, Scene, ArcRotateCamera, Vector3, HemisphericLight, MeshBuilder } from "@babylonjs/core";
import gsap from "gsap";
import { ScrollTrigger } from "gsap/ScrollTrigger";

gsap.registerPlugin(ScrollTrigger);

export function Babylon3DScrollVisualizer() {
  const canvasRef = useRef<HTMLCanvasElement>(null);
  const containerRef = useRef<HTMLDivElement>(null);

  useEffect(() => {
    if (!canvasRef.current) return;

    const engine = new Engine(canvasRef.current, true, { preserveDrawingBuffer: true, stencil: true });
    const scene = new Scene(engine);
    scene.clearColor.set(0, 0, 0, 0); // Прозрачный фон под тему

    const camera = new ArcRotateCamera("camera", -Math.PI / 2, Math.PI / 2.5, 4, Vector3.Zero(), scene);
    camera.attachControl(canvasRef.current, false); // Управление скроллом, а не драгом

    const light = new HemisphericLight("light", new Vector3(0, 1, 0), scene);
    light.intensity = 0.9;

    // Замените на SceneLoader.ImportMeshAsync для загрузки GLTF/GLB модели
    const box = MeshBuilder.CreateBox("model", { size: 1.8 }, scene);

    engine.runRenderLoop(() => {
      scene.render();
    });

    const trigger = ScrollTrigger.create({
      trigger: containerRef.current,
      start: "top top",
      end: "+=2000",
      pin: canvasRef.current,
      scrub: 1,
      onUpdate: (self) => {
        // Поворот 3D-модели от прогресса скролла
        box.rotation.y = self.progress * Math.PI * 2;
        box.rotation.x = Math.sin(self.progress * Math.PI) * 0.5;
      },
    });

    const handleResize = () => engine.resize();
    window.addEventListener("resize", handleResize);

    return () => {
      window.removeEventListener("resize", handleResize);
      trigger.kill();
      scene.dispose();
      engine.dispose();
    };
  }, []);

  return (
    <div ref={containerRef} className="relative w-full h-[2500px]">
      <canvas ref={canvasRef} className="sticky top-10 mx-auto w-full max-w-3xl h-[60vh] outline-none" />
    </div>
  );
}
```

---

### Рецепт 6: Микро-награда при конверсии через mo.js (CTA Burst Effect)

```tsx
"use client";

import React, { useRef } from "react";
// @ts-ignore
import mojs from "@mojs/core";

export function ConversionBurstButton({ children, onClick }: { children: React.ReactNode; onClick?: () => void }) {
  const btnRef = useRef<HTMLButtonElement>(null);

  const handleClick = (e: React.MouseEvent<HTMLButtonElement>) => {
    const rect = e.currentTarget.getBoundingClientRect();
    const x = rect.left + rect.width / 2;
    const y = rect.top + rect.height / 2;

    const burst = new mojs.Burst({
      left: x,
      top: y,
      radius: { 20: 80 },
      count: 10,
      children: {
        shape: "circle",
        radius: { 6: 0 },
        fill: ["#3b82f6", "#10b981", "#f59e0b", "#ec4899"],
        duration: 800,
        easing: "cubic.out",
      },
    });

    burst.play();
    onClick?.();
  };

  return (
    <button
      ref={btnRef}
      onClick={handleClick}
      className="relative px-8 py-4 rounded-2xl bg-primary text-primary-foreground font-semibold shadow-lg hover:shadow-xl active:scale-95 transition-all duration-150"
    >
      {children}
    </button>
  );
}
```
