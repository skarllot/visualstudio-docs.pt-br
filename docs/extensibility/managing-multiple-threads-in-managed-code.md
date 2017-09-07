---
title: "Como: gerenciar vários Threads em código gerenciado | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 59730063-cc29-4dae-baff-2234ad8d0c8f
caps.latest.revision: 7
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
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 21fcc9388b40baa9e003b4beb876ba2f0f23fbaf
ms.contentlocale: pt-br
ms.lasthandoff: 09/06/2017

---
# <a name="how-to-managing-multiple-threads-in-managed-code"></a>Como: gerenciar vários Threads em código gerenciado
Se você tiver uma extensão de VSPackage gerenciada que chama os métodos assíncronos ou tem operações executadas em threads que não seja o thread de interface de usuário do Visual Studio, você deve seguir as diretrizes fornecidas abaixo. Você pode manter o thread de interface do usuário responsiva porque ele não precisa aguardar o trabalho em outro thread para concluir. Você pode tornar seu código mais eficiente, porque você não tem mais threads que ocupam espaço de pilha e você pode tornar mais confiável e mais fácil depurar porque você evitar deadlocks e trava.  
  
 Em geral, você pode alternar do thread da interface do usuário a um thread diferente, ou vice-versa. Quando o método retorna, o segmento atual é o thread do qual ele foi originalmente chamado.  
  
> [!IMPORTANT]
>  As diretrizes a seguir usam as APIs no <xref:Microsoft.VisualStudio.Threading> namespace, em particular, o <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory> classe. As APIs no namespace são novas no [!INCLUDE[vs_dev12](../extensibility/includes/vs_dev12_md.md)]. Você pode obter uma instância de um <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory> do <xref:Microsoft.VisualStudio.Shell.ThreadHelper> propriedade `ThreadHelper.JoinableTaskFactory`.  
  
## <a name="switching-from-the-ui-thread-to-a-background-thread"></a>Alternando do Thread da interface do usuário para um Thread em segundo plano  
  
1.  Se você estiver usando o thread de interface do usuário e você deseja fazer o trabalho assíncrona em um thread em segundo plano, use Task.Run():  
  
    ```csharp  
    await Task.Run(async delegate{  
        // Now you're on a separate thread.  
    });  
    // Now you're back on the UI thread.  
  
    ```  
  
2.  Se você estiver usando o thread de interface do usuário e você deseja bloquear sincronicamente enquanto você estiver executando o trabalho em um thread em segundo plano, use o <xref:System.Threading.Tasks.TaskScheduler> propriedade `TaskScheduler.Default` dentro de <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.Run%2A>:  
  
    ```csharp  
    // using Microsoft.VisualStudio.Threading;  
    ThreadHelper.JoinableTaskFactory.Run(async delegate {  
        await TaskScheduler.Default;  
        // You're now on a separate thread.  
        DoSomethingSynchronous();  
        await OrSomethingAsynchronous();  
    });  
    ```  
  
## <a name="switching-from-a-background-thread-to-the-ui-thread"></a>Alternar de um Thread em segundo plano para o Thread de interface do usuário  
  
1.  Se você estiver em um thread em segundo plano e você deseja fazer algo no thread da interface do usuário, use <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A>:  
  
    ```csharp  
    // Switch to main thread  
    await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync();  
    ```  
  
     Você pode usar o <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A> método para alternar para o thread de interface do usuário. Esse método envia uma mensagem para o thread de interface do usuário com a continuação do método assíncrono atual e também se comunica com o restante da estrutura threading para definir a prioridade correta e evitar deadlocks.  
  
     Se o método de thread em segundo plano não é assíncrono e você não pode fazer assíncrona, você ainda pode usar o `await` sintaxe para alternar para o thread de interface do usuário ao encapsular seu trabalho com <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.Run%2A>, como no exemplo:  
  
    ```csharp  
    ThreadHelper.JoinableTaskFactory.Run(async delegate {  
        // Switch to main thread  
        await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync();  
        // Do your work on the main thread here.  
    });  
    ```
