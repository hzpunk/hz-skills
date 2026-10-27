---
name: mojs-motion
description: "Declarative SVG motion graphics and burst physics using @mojs/core for conversion effects, micro-interactions, and geometric particle animations."
---

# Mo.js Motion (`/mojs-motion`)

Декларативная анимация SVG-графики, геометрических частиц и физических взрывов для конверсионных микро-взаимодействий.

## Когда использовать:
- Анимация успешной отправки формы (burst particles).
- Эффектные кнопки призыва к действию (CTA hover/click physics).
- Интерактивные SVG-иконки и фоновые геометрические паттерны.

## Пример взрыва при конверсии (React / TypeScript):
```typescript
import mojs from '@mojs/core';

export function triggerConversionBurst(x: number, y: number) {
  const burst = new mojs.Burst({
    left: x,
    top: y,
    radius: { 10: 80 },
    count: 12,
    children: {
      shape: ['circle', 'rect'],
      fill: ['#A23B0B', '#E28743', '#2563EB', '#10B981'],
      radius: { 6: 0 },
      duration: 800,
      easing: 'cubic.out',
    },
  });

  burst.play();
}
```
