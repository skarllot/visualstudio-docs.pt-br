---
title: "Opções de usuário de solução (. Arquivos suo) | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- .suo files, VSPackages
- suo files, VSPackages
- solutions, .suo files
- solutions, user options
- solution user options (.suo) file
ms.assetid: 75258e0d-600d-4a3d-94f4-3d7ac12cb47c
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
ms.openlocfilehash: 3a466d6e803d0fe2cb2326633f5c255fd065b50a
ms.lasthandoff: 02/22/2017

---
# <a name="solution-user-options-suo-file"></a>Opções de usuário de solução (. Arquivos suo)
O arquivo de opções (. suo) de usuário de solução contém opções de solução por usuário. Esse arquivo não deve ser check-in para controle do código fonte.  
  
 O arquivo de opções (. suo) de usuário de solução é um armazenamento estruturado ou composto, um arquivo armazenado em um formato binário. Você pode salvar informações do usuário em fluxos com o nome do fluxo que está sendo a chave que será usada para identificar as informações no arquivo. suo. O arquivo de opções de usuário de solução é usado para armazenar as configurações de preferência do usuário e é criado automaticamente quando o Visual Studio salva uma solução.  
  
 Quando o ambiente abre um arquivo. suo, ele enumera todos os VSPackages atualmente carregados. Se um VSPackage implementa o <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>interface e o ambiente chama o <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.LoadUserOptions%2A>método VSPackage pedindo que ele carregar todos os seus dados do arquivo. suo.</xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.LoadUserOptions%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>  
  
 É responsabilidade do VSPackage saber quais fluxos poderia ter escrito no arquivo. suo. Para cada fluxo que escreveu, o VSPackage chama de volta para o ambiente por meio de <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.LoadPackageUserOpts%2A>para carregar um fluxo específico identificado pela chave, que é o nome do fluxo.</xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.LoadPackageUserOpts%2A> O ambiente, em seguida, chama de volta para o VSPackage para esse determinado fluxo passando o nome do fluxo de leitura e um `IStream` ponteiro para o <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.LoadPackageUserOpts%2A>método.</xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.LoadPackageUserOpts%2A>  
  
 Nesse ponto, a outra chamada é feita para `LoadUserOptions` para ver se há outra seção do arquivo. suo que deve ser lidos. Esse processo continua até que todos os fluxos de dados no arquivo. suo são lidos e processados pelo ambiente.  
  
 Quando a solução é salvo ou fechada, o ambiente chama o <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.SavePackageSolutionProps%2A>método com um ponteiro para o <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.SaveUserOptions%2A>método.</xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.SaveUserOptions%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.SavePackageSolutionProps%2A> Um `IStream` que contém as informações binárias a ser salvo é passado para o <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.WriteUserOptions%2A>método, que grava as informações de arquivo. suo e chama o `SaveUserOptions` método novamente para ver se há outro fluxo de informações para gravar o arquivo. suo.</xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.WriteUserOptions%2A>  
  
 Esses dois métodos, `SaveUserOptions` e `WriteUserOptions`, são chamados recursivamente para cada fluxo de informações a serem salvas no arquivo. suo, passando o ponteiro para `IVsSolutionPersistence`. Eles são chamados recursivamente para permitir a gravação de vários fluxos para o arquivo. suo. Dessa forma, as informações de usuário são mantidas com a solução em é a garantia de estar lá na próxima vez em que a solução for aberta.  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts></xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>   
 [Soluções](../../extensibility/internals/solutions.md)
