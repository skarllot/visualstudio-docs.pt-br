---
title: JavaScript no Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f3eee13e-30e4-4bc1-81f5-058d7e379b75
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: d4741ff741b89997bbfe4fea9b0f60bba84e63db
ms.lasthandoff: 02/22/2017

---
# <a name="javascript-in-visual-studio"></a>JavaScript no Visual Studio
O JavaScript é uma linguagem de primeira classe no Visual Studio. Você pode usar a maioria ou todos os auxílios de edição padrão (trechos de código IntelliSense, e assim por diante) ao escrever o código JavaScript no Visual Studio IDE. Você pode escrever código JavaScript para muitos tipos de aplicativos e serviços.  
  
 Para obter a documentação de referência da linguagem JavaScript, consulte [JavaScript](http://msdn.microsoft.com/library/d1et7k7c\(v=vs.94\).aspx).  
  
 Versões específicas do Visual Studio ou extensões específicas do Visual Studio podem ser necessárias para desenvolver serviços e tipos de aplicativo específicos usando HTML e JavaScript. A lista a seguir contém links para obtenção de mais informações.  
  
-   Para criar aplicativos de plataforma cruzada usando o Apache Cordova, [obtenha as Ferramentas do Visual Studio para Apache Cordova](http://go.microsoft.com/fwlink/p/?LinkId=397606).  
  
-   Para criar aplicativos [da Windows Store](http://dev.windows.com/develop), [do Windows Phone](http://dev.windows.com/develop) e universais (que dão suporte a ambas as plataformas), [obtenha as ferramentas](http://dev.windows.com/en-us/develop/downloads).  
  
-   Para criar serviços baseados em nuvem, consulte o [site do Microsoft Azure](http://azure.microsoft.com/documentation/).  
  
-   Para criar sites e aplicativos Web, [consulte o site do ASP.NET](http://www.asp.net/get-started/websites).  
  
    > [!NOTE]
    >  Você pode criar um site ASP.NET vazio e usá-lo para programação em HTML, CSS e JavaScript. O arquivo Webconfig fornecido pelo ASP.NET habilita a depuração no Visual Studio (ou você pode usar ferramentas F12 quando executa o aplicativo).  
  
 O editor de JavaScript no Visual Studio fornece é compatível com o IntelliSense. Para obter mais informações, consulte [JavaScript IntelliSense](../ide/javascript-intellisense.md).  
  
## <a name="whats-new-in-javascript"></a>Novidades no JavaScript  
 Novas funcionalidades para JavaScript são listadas na tabela a seguir.  
  
|Recurso|Descrição|  
|-------------|-----------------|  
|Classes|A nova sintaxe dá suporte a declaração de [classes](http://msdn.microsoft.com/Library/bf45ebad-4678-4062-88df-55d32b603c69).|  
|Promises|[Promises](http://msdn.microsoft.com/Library/358ad98b-f7fa-448c-9ee0-ef1e2a45e9c6) permitem codificação assíncrona mais fácil e limpa. Construtores Promise têm suporte, juntamente com os métodos de utilitário `all` e `race`.|  
|Iteradores|Agora você pode iterar pelos objetos que permitem iteração (incluindo matrizes, objetos de tipo matriz e iteradores), invocando um gancho de iteração personalizado com as instruções a serem executadas para o valor de cada propriedade distinta. Para obter mais informações, consulte [Iteradores e geradores](http://msdn.microsoft.com/Library/68ef5b2f-0349-492b-b557-73ff2a2f90cf). **Observação:** ainda não há suporte para geradores.|  
|Funções de seta|A função de seta (=>) fornece uma sintaxe abreviada para a palavra-chave `function`, que apresenta uma associação `this` léxica.|  
|Novos métodos para objetos internos|Os objetos internos [Array](http://msdn.microsoft.com/Library/08e5f552-0797-4b48-8164-609582fc18c9), [Math](http://msdn.microsoft.com/Library/607b94cb-921c-43cd-b514-fdbc13aeced6), [Number](http://msdn.microsoft.com/Library/76e87c37-cf6c-46cc-bafa-04be1fe3d78d), [Object](http://msdn.microsoft.com/Library/d24ef8fc-217b-4828-94e1-19f72780bae0) e [String](http://msdn.microsoft.com/Library/8063ecd5-5778-4e87-b985-b21420171914) incluem muitas novas propriedades e funções de utilitário para manipular e inspecionar dados.|  
|Aprimoramentos de literal de objeto|Os objetos agora dão suporte a propriedades computadas, definições de método concisas e sintaxe abreviada para propriedades cujo valor é inicializado com uma variável de mesmo nome. Para obter mais informações, consulte [Criando objetos](http://msdn.microsoft.com/Library/58d1baa5-4fe8-4a56-a926-5b11765df704).|  
|Proxies|[Proxies](http://msdn.microsoft.com/Library/2b89abee-04fa-47e6-9676-980016cff5f8) habilitam o comportamento personalizado para objetos.|  
|Parâmetros Rest|Parâmetros Rest permitem que você transforme argumentos consecutivos em uma chamada de função para uma matriz. Para obter mais informações, consulte [Funções](http://msdn.microsoft.com/Library/e2a72b5a-3edd-43d8-95e8-91721b38c1c1).|  
|Operador de espalhamento|O [operador de espalhamento](http://msdn.microsoft.com/Library/10263a4c-bd27-4d87-9917-fb4b6bf373db) (`…`) expande expressões que podem ser iteradas, transformando-as em argumentos individuais. Por exemplo, `a.b(…array)` é aproximadamente o mesmo que `a.b.apply(a, array)`.|  
|Símbolos|Os objetos [Symbol](http://msdn.microsoft.com/Library/2ad059f1-4b7f-4758-882a-c74ce1283ab0) permitem que sejam adicionadas propriedades aos objetos existentes sem a possibilidade de interferência com as propriedades do objeto existente, sem nenhuma visibilidade não intencional e sem outras adições não coordenadas por outro código.|  
|Cadeias de caracteres de modelo|[Cadeias de caracteres de modelo](http://msdn.microsoft.com/Library/f2e525a5-b0fc-49c3-95a0-641788e5c12a) são literais de cadeia de caracteres que permitem que expressões sejam avaliadas e concatenadas com o literal de cadeia de caracteres.|  
|Aprimoramentos Unicode|Foram feitos aperfeiçoamentos ao suporte a Unicode. Por exemplo, um novo formato de sequência de escape dá suporte a pontos de código astral (pontos de código com mais de quatro dígitos hexadecimais). Para obter mais informações, consulte [Caracteres especiais](http://msdn.microsoft.com/Library/3b38b1bd-1f0f-4748-b13e-55cab36fd126).|  
|WeakSet|Um [WeakSet](http://msdn.microsoft.com/Library/f97e6e7c-d678-4e32-978e-d949a7cafa3a) será uma coleção de objetos que serão removidos pela coleta de lixo se não forem referenciados em nenhum outro lugar.|
