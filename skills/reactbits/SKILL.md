---
name: reactbits
description: "Production guide and implementation patterns for React Bits (https://reactbits.dev). 100+ animated, interactive React/Tailwind/Framer Motion components: kinetic typography (SplitText, BlurText, ShinyText, DecryptedText), physics cards (SpotlightCard, TiltedCard, Magnet), and animated backgrounds (Aurora, Particles, Hyperspeed). Mandatory for all frontend work to ensure high-craft, anti-slop UI."
metadata:
  author: hz-ecosystem
  version: "1.0.0"
  source: "https://reactbits.dev"
---

# React Bits (`reactbits.dev`) Component & Motion Encyclopedia

Комплексное руководство и производственные шаблоны для компонентов из библиотеки **React Bits** (`https://reactbits.dev`).

React Bits — это библиотека компонентов и анимаций для React, Tailwind CSS и Framer Motion/GSAP, созданная для превращения скучных плоских интерфейсов в тактильные, кинетические и живые продукты без нейрослопного ощущения.

---

## 1. Кинетическая типографика (Text Animations)

### `SplitText` (Побуквенное и пословное появление заголовков)
Разделяет заголовок на буквы или слова с эффектом пружины и настраиваемым сдвигом.
```tsx
'use client';
import { motion } from 'framer-motion';

interface SplitTextProps {
  text: string;
  className?: string;
  delay?: number;
  animationFrom?: { opacity: number; transform: string };
  animationTo?: { opacity: number; transform: string };
  easing?: string | number[];
  threshold?: number;
  rootMargin?: string;
  textAlign?: 'left' | 'right' | 'center' | 'justify' | 'initial' | 'inherit';
  onLetterAnimationComplete?: () => void;
}

export function SplitText({
  text,
  className = '',
  delay = 50,
  animationFrom = { opacity: 0, transform: 'translate3d(0,25px,0)' },
  animationTo = { opacity: 1, transform: 'translate3d(0,0,0)' },
  easing = [0.25, 0.1, 0.25, 1],
}: SplitTextProps) {
  const words = text.split(' ').map(word => word.split(''));

  return (
    <p className={`inline-block overflow-hidden ${className}`}>
      {words.map((word, wordIndex) => (
        <span key={wordIndex} className="inline-block whitespace-nowrap mr-[0.25em]">
          {word.map((char, charIndex) => {
            const index = words.slice(0, wordIndex).reduce((acc, w) => acc + w.length, 0) + charIndex;
            return (
              <motion.span
                key={charIndex}
                initial={animationFrom}
                whileInView={animationTo}
                viewport={{ once: true }}
                transition={{
                  duration: 0.5,
                  delay: (index * delay) / 1000,
                  ease: easing,
                }}
                className="inline-block will-change-transform"
              >
                {char}
              </motion.span>
            );
          })}
        </span>
      ))}
    </p>
  );
}
```

### `BlurText` (Эффект прогрессивного рассеивания резкости)
Текст плавно проявляется из оптического размытия (`blur(12px)`) с подъемом по вертикали.
```tsx
'use client';
import { motion } from 'framer-motion';

export function BlurText({
  text,
  delay = 0.04,
  className = '',
}: {
  text: string;
  delay?: number;
  className?: string;
}) {
  const words = text.split(' ');

  return (
    <span className={`inline-flex flex-wrap gap-x-2 ${className}`}>
      {words.map((word, i) => (
        <motion.span
          key={i}
          initial={{ filter: 'blur(12px)', opacity: 0, y: 16 }}
          whileInView={{ filter: 'blur(0px)', opacity: 1, y: 0 }}
          viewport={{ once: true }}
          transition={{
            duration: 0.6,
            delay: i * delay,
            ease: [0.16, 1, 0.3, 1],
          }}
          className="inline-block will-change-transform"
        >
          {word}
        </motion.span>
      ))}
    </span>
  );
}
```

### `ShinyText` (Световой луч по поверхности букв)
Бегущий световой градиент через `background-clip: text`.
```tsx
export function ShinyText({
  text,
  disabled = false,
  speed = 4,
  className = '',
}: {
  text: string;
  disabled?: boolean;
  speed?: number;
  className?: string;
}) {
  const animationDuration = `${speed}s`;

  return (
    <span
      className={`inline-block bg-clip-text text-transparent bg-gradient-to-r from-muted-foreground via-foreground to-muted-foreground bg-[length:200%_100%] ${
        !disabled ? 'animate-shiny-text' : ''
      } ${className}`}
      style={{
        animationDuration,
        backgroundImage: 'linear-gradient(120deg, rgba(255, 255, 255, 0.3) 0%, rgba(255, 255, 255, 1) 50%, rgba(255, 255, 255, 0.3) 100%)',
      }}
    >
      {text}
    </span>
  );
}

// В tailwind.config.js или CSS:
// @keyframes shiny-text {
//   0% { background-position: 100% 0; }
//   100% { background-position: -100% 0; }
// }
// .animate-shiny-text { animation: shiny-text 4s linear infinite; }
```

### `DecryptedText` (Хакерская матричная дешифровка)
Случайные символы из набора (`!@#$%^&*()_+~|}{[]:;?><,./`) перед фиксацией финального текста.

---

## 2. Физика поверхностей и карточки (Components & Cards)

### `SpotlightCard` (Световой луч за курсором мыши)
Мягкое освещение границ и фона карточки в реальном времени.
```tsx
'use client';
import React, { useRef, useState } from 'react';

export function SpotlightCard({
  children,
  className = '',
  spotlightColor = 'rgba(255, 255, 255, 0.08)',
}: {
  children: React.ReactNode;
  className?: string;
  spotlightColor?: string;
}) {
  const divRef = useRef<HTMLDivElement>(null);
  const [position, setPosition] = useState({ x: 0, y: 0 });
  const [opacity, setOpacity] = useState(0);

  const handleMouseMove = (e: React.MouseEvent<HTMLDivElement>) => {
    if (!divRef.current) return;
    const rect = divRef.current.getBoundingClientRect();
    setPosition({ x: e.clientX - rect.left, y: e.clientY - rect.top });
  };

  return (
    <div
      ref={divRef}
      onMouseMove={handleMouseMove}
      onMouseEnter={() => setOpacity(1)}
      onMouseLeave={() => setOpacity(0)}
      className={`relative overflow-hidden rounded-2xl border border-border bg-card p-6 transition-colors ${className}`}
    >
      <div
        className="pointer-events-none absolute -inset-px transition-opacity duration-300"
        style={{
          opacity,
          background: `radial-gradient(600px circle at ${position.x}px ${position.y}px, ${spotlightColor}, transparent 40%)`,
        }}
      />
      <div className="relative z-10">{children}</div>
    </div>
  );
}
```

### `TiltedCard` (3D перспектива с физикой наклона)
Реалистичный 3D-наклон с расчетом угла по положению курсора относительно центра.
```tsx
'use client';
import React, { useRef } from 'react';
import { motion, useMotionValue, useSpring, useTransform } from 'framer-motion';

export function TiltedCard({
  children,
  className = '',
  maxTilt = 15,
}: {
  children: React.ReactNode;
  className?: string;
  maxTilt?: number;
}) {
  const ref = useRef<HTMLDivElement>(null);
  const x = useMotionValue(0);
  const y = useMotionValue(0);

  const mouseXSpring = useSpring(x, { stiffness: 300, damping: 30 });
  const mouseYSpring = useSpring(y, { stiffness: 300, damping: 30 });

  const rotateX = useTransform(mouseYSpring, [-0.5, 0.5], [`${maxTilt}deg`, `-${maxTilt}deg`]);
  const rotateY = useTransform(mouseXSpring, [-0.5, 0.5], [`-${maxTilt}deg`, `${maxTilt}deg`]);

  const handleMouseMove = (e: React.MouseEvent<HTMLDivElement>) => {
    if (!ref.current) return;
    const rect = ref.current.getBoundingClientRect();
    const width = rect.width;
    const height = rect.height;
    const mouseX = e.clientX - rect.left;
    const mouseY = e.clientY - rect.top;
    x.set(mouseX / width - 0.5);
    y.set(mouseY / height - 0.5);
  };

  const handleMouseLeave = () => {
    x.set(0);
    y.set(0);
  };

  return (
    <motion.div
      ref={ref}
      onMouseMove={handleMouseMove}
      onMouseLeave={handleMouseLeave}
      style={{
        rotateY,
        rotateX,
        transformStyle: 'preserve-3d',
      }}
      className={`relative will-change-transform ${className}`}
    >
      <div style={{ transform: 'translateZ(20px)' }}>{children}</div>
    </motion.div>
  );
}
```

### `Magnet` (Магнитная кнопка с пружиной)
Кнопка притягивается к курсору при приближении и возвращается с инерцией.
```tsx
'use client';
import React, { useRef } from 'react';
import { motion, useMotionValue, useSpring } from 'framer-motion';

export function Magnet({
  children,
  padding = 60,
  magnetStrength = 0.35,
}: {
  children: React.ReactNode;
  padding?: number;
  magnetStrength?: number;
}) {
  const ref = useRef<HTMLDivElement>(null);
  const x = useMotionValue(0);
  const y = useMotionValue(0);

  const springConfig = { damping: 15, stiffness: 150, mass: 0.1 };
  const springX = useSpring(x, springConfig);
  const springY = useSpring(y, springConfig);

  const handleMouseMove = (e: React.MouseEvent) => {
    if (!ref.current) return;
    const { left, top, width, height } = ref.current.getBoundingClientRect();
    const centerX = left + width / 2;
    const centerY = top + height / 2;
    const dist = Math.hypot(e.clientX - centerX, e.clientY - centerY);

    if (dist < Math.max(width, height) + padding) {
      x.set((e.clientX - centerX) * magnetStrength);
      y.set((e.clientY - centerY) * magnetStrength);
    } else {
      x.set(0);
      y.set(0);
    }
  };

  const handleMouseLeave = () => {
    x.set(0);
    y.set(0);
  };

  return (
    <motion.div
      ref={ref}
      onMouseMove={handleMouseMove}
      onMouseLeave={handleMouseLeave}
      style={{ x: springX, y: springY }}
      className="inline-block will-change-transform"
    >
      {children}
    </motion.div>
  );
}
```

---

## 3. Живые фоны и текстуры (Backgrounds)

- **`Aurora`**: Мягкие колышущиеся градиентные полосы северного сияния на CSS/WebGL.
- **`Particles`**: Интерактивная сеть плавающих микро-частиц, реагирующая на курсор с отталкиванием.
- **`Noise`**: Полупрозрачная зернистая текстура (`mix-blend-mode: overlay`, `opacity: 0.035`) для устранения эффекта "компьютерного пластика" в темных темах.
- **`StarBorder`**: Бегущий неоновый луч по граням с закруглением (`stroke-dashoffset`).

---

## 4. Правила внедрения в HZ Ecosystem

1. **Никакого нейрослопа:** Запрещены примитивные плоские серые карточки без ховер-состояний.
2. **Семантика токенов темы:** Все цвета фона, границ и текста берутся строго из CSS переменных проекта (`bg-card`, `border-border`, `text-foreground`).
3. **Производительность:** Только аппаратные свойства (`transform`, `opacity`, `filter`). Никаких анимаций `width`, `height`, `margin`, `top`, `left`.
4. **WCAG & A11y:** Все движения оборачивать в проверку `@media (prefers-reduced-motion: reduce)`.
