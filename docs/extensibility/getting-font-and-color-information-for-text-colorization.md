---
title: "Obtendo informações de cores para coloração de texto e fonte | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- text, coloring
- font and color control [Visual Studio SDK], coloring
ms.assetid: d1f985bd-743e-40b7-9458-d9af53647c91
caps.latest.revision: 22
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
ms.sourcegitcommit: ca7c86466fa23fb21a932f26dc24e37c71cf29b4
ms.openlocfilehash: 57b3d53f86d132779fb00608886fa7c479b71551
ms.lasthandoff: 04/05/2017

---
# <a name="getting-font-and-color-information-for-text-colorization"></a>Obtendo informações de cores para coloração de texto e fonte
O processo que renderiza ou exibe coloridos serão texto em elementos de interface do usuário depende do tipo de projeto, sua tecnologia e developer preferências. O **fontes e cores** página de propriedade armazena as configurações.  
  
 A maioria das implementações que exibem texto coloridos serão necessário o `T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults` e associados de interfaces para as configurações de exibição de apresentação, recuperar e armazenar texto.  
  
> [!NOTE]
>  Ao personalizar o editor de núcleo (que dá suporte a **EditorCategory texto**), é altamente recomendável que você use a tecnologia de cores no serviço de linguagem. Para obter mais informações, consulte [visão geral de cor e de fonte](../extensibility/font-and-color-overview.md).  
  
## <a name="getting-default-font-and-color-information"></a>Obtendo informações de cor e a fonte padrão  
 Todos os a **fontes e cores** as configurações de qualquer janela de exibição de texto devem ser especificadas no **exibir itens** de um **categoria**. Para obter mais informações, consulte [fontes e cores, ambiente, caixa de diálogo Opções](../ide/reference/fonts-and-colors-environment-options-dialog-box.md).  
  
 Para colorir, um VSPackage deve obter atual **fontes e cores** configurações. Um VSPackage pode fazer isso das seguintes maneiras, dependendo de suas necessidades:  
  
-   Use o mecanismo de persistência de fontes e cores para recuperar o estado atual ou armazenado. Para obter mais informações, consulte [acessar fonte armazenado e as configurações de cor](../extensibility/accessing-stored-font-and-color-settings.md).  
  
-   Use o <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>interface de um serviço que fornece dados de fontes e cores para obter uma instância de <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>, se o VSPackage também não é o provedor de fonte e cor.</xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> </xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>  
  
-   Implementar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>interface.</xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>  
  
 Para garantir que os resultados obtidos por meio de sondagem são atualizadas, pode ser útil usar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager>interface para determinar se uma atualização é necessária antes de chamar os métodos de recuperação do <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>interface.</xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> </xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager>  
  
 Depois que você obteve as informações de fonte e cor, analise o texto a ser exibido para identificar elementos exigir colorização e, em seguida, exibir o texto na janela usando apropriadas fontes e cores.  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider></xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults></xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>   
 [Usando fontes e texto](http://msdn.microsoft.com/Library/d43640f3-da94-4df2-a29d-a9d021a1c069)   
 [Trabalhando com cor](/cpp/windows/working-with-color-image-editor-for-icons)   
 [GDI (interface gráfica de dispositivo)](http://msdn.microsoft.com/en-us/7e1d4540-bb2e-4257-8eee-eee376acba83)
