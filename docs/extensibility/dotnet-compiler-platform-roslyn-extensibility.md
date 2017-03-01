---
title: Plataforma do compilador .NET (&quot;Roslyn&quot;) extensibilidade | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 564201b3-1e18-4b88-b615-42c2f57f3fe8
caps.latest.revision: 4
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
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
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 936132a3f39a00d40d64c2cc990f0e03d6992de7
ms.lasthandoff: 02/22/2017

---
# <a name="net-compiler-platform-quotroslynquot-extensibility"></a>Plataforma do compilador .NET (&quot;Roslyn&quot;) extensibilidade
A missão de núcleo do .NET Compiler Platform ("Roslyn") está abrindo os compiladores c# e Visual Basic e permitindo que ferramentas e tem desenvolvedores compartilhem nos compiladores informações detalhadas sobre os programas. Ferramentas de análise de código melhorar a qualidade do código e código geradores ajuda na criação do aplicativo. Medida ferramentas mais inteligentes, eles precisam acessar mais e mais do conhecimento profundo do código que possuem somente compiladores. Em vez de serem tradutores opacos (código-fonte e código objeto), os compiladores Roslyn oferecem APIs que você pode usar para tarefas relacionadas ao código em seus aplicativos e ferramentas.  
  
 A melhor parte é que os compiladores Roslyn, suas APIs, exemplos e explicações passo a passo e as ferramentas reais baseia essas APIs são inteiramente aberto em [github.com/dotnet/roslyn](https://github.com/dotnet/Roslyn). Vá para o site de OSS para saber mais e começar com o Roslyn. Você encontrará links para obter o mais recente c# e VB recursos que você pode usar como um usuário final, bem como links para começar como um construtor ferramenta aproveitar as APIs do Roslyn.  
  
## <a name="see-also"></a>Consulte também  
 [Introdução aos analisadores de Roslyn](../extensibility/getting-started-with-roslyn-analyzers.md)
