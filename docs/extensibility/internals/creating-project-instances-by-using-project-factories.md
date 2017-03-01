---
title: "Criação de instâncias de projetos usando fábricas de projeto | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project factories
- projects [Visual Studio SDK], project factories
ms.assetid: 94c90012-8669-459c-af8e-307ac242c8c4
caps.latest.revision: 13
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
ms.openlocfilehash: cc8780dbd1ea51c765f30cf7335ad40cc5cd8895
ms.lasthandoff: 02/22/2017

---
# <a name="creating-project-instances-by-using-project-factories"></a>Criação de instâncias de projetos usando fábricas de projeto
Projeto tipos em [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] usar um *factory projeto* para criar instâncias de objetos do projeto. Uma fábrica de projeto é semelhante a uma fábrica de classes padrão para objetos cocreatable. No entanto, os objetos do projeto não são cocreatable: só podem ser criados usando uma fábrica de projeto.  
  
 O [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE chama a fábrica de projeto implementada em seu VSPackage quando um usuário carrega um projeto existente ou cria um novo projeto no [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. O novo objeto de projeto fornece o IDE com informações suficientes para popular o Gerenciador de soluções. O novo objeto de projeto também fornece as interfaces necessárias para dar suporte a todas as ações de interface de usuário relevantes iniciadas pelo IDE.  
  
 Você pode implementar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>interface em uma classe em seu projeto.</xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory> Normalmente, ele reside em seu próprio módulo.  
  
 Para obter um exemplo de uma implementação do `IVsProjectFactory` de interface, consulte PrjFac.cpp contido no [projeto básico](http://msdn.microsoft.com/en-us/385fd2a3-d9f1-4808-87c2-a3f05a91fc36) diretório de exemplo.  
  
 Projetos que oferecem suporte a que está sendo agregada por um proprietário devem manter uma chave de proprietário no seu arquivo de projeto. Quando o <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>método for chamado em um projeto com uma chave de proprietário, o projeto de propriedade converte sua chave de proprietário em uma fábrica de projeto GUID, em seguida, chama o `CreateProject` método nesta fábrica de projeto para fazer a criação real.</xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>  
  
## <a name="creating-an-owned-project"></a>Criando um projeto de propriedade  
 Um proprietário cria um projeto de propriedade em duas fases:  
  
1.  Chamando o <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.PreCreateForOwner%2A>método.</xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.PreCreateForOwner%2A> Isso fornece o projeto pertencente a oportunidade de criar um objeto de projeto agregado com base em entrada controla `IUnknown`. O projeto de propriedade passa interno `IUnknown` e o objeto agregado para o projeto do proprietário. Isso dá o projeto pertencente a chance de armazenar interno `IUnknown`.  
  
2.  Chamando o <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.InitializeForOwner%2A>método.</xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.InitializeForOwner%2A> O projeto de propriedade faz todos os seu instanciação quando este método é chamado em vez de chamar `IVsProjectFactory::CreateProject` como seria o caso para projetos que não são de propriedade. A entrada `VSOWNEDPROJECTOBJECT` enumeração normalmente é o projeto de propriedade agregado. O projeto de propriedade pode usar essa variável para determinar se o seu objeto de projeto já foi criado (cookie não é igual a NULL) ou devem ser criados (cookie igual a NULL).  
  
 Tipos de projeto são identificados por um GUID, como o CLSID de um objeto COM cocreatable exclusivo do projeto. Normalmente, identificadores de fábrica de um projeto criação de instâncias de um único tipo de projeto, embora seja possível ter uma fábrica de projeto lidar com mais de um GUID de tipo de projeto.  
  
 Tipos de projeto são associados uma extensão de nome de arquivo específico. Quando um usuário tenta abrir um arquivo de projeto existente ou tenta criar um novo projeto clonando um modelo, o IDE usa a extensão no arquivo para determinar o GUID do projeto correspondente.  
  
 Assim que o IDE determina que se ele deve criar um novo projeto ou abra um projeto existente de um tipo específico, o IDE usa as informações no registro do sistema [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\8.0\Projects] para localizar qual VSPackage implementa a fábrica de projeto obrigatório. O IDE carrega esse VSPackage. No <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>método, o VSPackage deve registrar sua fábrica de projeto com o IDE chamando o <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterProjectTypes.RegisterProjectType%2A>método.</xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterProjectTypes.RegisterProjectType%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>  
  
 O principal método do `IVsProjectFactory` interface é <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>que deve lidar com dois cenários: abrir um projeto existente e criar um novo projeto.</xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A> A maioria dos projetos armazenar seu estado de projeto em um arquivo de projeto. Normalmente, os novos projetos são criados fazendo uma cópia do arquivo de modelo passada para o `CreateProject` método e, em seguida, abrir a cópia. Projetos existentes são instanciados pelo diretamente a abertura do arquivo de projeto passado para `CreateProject` método. O `CreateProject` método pode exibir os recursos adicionais da interface do usuário para o usuário conforme necessário.  
  
 Um projeto pode também não usar nenhum arquivo e, em vez disso, armazenar o estado do projeto em um mecanismo de armazenamento diferente do sistema de arquivos, como um banco de dados ou servidor Web. Nesse caso, o parâmetro de nome de arquivo é passado para o `CreateProject` método não é realmente um caminho de sistema de arquivos, mas uma cadeia de caracteres exclusiva — uma URL — para identificar os dados do projeto. Você não precisa copiar os arquivos de modelo que são passados para `CreateProject` para acionar a sequência apropriada de construção a ser executado.  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory></xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory></xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterProjectTypes></xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterProjectTypes>   
 [Lista de verificação: Criar novos tipos de projeto](../../extensibility/internals/checklist-creating-new-project-types.md)
