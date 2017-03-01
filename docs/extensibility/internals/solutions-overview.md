---
title: "Visão geral das soluções | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- solutions, about solutions
ms.assetid: 3b21e3a1-170a-4485-941e-6b04b7b27886
caps.latest.revision: 10
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
ms.openlocfilehash: 06ca562112b8b6feb711219502e3d10b1cb6f462
ms.lasthandoff: 02/22/2017

---
# <a name="solutions-overview"></a>Visão geral das soluções
Uma solução é um agrupamento de um ou mais projetos que trabalham juntos para criar um aplicativo. As projeto e informações de status referentes à solução são armazenados em dois arquivos de solução diferente. O arquivo de solução (. sln) é baseado em texto e pode ser colocado sob controle do código fonte e compartilhado entre os usuários. O arquivo de opção (. suo) de usuário da solução é binário. Como resultado, o arquivo. suo não pode ser colocado sob controle do código fonte e contém informações específicas do usuário.  
  
 Qualquer VSPackage pode gravar em qualquer tipo de arquivo de solução. Devido à natureza dos arquivos, há duas interfaces diferentes implementados para gravá-los. O <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>interface grava informações de texto para o arquivo e o <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>interface grava fluxos binários para o arquivo. suo.</xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts> </xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>  
  
> [!NOTE]
>  Um projeto não precisa explicitamente gravar uma entrada para si mesmo para o arquivo da solução; o ambiente que trata do projeto. Portanto, a menos que você deseja adicionar conteúdo adicional especificamente para o arquivo de solução, você não precisa registrar o VSPackage dessa maneira.  
  
 Cada suporte a persistência de solução de VSPackage usa três interfaces, o <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>interface, que é implementado pelo ambiente e chamado pelo VSPackage, e `IVsPersistSolutionProps` e `IVsPersistSolutionOpts`, que são ambas implementadas pelo VSPackage.</xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> O `IVsPersistSolutionOpts` interface só precisa ser implementado se informações particulares deve ser escrito por VSPackage para o arquivo. suo.  
  
 Quando uma solução é aberta, o seguinte processo ocorre.  
  
1.  O ambiente lê a solução.  
  
2.  Se o ambiente localiza um `CLSID`, ele carrega o VSPackage correspondente.  
  
3.  Se um VSPackage é carregado, o ambiente chama `QueryInterface` para <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>interface para a interface que requer o VSPackage.</xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>  
  
    1.  Durante a leitura de um arquivo. sln, o ambiente chama `QueryInterface` para `IVsPersistSolutionProps`.  
  
    2.  Ao ler de um arquivo. suo, o ambiente chama `QueryInterface` para `IVsPersistSolutionOpts`.  
  
 Informações específicas relativas ao uso desses arquivos podem ser encontradas no [solução (. Arquivos sln)](../../extensibility/internals/solution-dot-sln-file.md) e [opções de usuário de solução (. Arquivos suo)](../../extensibility/internals/solution-user-options-dot-suo-file.md).  
  
> [!NOTE]
>  Se você quiser criar uma nova configuração de solução consiste em configurações de dois projetos e excluindo um terço da compilação, você precisa usar as páginas de propriedade de interface do usuário ou automação. Você não pode alterar configurações do Gerenciador de compilação da solução e suas propriedades diretamente, mas você pode manipular o Gerenciador de compilação da solução usando o `SolutionBuild` classe de DTE no modelo de automação. Para obter mais informações sobre a configuração de soluções, consulte [configuração da solução](../../extensibility/internals/solution-configuration.md).  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage></xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts></xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps></xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence></xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>
