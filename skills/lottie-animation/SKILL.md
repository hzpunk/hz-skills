---
name: lottie-animation
description: "Vector Lottie animation integration: lightweight JSON playback, frame scrubbing tied to scroll position, and zero-runtime overhead."
---

# Lottie Animation (`/lottie-animation`)

Интеграция векторных анимаций Lottie (JSON). Идеально для легких интерактивных иллюстраций и скролл-скраббинга.

## Использование с GSAP ScrollTrigger:
```typescript
import lottie from 'lottie-web';
import { gsap } from 'gsap';
import { ScrollTrigger } from 'gsap/ScrollTrigger';

export function createScrollBoundLottie(container: HTMLElement, path: string) {
  const anim = lottie.loadAnimation({
    container,
    renderer: 'svg',
    loop: false,
    autoplay: false,
    path,
  });

  anim.addEventListener('DOMLoaded', () => {
    ScrollTrigger.create({
      trigger: container,
      start: 'top center',
      end: 'bottom center',
      scrub: true,
      onUpdate: (self) => {
        const frame = self.progress * (anim.totalFrames - 1);
        anim.goToAndStop(frame, true);
      },
    });
  });
}
```
