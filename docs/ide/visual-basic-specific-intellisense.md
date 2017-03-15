---
title: "IntelliSense específico do Visual Basic | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IntelliSense [Visual Basic]
- IntelliSense [Visual Studio], Visual Basic
ms.assetid: 4dec8753-05e5-4f74-b304-5f8c4ed8723b
caps.latest.revision: 10
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
ms.openlocfilehash: 2369d65e74ef46299b6379286ea6a647afef9355
ms.lasthandoff: 02/22/2017

---
# <a name="visual-basic-specific-intellisense"></a>IntelliSense específico do Visual Basic
O editor de código-fonte do Visual Basic oferece os seguintes recursos de IntelliSense:  
  
-   Dicas de sintaxe  
  
     Dicas de sintaxe são exibidas na sintaxe da instrução que você está digitando. Isso é útil para instruções de como [Declare](/dotnet/visual-basic/language-reference/statements/declare-statement).  
  
## <a name="automatic-completion"></a>Conclusão automática  
  
-   Conclusão em várias palavras-chave  
  
     Por exemplo, se você digitar `goto` e um espaço, o IntelliSense exibirá uma lista dos rótulos definidos em um menu suspenso. Outras palavras-chave com suporte incluem `Exit`, `Implements`, `Option` e `Declare`.  
  
-   Conclusão em `Enum` e `Boolean`  
  
     Quando uma instrução fizer referência a um membro de uma enumeração, o IntelliSense exibirá uma lista dos membros de `Enum`. Quando uma instrução fizer referência a um `Boolean`, o IntelliSense exibirá um menu suspenso de verdadeiro ou falso.  
  
 A conclusão pode ser desativada por padrão desmarcando **Listar membros automaticamente** na página de propriedades **Geral** na pasta **Visual Basic**.  
  
 Você pode invocar manualmente a conclusão invocando Listar Membros, Completar Palavra ou ALT + SETA PARA A DIREITA. Para obter mais informações, veja [Usando o IntelliSense](../ide/using-intellisense.md).  
  
## <a name="intellisense-in-zone"></a>IntelliSense por Zona  
 O IntelliSense por Zona ajuda desenvolvedores de Visual Basic que precisam implantar aplicativos por meio de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] e que estão restritos a configurações de confiança parcial. Este recurso:  
  
-   Permite escolher as permissões com que o aplicativo será executado.  
  
-   Exibe APIs na Zona escolhida como disponíveis em Listar Membros e exibe APIs que requerem permissões adicionais como não disponíveis.  
  
 Para obter mais informações, consulte [Segurança de acesso do código para aplicativos ClickOnce](../deployment/code-access-security-for-clickonce-applications.md).  
  
## <a name="see-also"></a>Consulte também  
 [Usando o IntelliSense](../ide/using-intellisense.md)
