# Recursos Complementares — AI Engineering from Scratch
<!-- Acumulativo; mantido pelo agente. Regra em ~/.config/opencode/AGENTS.md -->
<!-- Fonte para NotebookLM, junto com STUDY-GUIDE.md. Atualizado: 2026-10-18 -->

> **Como usar.** Para cada lição há duas partes: **(Do curso)** as recomendações do
> próprio curso (seção `Further Reading` da lição, quando existe) e
> **(Complementares)** recursos pesquisados na web — livros, vídeos, repositórios,
> artigos e cursos.
>
> **Legenda:** 📕 livro · 🎥 vídeo · 🧑‍💻 repositório · 📄 artigo/doc · 🎮 interativo · 🎓 curso

## Fase 0 · Setup & Tooling

### Lição 01 · Dev Environment
**Do curso.** A lição não tem seção `Further Reading`; cita apenas as páginas
oficiais de instalação das ferramentas: [uv](https://astral.sh/uv),
[fnm](https://fnm.vercel.app/), [rustup](https://sh.rustup.rs),
[juliaup](https://install.julialang.org) e o
[índice CUDA do PyTorch](https://download.pytorch.org/whl/cu124).

**Complementares.**
- 📄 **uv — documentação oficial** — https://docs.astral.sh/uv/ · o gerenciador que a lição usa (equivalente moderno ao seu conda).
- 📄 **conda — Managing environments** — https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html · criar, ativar e exportar ambientes.
- 📄 **PyTorch — Learn the Basics** — https://pytorch.org/tutorials/beginner/basics/intro.html · série interativa oficial: tensores, autograd, treino.
- 🎥 **Introduction to PyTorch — série oficial em vídeo** — https://pytorch.org/tutorials/beginner/introyt/introyt_index.html
- 🧑‍💻 **pytorch/tutorials** — https://github.com/pytorch/tutorials · notebooks de todos os tutoriais oficiais.
- 📕 **The Hitchhiker's Guide to Python** (K. Reitz & T. Schlusser) — https://docs.python-guide.org/ · capítulos de ambientes virtuais e empacotamento.
- 📄 **Real Python — Python Virtual Environments: A Primer** — https://realpython.com/python-virtual-environments-a-primer/ · venv vs conda na prática.

### Lição 02 · Git & Collaboration
**Do curso.** Sem seção `Further Reading`; o Exercício 3 pede para explorar o
histórico com `git log --oneline`.

**Complementares.**
- 📕 **Pro Git** (S. Chacon & B. Straub) — https://git-scm.com/book/en/v2 · gratuito e definitivo; há tradução em português.
- 🎮 **Learn Git Branching** — https://learngitbranching.js.org/ · visual e interativo; o melhor jeito de fixar branch/merge.
- 📄 **GitHub Docs — Authentication** — https://docs.github.com/en/authentication · por que a senha não funciona e como usar PAT/SSH.
- 📄 **GitHub Docs — Personal access tokens** — https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens
- 🧑‍💻 **github/gitignore** — https://github.com/github/gitignore · templates de `.gitignore` (inclui Python), para o Exercício 2.
- 🎓 **GitHub Skills** — https://skills.github.com/ · tutoriais práticos guiados dentro do próprio GitHub.

### Fase 0 — trilha geral (panorama)
- 🎓 **The Missing Semester of Your CS Education (MIT)** — https://missing.csail.mit.edu/ · shell, Git, edição e debug: cobre boa parte da Fase 0 inteira.
- 📕 **Automate the Boring Stuff with Python** (A. Sweigart) — https://automatetheboringstuff.com/ · gratuito online; bom para terminal e automação.
