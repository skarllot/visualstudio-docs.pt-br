---
title: "Trechos de código do Visual C++ | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 74e26fd4-e5ca-4611-a816-0a521b4947a0
caps.latest.revision: 2
author: gewarren
ms.author: gewarren
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: ca7c86466fa23fb21a932f26dc24e37c71cf29b4
ms.openlocfilehash: b4d0801f9e3924fd801f30b750d0f5dbfca634fd
ms.contentlocale: pt-br
ms.lasthandoff: 04/05/2017

---
# <a name="visual-c-code-snippets"></a>Trechos de código do Visual C++
No Visual Studio, você pode usar trechos de código para adicionar código comumente usado nos seus arquivos de código do C++. Em geral, você pode usar os trechos de código de forma bem parecida com o C#, mas o conjunto de trechos de código padrão é diferente.  
  
 Você pode adicionar um trecho de código em um local específico no seu código (inserção) ou envolver algum código selecionado com um trecho de código.  
  
## <a name="inserting-a-code-snippet"></a>Inserindo um trecho de código  
 Para inserir um trecho de código, abra um arquivo de código do C++ (.cpp ou .h), clique em algum lugar dentro do arquivo e siga um destes procedimentos:  
  
-   Clique com o botão direito do mouse para obter o menu de contexto e selecione **Inserir Trecho**  
  
-   No menu **Editar / IntelliSense**, selecione **Inserir Trecho**  
  
-   Use as teclas de atalho: **CTRL + K + X**  
  
 Você deve ver uma lista de opções que começam com **#if**. Ao selecionar **#if**, você verá o seguinte código adicionado ao arquivo:  
  
```cpp  
#if 0  
  
#endif // 0  
```  
  
 Em seguida, você pode substituir o 0 pela condição correta.  
  
## <a name="using-a-code-snippet-to-surround-selected-code"></a>Usar um trecho de código para envolver o código selecionado  
 Para usar um trecho de código para envolver o código selecionado, selecione uma linha (ou várias linhas) e siga um destes procedimentos:  
  
1.  Clique com o botão direito do mouse para obter o menu de contexto e selecione **Envolver com**  
  
2.  No menu **Editar / IntelliSense**, selecione **Envolver com**  
  
3.  Use as teclas de atalho: **CTRL + K + S**  
  
 Selecione **#if**. Você deve ver algo parecido com isso:  
  
```cpp  
#if 0  
#include "pch.h"  // or whatever line you had selected  
#endif // 0  
```  
  
 Em seguida, você pode substituir o 0 pela condição correta.  
  
## <a name="where-can-i-find-a-complete-list-of-the-c-code-snippets"></a>Onde posso encontrar uma lista completa dos trechos de código do C++?  
 Você pode encontrar a lista completa de trechos de código do C++ indo até o **Gerenciador de Trechos de Código** (no menu **Ferramentas**) e configurando a **Linguagem** para **Visual C++**. Na janela abaixo, expanda **Visual C++**. Você verá os nomes de todos os trechos de código do C++ em ordem alfabética.  
  
 Os nomes da maioria dos trechos de código são auto-explicativos, mas alguns nomes podem ser confusos.  
  
## <a name="class-vs-classi"></a>Class versus classi  
 O trecho **class** fornece a definição de uma classe chamada MyClass, com o construtor e o destruidor padrão apropriado, em que as definições do construtor e do destruidor estão localizadas fora da classe:  
  
```cpp  
class MyClass  
{  
public:  
MyClass();  
~MyClass();  
  
private:  
  
};  
  
MyClass::MyClass()  
{  
}  
  
MyClass::~MyClass()  
{  
}  
```  
  
 O trecho de código classi também fornece a definição de uma classe chamada MyClass, mas o construtor e o destruidor padrão estão definidos dentro da definição de classe:  
  
```cpp  
class MyClass  
{  
public:  
MyClass()  
{  
}  
  
~MyClass()  
{  
}  
  
private:  
  
};  
```  
  
## <a name="for-vs-foreach-vs-forr-vs-rfor"></a>For versus foreach versus forr versus rfor  
 Há quatro trechos de código for diferentes que fornecem diferentes tipos de loops de for.  
  
 O trecho **for** fornece um loop `for` em que a condição é baseada no comprimento (em `size_t`) de um objeto:  
  
```cpp  
for (size_t i = 0; i < length; i++)  
{  
  
}  
```  
  
 O trecho **foreach** fornece um loop `for each` que itera sobre os membros de uma coleção:  
  
```cpp  
for each (object var in collection_to_loop)  
{  
  
}  
```  
  
 O trecho **forr** fornece um loop `for` reverso em que a condição é baseada no comprimento (em inteiros) de um objeto:  
  
```cpp  
for (int i = length - 1; i >= 0; i--)  
{  
  
}  
```  
  
 O trecho **rfor** fornece um loop for (link) [baseado em intervalo](/cpp/cpp/range-based-for-statement-cpp):  
  
```cpp  
for (auto& i : v)  
{  
  
}  
```  
  
## <a name="the-destructor-snippet-"></a>O trecho de destruidor (~)  
 O trecho de destruidor (**~**) apresenta comportamento diferente em diferentes contextos. Se você inserir este trecho dentro de uma classe, ele fornecerá um destruidor para essa classe. Por exemplo, considerando o seguinte código:  
  
```cpp  
class SomeClass {  
  
};  
```  
  
 Se você inserir o trecho de destruidor, ele fornecerá um destruidor para a SomeClass:  
  
```cpp  
class SomeClass {  
    ~SomeClass()  
    {  
  
    }  
};  
```  
  
 Se você tentar inserir o trecho de destruidor fora de uma classe, ele fornecerá um destruidor com um nome de espaço reservado:  
  
```cpp  
~TypeNamePlaceholder()  
{  
  
```
