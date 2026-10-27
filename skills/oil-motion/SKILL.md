---
name: oil-motion
description: "Organic physics-based fluid motion, spring dampening, liquid UI transitions, and tactile drag-and-drop feedback."
---

# Oil Motion (`/oil-motion`)

Физика органического жидкого движения интерфейсов. Ликвидирует механическую сухость анимаций.

## Принципы:
- **Mass & Inertia:** У каждого объекта есть виртуальная масса — крупные модалки двигаются основательно, иконки — молниеносно.
- **Fluid Drag:** Перетаскиваемые элементы деформируются по направлению движения (`scaleX`/`scaleY` сжатие-растяжение).
