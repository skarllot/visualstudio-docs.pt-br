---
title: "JavaScript no Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f3eee13e-30e4-4bc1-81f5-058d7e379b75
caps.latest.revision: 17
caps.handback.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# JavaScript no Visual Studio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

JavaScript é uma linguagem de primeira classe no Visual Studio.  Você pode usar a maioria ou todos os auxílios de edição padrão \(trechos de código IntelliSense, e assim por diante\) ao escrever o código JavaScript no Visual Studio IDE.  Você pode escrever código JavaScript para muitos tipos de aplicativos e serviços.  
  
 Para obter a documentação de referência da linguagem JavaScript, consulte [JavaScript](http://msdn.microsoft.com/library/d1et7k7c\(v=vs.94\).aspx).  
  
 Versões específicas do Visual Studio ou extensões específicas do Visual Studio, podem ser necessário para desenvolver serviços usando HTML e JavaScript e tipos de aplicativos específicos.  A lista a seguir contém links para obter mais informações.  
  
-   Para criar aplicativos multiplataforma usando Apache Cordova [obter o Visual Studio Tools para o Apache Cordova](http://go.microsoft.com/fwlink/p/?LinkId=397606).  
  
-   Para criar [da Windows Store](http://dev.windows.com/develop), [Windows Phone](http://dev.windows.com/develop), e aplicativos universais \(que dão suporte a ambas as plataformas\), [Obtenha as ferramentas](http://dev.windows.com/en-us/develop/downloads).  
  
-   Para criar serviços baseados em nuvem, consulte o [site do Microsoft Azure](http://azure.microsoft.com/documentation/).  
  
-   Para criar sites e aplicativos web, [consulte o site do ASP.NET](http://www.asp.net/get-started/websites).  
  
    > [!NOTE]
    >  Você pode criar um site ASP.Net vazio e usá\-lo para a programação de HTML, CSS e JavaScript.  O arquivo Webconfig fornecido pelo ASP.NET habilita a depuração no Visual Studio \(ou você pode usar ferramentas F12 quando você executa o aplicativo\).  
  
 O editor de JavaScript no Visual Studio fornece é compatível com o IntelliSense.  Para obter mais informações, consulte [JavaScript IntelliSense](../ide/javascript-intellisense.md).  
  
## Novidades no JavaScript  
 Novos recursos para JavaScript são listados na tabela a seguir.  
  
|Recurso|Descrição|  
|-------------|---------------|  
|Classes|Nova sintaxe oferece suporte à declaração de [classes](../Topic/class%20Statement%20\(JavaScript\).md).|  
|Promessas|[Promessas](../Topic/Promise%20Object%20\(JavaScript\).md) permitem a fácil e limpeza assíncrona de codificação.  Promessa construtores são suportados, juntamente com o `all` e `race` métodos de utilitário.|  
|Iteradores|Agora você pode iterar sobre os objetos que pode ser iterados \(incluindo matrizes, objetos de matriz e iteradores\), invocando um gancho de iteração personalizado com instruções a serem executadas para o valor de cada propriedade distinto.  Para obter mais informações, consulte [Iteradores e geradores](../Topic/Iterators%20and%20Generators%20\(JavaScript\).md). **Note:**  Geradores ainda não são aceitas.|  
|Funções de seta|A função de seta \(\= \>\) fornece a sintaxe abreviada para a `function` palavra\-chave que apresenta um léxico `this` associação.|  
|Novos métodos para objetos internos|O [Objeto Array](../Topic/Array%20Object%20\(JavaScript\).md), [Objeto Math](../Topic/Math%20Object%20\(JavaScript\).md), [Objeto Number](../Topic/Number%20Object%20\(JavaScript\).md), [Objeto Object](../Topic/Object%20Object%20\(JavaScript\).md), e [Objeto String](../Topic/String%20Object%20\(JavaScript\).md) objetos internos incluem muitas novas funções de utilitário e propriedades para manipular e inspecionar dados.|  
|Aprimoramentos de literal de objeto|Objetos agora dão suporte a propriedades computadas e definições do método concisa sintaxe abreviada para propriedades cujo valor é inicializado com uma variável de mesmo nome.  Para obter mais informações, consulte [Criando objetos](../Topic/Creating%20Objects%20\(JavaScript\).md).|  
|Proxies|[Proxies](../Topic/Proxy%20Object%20\(JavaScript\).md) habilitar o comportamento personalizado para objetos.|  
|Parâmetros de REST|Parâmetros de REST permitem ativar argumentos consecutivos em uma chamada de função em uma matriz.  Para obter mais informações, consulte [Funções \(\)](../Topic/Functions%20\(JavaScript\).md).|  
|Operador de visualização|O [spread operador](../Topic/Spread%20Operator%20\(...\)%20\(JavaScript\).md) \(`…`\) expande expressões que pode ser iteradas em argumentos individuais.  Por exemplo, `a.b(…array)` é aproximadamente o mesmo `a.b.apply(a, array)`.|  
|Símbolos|[Símbolo](../Topic/Symbol%20Object%20\(JavaScript\).md) objetos permitem que propriedades sejam adicionadas aos objetos existentes sem possibilidade de interferência com as propriedades do objeto existente, com nenhuma visibilidade não intencional e com outras adições não coordenadas por outro código.|  
|Cadeias de caracteres de modelo|[Cadeias de caracteres de modelo](../Topic/Template%20Strings%20\(JavaScript\).md) são literais de cadeia de caracteres que permitem expressões sejam avaliadas e concatenado com a cadeia de caracteres literal.|  
|Aprimoramentos de Unicode|Aperfeiçoamentos foram feitos para suporte a Unicode.  Por exemplo, um novo formato de sequência de escape oferece suporte a pontos de código astral \(pontos de código com mais de quatro dígitos hexadecimais\).  Para obter mais informações, consulte [Caracteres especiais](../Topic/Special%20Characters%20\(JavaScript\).md).|  
|WeakSet|A [WeakSet](../Topic/WeakSet%20Object%20\(JavaScript\).md) é uma coleção de objetos que serão limpos se não forem referenciados em nenhum outro lugar.|