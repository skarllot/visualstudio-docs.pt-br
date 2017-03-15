---
title: Usando a estrutura de pacote gerenciado para um tipo de projeto (c#) | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- projects [Visual Studio SDK], creating with MPF
- MPF projects
- managed package framework, creating projects
ms.assetid: 926de536-eead-415b-9451-f1ddc8c44630
caps.latest.revision: 20
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
ms.sourcegitcommit: d5bc147592bfc36247c35f23ac2885055d096af3
ms.openlocfilehash: 1d70a70b942b3722ed61e1e8a2f2e54d96b916e4
ms.lasthandoff: 02/22/2017

---
# <a name="using-the-managed-package-framework-to-implement-a-project-type-c"></a>Usando a estrutura de pacote gerenciado para implementar um tipo de projeto (c#)
Estrutura de pacote gerenciado (MPF) fornece classes c# você pode usar ou herdar para implementar seus próprios tipos de projeto. MPF implementa muitas das interfaces do que Visual Studio espera um tipo de projeto para fornecer, deixando-o livre para se concentrar em como implementar as particularidades de seu tipo de projeto.  
  
## <a name="using-the-mpf-project-source-code"></a>Usando o código-fonte MPF projeto  
 A estrutura de pacote gerenciado para projetos (MPFProj) fornece classes auxiliares para criar e gerenciar o novo sistema de projeto. Diferentemente de outras classes no MPF, as classes do projeto não são incluídas nos assemblies fornecidos com o Visual Studio. Em vez disso, as classes do projeto são fornecidas como código-fonte em [MPF para projetos 2013](http://mpfproj12.codeplex.com).  
  
 Para adicionar esse projeto à sua solução de VSPackage, faça o seguinte:  
  
1.  Baixar os arquivos MPFProj *MPFProjectDir*.  
  
2.  No *MPFProjectDir*\Dev10\Src\CSharp\ProjectBase.file, altere o seguinte bloco:  
  
```  
<!-- Provide a default value for $(ProjectBasePath) -->  
  <PropertyGroup>  
    <ProjectBasePath >MPFProjDir\Dev10\Src\CSharp</ProjectBasePath>  
  </PropertyGroup>  
```  
  
1.  Crie um projeto de VSPackage.  
  
2.  Descarrega projeto VSPackage.  
  
3.  Editar o arquivo. csproj VSPackage adicionando o seguinte bloco antes da outra `<Import>` blocos:  
  
```  
<Import Project="MPFProjectDir\Dev10\Src\CSharp\ProjectBase.files" />  
  <PropertyGroup>  
    <!--To specify a different registry root to register your package, uncomment the TargetRegistryRoot tag and specify a registry root in it.  
    <TargetRegistryRoot></TargetRegistryRoot>-->  
    <RegisterOutputPackage>true</RegisterOutputPackage>  
    <RegisterWithCodebase>true</RegisterWithCodebase>  
  </PropertyGroup>  
```  
  
1.  Salvar o projeto.  
  
2.  Feche e reabra a solução de VSPackage.  
  
3.  Reabra o projeto de VSPackage. Você verá um novo diretório chamado ProjectBase.  
  
4.  Adicione a seguinte referência ao projeto de VSPackage:  
  
     Microsoft.Build.Tasks.4.0  
  
5.  Compile o projeto.  
  
## <a name="hierarchy-classes"></a>Hierarquia de Classes  
 A tabela a seguir resume as classes no MPFProj que dão suporte a hierarquias de projeto. Para obter mais informações, consulte [hierarquias e seleção](../../extensibility/internals/hierarchies-and-selection.md).  
  
|Nome da classe|  
|----------------|  
|`Microsoft.VisualStudio.Package.HierarchyNode`|  
|`Microsoft.VisualStudio.Package.ProjectNode`|  
|`Microsoft.VisualStudio.Package.ProjectContainerNode`|  
|`Microsoft.VisualStudio.Package.FileNode`|  
|`Microsoft.VisualStudio.Package.FolderNode`|  
|`Microsoft.VisualStudio.Package.ReferenceContainerNode`|  
|`Microsoft.VisualStudio.Package.ReferenceNode`|  
|`Microsoft.VisualStudio.Package.ProjectReferenceNode`|  
|`Microsoft.VisualStudio.Package.ComReferenceNode`|  
|`Microsoft.VisualStudio.Package.AssemblyReferenceNode`|  
|`Microsoft.VisualStudio.Package.BuildDependency`|  
  
## <a name="document-handling-classes"></a>Classes de manuseio de documento  
 A tabela a seguir lista as classes no MPF que oferecer suporte à manipulação de documentos. Para obter mais informações, consulte [abrindo e salvando itens de projeto](../../extensibility/internals/opening-and-saving-project-items.md).  
  
|Nome da classe|  
|----------------|  
|`Microsoft.VisualStudio.Package.DocumentManager`|  
|`Microsoft.VisualStudio.Package.FileDocumentManager`|  
  
## <a name="configuration-and-output-classes"></a>Configuração e Classes de saída  
 A tabela a seguir lista as classes no MPF que permitem que os tipos de projeto oferecer suporte a várias configurações, como coleções de saída do projeto, depuração e versão. Para obter mais informações, consulte [opções de configuração de gerenciamento de](../../extensibility/internals/managing-configuration-options.md).  
  
|Nome da classe|  
|----------------|  
|`Microsoft.VisualStudio.Package.ConfigProvider`|  
|`Microsoft.VisualStudio.Package.ProjectConfig`|  
|`Microsoft.VisualStudio.Package.BuildableProjectConfig`|  
|`Microsoft.VisualStudio.Package.OutputGroup`|  
|`Microsoft.VisualStudio.Package.ProjectElement`|  
  
## <a name="automation-support-classes"></a>Classes de suporte de automação  
 A tabela a seguir lista as classes que oferecem suporte a automação para que os usuários de seu tipo de projeto podem escrever suplementos no MPF.  
  
|Nome da classe|  
|----------------|  
|`Microsoft.VisualStudio.Package.Automation.OAProject`|  
|`Microsoft.VisualStudio.Package.Automation.OANavigableProjectItems`|  
|`Microsoft.VisualStudio.Package.Automation.OAProjectItems`|  
|`Microsoft.VisualStudio.Package.Automation.OAProjectItem`|  
|`Microsoft.VisualStudio.Package.Automation.OANestedProjectItem`|  
  
## <a name="properties-classes"></a>Classes de propriedades  
 A tabela a seguir lista as classes que permitem que os tipos de projeto MPF adicionar propriedades que os usuários podem procurar e modificar em um navegador de propriedade.  
  
|Nome da classe|  
|----------------|  
|`Microsoft.VisualStudio.Package.LocalizableProperties`|  
|`Microsoft.VisualStudio.Package.NodeProperties`|  
|`Microsoft.VisualStudio.Package.FileNodeProperties`|  
|`Microsoft.VisualStudio.Package.ProjectNodeProperties`|  
|`Microsoft.VisualStudio.Package.FolderNodeProperties`|  
|`Microsoft.VisualStudio.Package.ReferenceNodeProperties`|
