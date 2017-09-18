---
title: FIELD_MODIFIERS | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- FIELD_MODIFIERS
helpviewer_keywords:
- FIELD_MODIFIERS enumeration
ms.assetid: 1e44681c-1f03-41a9-9c04-b79f231b0822
caps.latest.revision: 15
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
ms.openlocfilehash: 3c0907df76806e239a1c10987afe6608bc169e5f
ms.lasthandoff: 02/22/2017

---
# <a name="fieldmodifiers"></a>FIELD_MODIFIERS
Especifica os modificadores para um tipo de campo.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
enum enum_FIELD_MODIFIERS {   
   FIELD_MOD_NONE             = 0x00000000,  
  
   // Modifier of the field  
   FIELD_MOD_ACCESS_NONE      = 0x00000001,  
   FIELD_MOD_ACCESS_PUBLIC    = 0x00000002,  
   FIELD_MOD_ACCESS_PROTECTED = 0x00000004,  
   FIELD_MOD_ACCESS_PRIVATE   = 0x00000008,  
  
   // Storage modifier of the field  
   FIELD_MOD_NOMODIFIERS      = 0x00000010,  
   FIELD_MOD_STATIC           = 0x00000020,  
   FIELD_MOD_CONSTANT         = 0x00000040,  
   FIELD_MOD_TRANSIENT        = 0x00000080,  
   FIELD_MOD_VOLATILE         = 0x00000100,  
   FIELD_MOD_ABSTRACT         = 0x00000200,  
   FIELD_MOD_NATIVE           = 0x00000400,  
   FIELD_MOD_SYNCHRONIZED     = 0x00000800,  
   FIELD_MOD_VIRTUAL          = 0x00001000,  
   FIELD_MOD_INTERFACE        = 0x00002000,  
   FIELD_MOD_FINAL            = 0x00004000,  
   FIELD_MOD_SENTINEL         = 0x00008000,  
   FIELD_MOD_INNERCLASS       = 0x00010000,  
   FIELD_TYPE_OPTIONAL        = 0x00020000,  
   FIELD_MOD_BYREF            = 0x00040000,  
   FIELD_MOD_HIDDEN           = 0x00080000,  
   FIELD_MOD_MARSHALASOBJECT  = 0x00100000,  
   FIELD_MOD_SPECIAL_NAME     = 0x00200000,  
   FIELD_MOD_HIDEBYSIG        = 0x00400000,  
  
   FIELD_MOD_WRITEONLY        = 0x80000000,  
   FIELD_MOD_ACCESS_MASK      = 0x000000ff,  
   FIELD_MOD_MASK             = 0xffffff00,  
   FIELD_MOD_ALL              = 0x7fffffff  
};  
typedef DWORD FIELD_MODIFIERS;  
```  
  
```c#  
public enum enum_FIELD_MODIFIERS {  
   FIELD_MOD_NONE             = 0x00000000,  
  
   // Modifier of the field  
   FIELD_MOD_ACCESS_NONE      = 0x00000001,  
   FIELD_MOD_ACCESS_PUBLIC    = 0x00000002,  
   FIELD_MOD_ACCESS_PROTECTED = 0x00000004,  
   FIELD_MOD_ACCESS_PRIVATE   = 0x00000008,  
  
   // Storage modifier of the field  
   FIELD_MOD_NOMODIFIERS      = 0x00000010,  
   FIELD_MOD_STATIC           = 0x00000020,  
   FIELD_MOD_CONSTANT         = 0x00000040,  
   FIELD_MOD_TRANSIENT        = 0x00000080,  
   FIELD_MOD_VOLATILE         = 0x00000100,  
   FIELD_MOD_ABSTRACT         = 0x00000200,  
   FIELD_MOD_NATIVE           = 0x00000400,  
   FIELD_MOD_SYNCHRONIZED     = 0x00000800,  
   FIELD_MOD_VIRTUAL          = 0x00001000,  
   FIELD_MOD_INTERFACE        = 0x00002000,  
   FIELD_MOD_FINAL            = 0x00004000,  
   FIELD_MOD_SENTINEL         = 0x00008000,  
   FIELD_MOD_INNERCLASS       = 0x00010000,  
   FIELD_TYPE_OPTIONAL        = 0x00020000,  
   FIELD_MOD_BYREF            = 0x00040000,  
   FIELD_MOD_HIDDEN           = 0x00080000,  
   FIELD_MOD_MARSHALASOBJECT  = 0x00100000,  
   FIELD_MOD_SPECIAL_NAME     = 0x00200000,  
   FIELD_MOD_HIDEBYSIG        = 0x00400000,  
  
   FIELD_MOD_WRITEONLY        = 0x80000000,  
   FIELD_MOD_ACCESS_MASK      = 0x000000ff,  
   FIELD_MOD_MASK             = 0xffffff00,  
   FIELD_MOD_ALL              = 0x7fffffff  
};  
```  
  
## <a name="members"></a>Membros  
 FIELD_MOD_ACCESS_TYPE  
 Indica que o campo não pode ser acessado.  
  
 FIELD_MOD_ACCESS_PUBLIC  
 Indica que o campo tem acesso público.  
  
 FIELD_MOD_ACCESS_PROTECTED  
 Indica que o campo tenha acesso protegido.  
  
 FIELD_MOD_ACCESS_PRIVATE  
 Indica que o campo possui acesso privado.  
  
 FIELD_MOD_NOMODIFIERS  
 Indica que o campo não tem nenhum modificador.  
  
 FIELD_MOD_STATIC  
 Indica que o campo é estático.  
  
 FIELD_MOD_CONSTANT  
 Indica que o campo é uma constante.  
  
 FIELD_MOD_TRANSIENT  
 Indica que o campo é transitório.  
  
 FIELD_MOD_VOLATILE  
 Indica que o campo volátil.  
  
 FIELD_MOD_ABSTRACT  
 Indica que o campo é abstrato.  
  
 FIELD_MOD_NATIVE  
 Indica que o campo é nativo.  
  
 FIELD_MOD_SYNCHRONIZED  
 Indica que o campo será sincronizado.  
  
 FIELD_MOD_VIRTUAL  
 Indica que o campo é virtual.  
  
 FIELD_MOD_INTERFACE  
 Indica que o campo é uma interface.  
  
 FIELD_MOD_FINAL  
 Indica que o campo final.  
  
 FIELD_MOD_SENTINEL  
 Indica que o campo é uma Sentinela.  
  
 FIELD_MOD_INNERCLASS  
 Indica que o campo é uma classe interna.  
  
 FIELD_TYPE_OPTIONAL  
 Indica que o campo é opcional.  
  
 FIELD_MOD_BYREF  
 Indica que o campo é um argumento de referência. Isso é especificamente para argumentos de método.  
  
 FIELD_MOD_HIDDEN  
 Indica que o campo deve ser ocultado ou apresentado em outro contexto; Por exemplo, [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] locais estáticos.  
  
 FIELD_MOD_MARSHALASOBJECT  
 Indica que o campo representa um objeto com um `IUnknown` interface.  
  
 FIELD_MOD_SPECIAL_NAME  
 Indica que o campo tem um nome especial, por exemplo, `.ctor` para um construtor ([!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] somente).  
  
 FIELD_MOD_HIDEBYSIG  
 Indica que o campo tem o `Overloads` palavra-chave aplicada a ele ([!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] somente).  
  
 FIELD_MOD_WRITEONLY  
 Indica que o campo é somente gravação. Esse valor não está incluído no `FIELD_MOD_ALL`, como o uso somente desses campos somente leitura para a avaliação da função. Um usuário deve solicitar explicitamente `FIELD_MOD_WRITEONLY` campos.  
  
 FIELD_MOD_ACCESS_MASK  
 Indica uma máscara de acesso de campo.  
  
 FIELD_MOD_MASK  
 Indica uma máscara para modificadores de campo.  
  
## <a name="remarks"></a>Comentários  
 Usado para o `dwModifiers` membro do [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md) estrutura.  
  
 Esses valores também são passados para o [EnumFields](../../../extensibility/debugger/reference/idebugcontainerfield-enumfields.md) método filtrar campos específicos.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md)   
 [EnumFields](../../../extensibility/debugger/reference/idebugcontainerfield-enumfields.md)
