# Atividade Prática 02
>
> [Universidade Federal do Ceará (UFC)](https://www.ufc.br/)\
> [Departamento de Computação (DC)](https://dc.ufc.br/pt/)\
> Disciplina: Engenharia de Sistemas Inteligentes (CK0444 – 2026.2)\
> Professor: [Lincoln S. Rocha](http://lattes.cnpq.br/0656977742590515)\
> E-mail: <lincoln@dc.ufc.br>
>

Prática com Git no Terminal do seu Computador

Objetivos da prática:

- Criar repositórios Git.
- Versionar arquivos em repositórios Git.
- Trabalhar com ramificações em repositórios Git.
- Realizar mesclagem de ramificações em repositórios Git.
- Resolver conclitos de mesclagem de ramificações em repositórios Git.

## 1. Pré-quequisitos

### 1.1. Verificando Git

Verifique se o Git está instalado no seu terminal de comandos (`shell` ou `console`).

```bash
git --version
```

### 1.2. Instalando Git

Caso o Git não esteja instalado, vá ao site do [Git](https://git-scm.com/install/) escolha a versão compatível com o seu Sistema Operacional, faça o downlaod e, em seguida, realize a instalação como recomendado no site do Git.

### 1.3. Configurando Usuário e E-mail

>
> Nota! Essa configuração deve ser postergada para mais tarde neste exercício (Veja passo `2.2`).
:

Usando o terminal de comandos (`shell` ou `console`), configure o Git com suas informações:

- Configuração Global

Essa configuração vai ser usada para todo repositório criado na máquina.

```bash
git config --global user.name "Seu Nome"
git config --global user.email seu.email@exemplo.com
```

- Configuração Local

Essa configuração vai ser usada para um repositório específico (`my_repo`).

```bash
cd my_repo
git config user.name "Seu Nome"
git config user.email seu.email@exemplo.com
```

## 2. Roteiro da Prática

### 2.1. Criando Diretório da Prática

Usando o terminal de comandos (`shell` ou `console`), crie a pasta `git-esi` e posicione o console dentro dela:

```bash
mkdir git-esi
cd git-esi
```

### 2.2. Criando o Repositório Git

Agora, iremos transformar o diretório `git-esi` em um repositório Git:

```bash
git init
```

Obs. Agora você pode usar a configuração global ou local descrita em `1.3` considerando como repositório o diretório `git-esi`.

### 2.3. Criando o módulo Python `calac.py`

Usando algum editor de código/texto, crie o arquivo `calc.py` dentro do diretório `git-esi`, escreva o seguite trecho código detro dele e, por fim, salve o arquivo:

```python
def sub(x, y): 
  return x - y
```

### 2.4. Verificando Status de `calc.py` no Git

Agora, verifique se o arquivo está sendo rastreado pelo Git, usando o seguite comando:

```bash
git status
```

### 2.5. Fazendo o Git Rastrear `calc.py`

Agora, iremos fazer com que esse arquivo passe a ser rastreado pelo Git usando o comando a seguir:

```bash
git add calc.py
```

ou, para contemplar todos os arquivos da pasta:

```bash
git add .
```

Repita as instruções do passo `2.4` e certifique-se de que o arquivo `calc.py` está sendo rastreado.

### 2.6. Registrando Primeiras Alterações de `calc.py`

Você agora vai registrar as alterações no repositório usando o comando ``commit``:

```bash
git commit -m "Primeira versão da calculadora."
```

### 2.7. Visualizando Log de Alterações

Verifique o registro de commits usando o comando log:

```bash
git log
```

### 2.8. Realizando Modificações em `calc.py`

Usando algum editor de código/texto, altere o arquivo `calc.py` para que ele fique igual ao código abaixo (adicionando a função `sum()`) e, em seguida, salve o arquivo:

```python
def sub(x, y): 
  return x - y

def sum(x, y):
  return x + y
```

### 2.9. Registrando Novas Alterações em `calc.py`

Adicione as alterações na área de `stage` para que possam ser gravadas (`commit`) no repositório repetindo as instruções descritas no passo `2.5`.

Você agora deve registrar as novas alterações no repositório usando o comando ``commit``:

```bash
git commit -m "Adicionando a função sum() na calculadora."
```

Repita as instruções do passo `2.7` para ver o log de alterações.

### 2.10. Crindo a Ramificação `ramo`

Agora, crie uma ramificação para trabalhar em paralelo com o arquivo:

```bash
git branch ramo
```

Para saber em qual ramificação do repostitório você está trabalhando, use o seguite comando:

```bash
git branch
```

### 2.11. Alternando para a Ramificação `ramo`

Alterne para a ramificação criada no passo `2.10` usando o seguite comando:

```bash
git checkout ramo
```

### 2.12. Realizando Modificações em `calc.py` de `ramo`

Usando um editor de texto/código, altere o arquivo `calc.py` para inserir a função `div()`, deixando o código como o descrito abaixo:

```python
def sub(x, y): 
  return x - y
  
def sum(x, y):
  return x + y

def div(x, y): 
  return x / y
```

### 2.13. Registrando Novas Alterações em `calc.py` de `ramo`

Adicione as alterações na área de `stage` para que possam ser gravadas (`commit`) no repositório repetindo as instruções descritas no passo `2.5`.

Você agora deve registrar as novas alterações na ramificação `ramo` do repositório usando o comando ``commit``:

```bash
git commit -m "Adicionando a função div() na calculadora."
```

Repita as instruções do passo `2.7` para ver o log de alterações.

### 2.14. Mesclando a Ramificação `ramo`

Faremos agora a mesclagem das alterações, unificando as versões correntes das ramificações `main` e `ramo`.

Primeiramente, mudaremos para o ramo `main`:

```bash
git checkout main
```

Agora, abra o arquivo `calc.py` no editor de código/texto e observe que o seu conteúdo está diferente da versão que está em `ramo`. Ao invés de usar um editor, podes usar o comando `cat` (Linux/MacOS) ou `type` (Windos) no terminal:

```bash
cat calc.py
```

ou

```bash
type calc.py
```

Após fechar o arquivo (caso tenha optado pelo uso do editor), execute o comando abaixo para fazer a mesclagem entre o conteúdo de `ramo` e `main`:

```bash
git merge ramo
```

Nota! Observe agora que o arquivo `calc.py` possui o conteúdo mesclado.

Repita as instruções do passo `2.7` para ver o log de alterações.

### 2.15. Crindo a Ramificação `hotfix`

Observe que a função `div(x, y)` do arquivo `calc.py` possui um bug, ela não trata o caso de divisão por zero. Assim, você deve criar uma ramificação (`hotfix`) para corrigir esse bug:

```bash
git branch hotfix
```

Nota! Observe que a ramificação `hotfix` foi criada, mas o `HEAD` ainda aponta para o ramificação `main`. Mantenha dessa forma e siga para o passo `2.16`.

### 2.16. Realizando Modificações em `calc.py` de `main`

Usando algum editor de código/texto, altere o arquivo `calc.py` para inserir a função `mult()`, deixando o código como o descrito abaixo:

```python
def sum(x, y):
  return x + y
  
def sub(x, y): 
  return x - y

def div(x, y): 
  return x / y

def mult(x, y): 
  return x * y
```

### 2.17. Registrando Novas Alterações em `calc.py` de `main`

Adicione as alterações na área de `stage` para que possam ser gravadas (`commit`) no repositório repetindo as instruções descritas no passo `2.5`.

Você agora deve registrar as novas alterações na ramificação `main` do repositório usando o comando ``commit``:

```bash
git commit -m "Adicionando a função mult() na calculadora."
```

Nota! Observe que as alterações foram feita na ramificação `main`.

Repita as instruções do passo `2.7` para ver o log de alterações.

### 2.18. Alternando para a Ramificação `hotfix`

Agora alterne para a ramimicação `hotfix`:

```bash
git checkout hotfix
```

### 2.19. Corrigindo Bug em `calc.py` de `hotfix`

Usando algum editor de código/texto, altere o arquivo `calc.py` para corrigir a função `div()`, deixando o código como o descrito abaixo:

```python
def sum(x, y):
  return x + y
  
def sub(x, y): 
  return x - y

def div(x, y):
  return x / y if y != 0 else None
```

### 2.20. Registrando a Correção de Bug de `calc.py` em `hotfix`

Adicione as alterações na área de `stage` para que possam ser gravadas (`commit`) no repositório repetindo as instruções descritos no passo `2.5`.

Você agora deve registrar as novas alterações na ramificação `hotfix` do repositório usando o comando ``commit``:

```bash
git commit -m "Bug fix divisão por zero na função div() da calculadora."
```

### 2.21. Mesclando a Ramificação `hotfix`

Faremos agora a mesclagem das alterações, unificando as versões correntes das ramificações `main` e `hotfix`:

```bash
git checkout main
```

Agora, abra o arquivo `calc.py` no editor de código/texto e observe que o seu conteúdo está diferente da versão que está em `hotfix`. Ao invés de usar um editor, podes usar o comando `cat` (Linux/MacOS) ou `type` (Windos) no terminal:

```bash
cat calc.py
```

ou

```bash
type calc.py
```

Após fechar o arquivo (caso tenha optado pelo uso do editor), execute o comando abaixo para fazer a mesclagem entre o conteúdo de `hotfix` e `main`:

```bash
git merge hotfix
```

Você deverá receber uma mensagem parecida com a descrita abaixo indicando que houve um `"confilo de merge"`:

```bash
Auto-merging calc.py
CONFLICT (content): Merge conflict in calc.py
Automatic merge failed; fix conflicts and then commit the result.
```

### 2.22. Resolvendo Conflito de Merge

Use algum editor de texto/código para editar o arquivo `calc.py`, elimine manualmente o conflito e salve o arquivo. Em seguida, execute os seguintes comandos:

```bash
git add calc.py
git commit
```

ou

```bash
git commit -a
```

### 2.23. Entrega da Tarefa

Agora você deve compactar o repositório `git-esi` gerando `git-esi.zip` e enviar via SIGAA como reposta desta tarefa. OBS. A análise do log do repositório será utilizado para verificar a realização correta da tarefa.
