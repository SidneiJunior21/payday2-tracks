# Repositório de CustomOSTs para Payday 2

Bem-vindo ao nosso repositório de trilhas sonoras customizadas (CustomOSTs) para Payday 2! Este espaço é dedicado a todos os heisters que desejam uma nova trilha sonora para seus assaltos. Aqui você encontrará uma coleção de músicas prontas para serem usadas no jogo, como também um tutorial e templates para você fazer sua propria track.

## Como Adicionar uma Trilha Sonora Customizada (CustomOST) no Jogo

Para utilizar as trilhas sonoras deste repositório, você precisa ter o jogo preparado para receber mods. O processo é simples, mas requer a instalação de algumas ferramentas essenciais.

### Pré-Requisitos

Antes de instalar qualquer música, você **precisa** ter os seguintes mods instalados:

1.  **SuperBLT**: É o carregador de mods fundamental para Payday 2. Ele permite que o jogo carregue mods em Lua, que são a base para a maioria das modificações, incluindo as de música.
2.  **BeardLib**: Uma biblioteca de modding que simplifica a criação e adição de conteúdo customizado, como heists, armas e, o mais importante para nós, músicas.
3.  **Custom OST Fixer/Converter**: Um mod que converte esse arquetipo de CustomOST para *BeardLib music module tracks*

Não é algo obrigatório, mas uma ótima recomendação:

1.  **Music Volume Mixer**: Um mod para controlar o volume de cada musica individualmente, muito útil por ser muito difícil de se manter um volume contante para cada track

### Passos para Instalação dos Pré-Requisitos

1.  **Instalando o SuperBLT:**
    * Baixe o arquivo `latest release DLL` do [site oficial do SuperBLT](https://superblt.znix.xyz/).
    * Extraia o arquivo `WSOCK32.dll` para a pasta principal do seu Payday 2 (a mesma pasta onde está o `payday2_win32_release.exe`).
    * Inicie o jogo. O SuperBLT pedirá para baixar o "base mod". Clique em "Sim" e espere o download terminar. O jogo irá fechar ou reiniciar.

2.  **Instalando o BeardLib:**
    * Baixe a versão mais recente do [BeardLib no ModWorkshop](https://modworkshop.net/mod/14924).
    * Abra o arquivo `.zip` baixado.
    * Extraia a pasta `BeardLib` para dentro da sua pasta `mods`, que está localizada no diretório principal do Payday 2 (`PAYDAY 2/mods/`). Se a pasta `mods` não existir, crie-a.

2.  **Instalando o Custom OST Fixer/Converter:**
    * Baixe a versão mais recente do [Custom OST Fixer/Converter](https://modworkshop.net/mod/40369).
    * Abra o arquivo `.zip` baixado.
    * Extraia a pasta `CustomOST_Fixer` para dentro da sua pasta `mods`, que está localizada no diretório principal do Payday 2 (`PAYDAY 2/mods/`). Se a pasta `mods` não existir, crie-a.
    * Crie uma pasta chamada `CustomOSTTracks` dentro da pasta `CustomOST_Fixer`.
   
### Instalando a CustomOST 

Com os pré-requisitos instalados, adicionar uma nova música é muito fácil:

1.  **Escolha e Baixe a Música:**
    * Navegue pelas pastas deste repositório.
    * Escolha a trilha sonora que você deseja e baixe a pasta inteira dela.

2.  **Instale no Jogo:**
    * Vá até a pasta `CustomOST_Fixer` dentro da sua pasta `mods` (localizada em `PAYDAY 2/mods/`).
    * Arraste e solte a pasta da música que você baixou para dentro da pasta `CustomOSTTracks`.

Pronto! A nova trilha sonora estará disponível no jogo. Você pode selecioná-la nas opções de áudio do jogo, e na seção de trilhas sonoras customizadas dentro do menu de preparação do Heist.

---

## Como Criar sua Própria CustomOST

Criar sua própria trilha sonora para Payday 2 requer um pouco de trabalho, mas é um processo gratificante. Você precisará de um software de edição de áudio e um editor de texto.

### Ferramentas Necessárias

* **Editor de Áudio**: [Audacity](https://www.audacityteam.org/download/) (gratuito e recomendado) ou qualquer outro software que permita cortar e exportar áudio.
* **Editor de Texto**: [Notepad++](https://notepad-plus-plus.org/) (recomendado) ou similar, para editar arquivos de configuração, o próprio bloco de notas nativo do windows também serve.
* **Template de Música**: Baixe o `Template OST` dentro deste repositório para usar como base para sua track.

### Estrutura de uma Trilha Sonora de Heist

Uma trilha sonora de heist em Payday 2 é dividida em 4 partes principais, que tocam em momentos diferentes do jogo:

* **Setup**: A música calma que toca durante a fase furtiva.
* **Control**: Uma faixa de transição, um pouco mais tensa, que toca quando o alarme soa ou antes do assalto começar.
* **Buildup (Anticipation)**: Uma seção crescente que prepara para o início da onda de assalto.
* **Assault**: A parte mais intensa da música, que toca durante as ondas de ataque da polícia.

Tenha em vista também que cada parte pode ter uma intro, uma parte que toca uma única vez antes de cada loop de alguma parte principal, geralmente sendo `begin_xxx.ogg`.

### Passo a Passo para Criar sua CustomOST

1.  **Prepare seus Arquivos de Áudio:**
    * Escolha a música que você quer usar.
    * Use o Audacity para cortar a música nas 4 seções (Setup, Control, Buildup, Assault). Tente fazer com que as transições e loops soem naturais.
    * Exporte cada uma dessas seções como um arquivo `.ogg`. É crucial usar o formato OGG, pois o jogo utiliza ele.

2.  **Configure a Estrutura de Pastas:**
    * Descompacte o "Music Module Template" que você baixou. Você terá uma estrutura de pastas.
    * Renomeie a pasta principal para o nome da sua música (ex: `MinhaMusicaIncrivel`).
    * Dentro da pasta `sounds`, coloque os seus 4 arquivos `.ogg` e renomeie-os para:
        * `Setup.ogg`
        * `control.ogg`
        * `buildup.ogg`
        * `assault.ogg`

3.  **Edite os Arquivos de Configuração:**
    * **` track.txt`**: Abra este arquivo com o Notepad++. Você verá algo como:
        ```txt
      {
          "id": "id_da_track",
          "volume": 6.0,
          "name": "nome da track",
          "fade_transition": true,
          "fade_duration": 1,
          "events": {
              "setup": {
	                "start_file": "begin_setup.ogg",
                  "file": "setup.ogg",
                  "alt": "setup_alt.ogg",
                  "alt_chance": 0.5
              },
              "control" : { 
	                "start_file": "begin_control.ogg",
                  "file": "control.ogg",
                  "alt": "control_alt.ogg",
                  "alt_chance": 0.5
              },     
              "buildup": {
	                "start_file": "begin_buildup.ogg",
                  "file": "buildup.ogg",
                  "alt": "buildup_alt.ogg",
                  "alt_chance": 0.5
              },
              "assault" : {
                  "start_file": "begin_assault.ogg",
                  "file": "assault.ogg",
                  "alt": "assault_alt.ogg",
                  "alt_chance": 0.5
              }
          }
      }
        ```
        * Altere `id_da_track` para um identificador **único** para sua música (sem espaços, use `_`), tenha em mente que esse id só serve como um identificador no xml do jogo, esse id nunca será visível dentro do jogo.
        * Altere `nome da track` para o nome que vai aparecer dentro do jogo.
        * Dentro de eventos, é obrigatório alterar as partes `file: xxx.ogg` dentro de cada parte (Setup, Control, Buildup, Assault); É opcional alterar os arquivos `start_file: begin_xxx.ogg` (que serve como uma parte que vai tocar no começo de cada loop) e `alt: "xxx_alt.ogg"` junto com `alt_chance: 0.5` (esses dois juntos servem para adicionar uma variante alternativa dessa parte em específico, para definir a chance dessa versão alternativa tocar no lugar da convencional altere o valor dentro de `alt_chance: 0.5`, esse valor vaira de 1 a 0, 1 tocando sempre e 0 nunca, mesmo não tendo tanto sentindo por esses valores como 1 e 0 kk).
**Obs: Caso nenhuma dessas partes opcionais forem usadas é necessário que elas sejam removidas do txt e da pasta da track.**

4.  **Teste sua Música:**
    * Coloque a pasta da sua CustomOST (ex: `MinhaMusicaIncrivel`) para dentro da pasta `CustomOSTTracks` (`PAYDAY 2/mods/CustomOST_Fixer/CustomOSTTracks`).
    * Inicie o jogo e verifique se a música aparece nas aba de tracks customizadas dentro de um heist, tenha em mente que para a lista de tracks ser atualizadas e sua track nova aparecer é necessário que o jogo recarregue a lista de OST, então sua nova track não será visível a partir do menu.

Parabéns, você criou sua própria trilha sonora para Payday 2! Sinta-se à vontade para fazer um "pull request" e adicioná-la a este repositório para que outros possam curtir.
