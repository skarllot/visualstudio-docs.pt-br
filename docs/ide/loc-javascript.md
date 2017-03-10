---
title: "&lt; Loc &gt; (JavaScript) | Microsoft Docs"
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
  - "< > Marca XML loc JavaScript"
  - "marca XML loc JavaScript"
ms.assetid: 0d3349b6-4bdd-418f-bc11-73665305baae
caps.latest.revision: 17
caps.handback.revision: 17
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# &lt; Loc &gt; (JavaScript)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Especifica o local e o tipo de arquivo de side\-car que fornece informações localizadas do IntelliSense.  
  
## Sintaxe  
  
```  
<loc filename="filename"  
    format="vsdoc|messagebundle" />  
```  
  
#### Parâmetros  
 `filename`  
 Opcional.  O nome de raiz do arquivo de side\-car que contém informações de localização para a cultura neutra.  Quando o Visual Studio procura por informações de localização, tenta encontrar uma versão cultura específica do arquivo.  Por exemplo, se `filename` é jquery.xml, o Visual Studio procura pela pasta correta cultura específica \(como JA\) no mesmo local que o arquivo .js que contém o elemento de `<loc>` .  Se encontra a pasta cultura específica, verifica se um arquivo de jquery.xml existe nele.  Se não pode localizar o arquivo correto, em vez disso use regras gerenciados do local de recurso.  O valor padrão para `filename` é o nome do arquivo atual, mas com uma extensão .xml em vez de .js.  
  
 `format`  
 Opcional.  O tipo de arquivo de side\-car usado para localização.  Use `messagebundle` para especificar o uso de pacotes de mensagem definida por metadados abertos de Ajax.  `messagebundle` é o formato recomendado.  No entanto, esse formato não é suportado em Microsoft Ajax ou em arquivos de .winmd.  Use `vsdoc` para especificar o formato de localização do .NET Framework de padrão que é usado por Microsoft Ajax e por Tempo de Execução do Windows.  Esse atributo é opcional.  `vsdoc` é o formato padrão.  
  
## Comentários  
 O elemento de `<loc>` deve aparecer na parte superior do arquivo na mesma seção que o elemento de `<reference>` .  As regras de uso para o elemento de `<loc>` são as mesmas que o elemento de `<reference>` .  Para obter mais informações, consulte “faz referência à seção das diretivas” em [JavaScript IntelliSense](../ide/javascript-intellisense.md).  
  
 O Visual Studio processa um único elemento de `<loc>` para cada arquivo .js.  Se vários elementos de `<loc>` estiverem presentes, somente um único elemento de `<loc>` é usado.  Comportamento para determinar qual elemento de `<loc>` a usar não está definido.  
  
 Ao usar o formato de pacote de mensagem, use o atributo de `locid` nos comentários de documentação XML para especificar o valor do atributo de `name` .  
  
## Exemplo  
 O exemplo a seguir mostra como usar o elemento de `<loc>` com formato de messagebundle.  Adicione o seguinte XML para um arquivo denominado messageFilename.xml e coloque o arquivo na pasta cultura específica correta, conforme especificado na descrição do parâmetro de `filename` .  
  
```  
<?xml version="1.0" encoding="utf-8" ?>  
<messagebundle>  
  <msg name="1">A class that represents a rectangle</msg>  
  <msg name="2">The height of a rectangle</msg>  
  <msg name="3">The width of a rectangle</msg>  
</messagebundle>  
  
```  
  
 Para o exemplo de messagebundle, adicione o seguinte código para um arquivo de JavaScript em seu projeto.  O elemento de `<loc>` deve aparecer como a primeira linha no arquivo de JavaScript.  Descrições nesse código serão substituídas por descrições localizadas, se disponível.  
  
```javascript  
/// <loc filename="messageFilename.xml" format="messagebundle"/>  
  
function doSomething(a,b)   
{  
    /// <summary locid='1'>description</summary>  
    /// <param name='a' locid='2'>parameter a description</param>  
    /// <param name='b' locid='3'>parameter b description</param>  
}  
  
```  
  
 O exemplo a seguir usa o formato de VSDoc.  Adicione o seguinte XML para um arquivo denominado scriptFilename.xml e coloque o arquivo na pasta correta cultura específica.  
  
```  
<?xml version="1.0" encoding="utf-8" ?>  
<doc>  
  <assembly>  
    <name>Lights</name>  
  </assembly>  
  <members>  
    <member name="M:illuminate">  
      <summary>Activates a light. </summary>  
      <param name='a'>The light to activate. </param>  
    </member>  
  </members>  
</doc>  
  
```  
  
 Para o exemplo de VSDoc, adicione o seguinte código para um arquivo de JavaScript em seu projeto.  Descrições nesse código serão substituídas por descrições localizadas, se disponível.  
  
```javascript  
/// <loc filename="scriptFilename.xml" format="vsdoc" />  
  
function illuminate(a)   
{  
    /// <summary locid='M:illuminate'>description</summary>  
    /// <param name='a' type='Number'>parameter a description</param>  
}  
  
```  
  
## Consulte também  
 [Comentários da documentação XML](../ide/xml-documentation-comments-javascript.md)