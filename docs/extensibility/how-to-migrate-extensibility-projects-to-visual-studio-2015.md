---
title: 'Como: migrar projetos de extensibilidade para o Visual Studio 2015 | Documentos do Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio SDK, upgrading
ms.assetid: 22491cdc-8f04-4e1c-8eb4-ff33798ec792
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
ms.openlocfilehash: 8b1779f02b72d099c84d63684911e42c18d5ce26
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-migrate-extensibility-projects-to-visual-studio-2015"></a>Como: migrar projetos de extensibilidade para o Visual Studio 2015
Aqui está como atualizar sua extensão.  
  
> [!IMPORTANT]
>  Se você pretende manter uma versão de sua solução de extensão para uma versão anterior do Visual Studio, certifique-se de fazer uma cópia antes de atualizá-lo. Pode ser difícil retornar a versão atualizada para seu estado anterior.  
  
#### <a name="to-upgrade-an-extensibility-solution"></a>Para atualizar uma solução de extensibilidade  
  
1.  Usando a cópia que você deseja atualizar, abri-lo na nova versão. Você será avisado de que a atualização não é reversível.  
  
2.  Após a atualização, altere o caminho do programa externo para a nova versão do devenv.exe. Clique com botão direito no nó do projeto no **Solution Explorer**, em seguida, escolha **propriedades**. No **depurar** guia, localize a caixa de texto por **Iniciar programa externo** e altere o caminho de devenv.exe para o caminho do Visual Studio 2015, que deve ter esta aparência:  
  
     **%ProgramFiles%\Microsoft visual Studio 14.0\Common7\IDE\devenv.exe**  
  
3.  Adicione uma referência ao Microsoft.VisualStudio.Shell.14.0.dll. (Com o botão direito no nó do projeto no **Solution Explorer** e, em seguida, escolha **adicionar /Reference**. Selecione o **extensões** guia e, em seguida, verifique **Microsoft.VisualStudio.Shell.14.0**.)  
  
4.  Compile a solução. Os arquivos compilados são implantados para:  
  
     **%LOCALAPPDATA%\Microsoft\VisualStudio.14.0Exp\Extensions\\<Author></Author>\>\\<Project></Project>\>\\<Project></Project>\>\\**.  
  
#### <a name="to-update-an-extensibility-project-to-nuget-vs-sdk-reference-assemblies"></a>Para atualizar um projeto de extensibilidade para assemblies de referência do SDK do VS NuGet  
  
1.  Determine os assemblies de referência do SDK do VS que precisa de seu projeto.  Em **Solution Explorer**, expanda o projeto **referências** nó e revise a lista de referências do projeto.  SDK do VS referencia assemblies terão o prefixo **Microsoft.VisualStudio** o nome (por exemplo: Microsoft.VisualStudio.Shell.14.0).  
  
2.  Remover os assemblies de referência do SDK do VS do projeto, selecionando-os, clique com botão direito e **remover**.  
  
3.  Adicione as versões do NuGet dos assemblies de referência do SDK do VS.  Enquanto estiver no **Solution Explorer referências** nó, abra o **Manage NuGet Packages...** caixa de diálogo.  Se você quiser saber mais sobre essa caixa de diálogo, consulte [gerenciar pacotes de NuGet usando a caixa de diálogo](http://docs.nuget.org/Consume/Package-Manager-Dialog). Os assemblies de referência do SDK do VS são publicados no [nuget.org](http://www.nuget.org) por [VisualStudioExtensibility](http://www.nuget.org/profiles/VisualStudioExtensibility).  
  
4.  Usando **nuget.org** como seu **origem do pacote**, procure o nome do pacote NuGet que corresponda ao assembly de referência desejado (por exemplo: Microsoft.VisualStudio.Shell.14.0) e instale-o em seu projeto.  O NuGet pode adicionar vários assemblies de referência para satisfazer as dependências do assembly inicial.  
  
     Se preferir, você pode adicionar todos os assemblies de referência de SDK do VS ao mesmo tempo instalando o SDK do VS [pacote Meta](http://www.nuget.org/packages/VSSDK_Reference_Assemblies).  
  
5.  Você também pode alternar para usar a versão do NuGet das ferramentas de compilação do SDK do VS. Este pacote do NuGet é [Microsoft.VSSDK.BuildTools](http://www.nuget.org/packages/Microsoft.VSSDK.BuildTools) e uma vez adicionado ao seu projeto incluem as ferramentas necessárias e arquivos para permitir que você crie seu projeto de extensibilidade em um computador sem o SDK do VS instalado de destino.  
  
> [!NOTE]
>  Não é necessário que você atualize seus projetos de extensibilidade existentes para usar as ferramentas e assemblies de referência do NuGet.  Eles podem continuar a criar usando as ferramentas instaladas com o SDK do VS e os assemblies de referência.
