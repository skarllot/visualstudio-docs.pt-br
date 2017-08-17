---
title: "Como: gerenciar uma galeria privada usando as configurações do registro | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSIX private galleries, managing
- managing VSIX private galleries
ms.assetid: 86b86442-4293-4cad-9fe2-876eef65f426
caps.latest.revision: 6
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
ms.translationtype: MT
ms.sourcegitcommit: 8ce054bf6149f0224785f4c3cd9274e86dc09d04
ms.openlocfilehash: 00c42a4dbd6a9a526d661b7fa04793d531acd8bc
ms.contentlocale: pt-br
ms.lasthandoff: 08/17/2017

---
# <a name="how-to-manage-a-private-gallery-by-using-registry-settings"></a>Como: gerenciar uma galeria privada usando as configurações do registro
Se você for um administrador ou desenvolvedor de uma extensão de Shell isolado, você pode controlar o acesso a controles, modelos e ferramentas na Galeria do Visual Studio, a Galeria de exemplos ou galerias privadas. Para tornar uma galeria disponível ou não está disponível, crie um arquivo de .pkgdef que descreve as chaves de registro modificadas e seus valores.  
  
## <a name="managing-private-galleries"></a>Gerenciar galerias privadas  
 Você pode criar um arquivo de .pkgdef para controlar o acesso a galerias em vários computadores. Este arquivo deve ter o formato a seguir.  
  
```  
[$RootKey$\ExtensionManager\Repositories\{UniqueGUID}]  
@={URI}  (REG_SZ)  
Disabled=0 | 1 (DWORD)  
Priority=0 (highest priority) ... MaxInt (lowest priority) (DWORD) (uint)  
Protocol=Atom Feed|Sharepoint (REG_SZ)  
DisplayName={DisplayName} (REG_SZ)  
DisplayNameResourceID={ID} (REG_SZ)  
DisplayNamePackageGuid={GUID} (REG_SZ)  
  
```  
  
 O `Repositories` chave refere-se para a Galeria para ser habilitado ou desabilitado. Galeria do Visual Studio e a Galeria de exemplos usam o seguinte repositório GUIDs:  
  
-   Galeria do Visual Studio: 0F45E408-7995-4375-9485-86B8DB553DC9  
  
-   Galeria de exemplos: AEB9CB40-D8E6-4615-B52C-27E307F8506C  
  
 O `Disabled` valor é opcional. Por padrão, uma galeria está habilitada.  
  
 O `Priority` valor determina a ordem na qual as galerias são listadas na caixa de diálogo Opções. Galeria do Visual Studio tem prioridade 10 e a Galeria de exemplos com prioridade de 20. Iniciam galerias privadas em prioridade 100. Se vários galerias têm o mesmo valor de prioridade, a ordem em que aparecem é determinada pelos valores de seus localizada `DisplayName` atributos.  
  
 O `Protocol` valor é necessário para galerias baseado no SharePoint ou Atom.  
  
 O `DisplayName`, ou ambos `DisplayNameResourceID` e `DisplayNamePackageGuid`, deve ser especificado. Se tudo for especificado, o `DisplayNameResourceID` e `DisplayNamePackageGuid` par é usado.  
  
## <a name="disabling-the-visual-studio-gallery-using-a-pkgdef-file"></a>Desabilitando a Galeria do Visual Studio usando um arquivo .pkgdef  
 Você pode desabilitar uma galeria em um arquivo .pkgdef. A entrada a seguir desabilita a Galeria do Visual Studio:  
  
```  
[$RootKey$\ExtensionManager\Repositories\{0F45E408-7995-4375-9485-86B8DB553DC9}]  
"Disabled"=dword:00000001  
  
```  
  
 A entrada a seguir desabilita a Galeria de exemplos:  
  
```  
[$RootKey$\ExtensionManager\Repositories\{AEB9CB40-D8E6-4615-B52C-27E307F8506C}]  
"Disabled"=dword:00000001  
  
```  
  
## <a name="see-also"></a>Consulte também  
 [Galerias privadas](../extensibility/private-galleries.md)
