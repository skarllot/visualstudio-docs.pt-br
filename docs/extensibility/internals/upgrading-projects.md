---
title: Atualizando projetos | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- upgrading VSPackages
- upgrading applications, strategies
- VSPackages, upgrade support
ms.assetid: e01cb44a-8105-4cf4-8223-dfae65f8597a
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
ms.openlocfilehash: 9e7207d4b11b8bb7d5236b8a48f2ba03d493949c
ms.lasthandoff: 02/22/2017

---
# <a name="upgrading-projects"></a>Atualizando projetos
Altera o modelo de projeto de uma versão do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] para o próximo pode exigir soluções e projetos de ser atualizado para que eles possam ser executados na versão mais recente. O [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] fornece uma interface que pode ser usado para implementar o suporte a atualização em seus próprios projetos.  
  
## <a name="upgrade-strategies"></a>Estratégias de atualização  
 Para dar suporte a uma atualização, sua implementação do sistema de projeto deve definir e implementar uma estratégia de atualização. Para determinar sua estratégia, você pode optar por suporte lado a lado (SxS) backup, backup de cópia ou ambos.  
  
-   Backup de SxS significa que um projeto copia somente os arquivos que precisam de atualização in loco, adicionando um sufixo de nome arquivo adequado, por exemplo, ". old".  
  
-   Backup de cópia significa que um projeto copia todos os itens de projeto para um local de backup fornecida pelo usuário. Os arquivos relevantes no local original do projeto podem ser atualizados.  
  
## <a name="how-upgrade-works"></a>Como a atualização funciona  
 Quando uma solução criada em uma versão anterior do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] é aberto em uma versão mais recente, as verificações IDE a solução de arquivo para determinar se ele precisa ser atualizado. Se a atualização for necessária, o **Upgrade Wizard** é iniciada automaticamente para percorrer o usuário pelo processo de atualização.  
  
 Quando uma solução precisa de atualização, ele consulta cada fábrica de projeto para sua estratégia de atualização. A estratégia determina se a fábrica de projeto dá suporte ao backup de cópia ou SxS. As informações são enviadas para o **Assistente de atualização de**, que coleta as informações necessárias para o backup e apresenta as opções aplicáveis ao usuário.  
  
### <a name="multi-project-solutions"></a>Soluções multiprojeto  
 Se uma solução que contém vários projetos e estratégias de atualização diferem, como quando um projeto de C++ que só oferece suporte a backup SxS e um projeto Web que dão suporte apenas a cópia, as fábricas de projeto devem negociar a estratégia de atualização.  
  
 A solução consulta cada fábrica de projeto para <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>.</xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> Depois, ele chama <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject_CheckOnly%2A>para verificar se os arquivos de projeto global necessário atualizar e determinar as estratégias de atualização com suporte.</xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject_CheckOnly%2A> O **Upgrade Wizard** é invocado.  
  
 Depois que o usuário conclui o assistente, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A>é chamado em cada fábrica de projeto para executar a atualização real.</xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> Para facilitar o backup, fornecem métodos de IVsProjectUpgradeViaFactory a <xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger>serviço para registrar os detalhes do processo de atualização.</xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger> Este serviço não pode ser armazenado em cache.  
  
 Depois de atualizar todos os arquivos global relevantes, cada fábrica de projeto pode optar por criar uma instância de um projeto. A implementação do projeto deve oferecer suporte a <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>.</xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> O <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A>método é chamado para atualizar todos os itens de projeto relevantes.</xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A>  
  
> [!NOTE]
>  O <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A>método não fornecem o serviço de SVsUpgradeLogger.</xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> Esse serviço pode ser obtido chamando <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A>.</xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A>  
  
## <a name="best-practices"></a>Práticas recomendadas  
 Usar o <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>serviço para verificar se você pode editar um arquivo antes de editá-lo e pode salvá-lo antes de salvá-lo.</xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave> Isso ajudará o backup e implementações de atualização lidar com arquivos de projeto sob controle de origem, arquivos com permissões insuficientes e assim por diante.  
  
 Use o <xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger>de serviço durante todas as fases de backup e de atualização para fornecer informações sobre o êxito ou falha do processo de atualização.</xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger>  
  
 Para obter mais informações sobre backup e atualizar os projetos, consulte os comentários para IVsProjectUpgrade vsshell2.idl.  
  
## <a name="see-also"></a>Consulte também  
 [Projetos](../../extensibility/internals/projects.md)   
 [Atualizando projetos personalizados](../../misc/upgrading-custom-projects.md)   
 [Atualizando Itens de Projeto](../../misc/upgrading-project-items.md)
