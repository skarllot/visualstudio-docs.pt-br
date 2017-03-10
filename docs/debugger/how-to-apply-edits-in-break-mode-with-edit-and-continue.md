---
title: "Como aplicar edi&#231;&#245;es no modo de interrup&#231;&#227;o com editar e continuar | Microsoft Docs"
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
  - "vs.debug.variables.failededit"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "VB"
helpviewer_keywords: 
  - "Modo de interrupção, aplicando alterações de código"
  - "código, editando o modo de interrupção"
  - "codificando, editando o modo de interrupção"
  - "Editar e Continuar [Visual Basic], aplicando edições no modo de interrupção"
  - "Editar e continuar, aplicando edições no modo de interrupção"
  - "edição, Modo de interrupção"
ms.assetid: 1eef7498-6a1f-4fba-8146-510adc6375c9
caps.latest.revision: 30
caps.handback.revision: 30
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Como aplicar edi&#231;&#245;es no modo de interrup&#231;&#227;o com editar e continuar
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Você pode usar Editar e Continuar para editar o código no modo de interrupção e, depois, continuar sem interromper e reiniciar a execução.  
  
 Editar e Continuar não está disponível nos seguintes cenários de depuração:  
  
-   Depuração de modo misto \(nativo\/gerenciado\).  
  
-   Depuração de SQL.  
  
-   Depurando um despejo do Dr.  Watson.  
  
-   Editando o código após uma exceção sem tratamento, quando a opção de **Voltar para a pilha de chamadas em exceções não tratadas** não está selecionada.  
  
-   Depurando um aplicativo inserido de tempo de execução.  
  
-   Depurando um aplicativo com **Anexar a** em vez de executando o aplicativo com **Iniciar** no menu **Depurar**.  
  
-   Depurando código otimizado.  
  
-   Depurando código gerenciado quando o destino é um aplicativo de 64 bits.  Se você desejar usar Editar e Continuar, deve definir o destino como x86.  \(*Projetos***Propriedades**, **Compilação** guia, configurações **Avançadas do Compilador.**\).  
  
-   Depurando uma versão antiga do código depois que uma nova versão não é compilada devido a erros de compilação.  
  
### Para editar código no modo de interrupção  
  
1.  Entre no modo de interrupção executando um destes procedimentos:  
  
    -   Defina um ponto de interrupção no código e escolha **Iniciar Depuração** no menu **Depurar** e aguarde até que o aplicativo atinja o ponto de interrupção.  
  
         – ou –  
  
    -   Inicie a depuração e selecione **Interromper Tudo** no menu **Depurar**.  
  
         – ou –  
  
    -   Quando uma ocorrer exceção, escolha **Habilitar Edição** no **Assistente de Exceção**.  
  
2.  Faça as alterações de código desejadas e legais.  
  
     Para obter mais informações, consulte [Edições não suportadas em Editar e Continuar do Visual Basic](../debugger/unsupported-edits-in-visual-basic-edit-and-continue.md).  
  
    > [!NOTE]
    >  Se você tentar fazer uma alteração de código que não seja permitida por Editar e Continuar, sua edição será sublinhada por uma linha ondulada roxa e uma tarefa será exibida na Lista de Tarefas.  Você não poderá continuar a execução do código a menos que desfaça a alteração de código ilegal.  
  
3.  No menu **Depurar**, clique em **Continuar** para retomar a execução.  
  
     O código agora é executado com as edições aplicadas incorporadas ao projeto.  
  
## Consulte também  
 [Edições não suportadas em Editar e Continuar do Visual Basic](../debugger/unsupported-edits-in-visual-basic-edit-and-continue.md)   
 [Editar e Continuar \(Visual Basic\)](../debugger/edit-and-continue-visual-basic.md)