---
name: apple-motion-design
description: "Apple WWDC design philosophy: fluid gesture tracking, spatial depth hierarchy, haptic timing, and natural mass-spring mechanics."
---

# Apple Motion Design (`/apple-motion-design`)

Стандарт дизайна и кинематики Apple (WWDC HIG).

## Инварианты:
1. **Fluid Gestures:** Анимация никогда не блокирует пользователя. Любой жест можно прервать в любой миллисекунде (interruptible animations).
2. **Spatial Hierarchy:** Элементы возникают из точки клика (origin-point expansion) и возвращаются обратно.
3. **Spring Mechanics:** Использование `spring(response: 0.35, dampingRatio: 0.86)` для максимально естественного отклика.
