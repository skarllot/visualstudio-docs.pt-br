---
title: Janelas de ferramenta no registro | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tool windows, registering
ms.assetid: c4bb8add-7148-49e4-a377-01d059fd5524
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
ms.openlocfilehash: dc99605a367bb3584f9766b50aa2a4ff382656c4
ms.lasthandoff: 02/22/2017

---
# <a name="tool-windows-in-the-registry"></a>Janelas de ferramenta no registro
Os VSPackages que fornecem as janelas de ferramentas devem ser registrados com [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] como provedores de janela de ferramenta. Janelas de ferramentas criadas usando o modelo de pacote do Visual Studio fazer isso por padrão. Provedores de janela de ferramenta tenham chaves de registro do sistema que especificam os atributos de visibilidade, como tamanho de janela de ferramenta padrão e o local, o GUID da janela que serve como o painel de janela de ferramenta e o estilo de encaixe.  
  
 Durante o desenvolvimento, provedores de janela de ferramenta gerenciado registrar janelas de ferramenta adicionando atributos ao código-fonte e, em seguida, executando o utilitário RegPkg.exe o assembly resultante. Para obter mais informações, consulte [registrando uma janela da ferramenta](../extensibility/registering-a-tool-window.md).  
  
## <a name="registering-unmanaged-tool-window-providers"></a>Registrar provedores de janela de ferramenta não gerenciado  
 Provedores de janela de ferramenta não gerenciados devem ser registrados com [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] na seção ToolWindows do registro do sistema. O fragmento de arquivo. reg a seguir mostra como uma janela de ferramenta dinâmica pode ser registrada:  
  
```  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\<version number>\ToolWindows\{f0e1e9a1-9860-484d-ad5d-367d79aabf55}]  
@="{01069cdd-95ce-4620-ac21-ddff6c57f012}"  
"Name"="Microsoft.Samples.VisualStudio.IDE.ToolWindow.DynamicWindowPane"  
"Float"="250, 250, 410, 430"  
"DontForceCreate"=dword:00000001  
  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\ToolWindows\{f0e1e9a1-9860-484d-ad5d-367d79aabf55}\Visibility]  
"{f1536ef8-92ec-443c-9ed7-fdadf150da82}"=dword:00000000  
```  
  
 Na primeira chave no exemplo acima, o número de versão é a versão do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], como 7.1 ou 8.0, a subchave {f0e1e9a1-9860-484d-ad5d-367d79aabf55} é o GUID do painel de janela de ferramenta (DynamicWindowPane) e o valor padrão {01069cdd-95ce-4620-ac21-ddff6c57f012} é o GUID do VSPackage fornecendo a janela da ferramenta. Para obter uma explicação das subchaves Float e DontForceCreate, consulte [configuração de exibição da janela de ferramenta](../extensibility/tool-window-display-configuration.md).  
  
 A segunda chave opcional, ToolWindows\Visibility, especifica os GUIDs dos comandos que exigem a janela da ferramenta que ficará visível. Nesse caso, não há nenhum comando especificado. Para obter mais informações, consulte [configuração de exibição da janela de ferramenta](../extensibility/tool-window-display-configuration.md).  
  
## <a name="see-also"></a>Consulte também  
 [Conceitos básicos do VSPackage](../misc/vspackage-essentials.md)
