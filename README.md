# Automatize a Compilação de LaTeX com GitHub Actions: 
## Como compilar documentos LaTeX diretamente no GitHub, sem precisar de instalações locais.

Este tutorial explica como configurar seu repositório no GitHub para compilar arquivos LaTeX diretamente na plataforma, sem a necessidade de instalar compiladores no seu computador. Com o GitHub Actions, você pode automatizar a compilação de documentos LaTeX em PDFs sempre que fizer alterações no repositório.

## 1. O que é Workflow e GitHub Actions?

O GitHub Actions é uma ferramenta de automação integrada ao GitHub que permite criar workflows (fluxos de trabalho) para automatizar tarefas, como compilação de código, execução de testes e implantação de aplicações. Com ele, é possível reduzir erros e economizar tempo ao automatizar processos repetitivos dentro do repositório.

Um workflow é um conjunto de instruções automatizadas que definem como determinadas tarefas serão executadas dentro de um repositório. Ele é descrito em um arquivo YAML, armazenado no diretório `.github/workflows`, e pode ser acionado automaticamente quando um evento ocorre no repositório. Cada repositório pode conter vários workflows, e cada um pode ser configurado para executar um conjunto específico de ações. Além disso, um workflow pode ser referenciado dentro de outro, permitindo a reutilização de processos.
- Para saber mais sobre a reutilização de workflows, confira: [Reutilizar fluxos de trabalho](https://docs.github.com/pt/actions/using-workflows).

### 1.1 Como funciona o GitHub Actions?
O GitHub Actions opera com base em três conceitos principais:

- `Eventos`: São os gatilhos que iniciam a execução de um workflow (ex.: `push`, `pull request`, `criação de uma tag`);
- `Workflows`: São os arquivos YAML que definem quais ações devem ser executadas quando um evento ocorre;
- `Ações`: São os blocos individuais de execução dentro de um workflow, que realizam tarefas específicas, como rodar um script, compilar código ou enviar notificações.

Por exemplo, um workflow pode ser configurado para rodar automaticamente testes unitários sempre que uma pull request for aberta. Isso ajuda a garantir que o código enviado para o repositório esteja funcionando corretamente antes de ser mesclado. Para uma explicação mais detalhada, confira: [Entendendo o GitHub Actions](https://docs.github.com/pt/actions/about-github-actions/understanding-github-actions).

No contexto deste tutorial, usaremos o GitHub Actions para configurar um workflow que compila arquivos LaTeX em PDFs automaticamente sempre que você fizer alterações no repositório.

## 2. Por que usar GitHub Actions para compilar LaTeX?
- `Sem necessidade de instalar compiladores localmente`: Você não precisa ter o LaTeX instalado no seu computador;
- `Automatização`: O PDF é gerado automaticamente sempre que você faz alterações no repositório;
- `Compatibilidade`: O GitHub Actions usa máquinas virtuais com Ubuntu, garantindo que a compilação funcione de forma consistente, independentemente do sistema operacional que você usa.

## 3. Passo a Passo para Configurar o Workflow de Compilação LaTeX

#### 3.1  Criar um Novo Repositório
- No GitHub, clique no botão `"New"` no canto superior direito;
- Dê um nome ao repositório (por exemplo, Test);
- Escolha se o repositório será público ou privado;
- Marque a opção `"Add a README file"` (opcional);
- Clique em `"Create repository"`.

> [!TIP]
> Apesar do **README** ser opcional, ele é importante para documentar e explicar o seu repositório. Ele funciona como a `"porta de entrada"` do projeto, ajudando outras pessoas (e até você no futuro) a entender rapidamente do que se trata o código ou como utilizá-lo.

#### 3.2 Adicionar Arquivos .tex ao Repositório
- No repositório criado, clique no botão `"Add file"` no canto superior direito;
- Escolha `"Upload files"`;
- Arraste os arquivos `.tex` para a área indicada ou clique em `"choose your files"` para selecioná-los;
- Clique em `"Commit changes"` para salvar as alterações;

> [!NOTE]  
> Além de fazer o upload de arquivos prontos, você também pode criar arquivos diretamente no GitHub sem precisar fazer o upload. Isso é útil se você quiser criar um arquivo **.tex** do zero ou editar algo diretamente na interface do GitHub.
> Basta escolher `"Create new file"` e adicionar a extensão do arquivo **.tex**.

#### 3.3 Configurar o Workflow de Compilação LaTeX

##### 3.3.1 Criar a Pasta do Workflow
- No seu repositório, clique no botão `"Add file"` e escolha `"Create new file"`.
- No campo de nome do arquivo, digite `.github/workflows/latex.yml`. Isso criará automaticamente a pasta `.github/workflows` e o arquivo `latex.yml`.

##### 3.3.2 Adicionar o Conteúdo do Workflow
No editor de texto que aparecer, cole o código abaixo para compilar um único arquivo **.tex**:

```yaml
nome: Compile LaTeX to PDF
on:
  push:
    branches:
      - main
jobs:
  build:
    runs-on: ubuntu-latest
```

```
nome: Compile LaTeX to PDF
on:
  push:
    branches:
      - main
jobs:
  build:
    runs-on: ubuntu-latest
```





