---
title: Distribuindo aplicativos do Shell isolado | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c503a985-d67a-4ef8-9123-7744a78f2f17
caps.latest.revision: 9
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
ms.openlocfilehash: 762212f756e094c56387054c054cddf02558c222
ms.lasthandoff: 02/22/2017

---
# <a name="distributing-isolated-shell-applications"></a>Distribuindo aplicativos do Shell isolado
Você deve instalar o Visual Studio e o SDK do Visual Studio para criar um aplicativo de shell isolado. Para distribuir o aplicativo para os computadores de outros usuários ou clientes, você deve incluir um pacote redistribuível especial para o shell isolado.  
  
## <a name="prerequisites-for-distributing-isolated-shell-applications"></a>Pré-requisitos para a distribuição de aplicativos do Shell isolado  
  
|Nome|Descrição|  
|----------|-----------------|  
|SDK do Visual Studio|O SDK, você deve ter para desenvolver e testar as extensões de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Você também pode usar o SDK para criar sua própria instância do shell do Visual Studio isolada.<br /><br /> Visual Studio é um pré-requisito para o SDK.|  
|Microsoft Visual Studio isolada redistribuível do Shell|O redistribuível incluir em seu programa de instalação quando você cria um ambiente de ferramentas no Visual Studio isolados shell. O pacote redistribuível do Shell isolado inclui o .NET Framework 4.5.|  
  
## <a name="creating-an-installation-program-for-the-application"></a>Criando um programa de instalação para o aplicativo  
 Você deve criar um programa de instalação especiais para seu aplicativo de shell integrado ou isolado. Para obter mais informações, consulte [instalando um aplicativo isolado do Shell](../extensibility/installing-an-isolated-shell-application.md).  
  
## <a name="allowing-for-updates-to-your-application"></a>Permitindo atualizações para seu aplicativo  
 O programa de instalação deve permitir a possibilidade de que seu aplicativo será atualizado, por atualizações da Microsoft ou atualizações da sua empresa. Para obter mais informações sobre atualizações, consulte [manutenção diretrizes para aplicativos isolados do Shell](../extensibility/servicing-guidelines-for-isolated-shell-applications.md).
