---
title: "__box | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "__box"
  - "__box_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Palavra-chave __box"
  - "boxing"
  - "conversão unboxing"
  - "conversão boxing, palavra-chave box"
ms.assetid: 935b4a4d-fc45-484c-87c6-d95cfc67cc9d
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# __box
> [!NOTE]
>  Este tópico se aplica apenas a versão 1 de Managed Extensions for C\+\+. Esta sintaxe só deve ser usada para manter o código da versão 1. Consulte [Boxing](/visual-cpp/windows/boxing-cpp-component-extensions) para obter informações sobre como usar a funcionalidade equivalente na nova sintaxe.  
  
 Cria uma cópia gerenciada de um objeto da classe Value.  
  
## Sintaxe  
  
```  
  
__box(  
value-class identifier  
)  
  
```  
  
## Comentários  
 O `__box` palavra\-chave é usada para criar um objeto gerenciado \(derivado de **System:: ValueType**\) de um objeto de classe Value existente. Quando o `__box` palavra\-chave é aplicado a uma classe Value:  
  
-   Um objeto gerenciado é alocado na heap de common language runtime.  
  
-   O valor atual do objeto da classe Value bit a bit é copiado para o objeto gerenciado.  
  
-   O endereço do novo objeto gerenciado é retornado.  
  
 Esse processo é conhecido como conversão boxing. Isso permite que qualquer objeto da classe value a ser usado em rotinas genéricas que funcionam para qualquer objeto gerenciado porque o objeto gerenciado é herdado indiretamente de **System:: Object** \(como **System:: ValueType** herda de **System:: Object**\).  
  
> [!NOTE]
>  O objeto boxed recém\-criado é uma cópia do objeto da classe Value. Portanto, as modificações no valor do objeto boxed não afetam o conteúdo do objeto da classe Value.  
  
## Exemplo  
 Eis um exemplo que faz boxing e unboxing:  
  
```  
// keyword__box.cpp  
// compile with: /clr:oldSyntax  
#using < mscorlib.dll >  
using namespace System;  
  
int main() {  
  Int32 i = 1;  
  System::Object* obj = __box(i);  
  Int32 j = *dynamic_cast<__box Int32*>(obj);  
}  
```  
  
 No exemplo a seguir, um tipo de valor não gerenciado \(`V`\) é convertido e passado como um parâmetro gerenciado para o `Positive` função.  
  
```  
// keyword__box2.cpp  
// compile with: /clr:oldSyntax  
#using <mscorlib.dll>  
using namespace System;  
  
__value struct V {  
   int i;  
};  
void Positive(Object*) {}   // expects a managed class  
  
int main() {  
   V v={10};   // allocate and initialize  
   Console::WriteLine(v.i);  
  
   // copy to the common language runtime heap  
   __box V* pBoxedV = __box(v);  
   Positive(pBoxedV);   // treat as a managed class  
  
   pBoxedV->i = 20;   // update the boxed version  
   Console::WriteLine(pBoxedV->i);  
}  
```  
  
 **10 20**