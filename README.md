# BOSS - Big Open Source Sister

Sistema de documentação e _GitHub Pages_ da organização **BOSS - Big Open Source Sister**

## Dependências

- [Markdown](https://www.markdownguide.org)
- [MkDocs](https://www.mkdocs.org)
- [Pipenv](https://github.com/pypa/pipenv)
- [Markdown Linter](https://github.com/markdownlint/markdownlint)

## Configuração

### Instalando o VirtualEnvWrapper

Recomendados a utilização de um ambiente virtual criado pelo módulo
virtualenvwrapper. Existe um sítio virtual com instruções em inglês para a
instalação que pode ser acessado
[aqui](https://virtualenvwrapper.readthedocs.io/en/latest/install.html).
Mas você pode também seguir o roteiro abaixo para a instalação do ambiente:

```shell
sudo python3 -m pip install -U pip             # Faz a atualização do pip
sudo python3 -m pip install virtualenvwrapper  # Instala o módulo virtualenvwrapper
```

**OBS**: Caso não tenha acesso de administrador na máquina remova o sudo do
início do comando e adicione a _flag_ `--user` ao final do comando.

Agora configure o seu _shell_ para utilizar o **virtualenvwrapper**, adicionando essas
duas linhas ao arquivo de inicialização do seu _shell_ (`.bashrc`, `.profile`, etc.)

```shell
export WORKON_HOME=\$HOME/.virtualenvs
source /usr/local/bin/virtualenvwrapper.sh
```

Caso queira adicionar um local específico de projeto basta adicionar uma
terceira linha com o seguinte _export_:

```shell
export PROJECT_HOME=/path/to/project
```

Execute o arquivo de inicialização do _shell_ para que as mudanças surtam
efeito, por exemplo:

```shell
source ~/.bashrc
```

Agora crie um ambiente virtual com o seguinte comando (colocando o nome que
deseja para o ambiente), neste exemplo usarei o nome **boss**:

```shell
mkvirtualenv -p $(which python3) boss
```

Para utilizá-lo:

```shell
workon boss
sudo python3 -m pip install pipenv
pipenv install # Irá instalar todas as dependências usadas no projeto
```

OBS: Novamente, caso necessário, adicione a _flag_ `--user` para fazer a
instalação do pacote do pipenv.

### Iniciando o servidor MkDocs

Agora basta executar o comando abaixo para rodar o servidor do _MkDocs_
localmente:

```shell
cd boss/
mkdocs serve
```

Acesse em um navegador o endereço `http://127.0.0.1:8000` e seu servidor local do
MkDocs deve estar funcionando com _live reloading_ para que você verifique as
modificações durante o desenvolvimento.

### Análise Estática

Para garantir a qualidade estática, mesmo nas documentações, este projeto faz
uso do [markdown linter](https://github.com/markdownlint/markdownlint). Este
serviço garante que boas práticas na escrita de documentos em _Markdown_ sejam
cumpridas.

Para executar o _linter_ basta executar:

```shell
gem install mdl
mdl boss
```

O relatório da execução será aprensentado no terminal. As regras usadas pelo
_mdl_ podem ser vistas nesse link:
[REGRAS](https://github.com/markdownlint/markdownlint/blob/master/docs/RULES.md)

### Gerando o CHANGELOG

Este repositório está munido de ferramenta para geração automática de
_changelog_. Faz o uso de um pacote simples em _Node.JS_ o __standard-version__.
Para gerar uma nova revisão e o _changelog_ do repositório execute:

```shell
yarn run release # Ou npm caso seja este seu gerenciador de pacotes JS
```

Para mais informações de uso e documentação apropriada acesse o seguinte
link: [standard-version](https://github.com/conventional-changelog/standard-version)