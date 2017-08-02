---
title: "Como posso depurar uma viola&#231;&#227;o de acesso? | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.access"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "depuração de violação de acesso"
  - "depurando [Visual Studio], violações de acesso"
ms.assetid: 9311d754-0ce9-4145-b147-88b6ca77ba63
caps.latest.revision: 18
caps.handback.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Como posso depurar uma viola&#231;&#227;o de acesso?
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

## Descrição do problema  
 Meu programa produz uma violação de acesso. Como depurar isso?  
  
## Solução  
 Se você receber uma violação de acesso em uma linha de código que cancela a referência de vários ponteiros, pode ser difícil descobrir quais ponteiro causou a violação de acesso. Iniciando na atualização 1 do Visual Studio 2015, a caixa de diálogo de exceção agora explicitamente nomeia o ponteiro que causou a violação de acesso.  
  
 Por exemplo, dado o código a seguir, você deve obter uma violação de acesso:  
  
```cpp  
#include <iostream>  
using namespace std;  
  
class ClassB {  
public:  
    	ClassC* C;  
    	ClassB() {  
		        C = new ClassC();  
    	}  
     void printHello() {  
		        cout << "hello world";  
    	}  
};  
  
class ClassA {  
public:  
    ClassB* B;  
	  ClassA() {  
		        B = nullptr;  
	    }  
};  
  
int main() {  
    ClassA* A = new ClassA();  
	  A->B->printHello();  
}  
```  
  
 Se você executar esse código na atualização 1 do Visual Studio 2015, você verá a seguinte caixa de diálogo de exceção:  
  
 ![AccessViolationCPlus](~/debugger/media/accessviolationcplus.png "AccessViolationCPlus")  
  
 Se você não puder determinar por que o ponteiro causou uma violação de acesso, rastrear o código para certificar\-se de que o ponteiro causando o problema foi atribuído corretamente.  Se ele é passado como um parâmetro, certifique\-se de que ela é passada corretamente e você não criar acidentalmente um [superficial cópia](http://stackoverflow.com/questions/184710/what-is-the-difference-between-a-deep-copy-and-a-shallow-copy). Em seguida, verificar se os valores não são sendo acidentalmente alterados em algum lugar no programa criando um ponto de interrupção de dados para o ponteiro em questão para certificar\-se de que não está sendo modificada em outro lugar no programa. Para obter mais informações sobre pontos de interrupção de dados, consulte a seção de ponto de interrupção de dados em [Usando pontos de interrupção](../debugger/using-breakpoints.md).  
  
## Consulte também  
 [Perguntas frequentes de depuração do código nativo](../debugger/debugging-native-code-faqs.md)