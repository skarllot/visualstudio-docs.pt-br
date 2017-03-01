---
title: "Utilitário de CreateExpInstance | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- experimental builds
- experimental hive
- experimental instance
- createexpinstance
- createexpinst
ms.assetid: 03779774-9401-49ae-997c-0c3ab25ed0d5
caps.latest.revision: 12
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
ms.openlocfilehash: 8fe27fd6b983c53ec8fda53783e6747d49a86588
ms.lasthandoff: 02/22/2017

---
# <a name="createexpinstance-utility"></a>Utilitário de CreateExpInstance
Use o utilitário CreateExpInstance para criar, redefinir, ou excluir uma instância experimental do Visual Studio. Você pode usar a instância experimental para depurar e testar as extensões do Visual Studio sem alterar o produto subjacente.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
CreateExpInstance.exe [/Create | /Reset | /Clean] /VSInstance=VsInstance /RootSuffix=Suffix  
```  
  
#### <a name="parameters"></a>Parâmetros  
 / Criar  
 Cria a instância experimental.  
  
 / Reset  
 Exclui a instância experimental e, em seguida, cria um novo.  
  
 /Clean  
 Exclui a instância experimental.  
  
 / VSInstance  
 O nome do diretório que contém a instância base do Visual Studio para copiar.  
  
 / RootSuffix  
 O sufixo a ser acrescentado ao nome do diretório de instância experimental.  
  
## <a name="remarks"></a>Comentários  
 Quando você estiver trabalhando em uma extensão do Visual Studio, você pode pressionar F5 para abrir a instância experimental do padrão e instalar a extensão atual. Se nenhuma instância experimental estiver disponível, o Visual Studio cria um que tenha as configurações padrão.  
  
 O local padrão da instância experimental depende do número de versão do Visual Studio. Por exemplo, para o Visual Studio 2015, o local é %localappdata%\Microsoft\VisualStudio\14.0Exp\ todos os arquivos no local de diretório são considerados parte dessa instância. Todas as instâncias experimentais adicionais não serão carregadas pelo Visual Studio, a menos que o nome do diretório é alterado para o local padrão.  
  
 Visual Studio não acessar o registro do sistema quando ele abre a instância experimental. Isso é diferente das versões anteriores do Visual Studio, que usou uma versão experimental da seção do registro.  
  
 O utilitário CreateExpInstance substitui o utilitário VsRegEx.  
  
 O exemplo a seguir redefine a instância experimental do padrão do Visual Studio.  
  
 **/VSInstance CreateExpInstance.exe /Reset =&14;.0 /RootSuffix = Exp**  
  
## <a name="see-also"></a>Consulte também  
 [Liberar um produto](../../misc/releasing-a-visual-studio-integration-product.md)
