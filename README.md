
# JQuery WebpAlt
WebpAlt troca as imagens no formato WEBP por imagens alternativas definidas por você quando o navegador não suportar o formato.

### Intro
Este projeto oferece uma solução simples para websites que possuem imagens no formato WEBP e tem dificuldades em serem carregados em navegadores sem suporte à extensão (ex. Safari).

Com ele você consegue definir imagens alternativas para serem carregadas sempre o navegador do visitante não oferecer suporte a extensão WEBP

## Requisitos

 - Jquery
 - Navegador com suporte a javascript

## Como funciona
Chame o script entre as tags `<head></head>` ou antes de fechar a tag `</body>`, é importante que ele seja carregado após o **JQuery**:

```html
 <script src="jquery.min.js"></script>
 <script src="jquery.webpalt.min.js"></script>
```
Agora inicie o plugin em uma tag ou seletor de sua preferência:

```html
<script>  
    $(function(){  
        $("img").WebpAlt(); 
    });
</script>
```

Por padrão, caso a fonte da imagem esteja no formato **WEBP**, o plugin irá procurar no elemento o atributo **data-altsrc** como fonte alternativa para a imagem, caso ele não esteja definido no DOM ele irá editar o URL a imagem e alterar a extensão final para uma extensão que pode ser definia nas configurações do plugin. 

O plugin utiliza um pacote do **modernizr** par adectar a compatibilidade do navegador com o formato WEBP, esse pacote já está incluso no código fonte do plugin e contem apenas a extensão do modernizr necessária para esta detecção, evitando códigos desnecessários em seu site.

### Opções e configurações
Existem algumas opções que você pode alterar para adaptar o comportamento do plugin para as suas necessidades:

| Opção | Tipo | Valor Padrão | Descrição |
|--|--|--|--|
| **altExtension** | string | `.png` | Extensão alternativa padrão. Pode ser definina individualmente no elemento com o atributo **data-altext** |
| **altSrcData** | string | `altsrc` | Atributo **"data"** que contem a **URL da imagem alternativa** para ser carregada no lugar do **WEBP**, caso não esteja definido no elemento, a **URL do WEBP** será utilizada como base para a **URL alternativa** sendo alterada apenas a **extensão** |
| **defaultSrcAttr** | string | `src` | Attributo que contém a referência ao WEBP, pode ser alterado caso utilize algum script de LazyLoad (data-src). |
| **afterItem** | function | `function (item){ };`| Funcão que será executada após o processamento individual de cada item, retorna o **item processado** como parâmetro. |
| **afterAll** | function | `function (itens){ };`| Funcão que será executada após o processamento geral, retorna o array de itens referentas ao seletor do plugin. |


### Funções de Callback
O plugin contém duas funções de callback que serão envocadas após o processamento individual de cada item e após o processamento completo. Você pode utilizá-los para fazer com que o plugin trabalhe juntamente com outros plugins relacionados a imgens.
#### Veja um exemplo com **JQuery LazyLoad**:
```html
<script src="jquery.min.js"></script>
<script src="jquery.webpalt.min.js"></script>
<script src="jquery.lazy/jquery.lazy.min.js"></script>
<script src="jquery.lazy/jquery.lazy.plugins.min.js"></script>


<script>  
    $(function(){  
        $("img").WebpAlt({
            defaultSrcAttr : "data-src",	//Define o atributo de referência do WEBP como data-src (padrão do JQuery LazyLoad).
            afterAll : function(itens){
		//Executa o LazyLoad após o processamento das imagens
		$("img").lazy();
            }
        }); 
    });
</script>
```

### Em breve
- Reconhecer também imagens de fundo definidas por CSS.
- Disponibilizar o plugin em CDN.


## Licença
Este pacote é um software gratuito distribuído sob os termos da licença MIT. # WebpAlt
O WebpAlt altera as imagens do webp para uma outra extensão quando o navegador do usuário não pode carregá-lo.

