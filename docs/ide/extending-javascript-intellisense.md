---
title: "Estendendo JavaScript IntelliSense | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "personalizando o JavaScript IntelliSense"
  - "estendendo o JavaScript IntelliSense"
  - "IntelliSense [JavaScript], estendendo"
  - "JavaScript, Estendendo o recurso IntelliSense"
  - "JavaScript, objeto do intellisense"
ms.assetid: 004e1ab6-bd7a-4327-9e01-89b9be96ba2f
caps.latest.revision: 39
caps.handback.revision: 39
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Estendendo JavaScript IntelliSense
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

O recurso de extensibilidade do IntelliSense Javascript permite que você personalize resultados do IntelliSense no editor de Javascript para bibliotecas de terceiros.  Isso pode melhorar a experiência de desenvolvedores que usam essas bibliotecas.  
  
 O serviço linguístico Javascript fornece recursos do IntelliSense para bibliotecas de terceiros Javascript que são adicionadas a um projeto.  Para a maioria das bibliotecas, a instrução completada é fornecida automaticamente pelo serviço linguístico.  A ilustração a seguir mostra um exemplo de conclusão da instrução:  
  
 ![Exemplo de conclusão da instrução](../ide/media/js_intellisense_completion.png "js\_intellisense\_completion")  
  
 Se sua biblioteca inclui descrições de variáveis, funções, e objetos em marcas padrões de comentário Javascript \(\/\), você se beneficia automaticamente, por padrão, os recursos de extensibilidade do IntelliSense, que fornecem informações descritivas em uma caixa pop\-up que aparece ao lado direito dos elementos em uma lista de conclusão, ou quando você digita o parêntese de abertura em uma chamada de função.  Os comentários na caixa pop\-up contêm a descrição do membro.  O exemplo a seguir mostra a caixa pop\-up para obter uma lista de conclusão.  
  
 ![Exemplo de uma caixa pop&#45;up de informações rápidas](../ide/media/js_intellisense_quickinfo.png "js\_intellisense\_quickinfo")  
  
 Para melhorar mais a experiência do desenvolvedor, você pode fornecer informações de tipo para os desenvolvedores na caixa janela pop\-up.  Você pode fornecer informações de tipo usando Javascript [Comentários da documentação XML](../ide/xml-documentation-comments-javascript.md) em vez de marcas padrões de comentário.  Você adicionar comentários de documentação XML usando marcas de comentário de triplo\- barra \(\/\) e um conjunto de elementos XML definido.  
  
 Como alternativa, você pode fornecer informações de tipo usando a extensibilidade do IntelliSense Javascript.  Esse recurso permite que você personalize resultados do IntelliSense criando extensões do Javascript e adicionando\-os ao contexto de script.  Na extensão, que é um arquivo Javascript, você assina os eventos que são expostas pelo objeto de `intellisense` de serviço linguístico.  Extensibilidade do IntelliSense Javascript é a solução preferencial para bibliotecas se um padrão de comportamento na biblioteca impede que o serviço linguístico Javascript fornece o nível desejado de suporte IntelliSense, se uma alternativa para declarativos comentários de documentação XML é necessária também.  Personalizando os resultados do IntelliSense, você pode criar uma experiência de primeira classe do IntelliSense, independentemente de todos os padrões de comportamento que pode restringir os recursos padrão de serviço linguístico.  Para obter mais informações, consulte [Conclusão de instrução para identificadores](../ide/statement-completion-for-identifiers.md).  
  
## Adicionando uma extensão para o contexto de script  
 Para que uma extensão do IntelliSense é executada, precisa ser adicionada ao contexto atual de script.  A extensão pode ser automaticamente adicionada ao contexto de script pelo mecanismo de descoberta automática, ou você pode adicionar a extensão para o contexto de script manualmente usando grupos de referência ou a diretiva de referência.  
  
 O mecanismo de descoberta automática permite que o serviço linguístico para localizar automaticamente as extensões que seguem a convenção de nomenclatura *libraryname*.intellisense.js do arquivo, e localizadas no mesmo diretório que a biblioteca que a extensão se aplica.  Por exemplo, uma extensão válido para a biblioteca de jQuery seria jQuery.intellisense.js.  Para as extensões mais restritivas de jQuery, você pode usar nomes de arquivo como jQuery\-1.7.1.intellisense.js \(uma extensão de versão específica jQuery.ui.intellisense.js \(\) ou uma extensão para uma biblioteca o escopo de jQuery\).  A versão mais restritiva de extensão é usada se mais de uma extensão é localizado para uma determinada biblioteca.  
  
 Se você desejar usar a extensão para todos os arquivos de projeto Javascript em vez disso, você pode escolher para adicionar a extensão para um grupo de referência.  Há vários tipos de grupos, qualquer um desses que incluem referências e implícitas desses de referência que incluem referências de trabalho dedicadas.  Para adicionar uma extensão, geralmente você precisa adicionar o arquivo como um grupo implícito de referência, um entre **Implícito \(Windows\)**, **Implícito \(Web\)**.  As referências implícitas estão no escopo para cada arquivo .js aberto no editor de códigos.  Quando você usa esse método, você precisará adicionar a extensão e o arquivo que a extensão é suplementando.  
  
 Use a página de **IntelliSense** da caixa de diálogo de **Opções** para adicionar uma extensão como um grupo de referência.  Você pode acessar a página de **IntelliSense** escolhendo **Ferramentas**, **Opções** na barra de menus e em seguida, escolha **Editor de Texto**, **JavaScript**, **IntelliSense**, **Referências**.  Para obter mais informações sobre grupos de referência, consulte [JavaScript IntelliSense](../ide/javascript-intellisense.md) e [Opções, Editor de Texto, JavaScript, IntelliSense](../ide/reference/options-text-editor-javascript-intellisense.md).  
  
 Se você desejar usar a extensão para um conjunto específico de arquivos, use uma diretiva de referência.  Quando você usa esse método, você precisa fazer referência a extensão e o arquivo que a extensão é suplementando.  Para obter informações sobre como usar a diretiva de referência, o [JavaScript IntelliSense](../ide/javascript-intellisense.md)consulte.  
  
## O IntelliSense de manipulação de eventos  
 O recurso de extensibilidade permite que você personalize resultados do IntelliSense assinar eventos como o evento de `statementcompletion` do objeto de `intellisense` de serviço linguístico.  O exemplo a seguir mostra uma extensão simples que é usada pelo serviço linguístico para ocultar os membros que começam com um sublinhado de conclusão da instrução.  Esse código é contido em underscorefilter.js e está no \\ \\*Caminho de instalação do Visual Studio*pasta \\ \\ Javascript referências.  
  
```javascript  
intellisense.addEventListener('statementcompletion', function (event) {  
    if (event.targetName === "this") return;  
  
    var filterRegex;  
  
    if (event.target === undefined || event.target === window)  
        filterRegex = /^_.*\d{2,}/;  
    else  
        filterRegex = /^_.*/;  
  
    event.items = event.items.filter(function (item) {  
        return !filterRegex.test(item.name);  
    });  
});  
```  
  
 No código anterior, a extensão verifica [propriedade de targetName](#TargetName) e as propriedades de [propriedade de destino](#Target) de evento de `statementcompletion` objeto para excluir objetos como `this` e `window`, e para garantir que uma lista válido de conclusão da instrução pode ser identificado.  Se uma lista para completar pode ser identificado, a extensão atualiza a coleção de [propriedade items](#Items) de conclusão da instrução filtrando para fora os membros que começam com um sublinhado.  
  
 Para exemplos adicionais, veja no \\ \\*Caminho de instalação do Visual Studio*pasta \\ \\ Javascript referências.  O arquivo de showPlainComments.js nesta pasta fornece exemplos de como usar outros eventos para fornecer suporte padrão do IntelliSense para marcas padrões de comentário Javascript \(\/\).  Como underscorefilter.js, showPlainComments.js já está disponível como uma extensão trabalhando, e você pode consultar informações resultante do IntelliSense para usar o comentário rótulo em seu código para variáveis, funções, e objetos.  Para exemplos adicionais, consulte [Exemplos de Código](#CodeExamples).  
  
> [!WARNING]
>  Se você alterar os arquivos de extensão incluídos com o Visual Studio, você pode desativar o Javascript IntelliSense ou o recurso suportado pela extensão.  
  
 No código de extensão, você pode criar manipuladores para os seguintes tipos de eventos usando `addEventListener`:  
  
-   `statementcompletion`, que adiciona um manipulador para um evento de conclusão da instrução.  A conclusão da instrução fornece uma lista de membros para um tipo específico que aparece após você digitar um caractere especial como um ponto \(.\), ou uma lista de identificadores que aparece quando você digita ou quando você pressionar o CTRL \+ J. o.  O tratador recebe um objeto de tipo `CompletionEvent`, que oferece suporte aos seguintes membros: [propriedade items](#Items), [propriedade de destino](#Target), [propriedade de targetName](#TargetName), e [propriedade de escopo](#Scope).  
  
-   `signaturehelp`, que adiciona um manipulador para informações de parâmetro do IntelliSense.  Informações de parâmetro fornece informações sobre o número, os nomes, e os tipos de parâmetros exigidos por uma função.  O tratador recebe um objeto de tipo `SignatureHelpEvent`, que oferece suporte aos seguintes membros: [propriedade de destino](#Target), [propriedade de parentObject](#ParentObject), [propriedade de functionComments](#FunctionComments), [propriedade de functionHelp](#FunctionHelp).  
  
-   `statementcompletionhint`, que adiciona um manipulador para informações rápidas do IntelliSense.  A caixa de informações rápidas pop\-up mostra a declaração completa para identificadores em seu código.  O tratador recebe um objeto de tipo `CompletionHintEvent`, que oferece suporte aos seguintes membros: [propriedade de completionItem](#CompletionItem), e [propriedade de symbolHelp](#SymbolHelp).  
  
 Para exemplos que mostram recursos do IntelliSense como a conclusão da instrução, informações de parâmetro, e informações rápidas, consulte [Usando IntelliSense](../ide/using-intellisense.md).  
  
> [!NOTE]
>  No Javascript, informações rápidas refere\-se a caixa pop\-up que aparece no lado direito de uma lista de conclusão.  Você não pode manualmente chamar informações rapidamente.  
  
##  <a name="intellisenseObject"></a> objeto do intellisense  
 A tabela a seguir mostra as funções que estão disponíveis para o objeto de `intellisense` .  O objeto de `intellisense` está disponível somente em tempo de design.  
  
|Função|Descrição|  
|------------|---------------|  
|`addEventListener(type, handler);`|Adiciona um manipulador de eventos para um evento do IntelliSense.<br /><br /> `type` é um valor de cadeia de caracteres.  Os valores válidos incluem `statementcompletion`, `signaturehelp`, e `statementcompletionhint`.<br /><br /> `handler` é uma função do manipulador de eventos que recebe um objeto de evento de um dos seguintes tipos:<br /><br /> -   `CompletionEvent`, usado para o evento de `statementcompletion` .<br />-   `SignatureHelpEvent`, usado para o evento de `signaturehelp` .<br />-   `CompletionHintEvent`, usado para o evento de `statementcompletionhint` .<br /><br /> Para exemplos que usam essa função, consulte [Exemplos de Código](#CodeExamples).|  
|`annotate(obj, doc);`|Especifica a documentação para um objeto copiando comentários de documentação de um objeto para outro objeto.<br /><br /> `obj` especifica o objeto para copiar a documentação.<br /><br /> `doc` especifica o objeto do qual deseja copiar a documentação.<br /><br /> Para um exemplo que mostra como usar essa função, considere [Adicionando anotações do IntelliSense](#Annotations).|  
|`getFunctionComments(func);`|Retorna os comentários para uma função especificada.<br /><br /> `func` especifica a função para que os comentários são retornados.<br /><br /> Você pode definir o parâmetro de `func` usando `completionItem.value`.<br /><br /> O objeto retornado de `functionComments` inclui os seguintes membros: `above`, `inside`, e `paramComment`.  Para obter mais informações, consulte a propriedade [propriedade de functionComments](#FunctionComments).<br /><br /> `getFunctionComments` pode ser chamado somente de dentro de um dos manipuladores de eventos registrados por `addEventListener`.<br /><br /> Para um exemplo que mostra como usar essa função, considere \\ \\*Caminho de instalação do Visual Studio*\\ \\ \\ showPlainComments.js Javascript referências.|  
|`logMessage(msg);`|Envia mensagens de diagnóstico para a janela de saída.<br /><br /> `msg` é uma cadeia de caracteres que contém a mensagem.<br /><br /> Para um exemplo que mostra como usar essa função, considere [Enviar mensagens para a janela de saída](#Logging).|  
|`nullWithCompletionsOf(value);`|Retorna um valor nulo especial para que a lista para completar é determinada pelo objeto passado para o parâmetro de `value` .<br /><br /> `value` determina a lista para completar para o valor retornado.  `value` pode ser qualquer tipo.<br /><br /> O valor de retorno nulo é tratado como o zero em tempo de design, mas a lista para completar para o valor de retorno é a mesma que a lista para completar para o parâmetro de `value` .<br /><br /> Um uso para essa função é o IntelliSense para fornecer um valor de retorno quando o tipo de retorno é previsível em tempo de execução, mas o valor de retorno é `null` em tempo de design.|  
|`redirectDefinition(func, definition);`|Instrui o IntelliSense para usar a função fornecida de definição em vez de função funcional original quando a ajuda ou **Ir Para Definição** de parâmetro são aplicativos.<br /><br /> `func` especifica a função de destino.<br /><br /> `definition` especifica a função a ser usada em vez da função de destino para informações e o **Ir Para Definição**de parâmetro.|  
|`setCallContext(func, thisArg);`|Define o contexto de chamada, ou o escopo, para a função especificada.<br /><br /> `func` especifica que a função para que define o escopo.<br /><br /> `thisArg` é um literal de objeto ao qual a palavra\-chave de `this` pode referir\-se, que especifica o novo escopo para o membro.  Você pode incluir argumentos para passar neste parâmetro, por exemplo, `intellisense.setCallContext(func, { thisArg: "", args: [23,2] });`<br /><br /> `setCallContext` fornece o comportamento similar a `Function.prototype.bind`, exceto que usado somente para suporte em tempo de design do IntelliSense.  Você pode usar `setCallContext` para definir o escopo da função se você precisar simular uma chamada para o código que não é de outra forma alcançável, de modo que quando você chama a função, a chamada de função inclua o escopo e os argumentos corretos.|  
|`undefinedWithCompletionsOf(value);`|Retorna um valor indefinido especial para que a lista para completar é determinada pelo objeto passado para o parâmetro de `value` .<br /><br /> `value` determina a lista para completar para o valor retornado.  `value` pode ser qualquer tipo.<br /><br /> O valor de retorno indefinido é tratado como indefinido em tempo de design, mas a lista para completar para o valor de retorno é a mesma que a lista para completar para o parâmetro de `value` .<br /><br /> Um uso para essa função é o IntelliSense para fornecer um valor de retorno quando o tipo de retorno é previsível em tempo de execução, mas o valor de retorno é indefinido em tempo de design.|  
|`version()`|Retorna a versão do Visual Studio.|  
  
## Membros de evento  
 As seções a seguir descrevem os membros que são expostos no objeto de eventos para os eventos a seguir: `statementcompletion`, `signaturehelp`, e `statementcompletionhint`.  
  
###  <a name="CompletionItem"></a> propriedade de completionItem  
 Retorna o identificador, conhecido como o item de conclusão, para que uma caixa pop\-up de informações rápidas é solicitada.  Esta propriedade está disponível para o objeto de evento de `statementcompletionhint` e para a propriedade de [propriedade items](#Items) do objeto de evento de `statementcompletion` .  
  
 Valor de retorno: objeto de `completionItem`  
  
 A seguir estão os membros do objeto de `completionItem` :  
  
-   `name`.  Leitura\/gravação quando usado na coleção de `items` ; caso contrário, somente leitura.  Retorna uma cadeia de caracteres que identifica o item de conclusão.  
  
-   `kind`.  Leitura\/gravação quando usado na coleção de `items` ; caso contrário, somente leitura.  Retorna uma cadeia de caracteres que representa o tipo de item de conclusão.  Os valores possíveis são método, campo, propriedade, variável, parâmetro, e reservado.  
  
-   `glyph`.  Leitura\/gravação quando usado na coleção de `items` ; caso contrário, somente leitura.  Retorna uma cadeia de caracteres que representa um ícone que é exibido na lista de conclusão.  Os valores possíveis para `glyph` usam o seguinte formato: x:*glyphType*, onde *glyphType* correspondem aos membros independentes de idioma na enumeração de <xref:Microsoft.VisualStudio.Language.Intellisense.StandardGlyphGroup> .  Por exemplo, `vs:GlyphGroupMethod` é possível para um valor `glyph`.  Quando `glyph` não é definido, a propriedade de `kind` determina o ícone padrão.  
  
-   `parentObject`.  Somente\-leitura.  Retorna o objeto pai.  
  
-   `value`.  Somente\-leitura.  Retorna um objeto que representa o valor do item de conclusão.  
  
-   `comments`.  Somente\-leitura.  Retorna uma cadeia de caracteres que contém os comentários que estão acima do campo ou variável.  
  
-   `scope`.  Somente\-leitura.  Retorna o escopo de item de conclusão.  Os valores possíveis são globais, locais, parâmetro, e membro.  
  
###  <a name="Items"></a> propriedade items  
 Obtém ou define a matriz de itens de conclusão da instrução.  Cada elemento na matriz é um objeto de [propriedade de completionItem](#CompletionItem) .  A propriedade de `items` está disponível para o objeto de evento de `statementcompletion` .  
  
 Valor de retorno: matriz  
  
###  <a name="FunctionComments"></a> propriedade de functionComments  
 Retorna os comentários para a função.  Esta propriedade está disponível para o objeto de evento de `signaturehelp` .  
  
 Valor de retorno: objeto de `comments`  
  
 A seguir estão os membros do objeto de `comments` :  
  
-   `above`.  Retorna os comentários acima da função.  
  
-   `inside`.  Retorna os comentários dentro da função, normalmente no formato de VSDoc.  
  
-   `paramComments`.  Retorna uma matriz que representa comentários para cada parâmetro na função.  Os membros da matriz incluem:  
  
    -   `name`.  Retorna uma cadeia de caracteres representando o nome do parâmetro.  
  
    -   `comment`.  Retorna uma cadeia de caracteres que contém o comentário de parâmetro.  
  
###  <a name="FunctionHelp"></a> propriedade de functionHelp  
 Retorna a ajuda para a função.  Esta propriedade está disponível para o objeto de evento de `signaturehelp` .  
  
 Valor de retorno: objeto de `functionHelp`  
  
 A seguir estão os membros do objeto de `functionHelp` :  
  
-   `functionName`.  Ler\/escrever.  Retorna uma cadeia de caracteres que contém o nome da função.  
  
-   `signatures`.  Ler\/escrever.  Obtém ou define a matriz das assinaturas de função.  Cada elemento na matriz é um objeto de `signature` .  Algumas propriedades de `signature` , como `locid`, correspondem aos atributos comuns de [Comentários da documentação XML](../ide/xml-documentation-comments-javascript.md) .  
  
     Membros do objeto de `signature` incluem:  
  
    -   `description`.  Ler\/escrever.  Retorna uma cadeia de caracteres que descreve a função.  
  
    -   `locid`.  Ler\/escrever.  Retorna um identificador de cadeia de caracteres que contém informações sobre localização da função.  
  
    -   `helpKeyword`.  Ler\/escrever.  Retorna uma cadeia de caracteres que contém a palavra\-chave da ajuda.  
  
    -   `externalFile`.  Ler\/escrever.  Retorna uma cadeia de caracteres que representa o arquivo que contém a identificação do membro  
  
    -   `externalid`.  Ler\/escrever.  Retorna uma cadeia de caracteres que representa a identificação do membro da função.  
  
    -   `params`.  Ler\/escrever.  Obtém ou define a matriz de parâmetros para a função.  Cada elemento na matriz de parâmetros é um objeto de `parameter` que tem propriedades que correspondem aos seguintes atributos do elemento de [\< param \>](../ide/param-javascript.md) :  
  
        -   `name`.  Ler\/escrever.  Retorna uma cadeia de caracteres que representa o nome do parâmetro.  
  
        -   `type`.  Ler\/escrever.  Retorna uma cadeia de caracteres que representa o tipo de parâmetro.  
  
        -   `elementType`.  Ler\/escrever.  Se o tipo é `Array`, retorna uma cadeia de caracteres que representa o tipo dos elementos da matriz.  
  
        -   `description`.  Ler\/escrever.  Retorna uma cadeia de caracteres que descreve o parâmetro.  
  
        -   `locid`.  Ler\/escrever.  Retorna um identificador de cadeia de caracteres que contém informações sobre localização da função.  
  
        -   `optional`.  Ler\/escrever.  Retorna uma cadeia de caracteres que indica se o parâmetro é opcional.  `true` indica que o parâmetro é opcional; `false` indica que não é.  
  
    -   `returnValue`.  Ler\/escrever.  Obtém ou define um objeto do valor de retorno com propriedades que correspondem aos seguintes atributos do elemento de [\< retorna \>](../ide/returns-javascript.md) :  
  
        -   `type`.  Ler\/escrever.  Retorna uma cadeia de caracteres que representa o tipo de retorno.  
  
        -   `elementType`.  Ler\/escrever.  Se o tipo é `Array`, retorna uma cadeia de caracteres que representa o tipo dos elementos da matriz.  
  
        -   `description`.  Ler\/escrever.  Retorna uma cadeia de caracteres que descreve o valor de retorno.  
  
        -   `locid`.  Ler\/escrever.  Retorna um identificador de cadeia de caracteres que contém informações sobre localização da função.  
  
        -   `helpKeyword`.  Ler\/escrever.  Retorna uma cadeia de caracteres que contém a palavra\-chave da ajuda.  
  
        -   `externalFile`.  Ler\/escrever.  Retorna uma cadeia de caracteres que representa o arquivo que contém a identificação do membro  
  
        -   `externalid`.  Ler\/escrever.  Retorna uma cadeia de caracteres que representa a identificação do membro da função.  
  
###  <a name="ParentObject"></a> propriedade de parentObject  
 Retorna o objeto pai de uma função de membro.  Por exemplo, para `document.getElementByID`, `parentObject` retorna o objeto de `document` .  Esta propriedade está disponível para o objeto de evento de `signaturehelp` .  
  
 Valor de retorno: objeto  
  
###  <a name="Target"></a> propriedade de destino  
 Retorna um objeto que representa o item à esquerda de caracteres do disparador, que é um ponto \(.\).  Para funções, `target` retorna a função para que informações de parâmetro é solicitada.  Esta propriedade está disponível para os objetos de `statementcompletion` e de `signaturehelp` .  
  
 Valor de retorno: objeto  
  
###  <a name="TargetName"></a> propriedade de targetName  
 Retorna uma cadeia de caracteres que representa o destino.  Por exemplo, para “isso. ”, retorna “ `targetName` este”.  Para “A.B” \(quando o cursor está após “B”\), `targetName` retorna “B”.  Esta propriedade está disponível para o objeto de evento de `statementcompletion` .  
  
 Valor de retorno: cadeia de caracteres  
  
###  <a name="SymbolHelp"></a> propriedade de symbolHelp  
 Retorna o item de conclusão de uma caixa de pop\-up informações rápidas é solicitada.  Esta propriedade está disponível para o objeto de evento de `statementcompletionhint` .  
  
 Valor de retorno: objeto de `symbolHelp` .  
  
 Algumas propriedades do objeto de `symbolHelp` , como `locid`, correspondem aos atributos comuns de [Comentários da documentação XML](../ide/xml-documentation-comments-javascript.md) .  
  
 A seguir estão os membros do objeto de `symbolHelp` :  
  
-   `name`.  Ler\/escrever.  Retorna uma cadeia de caracteres que contém o nome do identificador.  
  
-   `symbolType`.  Ler\/escrever.  Retorna uma cadeia de caracteres que representa o tipo do símbolo.  Os valores possíveis incluem desconhecido, booleana, o número, a cadeia de caracteres, o objeto, a função, a matriz, a data, e o Regex.  
  
-   `symbolDisplayType`.  Ler\/escrever.  Retorna uma cadeia de caracteres que contém o nome do tipo para exibir.  Se `symbolDisplayType` não é definido, `symbolType` é usado.  
  
-   `elementType`.  Ler\/escrever.  Se `symbolType` é `Array`, retorna uma cadeia de caracteres que representa o tipo dos elementos da matriz.  
  
-   `scope`.  Ler\/escrever.  Retorna uma cadeia de caracteres que representa o escopo do símbolo.  Os valores possíveis incluem global, localização, o parâmetro, e o membro.  
  
-   `description`.  Ler\/escrever.  Retorna uma cadeia de caracteres que contém uma descrição do símbolo.  
  
-   `locid`.  Ler\/escrever.  Retorna um identificador de cadeia de caracteres que contém informações sobre o símbolo de localização.  
  
-   `helpKeyword`.  Ler\/escrever.  Retorna uma cadeia de caracteres que contém a palavra\-chave da ajuda.  
  
-   `externalFile`.  Ler\/escrever.  Retorna uma cadeia de caracteres que representa o arquivo que contém a identificação do membro  
  
-   `externalid`.  Ler\/escrever.  Retorna uma cadeia de caracteres que representa a identificação do membro de símbolo.  
  
-   `functionHelp`.  Ler\/escrever.  Retorna [propriedade de functionHelp](#FunctionHelp), que podem conter informações quando é `symbolType` função.  
  
###  <a name="Scope"></a> propriedade de escopo  
 Retorna o escopo de conclusão do evento.  Os valores possíveis para o escopo de conclusão são globais e membros.  Esta propriedade está disponível para o objeto de evento de `statementcompletion` .  
  
 Valor de retorno: cadeia de caracteres  
  
## Extensões do IntelliSense de depuração  
 Você não pode depurar extensões, mas você pode usar a função de [objeto do intellisense](#intellisenseObject) para enviar informações para a janela de saída do Visual Studio.  Para um exemplo que mostra como usar essa função, considere [Enviar mensagens para a janela de saída](#Logging) posteriormente neste tópico.  Para que `logMessage` funcione, pelo menos um manipulador de eventos deve ser registrada em um extensão.  
  
##  <a name="CodeExamples"></a> Exemplos de Código  
 Esta seção inclui exemplos de código que mostram como usar as APIs de extensibilidade do IntelliSense.  Também há outras maneiras de usar essas APIs.  Para exemplos adicionais, consulte os seguintes arquivos no diretório \\ \\*Caminho de instalação do Visual Studio*pasta \\ \\ Javascript referências.  Esses são exemplos de trabalho usados pelo serviço linguístico Javascript.  
  
-   underscoreFilter.js.  Esse código oculta membros particulares do IntelliSense.  Inclui manipuladores de eventos para o evento de `statementcompletion` .  
  
-   showPlainComments.js.  Esse código fornece suporte IntelliSense para comentários padrão.  Inclui manipuladores de eventos para os eventos de `signaturehelp` e de `statementcompletionhint` .  
  
###  <a name="Annotations"></a> Adicionando anotações do IntelliSense  
 O procedimento a seguir mostra como fornecer suporte a documentação do IntelliSense para uma biblioteca de terceiros sem alterar a biblioteca diretamente.  Para fazer isso, você pode usar `intellisense.annotate` em um extensão.  
  
 Para que este exemplo funcione, você precisa dos seguintes arquivos Javascript em seu projeto:  
  
-   demoLib.js, que é um arquivo de projeto que representa uma biblioteca de terceiros.  
  
-   demoLib.intellisense.js, que é a extensão do IntelliSense.  Este arquivo não precisa ser incluído no projeto, mas precisa estar na mesma pasta que exampleLib.js.  
  
-   appCode.js, que é um arquivo de projeto que representa o código do aplicativo.  
  
##### Para adicionar uma anotação do IntelliSense  
  
1.  Adicione o seguinte código a demoLib.js.  
  
    ```javascript  
    function someFunc(a) { };  
    var rectangle;  
  
    ```  
  
2.  Adicione o seguinte código a demoLib.intellisense.js.  
  
    ```javascript  
    intellisense.annotate(someFunc, function (a) {  
        /// <signature>  
        /// <summary>Description of someFunc</summary>  
        /// <param name="a">Param a</param>  
        /// </signature>  
    });  
  
    intellisense.annotate(window, {  
        // This is a comment on a global variable named rectangle.  
        rectangle: undefined  
    });  
    ```  
  
3.  Adicione a seguinte diretiva de referência como a primeira linha em appCode.js.  O caminho usado aqui indica que os arquivos de Javascript estão na mesma pasta.  
  
    ```javascript  
    /// <reference path="demoLib.js" />  
  
    ```  
  
4.  Em appCode.js, digite o código a seguir.  Você verá os comentários de documentação XML na extensão exibida como informações de parâmetro do IntelliSense.  
  
     ![Exemplo mostrando o uso de intellisense.annotate](../ide/media/js_intellisense_annotate_paraminfo.png "js\_intellisense\_annotate\_paraminfo")  
  
5.  Em appCode.js, digite o código a seguir.  Quando você digita, você verá os comentários padrão na extensão exibida como informações rápidas do IntelliSense.  
  
     ![Exemplo mostrando o uso de intellisense.annotate](../ide/media/js_intellisense_annotations.png "js\_intellisense\_annotations")  
  
###  <a name="Logging"></a> Enviar mensagens para a janela de saída  
 O procedimento a seguir mostra como enviar mensagens para a janela de saída.  Você pode enviar mensagens para ajudá\-lo a depurar extensões do IntelliSense.  
  
 Para que este exemplo funcione, você precisa dos seguintes arquivos Javascript em seu projeto:  
  
-   exampleLib.js, que é um arquivo de projeto que representa uma biblioteca de terceiros.  
  
-   exampleLib.intellisense.js, que é a extensão do IntelliSense.  Este arquivo não precisa ser incluído no projeto, mas precisa estar na mesma pasta que exampleLib.js.  
  
-   appCode.js, que é um arquivo de projeto que representa o código do aplicativo.  
  
##### Para enviar uma mensagem para a janela de saída  
  
1.  Adicione o seguinte código a exampleLib.js.  
  
    ```javascript  
    var someVar = {  
        a: 1,  
        b: 'hello'  
    };  
    ```  
  
2.  Adicione o seguinte código a exampleLib.intellisense.js.  
  
    ```javascript  
    intellisense.addEventListener('statementcompletion', function (e) {  
        // Prints out statement completion info: Either (1) the member   
        // list, if the trigger character was typed, or (2) the   
        // statement completion identifiers.  
        // e.target represents the object left of the trigger character.  
        intellisense.logMessage(  
            e.target ? 'member list requested, target: ' + e.targetName : 'statement completion for current scope requested');  
  
        // Prints out all statement completion items.  
        e.items.forEach(function (item) {  
            intellisense.logMessage('[completion item] ' + item.name + ', kind:' + item.kind + ', scope:' + item.scope + ', value:' + item.value);  
        });  
    });  
    ```  
  
3.  Adicione a seguinte diretiva de referência como a primeira linha em appCode.js.  O caminho usado aqui indica que os arquivos de Javascript estão na mesma pasta.  
  
    ```javascript  
    /// <reference path="exampleLib.js" />  
  
    ```  
  
4.  Na janela de saída, escolha **Javascript serviço linguístico** na lista de **Mostrar saída de** .  \(Para exibir a janela de saída, **Saída** selecione no menu de exibição.\)  
  
5.  Em appCode.js, digite o código a seguir.  Quando você digita, a janela de saída mostra mensagens de serviço linguístico.  A primeira mensagem na janela de saída indica que a conclusão da instrução para o escopo atual esteve solicitada.  
  
    ```javascript  
    some  
    ```  
  
     A seguir está uma exibição parcial de saída que você deve consulte.  
  
    ```scr  
    03:16:14.3113: statement completion for current scope requested  
    03:16:14.3113: [completion item] break, kind:reserved, scope:undefined, value:undefined  
    03:16:14.3113: [completion item] case, kind:reserved, scope:undefined, value:undefined  
    03:16:14.3113: [completion item] catch, kind:reserved, scope:undefined, value:undefined  
  
    …  
    ```  
  
6.  Escolha o botão de **Limpar Tudo** na janela de saída.  
  
7.  Digite o seguinte código:  A primeira mensagem na janela de saída indica que uma lista de membros esteve solicitada.  
  
    ```javascript  
    someVar.  
    ```  
  
     A seguir está uma exibição parcial de saída que você deve ver:  
  
    ```scr  
    03:17:43.4032: member list requested, target: someVar  
    03:17:43.4032: [completion item] a, kind:field, scope:member, value:1  
    03:17:43.4032: [completion item] b, kind:field, scope:member, value:hello  
    03:17:43.4032: [completion item] constructor, kind:method, scope:member, value:  
  
    …  
    ```  
  
###  <a name="Icons"></a> Alterando os ícones do IntelliSense  
 O procedimento a seguir mostra como alterar os ícones exibidos pelo IntelliSense por padrão.  Isso pode ser útil quando você fornece informações sobre conceitos do IntelliSense biblioteca\- específicos como namespaces, classes, interfaces, enumerações e.  
  
 Para valores disponíveis no ícone, consulte <xref:Microsoft.VisualStudio.Language.Intellisense.StandardGlyphGroup>.  
  
 Para que este exemplo funcione, você precisa dos seguintes arquivos Javascript em seu projeto:  
  
-   exampleLib.js, que é um arquivo de projeto que represens uma biblioteca de terceiros.  
  
-   exampleLib.intellisense.js, que é a extensão do IntelliSense.  Este arquivo não precisa ser incluído no projeto, mas precisa estar na mesma pasta que exampleLib.js.  
  
-   appCode.js, que é um arquivo de projeto que representa o código do aplicativo.  
  
##### Para alterar os ícones  
  
1.  Adicione o seguinte código a exampleLib.js.  
  
    ```javascript  
    function Namespace(name) {  
        this._isNamespace = true;  
        window[name] = this;  
    };  
  
    function Enum(values) {  
        var e = Object.create(values);  
        e._isEnum = true;  
        return e;  
    };  
  
    var SomeNamespace = new Namespace('SomeNamespace');  
    // A constructor function is considered a class.  
    SomeNamespace.SomeClass1 = function () { }  
    SomeNamespace.Enum1 = new Enum({ VALUE1: 0, VALUE2: 1 });  
    ```  
  
2.  Adicione o seguinte código a exampleLib.intellisense.js.  
  
    ```javascript  
    intellisense.addEventListener('statementcompletion', function (e) {  
        e.items.forEach(function (item) {  
            // Detect a namespace by using the _isNamespace flag.  
            if (item.value && item.value._isNamespace) {  
                item.glyph = 'vs:GlyphGroupNamespace';  
                }  
  
            if (item.parentObject && item.parentObject._isNamespace) {  
                // The item is a member of a namespace.   
  
                // All constructor functions that are part of a namespace   
                // are considered classes.   
                // A constructor function starts with  
                // an uppercase letter by convention.    
                if (typeof item.value == 'function' && (item.name[0].toUpperCase()   
                    == item.name[0])) {  
                    item.glyph = 'vs:GlyphGroupClass';  
                }  
  
                // Detect an enumeration by using the _isEnum flag.  
                if (item.value && item.value._isEnum) {  
                    item.glyph = 'vs:GlyphGroupEnum';  
                }  
            }  
        });  
    });  
  
    intellisense.addEventListener('statementcompletionhint', function (e) {  
        if (e.completionItem.value) {  
            if (e.completionItem.value._isNamespace) {  
                e.symbolHelp.symbolDisplayType = 'Namespace';  
            }  
            if (e.completionItem.value._isEnum) {  
                e.symbolHelp.symbolDisplayType = 'Enum';  
            }  
        }  
    });  
    ```  
  
3.  Adicione a seguinte diretiva de referência como a primeira linha em appCode.js.  O caminho usado aqui indica que os arquivos de Javascript estão na mesma pasta.  
  
    ```javascript  
    /// <reference path="exampleLib.js" />  
  
    ```  
  
4.  Em appCode.js, digite o código a seguir.  Quando você digita, você verá que o ícone para o namespace mudou “{}”, como é usado em C\#.  
  
     ![Exemplo mostrando o uso da propriedade de glifo](../ide/media/js_intellisense_glyph_namespace.png "js\_intellisense\_glyph\_namespace")  
  
5.  Em appCode.js, digite o código a seguir.  Quando você digita, você verá um novo ícone de enumeração para o membro Enum1, e um novo ícone de classe para o membro SomeClass1.  
  
     ![Exemplo mostrando o uso da propriedade de glifo](../ide/media/js_intellisense_glyph_class_enum.png "js\_intellisense\_glyph\_class\_enum")  
  
###  <a name="Overriding"></a> Evitando efeitos de tempo de execução nos resultados do IntelliSense  
 O código de blocos de serviço linguístico Javascript para fornecer dinamicamente informações do IntelliSense.  Como resultado, o comportamento em tempo de execução pode ocasionalmente interferir com os resultados desejados.  O procedimento a seguir mostra como substituir resultados do IntelliSense quando o comportamento em tempo de execução resulta em IntelliSense incorreto.  
  
 Para que este exemplo funcione, você precisa dos seguintes arquivos Javascript em seu projeto:  
  
-   exampleLib.js, que é um arquivo de projeto que representa uma biblioteca de terceiros.  
  
-   exampleLib.intellisense.js, que é a extensão do IntelliSense.  Este arquivo não precisa ser incluído no projeto, mas precisa estar na mesma pasta que exampleLib.js.  
  
-   appCode.js, que é um arquivo de projeto que representa o código do aplicativo.  
  
##### Para evitar efeitos de tempo de execução nos resultados do IntelliSense  
  
1.  Adicione o seguinte código a exampleLib.js.  
  
    ```javascript  
    function after(count, func) {  
        return function () {  
            if (--times < 1) {  
                return func.apply(this, arguments);  
            }  
        };  
    };  
    ```  
  
     No código anterior, a função set ignora chamadas inicial, com base no valor de `count`, e retorna resultados.  
  
2.  Adicione a seguinte diretiva de referência como a primeira linha em appCode.js.  O caminho usado aqui indica que os arquivos de Javascript estão na mesma pasta.  
  
    ```javascript  
    /// <reference path="exampleLib.js" />  
  
    ```  
  
3.  Em appCode.js, digite o código a seguir.  A lista do IntelliSense aparece em vez de como a função é chamada nunca definido, o que significa que a função de `throttled` não retorna os resultados.  
  
     ![Exemplo de substituição intellisense resultados](../ide/media/js_intellisense_override.png "js\_intellisense\_override")  
  
4.  Adicione o seguinte código a exampleLib.intellisense.js.  Isso irá alterar o comportamento de tempo de design para que o IntelliSense é mostrado para a função set, como esperado.  
  
    ```javascript  
    window.after = function (count, func) {  
        // Just return func.   
        return func;  
    };  
    ```  
  
5.  Em appCode.js, testar os resultados digitando o mesmo código que você digitou anteriormente.  Desta vez, o IntelliSense fornecem informações desejada.  
  
     ![Exemplo de substituição IntelliSense resultados](../ide/media/js_intellisense_override_fixed.png "js\_intellisense\_override\_fixed")  
  
## Consulte também  
 [JavaScript IntelliSense](../ide/javascript-intellisense.md)   
 [Conclusão de instrução para identificadores](../ide/statement-completion-for-identifiers.md)