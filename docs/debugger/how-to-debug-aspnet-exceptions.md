---
title: "Como depurar exce&#231;&#245;es do ASP.NET | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "ASP.NET, exceções"
  - "depurando [Visual Studio], Exceções ASP.NET"
  - "exceções, ASP.NET"
ms.assetid: 1810096e-de8c-435e-be3d-f365d0cd0a6a
caps.latest.revision: 23
caps.handback.revision: 23
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Como depurar exce&#231;&#245;es do ASP.NET
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

A depuração de exceções é uma parte importante do desenvolvimento de um aplicativo [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] robusto.  Você pode encontrar informações gerais sobre como depurar exceções em [Gerenciando exceções com o depurador](../debugger/managing-exceptions-with-the-debugger.md).  
  
 Para depurar as exceções não tratadas do [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], você deve se certificar de que o depurador é interrompido para elas.  O tempo de execução do [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] tem um manipulador de exceção de nível superior.  Portanto, por padrão, o depurador nunca é interrompido em exceções não tratadas.  Para interromper o depurador quando uma exceção é lançada, você deve selecionar a configuração **Interromper quando uma exceção for: Lançada** para essa exceção específica na caixa de diálogo **Exceções**.  
  
 Se você tiver habilitado Apenas Meu Código, **Interromper quando uma exceção for: Lançada** não fará com que o depurador seja imediatamente interrompido caso uma exceção seja lançada em um método do .NET Framework ou em outro código do sistema.  Em vez disso, a execução continua até que o depurador atinja código que não seja do sistema, e então é interrompida.  Como resultado, você não precisa depurar o código do sistema quando ocorre uma exceção.  
  
 Apenas Meu Código oferece outra opção que pode ser ainda mais útil: **Interromper quando uma exceção for: Sem tratamento do usuário**.  Se você escolher essa configuração para uma exceção, o depurador interromperá a execução no código do usuário, mas apenas se a exceção não for detectada e não for tratada pelo código do usuário.  Essa configuração anula o efeito do manipulador de exceção de nível superior do [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], porque esse manipulador está em código de não usuário.  
  
### Para ativar a depuração de exceções do ASP.NET com Apenas Meu Código  
  
1.  No menu **Depurar**, clique em **Exceções**.  
  
     A caixa de diálogo **Exceções** é exibida.  
  
2.  Na linha **Exceções do Common Language Runtime**, selecione **Lançadas** ou **Sem tratamento do usuário**.  
  
     Para usar a configuração **Sem tratamento do usuário**, **Apenas Meu Código** deve estar ativado.  
  
### Para usar as práticas recomendadas para o tratamento de exceção do ASP.NET  
  
-   Coloque blocos de `try … catch` em torno do código que pode lançar exceções que você pode prever e sabe como manipular.  Por exemplo, se o aplicativo estiver fazendo chamadas para um serviço Web XML ou diretamente para o SQL Server, o código deve estar em blocos **try … catch** porque várias exceções podem ocorrer.