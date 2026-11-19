---
name: creative-motion-components
description: "Master encyclopedia and implementation guide for high-end web components, creative layouts, and micro-interactions. Combines 21st.dev, React Bits, Superdesign.dev, UI-Layouts, Magic UI, Aceternity UI, Motion Primitives, HeroUI, and Bklit. Use when building award-winning landing pages, hero reveals, bento grids, glowing cards, magnetic controls, kinetic typography, and fluid interactive widgets."
metadata:
  author: hz-ecosystem
  version: "1.1.0"
---

# Creative Motion & Components Encyclopedia

Comprehensive guide and implementation blueprints for high-end creative web components, layout architectures, and interactive motion patterns.

---

## 1. 21st.dev & Design Engineering Registry (`21st.dev`)
- **Philosophy**: Open-source component registry for design engineers. Integrates directly with shadcn/ui and Tailwind tokens.
- **Key Primitives**:
  - `Shimmer Button`: Ambient glow with traveling gradient shimmer on interaction.
  - `Dynamic Island / Floating Bar`: Morphing navigation and context bar with liquid spring transitions.
  - `Animated Bento Grid`: Dynamic perspective layout with interactive micro-widgets.
  - `Border Beam`: Continuous moving particle beam tracing the curved border of containers.

---

## 2. React Bits (`reactbits.dev`)
- **Kinetic Text Animations**:
  - `SplitText`: Splits into character / word spans with staggered spring entrance (`staggerChildren: 0.03`).
  - `BlurText`: Transitions from `filter: blur(10px); opacity: 0; transform: translateY(20px)` to crisp typography.
  - `DecryptedText`: Random matrix hacker cipher scrambling before settling onto final characters.
  - `TrueFocus`: Subtle focus lens blur over surrounding text, highlighting the active word.
  - `ShinyText`: CSS background-clip gradient shimmering across text using `@keyframes shimmer`.
- **Interactive Cards & Physics**:
  - `SpotlightCard`: Mousemove-driven radial gradient overlay (`radial-gradient(circle at ${x}px ${y}px, rgba(255,255,255,0.08), transparent 80%)`).
  - `TiltedCard`: 3D perspective tilt (`rotateX`, `rotateY`) calculated from pointer offset from card center.
  - `Magnet`: Magnetic pull on buttons and icons with spring physics dampening on cursor proximity.

---

## 3. Superdesign.dev & Portal Hero Reveals
### Animated Portal Hero (Parts to Uncover Full-Bleed Image)
- **Concept**: Split hero overlay (doors / curtain / dual clip-path panels) that translates outward on scroll or initial load while scaling an underlying background image from `scale(0.8)` to `scale(1.0)`.
- **Implementation Blueprint**:
  ```tsx
  'use client';
  import { motion, useScroll, useTransform } from 'framer-motion';
  import { useRef } from 'react';

  export function PortalHero({ src, title }: { src: string; title: string }) {
    const containerRef = useRef<HTMLDivElement>(null);
    const { scrollYProgress } = useScroll({
      target: containerRef,
      offset: ['start start', 'end start']
    });

    const leftX = useTransform(scrollYProgress, [0, 1], ['0%', '-100%']);
    const rightX = useTransform(scrollYProgress, [0, 1], ['0%', '100%']);
    const imageScale = useTransform(scrollYProgress, [0, 1], [0.8, 1.05]);
    const opacity = useTransform(scrollYProgress, [0, 0.8], [1, 0]);

    return (
      <div ref={containerRef} className="relative h-[200vh] w-full">
        <div className="sticky top-0 h-screen w-full overflow-hidden">
          <motion.div style={{ scale: imageScale }} className="absolute inset-0">
            <img src={src} alt="Hero" className="h-full w-full object-cover" />
          </motion.div>

          <motion.div
            style={{ x: leftX }}
            className="absolute inset-y-0 left-0 w-1/2 bg-background border-r border-border z-10 flex items-center justify-end pr-8"
          >
            <motion.h1 style={{ opacity }} className="text-6xl font-bold tracking-tight text-foreground">
              {title.split(' ')[0]}
            </motion.h1>
          </motion.div>

          <motion.div
            style={{ x: rightX }}
            className="absolute inset-y-0 right-0 w-1/2 bg-background border-l border-border z-10 flex items-center justify-start pl-8"
          >
            <motion.h1 style={{ opacity }} className="text-6xl font-bold tracking-tight text-primary">
              {title.split(' ').slice(1).join(' ')}
            </motion.h1>
          </motion.div>
        </div>
      </div>
    );
  }
  ```

---

## 4. UI-Layouts (`ui-layouts.com`)
- **Sticky Scroll Card Stacking**:
  - Cards stay pinned with `position: sticky; top: calc(20vh + i * 24px)` while subsequent cards overlap and scale slightly down (`scale(0.95)` to `scale(1)`).
- **Perspective 3D Bento Grids**:
  - CSS subgrids with `transform-style: preserve-3d; perspective: 1000px;` and micro-rotations on cursor hover.
- **Interactive Timeline**:
  - Scroll-linked SVG path drawing using `pathLength: scrollYProgress` with pulsing waypoint markers.

---

## 5. Magic UI (`magicui.design`)
- `BorderBeam`: Glowing particle beam traveling along the border radius of a container via SVG stroke-dashoffset animation.
- `Marquee`: Seamless horizontal or vertical ticker with pause on hover and reverse velocity options.
- `Animated Grid Pattern` / `Retro Grid`: Perspective-tilted infinite grid moving toward the viewer with subtle glowing squares.
- `Number Ticker`: Spring-eased count-up for statistics and metrics.
- `Animated Beam`: Curved SVG cubic-bezier connection beams with moving light pulses between node endpoints.
- `Orbiting Circles`: Concentric orbital rings with rotating SVG icons / avatars.

---

## 6. Aceternity UI (`ui.aceternity.com`)
- `Background Beams`: High-speed ray-traced laser beams intersecting behind hero typography.
- `Tracing Beam`: Glowing SVG beam tracing document scroll progress alongside text articles.
- `Hero Parallax`: Multi-layer perspective tilt with staggered translations on scroll.
- `Lamp Effect`: Architectural spotlight cone illuminating primary hero headlines.
- `Canvas Reveal Effect`: Interactive dot matrix / noise canvas fading out on card hover.
- `Wobble Card`: Rubber-band inertial wobble using Framer Motion springs on mouse departure.

---

## 7. Motion Primitives (`motion-primitives.com`)
- `TextMorph`: Smooth morphing between words with shared letters animating to their new positions.
- `Dynamic Island`: Liquid spring expanding pill for status notifications, callouts, and audio controls.
- `Magnetic Container`: Composable wrapper injecting spring cursor attraction into any child element.
- `Border Trail`: Running animated gradient edge around cards with zero DOM pollution.

---

## 8. Codrops Tympanus (`tympanus.net/codrops/demos/`)
- **Liquid Distortions**: SVG `<filter id="liquid">` with `<feTurbulence>` and `<feDisplacementMap>` animated via requestAnimationFrame for organic fluid rippling.
- **WebGL Page Morphing**: Morphing between layouts using vertex shaders and texture cross-fading.
- **Horizontal Kinetic Scroll**: Transform-based horizontal layout scroll with velocity skew (`skewX(clamp(-10deg, velocity, 10deg))`).

---

## 9. HeroUI / NextUI (`heroui.com`)
- Accessible primitives with clean compound component architecture.
- Full keyboard navigation and ARIA attributes built-in.
- Modals with fluid backdrop blur, focus trapping, and spring escape.

---

## 10. Bklit (`bklit.com`)
- Industrial telemetry status cards, dense dark-mode charts, and tactile telemetry widgets.
- Real-time performance meters and multi-period toggle switches.
