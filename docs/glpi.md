# Introdução ao GLPI

## Instalação do GLPI

Como já vimos, o **GLPI** é um sistema de gerenciamento de TI. Nele você pode adicionar ativos, chamados, criação de usuários, etc. Há mais funcionalidades nele porém vamos para o processo de como podemos instalar o GLPI. Diante mão já venho dizer que há três maneiras básicas de instalar o **GLPI**, são elas: <br> 
 
### Algumas formas de instalar
 - [XAMPP](https://www.apachefriends.org/pt_br/index.html): O XAMPP é uma distribuição do Apache fácil de instalar contendo PHP, MySQL e Perl. 
 - [WSL](https://learn.microsoft.com/pt-br/windows/wsl/): Subsistema Windows para Linux.
 - [VitualBox](https://www.virtualbox.org/): Uma VM é uma representação virtual de um computador físico.

## Meu processo de instalação e configuração

### Primeiro Passo

Eu utilizei o **XAMPP** para usar o GLPI, pois eu queria ver como ele iria conseguir executar o GLPI. **Primeiro passo** é instalar o [XAMPP](https://www.apachefriends.org/pt_br/download.html). Quando você entrar no site haverá três opções, no meu caso eu usei a versão do windows:


| Versão              | Soma de verificação | tamanho |
| ------------------- | ------------------- | ------- |
| 8.0.30 / PHP 8.0.30 | md5 sha1            | 144mb   |

Como o XAMPP instalado agora você tem que baixar uma pasta do [GLPI](https://glpi-project.org/pt-br/baixar/) **A versão mais recente estável**, que é a  GLPI 10.0.15. Agora temos tudo que precisamos para utilizar o GLPI :smile:.

### Segundo Passo

Na **segunda parte** agora você vai ter que pegar a pasta GLPI que você baixou e extrair ela. Após extrair a pasta, você vai recotar ela e ir para a pasta do **XAMPP**. Entre na pasta XAMPP e você verá várias paginas:

![pastas do XAMPP](img/xampp-src.png)

Localize a pasta htdocs, bote a pasta que voceê recortou dentro dela, e agora o **XAMPP** vai conseguir usar as funcionalidades do GLPI. 

### Terceiro Passo

**OBS:** essa **terceira parte** é um problema que pode acontecer se você tiver o mysql instalado, pois tanto o **MYSQL** quanto o **XAMPP** utiliza a porta *3306* principal no [**mySQL**](https://www.mysql.com/), porém como eu já estava utilizando ele no root, do **mySQL WorkBeench** eu tive que fazer umas configurações a mais no XAMPP. Então se você não tiver esse problema você pode pular para o [**Quarto Passo**](#quarto-passo). O problema que me forneceu foi esse aqui:

```
09:25:43  [mysql]     Problem detected!
09:25:43  [mysql]     Port 3306 in use by "Unable to open process"!
09:25:43  [mysql]     MySQL WILL NOT start without the configured ports free!
09:25:43  [mysql]     You need to uninstall/disable/reconfigure the blocking application
09:25:43  [mysql]     or reconfigure MySQL and the Control Panel to listen on a different port
```

Caso você receba esse erro, você pode ir em **ACTIONS** e na parte onde está escrito **config** tanto no Module **Apache** como no Module **mySQL**, você terá que trocar a porta que está padrão 3306, para a porta 3307. No Module do mySQL haverá o arquivo **my.ini**, entre nele com o bloca de notas e encontre onde o sistema botou como padrão a porta 3306 e troque para 3307, e depois salve o arquivo editado. Para você achar mais rapido recomendo que use o atalho `Crtl + F` e após ele pesquise sobre 3306. Faça esse mesmo processo no pasta do Module do Apache, onde o nome do arquivo é **php.ini**, e troque tudo para a porta 3307. Pronto, agora você terá o seu banco rodando na porta 3307 como está abaixo :arrow_down:

![XAMPP em Execução](img/xampp-execucao.png)

### Quarto Passo

Agora temos tudo que precisamos para utilizar o **GLPI**. Primeiro clique em start tanto no **Apache** como no **mySQL**, após isso você pode ir no seu navegador principal e bote a `URL: http://localhost/glpi`, quando você botar isso você será direcionando para a aba principal do **GLPI**.

#### Primeiro Passo GLPI

No **Primeiro passo** ele vai pedir que tipo de linguagem você quer definir como padrão para o seu sistema. No meu caso eu utlizei a linguagem portuguesa mesmo.

#### Segundo Passo GLPI

No **Segundo passo** haverá um nota de licença do  **GLPI**, só aperte o botão **Continuar** e você irá para o terceiro passo.

#### Terceiro Passo GLPI

No **Terceiro passo** você terá duas opções **Instalar** e **Atualizar**, se você fez tudo que eu lhe falei até o momento, aperte no botão de instalar.

#### Quarto Passo

Após isso você perceberá que vai haver várias coisas faltando no seu setup, porém você só precisará alterar duas para que o seu sistema esteja pronto. Veja abaixo :arrow_down:

![GLPI problema](img/glpi-problema.png)
[Referência da imagem](https://www.youtube.com/watch?v=7-CqrK9pxz4&t=9s)

Veja que o **gd** e o **intl** não estão no seu sistema. Neste caso você terá que adicionar eles. Vá no **Module Apache**, como fizemos na outra vez e de novo entre no **config** do **php.ini**. Localize o **gd** e o **intl** dentro do arquivo, pois possivelmente eles estarão comentado. Descomente eles e salva o arquivo no bloco de notas. Atualize o navegador e agora você pode ir para a próxima etapa, somente clicando em **Continuar**

#### Quinto Passo

Agora você irar criar uma conexão com  o banco de dados para armazenar seus arquivos.

| Enderço do servidor | Usuário SQL | Senha |
| ------------------- | ----------- | ----- |
| localhost           | root        |       |

Feito isto, clique em **Continuar**

#### Sexto Passo

Agora ele vai pedir para você criar um banco de dados. Você pode botar qualquer nome para o seu banco, no meu caso eu botei *glpi*, após isso, aperte em **Continuar**.

#### Sétimo Passo

Ele vai perguntar se pode fazer agora a criação do banco de dados,  aperte em **Continuar**.

#### Oitavo Passo

Ele vai pedir a coleta de dados, aperte em **Continuar**.

#### Nona Passo

Finalmente ele vai perguntar se você deseja utilizar o **GLPI**. Aperte em **Usar o GLPI**.

#### Decimo Passo 

Agora é só entrar no sistema e configurar de acordo com o que você deseja.

| Nome do utilizador | Palavra passe |
| ------------------ | ------------- |
| glpi               | glpi          |

**Utilize o que está acima para entrar como administrador no seu sistema GLPI**

### Quinto Passo

Se você chegou até aqui, você finalmente vai pode utilizar o seu sistema glpi, veja como ficou o meu projeto abaixo:

![GLPI - 1](img/glpi2.png)

![GLPI - 2](img/glpi3.png)

![GLPI - 3](img/glpi4.png)

![GLPI - 4](img/glpi5.png)


Caso você ainda tenha problemas, [CLIQUE AQUI](https://www.youtube.com/watch?v=7-CqrK9pxz4&t=9s) para mais informações sobre esse mesmo processo


