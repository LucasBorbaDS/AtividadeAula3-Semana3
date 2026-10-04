# Atividade Aula 3 - Semana 3

Guia de instalação do ambiente para trabalhar com **Análise de Dados** e
**Ciência de Dados** no Windows utilizando Python e o gerenciador de
dependências [uv](https://docs.astral.sh/uv/).

## 1. Instalação do VS Code

O Visual Studio Code será utilizado para escrever os códigos e abrir os
notebooks.

1. Acesse o [site oficial do Visual Studio Code](https://code.visualstudio.com/).
2. Clique em **Download for Windows**.
3. Execute o instalador e aceite os termos de licença.
4. Na tela de tarefas adicionais, marque **Adicionar ação "Abrir com Code"**.
5. Conclua a instalação.

## 2. Instalação e configuração do Git

O Git permite controlar o histórico do projeto e enviar os trabalhos para o
GitHub.

1. Baixe o [Git for Windows](https://git-scm.com/).
2. Execute o instalador mantendo as opções padrão.
3. Abra o **PowerShell** e configure sua identidade:

   ```powershell
   git config --global user.name "Nome de Usuário"
   git config --global user.email "seu.email@github.com"
   ```

Substitua os valores de exemplo pelos dados associados à sua conta do GitHub.

## 3. Instalação do Python pelo uv

O `uv` simplifica a instalação do Python e o gerenciamento do ambiente virtual.

No PowerShell, execute:

```powershell
powershell -ExecutionPolicy ByPass -c "irm https://astral.sh/uv/install.ps1 | iex"
```

Feche o PowerShell, abra uma nova janela e instale uma versão compatível do
Python:

```powershell
uv python install 3.14
```

Também é possível instalar a versão estável mais recente com:

```powershell
uv python install
```

## 4. Criação do projeto

No PowerShell, navegue até a pasta onde deseja criar o projeto e execute:

```powershell
uv init meu-projeto-aula --app
cd meu-projeto-aula
uv venv
```

Para ativar o ambiente virtual no Windows:

```powershell
.venv\Scripts\Activate.ps1
```

> A ativação é opcional. Também é possível executar comandos diretamente no
> ambiente isolado usando `uv run`.

## 5. Instalação das bibliotecas de Data Science

Dentro da pasta do projeto, instale as bibliotecas com:

```powershell
uv add pandas numpy jupyterlab openpyxl matplotlib seaborn scipy scikit-learn statsmodels plotly
```

### Bibliotecas incluídas

| Biblioteca | Utilização |
| --- | --- |
| `pandas` | Leitura, organização e análise de tabelas e arquivos de dados. |
| `numpy` | Cálculos numéricos e manipulação de arrays. |
| `openpyxl` | Leitura e gravação de planilhas do Excel. |
| `matplotlib` | Criação de gráficos e visualizações. |
| `seaborn` | Visualizações estatísticas baseadas no Matplotlib. |
| `scipy` | Funções científicas, estatística e álgebra linear. |
| `statsmodels` | Modelos estatísticos, testes de hipótese e séries temporais. |
| `scikit-learn` | Pré-processamento, machine learning e avaliação de modelos. |
| `plotly` | Criação de gráficos interativos. |
| `jupyterlab` | Criação e execução de notebooks. |

Após a instalação, o `uv` atualizará o `pyproject.toml` e criará ou atualizará
o `uv.lock` com as versões compatíveis das dependências.

## 6. Execução de notebooks no VS Code

1. Abra o VS Code.
2. Selecione **File > Open Folder...** e abra a pasta do projeto.
3. Crie um arquivo `aula.ipynb` ou `aula.py`.
4. Em um notebook, clique em **Selecionar Kernel** (*Select Kernel*).
5. Escolha o ambiente Python que contém a etiqueta `.venv`.

O projeto também contém o arquivo [`manual_instalacao.txt`](./manual_instalacao.txt)
com as instruções em formato texto.

## 7. Commit e envio do projeto para o GitHub

### Publicar o projeto usando o VS Code

1. Abra a pasta do projeto no VS Code em **File > Open Folder...**.
2. Na barra lateral, abra **Source Control** (ícone de ramificação) ou use
   `Ctrl+Shift+G`.
3. Se aparecer a opção **Initialize Repository**, clique nela para criar o
   repositório Git local.
4. Na seção **Changes**, confira os arquivos que serão enviados. Clique no
   botão `+` ao lado de **Changes** para preparar todos os arquivos (*Stage*).
5. Digite uma mensagem, por exemplo `Adiciona projeto de análise de dados`, no
   campo de mensagem e clique em **Commit**.
6. Clique em **Publish Branch** ou **Publish to GitHub**.
7. Entre no GitHub quando solicitado, escolha o nome do repositório e selecione
   se ele será público ou privado.
8. Confirme a publicação. O VS Code criará o repositório no GitHub e enviará o
   commit automaticamente.

> Se o VS Code perguntar se deseja adicionar ou substituir arquivos, mantenha
> o README e os arquivos do projeto que já estão na pasta local. Não publique
> a pasta `.venv`.

### Enviar alterações futuras pelo VS Code

1. Salve os arquivos modificados.
2. Abra **Source Control** (`Ctrl+Shift+G`) e revise a lista **Changes**.
3. Clique em `+` para preparar os arquivos desejados.
4. Escreva uma mensagem que descreva a alteração e clique em **Commit**.
5. Clique em **Sync Changes** ou em **Push** para enviar as alterações ao
   GitHub.

> Evite adicionar senhas, chaves de API ou outros dados pessoais ao
> repositório. Utilize um arquivo `.gitignore` para excluir arquivos
> desnecessários, como a pasta `.venv`.