# Guia de Estudos — AI Engineering from Scratch
<!-- Arquivo acumulativo; mantido pela skill study-guide. Não reordenar. -->
<!-- Fonte única para upload no NotebookLM. Atualizado: 2026-10-18 -->

> **Como usar.** Suba este arquivo como fonte no NotebookLM. Cada seção é
> autocontida: conceito, comandos para repetir e um exercício. A ordem segue a
> curva do curso, do mais simples ao mais avançado, e cresce a cada lição.
>
> **Conteúdo:** as seções são escritas automaticamente pelo agente a partir de cada
> lição estudada.

## 01 · Camadas de um ambiente de IA (Fase 0 · Lição 01)
**Conceito.** Um ambiente de IA tem quatro camadas que se instalam de baixo para
cima: (1) Sistema — SO, shell, drivers; (2) Gerenciadores de pacote; (3) Runtimes
de linguagem; (4) Bibliotecas de IA. Pacotes de IA dependem do runtime; o runtime
depende do sistema. Inverter essa ordem é a causa da maioria dos conflitos.

**Comandos para repetir.**
```bash
git --version           # sistema
python3 --version       # runtime
node --version          # runtime
conda env list          # gerenciador / ambientes
```

**Exercício.** Liste suas quatro camadas com uma versão de cada. Se alguma
estiver faltando, anote o comando de correção antes de seguir.

**Incremento.** Com a base pronta, o próximo passo é isolar as dependências do
curso num ambiente dedicado.

## 02 · Ambiente Python isolado com conda (Fase 0 · Lição 01)
**Conceito.** Um ambiente virtual isola as versões de pacotes por projeto, para
que atualizar uma biblioteca num projeto não quebre outro. O `conda` cria e
ativa esse ambiente dedicado.

**Comandos para repetir.**
```bash
conda create -n ai_eng_scratch python=3.12   # criar (uma vez)
conda activate ai_eng_scratch                 # ativar
which python                                  # deve apontar para o env, não o base
pip list                                      # pacotes do env ativo
conda deactivate                              # sair
```

**Exercício.** Ative `ai_eng_scratch` e confirme com `which python` que o
interpretador é o do ambiente, não o `base`.

**Incremento.** Ambiente ativo → instalar a principal biblioteca de IA.

## 03 · Instalar e verificar o PyTorch (Fase 0 · Lição 01)
**Conceito.** Com o ambiente ativo, instala-se o PyTorch. Em máquina sem GPU
NVIDIA o build é CPU-only e **não** se usa `--index-url .../cuXXX`. CUDA é
exclusivo de GPUs NVIDIA; em Apple Silicon usa-se MPS.

**Comandos para repetir.**
```bash
python -m pip install torch torchvision torchaudio
python -c "import torch; print('torch', torch.__version__); print('CUDA:', torch.cuda.is_available())"
```

**Exercício.** Rode a verificação, anote a versão do torch e o valor de
`torch.cuda.is_available()`. Explique por que ele pode ser `False` e ainda assim
tudo funcionar.

**Incremento.** Ambiente completo → verificar de uma vez se o curso está pronto.

## 04 · Preflight do curso (Fase 0 · Lição 01)
**Conceito.** O curso traz um verificador que checa apenas o que a rota escolhida
precisa e, em cada falha, imprime o comando de correção. Rode sempre da raiz do
repositório.

**Comandos para repetir.**
```bash
python3 phases/00-setup-and-tooling/01-dev-environment/code/verify.py --route beginner
python3 phases/00-setup-and-tooling/01-dev-environment/code/verify.py --route ml-foundations --show-later
```

**Exercício.** Rode `--route beginner` e corrija a primeira linha `[FAIL]`, se
houver, antes de olhar a próxima.

**Incremento.** Ambiente ok → começar a versionar o trabalho com Git.

## 05 · Git: identidade (Fase 0 · Lição 02)
**Conceito.** Antes do primeiro commit, configure quem assina cada mudança. Sem
isso, o Git falha ou inventa uma identidade. Isso é global ao usuário.

**Comandos para repetir.**
```bash
git config --global user.name "Seu Nome"
git config --global user.email "voce@exemplo.com"
git config --global user.name      # conferir
```

**Exercício.** Configure nome e e-mail e confirme com
`git config --global user.name`.

**Incremento.** Identidade pronta → o fluxo de salvar e enviar.

## 06 · Git: fluxo diário (Fase 0 · Lição 02)
**Conceito.** Quatro áreas: working directory → staging (`add`) → repositório
local (`commit`) → remoto (`push`). A staging area permite escolher e revisar o
que entra em cada commit, montando histórias limpas.

**Comandos para repetir.**
```bash
git status
git add arquivo.py
git add -p                  # escolher trechos (commit parcial)
git commit -m "mensagem curta"
git push origin main
git log --oneline
```

**Exercício.** Crie um arquivo, faça `add` + `commit` e confirme com
`git log --oneline`.

**Incremento.** Já sabe salvar → separar experimentos sem quebrar o `main`.

## 07 · Git: branches (Fase 0 · Lição 02)
**Conceito.** Um branch é um ponteiro para um commit que avança conforme você
trabalha — criar é instantâneo e barato. Serve para experimentar sem afetar o
`main`.

**Comandos para repetir.**
```bash
git checkout -b experiment/meu-teste   # cria e muda para o branch
git checkout main                      # volta ao main
git merge experiment/meu-teste         # traz as mudanças
git branch                             # lista branches
```

**Exercício.** Crie um branch, faça um commit nele, volte ao `main` e faça o
merge. Confirme com `git log --oneline`.

**Incremento.** Trabalho isolado → publicar num remoto seu.

## 08 · Git: remotes e fork (Fase 0 · Lição 02)
**Conceito.** `origin` é o seu fork; `upstream` é o repositório original, onde
você normalmente não tem escrita. Sem um fork próprio, `git push` no repo do
curso falha.

**Comandos para repetir.**
```bash
git remote -v
git remote rename origin upstream
git remote add origin https://github.com/SEU-USUARIO/ai-engineering-from-scratch.git
git remote remove origin            # desfaz o add
git remote set-url origin <nova-url>  # troca só a URL
```

**Exercício.** Liste os remotes com `git remote -v` e explique para onde um
`git push` iria em cada configuração.

**Incremento.** Remoto definido → autenticar sem depender de senha.

## 09 · Git: autenticação sem senha (Fase 0 · Lição 02)
**Conceito.** O GitHub não aceita a senha da conta em HTTPS. Use um Personal
Access Token (PAT), o GitHub CLI (`gh`) ou uma chave SSH.

**Comandos para repetir.**
```bash
# PAT: usuário = seu login; senha = o token (escopo repo)
git config --global credential.helper cache    # guarda na sessão (mais seguro)
git config --global credential.helper store    # guarda em texto puro (~/.git-credentials)

# GitHub CLI
gh auth login && gh auth setup-git

# SSH
ssh-keygen -t ed25519 -C "voce@exemplo.com"
ssh -T git@github.com
```

**Exercício.** Se aparecer `Invalid username or token`, diga qual dos três
caminhos você escolheu e por quê.

**Incremento.** Versionamento completo → seguir para as fundações matemáticas
(Fase 1, começando por Álgebra Linear).

## 10 · Git: ignorar arquivos grandes (Fase 0 · Lição 02)
**Conceito.** Git não foi feito para binários grandes — checkpoints de modelo
chegam a gigabytes. Eles ficam fora do versionamento e são re-gerados ou
guardados à parte.

**Comandos para repetir.**
```bash
# .gitignore na raiz do repositório
printf '*.pt\n*.pth\n*.safetensors\n' > .gitignore

git status                     # os arquivos ignorados não devem aparecer
git check-ignore -v modelo.pt  # mostra qual regra ignorou um arquivo
```

**Exercício.** Crie o `.gitignore` com `*.pt`, `*.pth`, `*.safetensors`; crie um
`vazio.pt` e confirme que ele não aparece em `git status`.

**Incremento.** Com o repositório limpo, o próximo passo é ler o que já foi feito.

## 11 · Git: inspecionar o histórico (Fase 0 · Lição 02)
**Conceito.** O histórico registra como o projeto evoluiu. Saber lê-lo ajuda a
achar quando algo mudou e por quê.

**Comandos para repetir.**
```bash
git log --oneline
git log --oneline -- phases/00-setup-and-tooling   # só um caminho
git show --stat <hash>                             # o que um commit mudou
git diff                                           # mudanças ainda não commitadas
```

**Exercício.** Abra um commit com `git show --stat <hash>` e liste quais arquivos
ele adicionou.

**Incremento.** Histórico legível → saber executar o que o curso traz.

## 12 · Rodar e testar uma lição (Fase 0 · apoio)
**Conceito.** Cada lição traz código executável e testes. Rodar o código da lição
transforma leitura em prática; é o coração do método "Build It / Use It".

**Comandos para repetir.**
```bash
# executar o código de uma lição (exemplo: Fase 1, Lição 01)
python3 phases/01-math-foundations/01-linear-algebra-intuition/code/vectors.py

# dentro de code/, rodar a suíte de testes da lição
cd phases/<fase>/<licao>/code
python3 main.py
python3 -m unittest discover tests -v

# explorar a estrutura do repositório
find phases -maxdepth 2 -type d | head
```

**Exercício.** Rode o `vectors.py` da Fase 1 e depois a suíte de testes de uma
lição que tenha `code/tests/`.

**Incremento.** Agora você consegue ler, versionar e executar o curso — pronto
para a Lição 03 (GPU Setup & Cloud).

