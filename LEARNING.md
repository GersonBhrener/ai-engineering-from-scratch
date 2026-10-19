# My AI Engineering Path
<!-- Managed by the ai-engineering-from-scratch learning skills.
     Repo: https://github.com/rohitg00/ai-engineering-from-scratch -->

## Mission
Estou aprendendo engenharia de IA para fazer uma **transição de carreira**.
Ainda não sei exatamente o que quero construir ao final — o objetivo de estudo
segue em aberto, então começo pelas fundações e deixo o alvo se definir ao
longo do caminho.

## Placement
- Date: 2026-10-17
- Score: 2/10 — Math & Statistics 2/2, Classical ML 0/2, Deep Learning 0/2, NLP & Transformers 0/2, Applied AI 0/2
- Entry point: Phase 1: Math Foundations
- Pace: ~5 h/week

## Path
| Phase | Name | Status | Est. hours |
|-------|------|--------|------------|
| 0 | Setup & Tooling | Do | 16 |
| 1 | Math Foundations | Do | 23 |
| 2 | ML Fundamentals | Do | 26 |
| 3 | Deep Learning Core | Do | 15 |
| 4 | Computer Vision | Do | 27 |
| 5 | NLP — Foundations to Advanced | Do | 30 |
| 6 | Speech & Audio | Do | 18 |
| 7 | Transformers Deep Dive | Do | 14 |
| 8 | Generative AI | Do | 14 |
| 9 | Reinforcement Learning | Do | 13 |
| 10 | LLMs from Scratch | Do | 26 |
| 11 | LLM Engineering | Do | 19 |
| 12 | Multimodal AI | Do | 65 |
| 13 | Tools & Protocols | Do | 76 |
| 14 | Agent Engineering | Do | 55 |
| 15 | Autonomous Systems | Do | 20 |
| 16 | Multi-Agent & Swarms | Do | 28 |
| 17 | Infrastructure & Production | Do | 34 |
| 18 | Ethics, Safety & Alignment | Do | 31 |
| 19 | Capstone Projects | Do | 620 |

Total (Review + Do): ~1170 hours across 20 phases.

## Progress log
| Date | Lesson | Quiz | Note |
|------|--------|------|------|
| 2026-10-17 | 0/01 Dev Environment | 3/3 | Env pronto: conda `ai_eng_scratch` com torch 2.10.0 (CPU-only, sem nvidia-smi). Entendeu a pilha de 4 camadas de baixo para cima e por que o runtime precede o pacote. |
| 2026-10-18 | 0/02 Git & Collaboration | 2/3 | Fluxo `add → commit → push`, branches com `checkout -b`, staging area e `.gitignore` de checkpoints (`.pt`/`.pth`/`.safetensors`). Errou só o *porquê* de ignorar os checkpoints (são grandes e re-geráveis, não "arquivos de teste"). |

## Review queue
- **Git identity** — configurar `user.name`/`user.email` (global ou local); sem isso o `git commit` falha.
- **Push para o fork** — `Invalid username or token`: escolher PAT, `gh auth login` ou SSH.
- **Por que ignorar binários no Git** — revisar: checkpoints = grandes e re-geráveis; Git versiona binário, só que mal.
