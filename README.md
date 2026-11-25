# app-bet-t1w

<!-- brainlife-app:begin (generated from the App manifest; edit the manifest, not this block) -->

> **Skull-strips a T1-weighted image with FSL 6.0.4 BET and outputs the brain-extracted T1w volume.**

Runs FSL bet on a T1w image with a configurable fractional intensity threshold (-f) and optional robust brain centre estimation (-R) or bias field and neck cleanup (-B), inside the brainlife/fsl:6.0.4 container. Use it for brain extraction before registration or segmentation. Lower frac values give larger brain estimates; enable bias_neck_cleanup for images with a lot of neck.

| | |
|---|---|
| 📥 **Inputs** | `neuro/anat/t1w` |
| 📤 **Outputs** | `neuro/anat/t1w` |
| 🐳 **Container** | `brainlife/fsl:6.0.4` |
| ⚙️ **Resources** | 4 GB memory · 1 h walltime |
| 🔗 **Run it** | [doi.org/10.25663/brainlife.app.995](https://doi.org/10.25663/brainlife.app.995) |

#### 📥 Inputs

| Input | Datatype | Required | Description |
|---|---|---|---|
| `t1` | `neuro/anat/t1w` | yes | T1-weighted NIfTI image to skull-strip. |

#### 📤 Outputs

| Output | Datatype | Description |
|---|---|---|
| `t1_brain` | `neuro/anat/t1w` | Skull-stripped T1w brain volume produced by FSL BET |

<details>
<summary><b>⚙️ Parameters</b> (3)</summary>

| Parameter | Type | Default | Description |
|---|---|---|---|
| `frac` | number | `0.5` | BET fractional intensity threshold (0-1) |
| `robust` | boolean | `false` | Use robust brain centre estimation (-R) |
| `bias_neck_cleanup` | boolean | `false` | Bias field + neck cleanup (-B) |

</details>

<!-- brainlife-app:end -->

Skull-strip a T1w MRI with FSL BET

## Inputs

- `t1` (neuro/anat/t1w)

## Outputs

- `t1_brain` (neuro/anat/t1w) -- Skull-stripped T1w brain volume produced by FSL BET

## Usage

Brainlife.io: run via `faber-app-run`/`faber-app-pipeline` (once registered
with `faber-app-create`), or the web UI.

Locally (outside brainlife): copy `config.json.example` to `config.json`,
fill in real file paths, then run `./main` from this directory. `main` pulls
its own container (`singularity exec docker://...`) -- no local install of
the underlying tool needed, only Singularity itself.

Entrypoint: `run_bet.sh`

## Authors

- Gabriele Amorosino <g.amorosino@gmail.com>

#### MIT Copyright (c) 2026 Gabriele Amorosino
