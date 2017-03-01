---
title: Registrando manipuladores de comandos do Assembly de interoperabilidade | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- interop assemblies, command handlers
- command handling with interop assemblies, registering
ms.assetid: 303cd399-e29d-4ea1-8abe-5e0b59c12a0c
caps.latest.revision: 19
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
ms.openlocfilehash: 9b9c7accacde48f691d631b91905d5c292532efc
ms.lasthandoff: 02/22/2017

---
# <a name="registering-interop-assembly-command-handlers"></a>Registrando manipuladores de comandos do Assembly de interoperabilidade
Um VSPackage deve registrar [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] para que o ambiente de desenvolvimento integrado (IDE) encaminha seus comandos corretamente.  
  
 O registro pode ser atualizado editando manualmente ou usando um arquivo de registro (. rgs). Para obter mais informações, consulte [criação de Scripts do registrador](/visual-cpp/atl/creating-registrar-scripts).  
  
 Estrutura de pacote gerenciado (MPF) fornece essa funcionalidade por meio de <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute>classe.</xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute>  
  
 [Referência de formato de tabela do comando](http://msdn.microsoft.com/en-us/09e9c6ef-9863-48de-9483-d45b7b7c798f) recursos estão localizados em dlls de interface do usuário de satélite não gerenciado.  
  
## <a name="command-handler-registration-of-a-vspackage"></a>Registro do manipulador de comando de um VSPackage  
 Um VSPackage funciona como um manipulador para a interface do usuário (IU)-baseado em comandos exige uma entrada de registro denominada após o VSPackage `GUID`. Essa entrada de registro Especifica o local do arquivo de recursos de interface do usuário do VSPackage e do recurso de menu dentro desse arquivo. A entrada de registro está localizada em HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\\*\<versão >*\Menus, onde * \<versão >* é a versão do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], por exemplo 9.0.  
  
> [!NOTE]
>  O caminho raiz do HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\*\<versão >* pode ser substituído por uma alternativa raiz quando o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] shell é inicializado. Para obter mais informações sobre o caminho raiz, consulte [instalando os VSPackages com o Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md).  
  
### <a name="the-ctmenu-resource-registry-entry"></a>A entrada de registro de recurso CTMENU  
 A estrutura da entrada do registro é:  
  
```  
HKEY_LOCAL_MACHINE\Software\VisualStudio\<Version>\  
  Menus\  
    <GUID> = <Resource Information>  
```  
  
 \<*GUID*> é o `GUID` do VSPackage no formato {XXXXXX-XXXX-XXXX-XXXX-XXXXXXXXX}.  
  
 *\<Informações sobre o recurso >* consiste em três elementos separados por vírgulas. Esses elementos são, em ordem:  
  
 \<*Caminho para a DLL do recurso*>, \< *ID de recurso do Menu*>, \< *Menu versão*>  
  
 A tabela a seguir descreve os campos de \< *informações sobre o recurso*>.  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|\<*Caminho para a DLL de recurso*>|Este é o caminho completo para a DLL que contém o recurso de menu do recurso ou estiver em branco, indicando que os recursos do VSPackage DLL deve ser usado (como especificado na subchave pacotes onde o VSPackage em si é registrado).<br /><br /> É comum deixar esse campo em branco.|  
|\<*ID de recurso do menu*>|Esta é a ID de recurso a `CTMENU` recursos que contém todos os elementos de interface do usuário para o VSPackage como compilados a partir de um [VSCT](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md) arquivo.|  
|\<*Versão de menu*>|Este é um número usado como uma versão para o `CTMENU` recursos. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]usa esse valor para determinar se ele precisa remerge o conteúdo da `CTMENU` recurso com o cache de todos os `CTMENU` recursos. Um remerge é disparada, executando o comando de instalação devenv.<br /><br /> Esse valor deve ser inicialmente definido como 1 e incrementado após cada alteração no `CTMENU` recursos e antes que ocorra o remerge.|  
  
### <a name="example"></a>Exemplo  
 Aqui está um exemplo de um par de entradas de recurso:  
  
```  
HKEY_LOCAL_MACHINE\Software\VisualStudio\9.0Exp\  
  Menus\  
    {019971D6-4685-11D2-B48A-0000F87572EB} = ,1, 10  
    {1b027a40-8f43-11d0-8d11-00a0c91bc942} = , 10211, 3  
```  
  
## <a name="see-also"></a>Consulte também  
 [Como os VSPackages adicionar elementos de Interface do usuário](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Comandos e Menus que usam Assemblies de interoperabilidade](../../extensibility/internals/commands-and-menus-that-use-interop-assemblies.md)
