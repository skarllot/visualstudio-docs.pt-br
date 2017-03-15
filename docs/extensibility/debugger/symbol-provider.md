---
title: "Provedor de símbolo | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- symbol handler
- debugging [Debugging SDK], symbol handler
ms.assetid: 5fce651b-fead-4418-81b0-a011df7644ab
caps.latest.revision: 17
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
ms.openlocfilehash: 7c8719513e713d8fa633233dbd6aace5d64bfeb8
ms.lasthandoff: 02/22/2017

---
# <a name="symbol-provider"></a>Provedor de símbolo
Uma implementação do avaliador de expressão deve acessar as informações de depuração simbólica geradas pelo compilador de linguagem para avaliar as variáveis e expressões. Ele faz isso consome as interfaces de um provedor de símbolo (SP), também chamado de um manipulador de símbolo.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]fornece o SPs para código gerenciado, bem como código nativo usando o formato de arquivo de símbolo de banco de dados do programa (PDB). A menos que haja um forte necessário para o seu programa usar símbolos armazenados em um formato personalizado, é recomendável que você use os SPs fornecidos pelo [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## <a name="implementation-notes"></a>Notas de implementação  
 O [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] mecanismos de depuração esperam para se comunicar com os SPs usando as interfaces do Common Language Runtime (CLR). Como resultado, um SP estará trabalhando com os mecanismos de depuração do Visual Studio deve suportar o CLR. Uma lista completa de CLR de todas as interfaces de depuração pode ser encontrada em debugref.doc, que é parte do [!INCLUDE[winsdklong](../../deployment/includes/winsdklong_md.md)].  
  
 Se o SP trabalhar apenas com o mecanismo de depuração personalizado, você pode implementar o SP conforme apropriado dependendo das necessidades do seu mecanismo de depuração.  
  
## <a name="see-also"></a>Consulte também  
 [Componentes do depurador](../../extensibility/debugger/debugger-components.md)
