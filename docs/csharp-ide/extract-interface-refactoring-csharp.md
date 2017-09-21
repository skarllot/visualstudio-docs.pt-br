---
title: "Extract Interface Refactoring (C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.csharp.refactoring.extractinterface"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "refactoring [C#], Extract Interface"
  - "Extract Interface refactoring operation [C#]"
ms.assetid: 7d0aa225-3b33-4331-9652-5a67cac6f3d0
caps.latest.revision: 25
caps.handback.revision: 25
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Extract Interface Refactoring (C#)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

A extração da Interface é uma operação de refatoração que oferece uma maneira fácil para criar uma nova interface com membros que se originam de uma classe existente, struct ou interface.  
  
 Quando vários clientes usam o mesmo subconjunto de membros de uma classe, struct ou interface, ou quando várias classes, structs ou interfaces têm um subconjunto de membros em comum, pode ser útil abranger o subconjunto de membros em uma interface.  Para obter mais informações sobre o uso de interfaces, consulte [Interfaces](/dotnet/csharp/programming-guide/interfaces/index).  
  
 A extração da Interface gera uma interface em um novo arquivo e posiciona o cursor no início do novo arquivo.  Você pode especificar quais membros para extrair para a nova interface, o nome da nova interface e o nome do arquivo gerado usando o  **Extrair Interface** caixa de diálogo.  
  
### Para usar a extrair Interface  
  
1.  Crie um aplicativo de console chamado  `ExtractInterface`e, em seguida, substitua `Program` com o seguinte código  
  
    ```c#  
    // Invoke Extract Interface on ProtoA.  
    // Note:  the extracted interface will be created in a new file.  
    class ProtoA  
    {  
        public void MethodB(string s) { }  
    }  
    ```  
  
2.  Com o cursor posicionado no `MethodB`e clique em  **Extrair Interface** sobre o  **Refactor** menu.  
  
     O  **Extrair Interface** caixa de diálogo aparece.  
  
     Você também pode digitar o atalho de teclado CTRL \+ R, I para exibir o  **Extrair Interface** caixa de diálogo.  
  
     Você pode também clica o mouse, aponte para  **Refactor**e, em seguida, clique em  **Extrair Interface** para exibir o  **Extrair Interface** caixa de diálogo.  
  
3.  Clique em  **Selecionar todos os**.  
  
4.  Clique em **OK**.  
  
     Você verá o novo arquivo, IProtoA.cs e o código a seguir:  
  
    ```c#  
    using System;  
    namespace TopThreeRefactorings  
    {  
        interface IProtoA  
        {  
            void MethodB(string s);  
        }  
    }  
    ```  
  
## Comentários  
 Este recurso só é acessível quando o cursor é posicionado na classe, struct ou interface que contém os membros que você gostaria de extrair.  Quando o cursor está nesta posição, invoca a operação de refatoração Extrair Interface.  
  
 Quando você chama a extração da interface em uma classe ou em uma struct, a lista de interfaces e bases é modificada para incluir o nome da nova interface.  Quando você chama a extração da interface em uma interface, a lista de interfaces e bases não é modificada.  
  
## Consulte também  
 [Refactoring \(C\#\)](../csharp-ide/refactoring-csharp.md)