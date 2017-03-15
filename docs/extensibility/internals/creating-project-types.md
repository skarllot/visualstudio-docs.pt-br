---
title: Criando tipos de projeto | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project types, new
- projects [Visual Studio SDK], new project types
ms.assetid: bdb2d22e-d622-450c-bb2d-98152a745fcf
caps.latest.revision: 25
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
ms.openlocfilehash: 80379373e19844c49ae5106507fde3adfdf70a1c
ms.lasthandoff: 02/22/2017

---
# <a name="creating-project-types"></a>Criando tipos de projeto
Você pode estender [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] criando um novo tipo de projeto. Para criar um novo tipo de projeto, você deve compreender vários conceitos e concluir várias etapas. Os tópicos a seguir fornecem uma visão geral de como criar tipos de projeto.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Decisões de Design de tipo de projeto](../../extensibility/internals/project-type-design-decisions.md)  
 Descreve o item, persistência de arquivo de projeto e as decisões de design mechanic de compromisso que você precisa fazer antes de criar um novo tipo de projeto.  
  
 [Lista de verificação: Criar novos tipos de projeto](../../extensibility/internals/checklist-creating-new-project-types.md)  
 Fornece uma visão geral das etapas que você deve seguir para criar um novo tipo de projeto que oferece suporte a tarefas de programação como edição de código e compilação, criação, depuração e implantando aplicativos no seu projeto.  
  
 [Criação de instâncias de projetos usando fábricas de projeto](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)  
 Fornece informações sobre como fornecer e usar uma fábrica de projeto para criar instâncias de um novo projeto.  
  
 [Registrar um tipo de projeto](../../extensibility/internals/registering-a-project-type.md)  
 Fornece exemplos de código de instruções do registro que fornecem caminhos padrão e dados e uma tabela que contém entradas do script do registro para cada instrução.  
  
 [Persistência de projeto](../../extensibility/internals/project-persistence.md)  
 Discute o uso de `IPersistFileFormat` para manter os arquivos e objetos do projeto não baseados em arquivo.  
  
 [Usando MSBuild](../../extensibility/internals/using-msbuild.md)  
 Descreve como o tipo de projeto pode usar o [!INCLUDE[vstecmsbuild](../../extensibility/internals/includes/vstecmsbuild_md.md)] criar mecanismo para permitir aos usuários criar de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] na linha de comando.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Suporte a ferramentas de navegação de símbolo](../../extensibility/internals/supporting-symbol-browsing-tools.md)  
 Explica a arquitetura do código, ferramentas de visualização, como o **Pesquisador de objetos** e **Class View** janela. Descreve as interfaces e métodos que são usados para implementar a pesquisa de objetos em um VSPackage.  
  
 [Adicionando o projeto e modelos de Item de projeto](../../extensibility/internals/adding-project-and-project-item-templates.md)  
 Discute a importância que projetos reproduzir determinar qual editor é usado quando um item de projeto é aberto e como os recursos de projeto podem ser manipulados.  
  
 [Instalando os VSPackages com o Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md)  
 Mostra como fornecer o VSPackage sua própria identidade exclusiva e como encapsular suas DLLs de VSPackage e outras informações em um pacote do Windows Installer (. Arquivo MSI) para implantação para seus clientes.  
  
 [Hierarquias no Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)  
 Descreve como [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] hierarquias de modos de exibição e endereços.  
  
 [VSPackages](../../extensibility/internals/vspackages.md)  
 Fornece uma visão geral de um VSPackage, um objeto COM instalável que estende o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ambiente e discute como implementar seu próprio VSPackage.  
  
 [Tipos de projeto](../../extensibility/internals/project-types.md)  
 Descreve como usar os projetos para modificar o código, compilar e criar o código e executar e depurar o código e fornece links para tópicos detalhados sobre como criar tipos de projeto.
