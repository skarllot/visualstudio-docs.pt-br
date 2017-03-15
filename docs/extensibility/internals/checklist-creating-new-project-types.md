---
title: "Lista de verificação: Criar novos tipos de projeto | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- projects [Visual Studio SDK], creating new types
- project types, checklist for creating
ms.assetid: 29eb9c3b-1933-4741-aa85-65a33f0825ba
caps.latest.revision: 23
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
ms.openlocfilehash: 8dc3af4caba0677fafd8a14cb5e8be808054ea6e
ms.lasthandoff: 02/22/2017

---
# <a name="checklist-creating-new-project-types"></a>Lista de verificação: Criar novos tipos de projeto
Você deve concluir várias tarefas para criar um novo tipo de projeto. A lista de verificação a seguir fornece um guia para essas tarefas.  
  
1.  Crie a funcionalidade para o novo tipo de projeto. Para obter mais informações, consulte [decisões de Design de tipo de projeto](../../extensibility/internals/project-type-design-decisions.md).  
  
2.  Determine quais editores são usados para código e outros elementos do projeto. Você pode usar o núcleo ou editores padrão, ou você pode criar e usar editores específicos do projeto. Para obter mais informações, consulte [criando personalizados editores e Designers](../../extensibility/creating-custom-editors-and-designers.md) e [como: abrir editores específicos do projeto](../../extensibility/how-to-open-project-specific-editors.md).  
  
3.  Determinar o nível de participação seus itens de projeto terá o **Class View** e **Pesquisador de objetos**. Para obter mais informações, consulte [ferramentas de navegação de símbolo de suporte](../../extensibility/internals/supporting-symbol-browsing-tools.md).  
  
4.  Derive novas classes com base nas decisões de design que você fez anteriormente para seu projeto e itens de projeto.  
  
5.  Escreva o código para os seguintes componentes do tipo de projeto:  
  
    -   Fábrica de projeto, para gerenciar a criação de novos projetos e abrir projetos existentes. Para obter mais informações, consulte [criar projeto instâncias por usando projeto fábricas](../../extensibility/internals/creating-project-instances-by-using-project-factories.md).  
  
    -   Hierarquia de projeto e manipulação de comandos. Para obter mais informações, consulte [fora da compilação: usando Classes do projeto HierUtil7 para implementar um tipo de projeto (C++)](http://msdn.microsoft.com/en-us/a5c16a09-94a2-46ef-87b5-35b815e2f346), [elementos de um modelo de projeto](../../extensibility/internals/elements-of-a-project-model.md), [componentes principais do projeto modelo](../../extensibility/internals/project-model-core-components.md) e [MenuCommands Vs. OleMenuCommands](../../misc/menucommands-vs-olemenucommands.md).  
  
    -   Gerenciamento de itens de projeto, incluindo a adição de seu projeto para o **novo projeto** caixa de diálogo. Para obter mais informações, consulte [Adicionar projeto e modelos de Item de projeto](../../extensibility/internals/adding-project-and-project-item-templates.md) e [registro de modelos de projeto e Item](../../extensibility/internals/registering-project-and-item-templates.md).  
  
    -   Persistência de estado do projeto e itens individuais. Para obter mais informações, consulte [abrindo e salvando itens de projeto](../../extensibility/internals/opening-and-saving-project-items.md). Para persistência de informações de solução, consulte [soluções](../../extensibility/internals/solutions.md).  
  
    -   Propriedades independentes de configuração para exibir na janela Propriedades. Para obter mais informações, consulte [estendendo propriedades](../../extensibility/internals/extending-properties.md).  
  
    -   Propriedades de configuração do projeto conforme implementado nas páginas de propriedade para mostrar as propriedades dependentes de configuração. Para obter mais informações, consulte [opções de configuração de gerenciamento de](../../extensibility/internals/managing-configuration-options.md).  
  
    -   Enumerando saídas para implantação. Para obter mais informações, consulte [configuração do projeto para a saída](../../extensibility/internals/project-configuration-for-output.md).  
  
    -   Serviços de inicialização do projeto. Para obter mais informações, consulte [elementos de um modelo de projeto](../../extensibility/internals/elements-of-a-project-model.md) e [componentes principais do projeto modelo](../../extensibility/internals/project-model-core-components.md).  
  
    -   Objetos ou classes derivadas de `IDispatch`, disponível para automação.  
  
    -   Arquivos de tabela de comando XML (VSCT). Para obter mais informações, consulte [tabela de comando do Visual Studio (. Arquivos VSCT)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
6.  Testar, depurar e iniciar o tipo de projeto.  
  
7.  Exibir o seu projeto no **projeto** guia do **adicionar referência** caixa de diálogo definindo `VARIANT_TRUE` como o valor para `VSHPROPID_ShowProjInSolutionPage`. Para obter mais informações, consulte <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>e <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>.</xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> </xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>  
  
8.  Crie o arquivo do Microsoft Installer (. msi) para instalar seu VSPackages. Para obter mais informações, consulte [instalando os VSPackages com o Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md), [registro de um tipo de projeto](../../extensibility/internals/registering-a-project-type.md), e [VSPackages](../../extensibility/internals/vspackages.md).  
  
## <a name="see-also"></a>Consulte também  
 [Hierarquias no Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)   
 [Quando criar tipos de projeto](../../extensibility/internals/when-to-create-project-types.md)   
 [Criando tipos de projeto](../../extensibility/internals/creating-project-types.md)
