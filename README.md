# Themes Pack 2.0 - by caulecriativo.com


Criado por Ricardo Correia para a comunidade Home Assistant Brasil
São 10 cores modernas, totalizando 40 temas diferentes!

Quero pedir apenas 2 coisas para quem se beneficiar com esses temas:

1) Entre na comunidade HABR no Discord: [habr.ml](http://habr.ml)
2) Siga meu estúdio de criação no instagram: [caulecriativo.com](http://caulecriativo.com) ☺️

Faça bom aproveito dos temas =)<br><br>
![](https://github.com/orickcorreia/ha-themes-pack-2.0/blob/master/images/pack1.png)
![](https://github.com/orickcorreia/ha-themes-pack-2.0/blob/master/images/pack2.png)
![](https://github.com/orickcorreia/ha-themes-pack-2.0/blob/master/images/pack3.png)
![](https://github.com/orickcorreia/ha-themes-pack-2.0/blob/master/images/pack4.png)<br><br>
![](https://github.com/orickcorreia/ha-themes-pack-2.0/blob/master/images/01-rose.png)
![](https://github.com/orickcorreia/ha-themes-pack-2.0/blob/master/images/02-purple.png)
![](https://github.com/orickcorreia/ha-themes-pack-2.0/blob/master/images/03-blue.png)
![](https://github.com/orickcorreia/ha-themes-pack-2.0/blob/master/images/04-aqua.png)
![](https://github.com/orickcorreia/ha-themes-pack-2.0/blob/master/images/05-green.png)
![](https://github.com/orickcorreia/ha-themes-pack-2.0/blob/master/images/06-yellow.png)
![](https://github.com/orickcorreia/ha-themes-pack-2.0/blob/master/images/07-orange.png)
![](https://github.com/orickcorreia/ha-themes-pack-2.0/blob/master/images/08-coral.png)
![](https://github.com/orickcorreia/ha-themes-pack-2.0/blob/master/images/09-pink.png)
![](https://github.com/orickcorreia/ha-themes-pack-2.0/blob/master/images/10-gray.png)
<br>
# Instalação dos temas
## Se você já tem um arquivo themes.yaml
Então é só copiar o código ou fazer download do [**themes.yaml** clicando aqui](https://github.com/orickcorreia/ha-themes-pack-2.0/blob/master/src/pt-br/themes.yaml).<br><br>
## Se você AINDA NÃO tem um arquivo themes.yaml
Então você precisa configurar seu arquivo **configuration.yaml**, acrescentando o código que segue abaixo:
<br>
```
frontend:
  themes: !include themes.yaml
```
Após inserir a configuração no seu **configuration.yaml**, faça o download do arquivo [**themes.yaml** clicando aqui](https://raw.githubusercontent.com/orickcorreia/ha-themes-pack-2.0/master/src/pt-br/themes.yaml) e copie esse arquivo para sua pasta **config**. O arquivo **themes.yaml** deve estar na mesma pasta do arquivo **configuration.yaml**.<br><br>
## Download dos backgrounds
10 dos 40 temas possuem backgrounds que precisam ser baixados e copiados para o seu servidor do Home Assistant.<br>
Baixe os backgrounds [**clicando aqui.**](https://github.com/orickcorreia/ha-themes-pack-2.0/raw/master/src/backgrounds.zip) Extraia o arquivo **.zip** e copie a pasta **backgrounds** para dentro da pasta **config/www/**.<br>
ATENÇÃO! Se a pasta **www** ainda não existir, crie ela dentro da pasta **config**.
<br>
ATENÇÃO! Para exibir os backgrounds vc vai precisar colocar esse código em cada views da sua interface lovelace:
```
background: var(--background-image)
```
Exemplo de como deve ficar:
```
  - title: Home #título da sua view
    path: home #caminho para o url
    background: var(--background-image) #configuração para exibir o background
    icon: mdi:home-circle #icone da sua view
    cards:
```

Feito isso, reinicie o seu Home Assistante e os temas estarão disponíveis para uso.
<br><br>
# Criando seletor automático para usar na interface (opcional)
Vamos criar um seletor de temas para ser implementado na sua interface do usuário. É uma forma prática de alterar o tema instantaneamente em todos os dispositivos conectados ao seu Home Assistant. Veja como funciona no gif abaixo:<br>
![](https://github.com/orickcorreia/ha-themes-pack-2.0/blob/master/images/seletor.gif)

## 1ª Etapa - Criando o input_select
O input_select será usado para criar a lista de seleção com os temas que eu criei.<br>
Se você nunca usou input select, [saiba mais clicando aqui](https://www.home-assistant.io/integrations/input_select)<br><br>
```
input_select:

  themes:
    name: 'Temas'
    icon: mdi:format-paint
    options:
      - Black Rose - Flat
      - Black Purple - Flat
      - Black Blue - Flat 
      - Black Aqua - Flat
      - Black Green - Flat
      - Black Yellow - Flat
      - Black Orange - Flat
      - Black Coral - Flat
      - Black Pink - Flat
      - Black Gray - Flat
      - Dark Rose - Flat
      - Dark Purple - Flat
      - Dark Blue - Flat 
      - Dark Aqua - Flat
      - Dark Green - Flat
      - Dark Yellow - Flat
      - Dark Orange - Flat
      - Dark Coral - Flat
      - Dark Pink - Flat
      - Dark Gray - Flat
      - Light Rose - Flat
      - Light Purple - Flat
      - Light Blue - Flat 
      - Light Aqua - Flat
      - Light Green - Flat
      - Light Yellow - Flat
      - Light Orange - Flat
      - Light Coral - Flat
      - Light Pink - Flat
      - Light Gray - Flat
      - Black Rose - Transparent
      - Black Purple - Transparent
      - Black Blue - Transparent 
      - Black Aqua - Transparent
      - Black Green - Transparent
      - Black Yellow - Transparent
      - Black Orange - Transparent
      - Black Coral - Transparent
      - Black Pink - Transparent
      - Black Gray - Transparent      
      - Default
```
Reinicie o seu Home Assistant para que o input_select seja criado.<br>

Resultado:
* input_select.themes
<br><br>

## 2ª Etapa - Automação do seletor de temas no Node-RED

ATENÇÃO! Se você nunca usou o Node-RED, [saiba mais clicando aqui.](https://github.com/hassio-addons/addon-node-red)<br><br>
Vamos criar um flow no Node-RED para definir o tema automaticamente toda vez que você escolher um tema na sua interface.<br>
É bem simples! Basta fazer o download do arquivo .json ou copiar o código e colar na janela de importação do Node-RED.<br>
[Clique aqui para copiar ou fazer download do código dos fluxos do Node-RED](/src/seletor_theme_nodered.json)<br><br>
Após importar o flow para o seu Node-RED, clique em **Deply**<br><br>

## 3ª Etapa - Implementando o seletor na sua interface

Agora é só inserir o código do seletor na sua interface.
* Se você usa a interface no Modo YAML, copie o código e insira no seu **ui-lovelace.yaml**
* Se você usa a interface no modo automático, vá até o modo de edição da sua interface, escolha a opção "manual" lá no final, depois copie e cole o código abaixo.

``` 
- type: entities
  show_header_toggle: false
  entities:
    - entity: input_select.themes

``` 

### Agora é só aproveitar!
