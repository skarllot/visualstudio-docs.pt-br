---
title: "Caixa de diálogo Opções, Projetos e Soluções, Compilar e Executar | Microsoft Docs"
ms.custom: 
ms.date: 7/14/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Projects.Build_and_Run
- VS.ToolsOptionsPag.Projects.Build_and_Run
helpviewer_keywords:
- builds [Visual Studio], setting up
- run actions
- debugger, run options
ms.assetid: c884976e-c0df-4c6d-8e3a-856ea2bd547c
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: e48ebcafaca37505dbcc92bce682d0c6169004e1
ms.openlocfilehash: 8e5165b4b17195e5f9172dd25962c9486a7aeeeb
ms.contentlocale: pt-br
ms.lasthandoff: 07/26/2017

---

# <a name="options-dialog-box--projects-and-solutions-build-and-run"></a>Caixa de diálogo Opções, Projetos e Soluções, Compilar e Executar

Nesta caixa de diálogo, você pode especificar o número máximo de projetos do Visual C++ ou do Visual C# que podem ser compilados ao mesmo tempo, determinados comportamentos de build padrão e algumas configurações de log de build. Para acessar essas opções, selecione **Ferramentas > Opções**, expanda **Projetos e Soluções** e selecione **Compilar e executar**.
  
**número máximo de compilações paralelas de projetos**  
Especifica o número máximo de projetos do Visual C++ e do Visual C# que podem ser compilados ao mesmo tempo. Para otimizar o processo de build, o número máximo de compilações paralelas de projetos é automaticamente definido como o número de CPUs do seu computador. O máximo é de 32.  

**Somente compilar dependências e projetos de inicialização ao Executar**  
Compila o projeto de inicialização e suas dependências quando você usa a tecla F5 e seleciona o comando de menu **Depurar > Iniciar** ou os comandos aplicáveis no menu **Compilar**. Se ficar desmarcado, todos os projetos e dependências serão compilados. 

**Ao Executar, quando os projetos estiverem desatualizados**  
*Aplica-se somente a projetos [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)].*

Ao executar um projeto com F5 ou com o comando **Depurar > Iniciar**, a configuração padrão **Avisar para compilar** exibe uma mensagem se uma configuração do projeto estiver desatualizada. Selecione **Compilar sempre** para compilar o projeto sempre que ele for executado. Selecione **Nunca compilar** para suprimir todos os builds automáticos quando um projeto for executado.

**Ao Executar, quando ocorrerem erros de build ou implantação**  
*Aplica-se somente a projetos [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)].*

Ao executar um projeto com F5 ou com o comando **Depurar > Iniciar**, a configuração padrão **Solicitar inicialização** exibe uma mensagem se o projeto dever ser executado mesmo que o build tenha falhado. Selecione **Iniciar versão antiga** para iniciar automaticamente a última compilação boa, o que pode resultar em incompatibilidades entre o código em execução e o código-fonte. Selecione **Não iniciar** para suprimir a mensagem.

**Para novas soluções, use o projeto selecionado atualmente como o projeto de inicialização**  
Quando essa opção é definida, novas soluções usam o projeto selecionado atualmente como o projeto de inicialização.  

**Detalhamento da saída de build do projeto no MSBuild**  
Determina quanta informação aparece na Janela de **Saída** para o build.  

**Detalhamento do arquivo de log de build do projeto no MSBuild**  
*Aplica-se somente a projetos [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)].*

Determina quanta informação é gravada no arquivo de log de build, que está localizado em \\...\\*ProjectName*\Debug\\*ProjectName*.log.  

## <a name="see-also"></a>Consulte também  
-[Compilando e criando](../../ide/compiling-and-building-in-visual-studio.md)
- [Caixa de diálogo Opções, Projetos e Soluções](projects-and-solutions-options-dialog-box.md)
- [Caixa de diálogo Opções, Projetos e Soluções, Projetos Web](options-dialog-box-projects-and-solutions-web-projects.md)
