---
name: warp-ctc
description: "Fast, parallel GPU/CPU Connectionist Temporal Classification (CTC) loss for sequence learning in speech, OCR, and NLP models."
---

# Warp-CTC (`/warp-ctc`)

Высокопроизводительное вычисление CTC-loss (Connectionist Temporal Classification) для моделей распознавания речи (ASR) и рукописного текста (OCR).

## Инварианты:
- Параллельное выполнение на CUDA / OpenMP.
- В 10–50 раз быстрее наивных реализаций на PyTorch/TensorFlow.
- Используется при обучении рекуррентных и конволюционных сетей без явного выравнивания (alignment).
