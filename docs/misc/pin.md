---
title: "__pin | Microsoft Docs"
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
  - "__pin"
  - "__pin_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ponteiros de fixação, palavra-chave PIN"
  - "tipos não gerenciados"
  - "Palavra-chave __pin"
ms.assetid: 8b55c792-5654-4669-bb0e-a52100f4cabe
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# __pin
**Observação** neste tópico se aplica somente à versão 1 de Managed Extensions for C\+\+. Esta sintaxe só deve ser usada para manter o código da versão 1. Consulte [pin\_ptr \(C\+\+\/CLI\)](/visual-cpp/windows/pin-ptr-cpp-cli) para obter informações sobre como usar a funcionalidade equivalente na nova sintaxe.  
  
 Impede que um objeto ou incorporado de uma classe gerenciada seja movido pelo common language runtime durante a coleta de lixo.  
  
## Sintaxe  
  
```  
  
__pin   
identifier  
  
```  
  
## Comentários  
 O `__pin` palavra\-chave declara um ponteiro para um objeto ou incorporado de uma classe gerenciada e impede que o objeto seja movido durante a coleta de lixo pelo common language runtime. Isso é útil ao passar o endereço de uma classe gerenciada para uma função não gerenciada porque o endereço não será alterado inesperadamente durante a resolução da chamada de função não gerenciada.  
  
 Um ponteiro de fixação permanece válido no seu escopo léxico. Assim que o ponteiro de fixação sair do escopo, o objeto não é mais considerado fixado \(a menos, é claro, existem outros ponteiros de fixação apontando para ou no objeto\).  
  
 O MSIL não tem nenhum conceito de "escopo de bloco"\-\-ao vivo todas as variáveis locais no escopo da função. Para informar ao sistema que a fixação não está mais em vigor, o compilador gera código que atribui NULL ao ponteiro de fixação. Isso também é que você pode fazer por conta própria, se você precisar desafixar o objeto sem sair do bloco.  
  
 Você não deve converter seu ponteiro de fixação em um ponteiro não gerenciado e continuar usando esse ponteiro não gerenciado depois que o objeto não estiver mais fixado \(depois que o ponteiro de fixação sair do escopo\). Ao contrário dos ponteiros gc, fixando ponteiros pode ser convertido para nogc, ponteiros não gerenciados. No entanto, é responsabilidade do usuário para manter a fixação enquanto o ponteiro não gerenciado está em uso.  
  
 Usando um ponteiro de fixação para obter o endereço de uma variável e, em seguida, usar esse endereço depois que o ponteiro de fixação sair do escopo, não deve ser feito.  
  
```  
// keyword_pin_scope_bad.cpp  
// compile with: /clr:oldSyntax /LD  
#using <mscorlib.dll>  
__gc struct X {  
   int x;  
};  
  
int* Get_x( X* pX ) {  
   int __pin* px = &pX -> x;  
   return px;   // BE CAREFUL px goes of scope,   
                // so object pointed by it is no longer pinned,  
                // making the return value unsafe.  
}  
```  
  
 O exemplo a seguir mostra o comportamento correto:  
  
```  
// keyword_pin_scope_good.cpp  
// compile with: /clr:oldSyntax /LD  
#using <mscorlib.dll>  
__gc struct X {  
   int x;  
};  
  
int Get_x( X* pX ) {  
   int __pin* px = &pX -> x;  
   return *px;   // OK, value obtained from px before px out of scope  
}  
```  
  
## Exemplo  
 No exemplo a seguir, o objeto apontado por `pG` é fixado até que ele passa fora do escopo:  
  
```  
// keyword__pin.cpp  
// compile with: /clr:oldSyntax  
#using <mscorlib.dll>  
#include <iostream>  
  
__gc class G {   
public:   
   int i;   
   G() {i = 0;};  
};  
  
class H {  
public:  
   // unmanaged function  
   void incr(int * i) {  
      (*i)++;   
      std::cout << *i << std::endl;  
   };  
};  
  
int main() {  
   G __pin * pG = new G;  // pG is a pinning pointer  
   H * h = new H;  
   // pointer to managed data passed as actual parameter of unmanaged   
   // function call  
   h->incr(& pG -> i);   
}  
```  
  
## Saída  
  
```  
1  
```