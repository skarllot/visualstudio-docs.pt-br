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
ms.translationtype: Human Translation
ms.sourcegitcommit: 5ea9179ad37514ffad4876177b05150eecc22def
ms.openlocfilehash: 34c400c280096acb7e0ce272fa717cbc2f8f0d8a
ms.contentlocale: pt-br
ms.lasthandoff: 05/24/2017

---
# Codificações e quebras de linha
<a id="encodings-and-line-breaks" class="xliff"></a>
No Visual Studio, é possível usar os configurações **Arquivo/Opções avançadas de salvamento** configurações para determinar o tipo de quebra de linha caracteres que você deseja. Também é possível alterar a codificação de um arquivo com as mesmas configurações.  
  
> [!NOTE]
>  Se você tiver determinados tipos de configurações de desenvolvimento (Visual Basic, F#, Desenvolvimento para a Web), talvez você não veja **Opções avançadas de salvamento** no menu. Para alterar suas configurações (por exemplo para Geral), abra **Ferramentas/Importar e Exportar Configurações**. Para obter mais informações, confira [Personalizar o IDE do Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
 No Visual Studio, os seguintes caracteres são interpretados como quebras de linha:  
  
-   CRLF: retorno de carro + alimentação de linha, caracteres Unicode 000D + 000A  
  
-   LF: alimentação de linha, caractere Unicode 000A  
  
-   NEL: próxima linha, caractere Unicode 0085  
  
-   LS: separador de linha, caractere Unicode 2028  
  
-   PS: separador de parágrafo, caractere Unicode 2029  
  
 O texto copiado de outros aplicativos mantém a codificação original e os caracteres de quebra de linha. Por exemplo, quando você copia texto do Bloco de notas e o cola em um arquivo de texto no Visual Studio, o texto tem as mesmas configurações que ele tinha no Bloco de notas.  
  
 Quando você abre um arquivo que caracteres com uma quebra de linha diferente, talvez você veja uma caixa de diálogo que pergunta se os caracteres de quebra de linha inconsistentes devem ser normalizados e quais os tipo de quebras de linha você deseja escolher.
