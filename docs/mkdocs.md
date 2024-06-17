# Introdução ao MkDocs

MkDocs é uma ferramenta de geração de sites estáticos voltada especificamente para a criação de documentação de projetos. Escrito em Python, MkDocs é conhecido por sua simplicidade e eficiência, permitindo que desenvolvedores e equipes técnicas criem e mantenham documentação de alta qualidade com o mínimo de esforço. Com isso, utlizamos ele para que pudessemos documentar a respeito dos sistemas que utilizamos ao decorrer do período.

## Instalação do MkDocs

### Primeiro Passo 

Se você for instalar o MkDocs pelo Windows, você têm que ter o Python e o pip na sua maquina, para saber mais a respeito [CLIQUE AQUI](https://www.python.org/downloads/). Com o python e o pip instalado veja se ele está na sua maquina com o comando `python --version` e `pip --version`, se aparecer a versão que você escolheu, você está com ele na sua maquina.

### Segundo Passo

Entre como administrador no **PowerShell** e faça o seguinte comando `pip install mkdocs` e você irar ter os comandos do mkdocs para fazer um novo projeto.

### Terceiro Passo

Para criar um novo projeto e entrar dentro dele basta fazer o comando `mkdocs new my-project` e depois entre na pasta com o comando `cd my-project`

### Quarto Passo

Agora veja o seu codigo no navegador usando o comando `mkdocs serve` e depois pegue a url e bote no navegador para ver. E pronto, você agora está usando o mkdocs.

### Quinto Passo

Antes de entrarmos nas configurações do **mkdocs.yml** você pode baixar um tema personalizado, que no meu caso eu usei o tema mkdocs material. Para utilizar ele basta fazer o comando no terminal `pip install mkdocs-material` e você poderar agora utilizar as funcionalidades do **material** oferece.

## Configuração

Nesta parte irei falar como configurei e personalizei o meu documento, ou seja, você não precisa fazer do jeito que eu fiz, porém se você gostou da estrutura deste documento, sinta-se a vontade para seguir o passo a passo abaixo :arrow_down:.


### Primeiro Passo

`site_name: Documentação dos Sitemas` -> Aqui você pode dar o nome que você quiser para o seu site.

### Segundo Passo

```
nav:
  - Home: index.md
  - Sobre: about.md
  - Introdução: intro.md
  - GLPI: glpi.md
  - MkDocs: mkdocs.md
  - Conclusão: conclusao.md
```
Aqui é uma estrutura de nav, ou seja, direcionamento para outras páginas do seu documento.

### Terceiro Passo

```
theme:
  name: material // utilizando o tema que eu escolhi 
  palette:  // Aqui eu configurei a paleta de cores pro meu documento, veja que tem modo light/dark
    # Light mode
    - scheme: default
      primary: teal
      accent: pink
      toggle:
        icon: material/toggle-switch 
        name: Switch to dark mode

    # Dark mode
    - scheme: slate
      primary: pink
      accent: teal
      toggle:
        icon: material/toggle-switch-off-outline
        name: Switch to light mode
  font:
     text: Roboto Mono  // fonte do texto
  language: pt-BR  // Principal linguagem
  features:
    - search.suggest // Oferece sugestões automáticas à medida que você digita na barra de pesquisa, ajudando a encontrar resultados relevantes mais rapidamente.
    - search.highlight // Destaca os termos de pesquisa nos resultados e na página de conteúdo para facilitar a visualização das palavras-chave procuradas.
    - search.share // Permite compartilhar os resultados da pesquisa por meio de links diretos, facilitando a distribuição de conteúdo específico.
    - navigation.instant  //  Habilita a navegação instantânea entre páginas, carregando o conteúdo de forma dinâmica sem recarregar toda a página.
    - navigation.instant.prefetch  // Pré-carrega as páginas próximas ou mais prováveis de serem acessadas, melhorando a velocidade de navegação.
    - navigation.instant.progress // Exibe uma barra de progresso durante a navegação instantânea para indicar o carregamento das páginas.
    - navigation.top // Adiciona um botão ou link que permite voltar rapidamente ao topo da página atual, melhorando a experiência do usuário na navegação de longos documentos.
  
  extra_css:
    - stylesheets/extra.css // Algumas configurações de tempo usando o css
  extra:
   social:
    - icon: fontawesome/brands/mastodon   //  Este código adiciona um ícone do Mastodon da coleção Font Awesome. 
      link: https://fosstodon.org/@squidfunk
    - icon: fontawesome/brands/mastodon
      link: https://fosstodon.org/@squidfunk
```
### Quarto Passo 

```
plugins:  // pliugins para o search
  - search
markdown_extensions:  // Utilizando uma extensão de emoji 
  - pymdownx.emoji:
      emoji_generator: !!python/name:pymdownx.emoji.to_svg
```

Com isso você terá todas as suas funcionalidades que eu tive para fazer está documentação :smile:.