---
title: Gerenciando assinatura de assembly e de manifesto | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- manifests [Visual Studio]
- signing manifests [Visual Studio]
- application manifests [Visual Studio]
- assemblies [Visual Studio], signing
ms.assetid: 6c1ef36b-25f7-4ad0-b29a-51801b7a5420
caps.latest.revision: 15
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
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
translationtype: Human Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: 85474fe229980aac7c57205f111656d4264045d1
ms.lasthandoff: 02/22/2017

---
# <a name="managing-assembly-and-manifest-signing"></a>Gerenciando Assinatura de Assembly e Manifesto
A assinatura de nome forte fornece a um componente de software uma identidade global exclusiva. Nomes fortes são usados para assegurar que o assembly não pode ser falsificado por outra pessoa e para assegurar que dependências do componente e instruções de configuração são mapeadas para o componente e a versão do componente corretos.  
  
 Um nome forte consiste na identidade do assembly (nome de texto simples, número de versão e informações de cultura), além de um token de chave pública e uma assinatura digital.  
  
 Para obter informações sobre como assinar assemblies em projetos do Visual Basic e do C#, consulte [Criando e usando assemblies de nomes fortes](http://msdn.microsoft.com/Library/ffbf6d9e-4a88-4a8a-9645-4ce0ee1ee5f9).  
  
 Para obter informações sobre como assinar assemblies em projetos do Visual C++, consulte [Assemblies de nome forte (assinatura de assembly) (C++/CLI)](/visual-cpp/dotnet/strong-name-assemblies-assembly-signing-cpp-cli).  
  
## <a name="asset-types-and-signing"></a>Tipos de ativos e assinatura  
 É possível assinar manifestos de assemblies e do aplicativo do .NET. Eles incluem o seguinte:  
  
-   executáveis (.exe)  
  
-   manifestos do aplicativo (.exe.manifest)  
  
-   manifestos de implantação (.application)  
  
-   assemblies com componentes compartilhados (.dll)  
  
 É necessário assinar os seguintes tipos de ativo:  
  
1.  assemblies, se você desejar implantá-los no GAC (cache de assembly global).  
  
2.  manifestos do aplicativo e de implantação [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]. O Visual Studio permite a assinatura por padrão desses aplicativos.  
  
3.  Assemblies de interoperabilidade primários, que são usados para a interoperabilidade COM. O utilitário TLBIMP impõe uma nomenclatura forte ao criar um assembly de interoperabilidade primário com base em uma biblioteca de tipos COM.  
  
 Em geral, não se deve assinar executáveis. Um componente de nome forte não pode referenciar um componente que não tem um nome forte implantado com o aplicativo. O Visual Studio não assina executáveis do aplicativo, mas em vez disso, assina o manifesto do aplicativo, que aponta para o executável de nome fraco. Em geral, você deve evitar a assinatura de componentes privados ao aplicativo, pois sua assinatura pode dificultar o gerenciamento de dependências.  
  
## <a name="how-to-sign-an-assembly-in-visual-studio"></a>Como assinar um assembly no Visual Studio  
 Assine um aplicativo ou componente usando a guia **Assinatura** da janela Propriedades do projeto (clique com o botão direito do mouse no nó do projeto no **Gerenciador de Soluções** e selecione **Propriedades**, digite **propriedades do projeto** na janela **Início Rápido** ou pressione ALT+ENTER na janela **Gerenciador de Soluções**). Selecione a guia **Assinatura** e, em seguida, marque a caixa de seleção **Assinar o assembly**.  
  
 Especifique um arquivo de chave. Se você optar por criar um novo arquivo de chave, observe que os novos arquivos de chave são sempre criados no formato .pfx. É necessário um nome e uma senha para o novo arquivo.  
  
> [!WARNING]
>  Você sempre deve proteger o arquivo de chave com uma senha para evitar o uso por outra pessoa. Também é possível proteger as chaves usando provedores ou repositórios de certificados.  
  
 Você também pode apontar para uma chave já criada. Para obter mais informações sobre como criar chaves, consulte [Como criar um par de chaves pública-privada](http://msdn.microsoft.com/Library/05026813-f3bd-4d7c-9e0b-fc588eb3d114).  
  
 Se você tiver acesso somente a uma chave pública, é possível usar a assinatura com atraso para adiar a atribuição da chave. Habilite a assinatura com atraso selecionando a caixa de seleção **Somente sinal de atraso**. Um projeto com assinatura com atraso não será executado e não é possível depurá-lo. No entanto, é possível ignorar a verificação durante o desenvolvimento usando [Sn.exe (Ferramenta de Nome Forte)](http://msdn.microsoft.com/Library/c1d2b532-1b8e-4c7a-8ac5-53b801135ec6) com a opção `-Vr`.  
  
 Para obter informações sobre como assinar manifestos, consulte [Como assinar manifestos do aplicativo e de implantação](../ide/how-to-sign-application-and-deployment-manifests.md).  
  
## <a name="see-also"></a>Consulte também  
 [Assemblies de nomes fortes](http://msdn.microsoft.com/Library/d4a80263-f3e0-4d81-9b61-f0cbeae3797b)   
 [Assemblies de nome forte (assinatura de assembly) (C++/CLI)](/visual-cpp/dotnet/strong-name-assemblies-assembly-signing-cpp-cli)
