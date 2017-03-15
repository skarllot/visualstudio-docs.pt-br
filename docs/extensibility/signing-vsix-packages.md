---
title: Assinando pacotes VSIX | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- signature
- signing
- authenticode
- vsix
- packages
ms.assetid: e34cfc2c-361c-44f8-9cfe-9f2be229d248
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
ms.openlocfilehash: da489f0fd0483cddbefb2899eb91bd1d56735d62
ms.lasthandoff: 02/22/2017

---
# <a name="signing-vsix-packages"></a>Assinando pacotes VSIX
Assemblies de extensão não precisa ser assinados antes que estes sejam executados no Visual Studio, mas é uma boa prática fazer isso.  
  
 Se você quiser proteger sua extensão e verifique se que ele não foi adulterado, você pode adicionar uma assinatura digital a um pacote VSIX. Quando um VSIX está conectado, o instalador VSIX exibirá uma mensagem indicando que ele seja assinado, além de obter mais informações sobre a assinatura em si. Se o conteúdo do VSIX foram modificado e VSIX não foi assinado novamente, o instalador VSIX mostrará que a assinatura não é válida. A instalação não for interrompida, mas o usuário é avisado.  
  
> [!IMPORTANT]
>  A partir de 2015, pacotes VSIX assinados usando algo diferente de criptografia SHA256 serão identificados como tendo uma assinatura inválida. Instalação do VSIX não é bloqueada, mas o usuário será avisado.  
  
## <a name="signing-a-vsix-with-vsixsigntool"></a>Assinar um VSIX com VSIXSignTool  
 Há uma criptografia SHA256 disponível na ferramenta de assinatura [VisualStudioExtensibility](http://www.nuget.org/profiles/VisualStudioExtensibility) em nuget.org em [VsixSignTool](http://www.nuget.org/packages/Microsoft.VSSDK.Vsixsigntool).  
  
#### <a name="to-use-the-vsixsigntool"></a>Para usar o VSIXSignTool  
  
1.  Adicione seu VSIX para um projeto.  
  
2.  Clique com o botão direito no nó do projeto no Gerenciador de soluções, selecionando **adicionar | Gerenciar pacotes NuGet**.  Para obter mais informações sobre o NuGet e adicionar NuGet pacotes consulte [visão geral do NuGet](http://docs.nuget.org/) e [gerenciar pacotes de NuGet usando a caixa de diálogo](http://docs.nuget.org/Consume/Package-Manager-Dialog).  
  
3.  Procure VSIXSignTool de VisualStudioExtensibility e instalar o pacote do NuGet.  
  
4.  Agora você pode executar o VSIXSignTool do local de pacotes locais do projeto. Consulte a Ajuda de linha de comando da ferramenta para seu cenário de autenticação (VSIXSignTool.exe /?).  
  
 Por exemplo, para conectar-se com uma senha protegida no arquivo de certificado:  
  
 VSIXSignTool.exe logon /f \<certfile > / p \<senha > \<VSIXfile >  
  
## <a name="see-also"></a>Consulte também  
 [Envio de extensões do Visual Studio](../extensibility/shipping-visual-studio-extensions.md)
