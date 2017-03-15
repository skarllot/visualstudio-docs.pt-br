---
title: "Codificações e quebras de linha | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.Encoding
helpviewer_keywords:
- line breaks
- encoding
- Visual Studio, encoding
- editors, line breaks
- line break characters
- Visual Studio, line break characters
ms.assetid: 8f9b3ffc-7b8d-44f4-87cb-dc29105be12d
caps.latest.revision: 8
author: kempb
ms.author: kempb
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
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 99d60dc8f36d108b0882c6e6c7c66f2910f6d460
ms.lasthandoff: 02/22/2017

---
# <a name="encodings-and-line-breaks"></a>Codificações e quebras de linha
No Visual Studio, é possível usar os configurações **Arquivo/Opções avançadas de salvamento** configurações para determinar o tipo de quebra de linha caracteres que você deseja. Também é possível alterar a codificação de um arquivo com as mesmas configurações.  
  
> [!NOTE]
>  Se você tiver determinados tipos de configurações de desenvolvimento (Visual Basic, F#, Desenvolvimento para a Web), talvez você não veja **Opções avançadas de salvamento** no menu. Para alterar suas configurações (por exemplo para Geral), abra **Ferramentas/Importar e Exportar Configurações**. Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 No Visual Studio, os seguintes caracteres são interpretados como quebras de linha:  
  
-   CRLF: retorno de carro + alimentação de linha, caracteres Unicode 000D + 000A  
  
-   LF: alimentação de linha, caractere Unicode 000A  
  
-   NEL: próxima linha, caractere Unicode 0085  
  
-   LS: separador de linha, caractere Unicode 2028  
  
-   PS: separador de parágrafo, caractere Unicode 2029  
  
 O texto copiado de outros aplicativos mantém a codificação original e os caracteres de quebra de linha. Por exemplo, quando você copia texto do Bloco de notas e o cola em um arquivo de texto no Visual Studio, o texto tem as mesmas configurações que ele tinha no Bloco de notas.  
  
 Quando você abre um arquivo que caracteres com uma quebra de linha diferente, talvez você veja uma caixa de diálogo que pergunta se os caracteres de quebra de linha inconsistentes devem ser normalizados e quais os tipo de quebras de linha você deseja escolher.
