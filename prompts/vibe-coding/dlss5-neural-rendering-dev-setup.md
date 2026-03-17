# NVIDIA DLSS 5 Neural Rendering — Developer Setup Guide

> **GTC 2026 Keynote (March 17):** NVIDIA announced DLSS 5 — a paradigm shift from upscaling to full neural rendering. AI generates photoreal lighting, materials, and reflections in real-time. Launching Fall 2026 via the Streamline SDK.

## What You Get
Integrate neural rendering into your game or 3D app. DLSS 5 uses trained neural networks to generate physically-accurate lighting and materials that surpass traditional ray tracing quality at a fraction of the cost.

## Quick Integration (Streamline SDK)

```cpp
// 1. Initialize Streamline (if you already ship DLSS 4.x, this is familiar)
#include <sl.h>
#include <sl_dlss.h>

sl::Preferences prefs{};
prefs.showConsole = false;
prefs.logLevel = sl::LogLevel::eDefault;
slInit(prefs);

// 2. Check DLSS 5 Neural Rendering support
sl::Feature feature = sl::kFeatureDLSS_NeuralRendering;
sl::AdapterInfo adapterInfo{};
if (SL_FAILED(slIsFeatureSupported(feature, adapterInfo))) {
    // Fallback to DLSS 4.x or native rendering
    printf("DLSS 5 not supported — needs RTX 50-series or later\n");
}

// 3. Configure neural rendering controls
sl::DLSSNeuralOptions neuralOpts{};
neuralOpts.mode = sl::DLSSNeuralMode::eQuality;  // ePerformance | eBalanced | eQuality
neuralOpts.intensity = 0.8f;         // 0.0 (subtle) → 1.0 (full neural)
neuralOpts.preserveArtDirection = true;  // Respects your art style
neuralOpts.colorGradingPass = true;      // Apply AFTER your post-processing
```

## Developer Controls Cheat Sheet

| Control | Values | Use Case |
|---------|--------|----------|
| `intensity` | 0.0–1.0 | Blend between traditional and neural rendering |
| `preserveArtDirection` | bool | Prevent AI from overriding stylized visuals |
| `maskRegions` | texture | Exclude UI, HUD, or specific areas from neural pass |
| `colorGradingPass` | bool | Apply neural rendering before/after color grading |
| `materialOverride` | enum | Force specific material models (metal, glass, cloth) |

## Unreal Engine 5 — Plugin Setup

```ini
# DefaultEngine.ini
[/Script/Engine.RendererSettings]
r.Streamline.Enable=1
r.DLSS5.NeuralRendering=1
r.DLSS5.Intensity=0.85
r.DLSS5.PreserveArtDirection=True
r.DLSS5.MaskUIElements=True
```

## Performance Impact Estimate

| Scenario | Without DLSS 5 | With DLSS 5 | Notes |
|----------|----------------|-------------|-------|
| 4K ray-traced scene | 30 FPS | 90+ FPS | RTX 5090 |
| Complex reflections | Heavy RT cost | Near-free | Neural material inference |
| Dynamic GI | Noisy at low samples | Clean | Neural denoising + generation |

## Supported Hardware
- **Minimum:** RTX 50-series (Blackwell architecture)
- **Optimal:** RTX 5080/5090 or Vera Rubin workstation GPUs
- **Fallback:** RTX 40-series gets DLSS 4.x path automatically

## Key Links
- [NVIDIA Streamline SDK](https://developer.nvidia.com/rtx/streamline)
- [DLSS Programming Guide](https://developer.nvidia.com/rtx/dlss/get-started)

---

> 💡 **Want the full DLSS 5 Production Pipeline?** Complete integration with A/B quality testing, multi-platform fallback chains, performance profiling scripts, and CI/CD rendering benchmarks → [AI Dev Toolkit PRO](https://ai-dev-toolkit-five.vercel.app) — $9 one-time
