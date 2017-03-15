---
title: "Eliminação de ~ SAK arquivos | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- temporary files
- ~sak files
- source control plug-ins, ~SAK files
ms.assetid: 5277b5fa-073b-4bd1-8ba1-9dc913aa3c50
caps.latest.revision: 15
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
ms.openlocfilehash: 0a571312fd08c8ba57b4b2103dc7343d205c8479
ms.lasthandoff: 02/22/2017

---
# <a name="elimination-of-sak-files"></a>Eliminação de ~ SAK arquivos
No código-fonte controle plug-in API 1.2, o ~ SAK arquivos foram substituídos por novas funções que detecta se um plug-in de controle de origem suporta o arquivo MSSCCPRJ e check-outs compartilhados e sinalizadores de recurso.  
  
## <a name="sak-files"></a>~ Arquivos de SAK  
 Visual Studio .NET 2003 criou arquivos temporários com o prefixo ~ SAK. Esses arquivos são usados para determinar se um plug-in de controle de origem suporta:  
  
-   MSSCCPRJ. Arquivos SCC.  
  
-   Múltiplos (compartilhados) check-outs.  
  
 Para plug-ins que oferecem suporte a funções avançadas fornecidas a fonte de controle de plug-in API 1.2, o IDE pode detectar esses recursos sem criar arquivos temporários com o uso de novos recursos, sinalizadores e funções, detalhadas nas seções a seguir.  
  
## <a name="new-capability-flags"></a>Novos sinalizadores de recurso  
 `SCC_CAP_SCCFILE`  
  
 `SCC_CAP_MULTICHECKOUT`  
  
## <a name="new-functions"></a>Novas funções  
 [SccWillCreateSccFile](../../extensibility/sccwillcreatesccfile-function.md)  
  
 [SccIsMultiCheckoutEnabled](../../extensibility/sccismulticheckoutenabled-function.md)  
  
 Se um plug-in de controle de origem suporta vários check-outs (compartilhados), ele declara o `SCC_CAP_MULTICHECKOUT` capacidade e implementa o `SccIsMultiCheckOutEnabled` função. Essa função é chamada sempre que ocorre uma operação de check-out em qualquer um dos projetos sob controle de origem.  
  
 Se um plug-in de controle de origem oferece suporte à criação e ao uso de um MSSCCPRJ. Arquivos SCC, ele declara o `SCC_CAP_SCCFILE` capacidade e implementa o [SccWillCreateSccFile](../../extensibility/sccwillcreatesccfile-function.md). Essa função é chamada com uma lista de arquivos. A função retorna `TRUE/FALSE` para cada arquivo indicar se o Visual Studio deve usar um MSSCCPRJ. Arquivos SCC para ele. Se o plug-in de controle de origem decidir não oferecer suporte a esses novos recursos e funções, ele pode usar a seguinte chave do registro para desabilitar a criação desses arquivos:  
  
 [HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl] "DoNotCreateTemporaryFilesInSourceControl" = DWORD:&00000;001  
  
> [!NOTE]
>  Se essa chave do registro é definida como DWORD:&00000;000, é equivalente à chave sendo inexistente e Visual Studio ainda tentará criar arquivos temporários. No entanto, se a chave do registro é definida como DWORD:&00000;001, o Visual Studio não tenta criar arquivos temporários. Em vez disso, ele pressupõe que o plug-in de controle de origem não suporta o MSSCCPRJ. Arquivos SCC e não oferece suporte a check-outs compartilhados.  
  
## <a name="see-also"></a>Consulte também  
 [Novidades na origem controle plug-in API versão 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
