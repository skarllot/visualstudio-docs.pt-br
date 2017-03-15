---
title: "Passo a passo: usando o IntelliTrace | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e1c9c91a-0009-4c4e-9b4f-c9ab3a6022a7
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Passo a passo: usando o IntelliTrace
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Você pode usar o IntelliTrace para coletar informações sobre eventos específicos ou categorias de eventos ou chamadas de função individuais além de eventos. Os procedimentos a seguir mostram como fazer isso.  
  
 Você pode usar o IntelliTrace no Visual Studio Enterprise edition \(mas não as edições Professional ou comunidade\).  
  
##  <a name="GettingStarted"></a> Usando o IntelliTrace somente com eventos  
 Você pode tentar depurar com eventos do IntelliTrace apenas. Eventos do IntelliTrace são eventos do depurador, exceções, eventos do .NET Framework e outros eventos do sistema. Você deve ativar ou desativar eventos específicos para controlar os eventos que o IntelliTrace registra antes de você iniciar a depuração. Para obter mais informações, consulte [Recursos do IntelliTrace](../debugger/intellitrace-features.md).  
  
 As etapas a seguir mostram como depurar com eventos do IntelliTrace somente:  
  
1.  Ative o evento do IntelliTrace para acesso a arquivos. Vá para o **Ferramentas \/ opções \/ IntelliTrace \/ eventos do IntelliTrace** página e, em seguida, expanda o **arquivo** categoria. Verifique o **arquivo** categoria de evento. Isso faz com que todos os arquivos eventos \(acessar, fechar, excluir\) a ser verificada.  
  
2.  Crie um aplicativo de console c\#. No arquivo Program.cs, adicione o seguinte `using` instrução:  
  
    ```c#  
    using System.IO;  
    ```  
  
3.  Criar um <xref:System.IO.FileStream> no método Main, lê\-lo, fechá\-lo e excluí\-lo. Adicione outra linha apenas para ter um local para definir um ponto de interrupção:  
  
    ```c#  
    static void Main(string[] args)  
    {  
        FileStream fs = File.Create("WordSearchInputs.txt");  
        fs.ReadByte();  
        fs.Close();  
        File.Delete("WordSearchInputs.txt");  
  
        Console.WriteLine("done");  
    }  
    ```  
  
4.  Defina um ponto de interrupção `Console.WriteLine("done");`  
  
5.  Inicie a depuração como de costume. \(Pressione **F5** ou clique em **Depurar \/ iniciar depuração**.  
  
    > [!TIP]
    >  Manter o **locais** e **Autos** janelas abertas enquanto você estiver depurando para ver e registre os valores nessas janelas.  
  
6.  A execução pára no ponto de interrupção. Se você não vir o **Ferramentas de diagnóstico** janela, clique em **Debug \/ Windows \/ eventos do IntelliTrace**.  
  
     No **Ferramentas de diagnóstico** janela, encontrar o **eventos** guia \(você verá 3 guias, **eventos**, **uso de memória**, e **uso de CPU**\). O **eventos** guia exibe uma lista cronológica de eventos, terminando com o último evento antes que o depurador interrompe a execução. Você deve ver um evento chamado **acesso WordSearchInputs.txt**.  
  
     Captura de tela a seguir é da atualização 1 do Visual Studio 2015.  
  
     ![IntelliTrace&#45;Update1](../debugger/media/intellitrace-update1.png "IntelliTrace\-Update1")  
  
7.  Selecione o evento para expandir seus detalhes.  
  
     Captura de tela a seguir é da atualização 1 do Visual Studio 2015.  
  
     ![IntelliTraceUpdate1&#45;SingleEvent](../debugger/media/intellitraceupdate1-singleevent.png "IntelliTraceUpdate1\-SingleEvent")  
  
     Você pode escolher o link do nome do caminho para abrir o arquivo. Se o nome de caminho completo não estiver disponível, o **Abrir arquivo** caixa de diálogo é exibida.  
  
     Clique em **Ativar histórico de depuração**, que define contexto do depurador para a hora em que o evento selecionado foi coletado, mostrando os dados históricos no **pilha de chamadas**, **locais** e os outros participantes janelas do depurador. Se o código\-fonte estiver disponível, o Visual Studio move o ponteiro para o código correspondente na janela de origem, para que você possa examiná\-lo.  
  
     Captura de tela a seguir é da atualização 1 do Visual Studio 2015.  
  
     ![HistoricalDebugging&#45;Update1](../debugger/media/historicaldebugging-update1.png "HistoricalDebugging\-Update1")  
  
8.  Se você não encontrar o erro, tente examinar outros eventos que levam ao bug. Você também pode ter informações de chamada de registro do IntelliTrace para que você possa depurar chamadas de função.  
  
## Usando o IntelliTrace com eventos e chamadas de função  
 O IntelliTrace poderá registrar chamadas de função com eventos. Isso permite que você consulte o histórico da pilha de chamadas e retroceda e avance por meio de chamadas em seu código. O IntelliTrace registra dados como nomes de função, pontos de entrada e saída da função e determinados valores de parâmetros e valores de retorno. Consulte [Recursos do IntelliTrace](../debugger/intellitrace-features.md).  
  
1.  Ative a coleta de chamada. \(No **Ferramentas \/ opções \/ IntelliTrace \/ geral**, selecione **eventos do IntelliTrace e informações de chamada**. IntelliTrace começará a coletar essas informações quando a próxima sessão de depuração é iniciada.  
  
    > [!TIP]
    >  Isso pode reduzir a velocidade de seu aplicativo e aumentar o tamanho dos arquivos de log IntelliTrace \(arquivos. itrace\) que você está salvando em disco. Para obter o máximo de dados chamada mas minimizar os efeitos, registrar dados somente dos módulos que lhe interessam. Para alterar o tamanho máximo dos arquivos. itrace, vá para **Ferramentas \/ opções \/ IntelliTrace \/ avançado**, e especifique a quantidade máxima de espaço em disco. O padrão é 250 MB.  
  
2.  Inicie a depuração do aplicativo de console c\# criado na seção anterior. A execução pára no ponto de interrupção. Se você não vir o **Ferramentas de diagnóstico** janela, clique em **Debug \/ Windows \/ eventos do IntelliTrace**.  
  
3.  Alterne para o **chamadas** guia.  
  
     Agora você vê chamadas de função do aplicativo, começando com a chamada de raiz \(na solução atual, o ponto de entrada principal\) e terminando com o local em que a execução interrompe.  
  
     Selecione uma das chamadas de função e clique duas vezes nele. Você deve ver os pontos de entrada e saída da função, bem como as chamadas que a chamada atual fez para outras funções e os eventos do IntelliTrace gerados pela chamada. Se você não tiver o histórico de depuração ativado, esta ação ativa. Para obter mais informações sobre o histórico de depuração, consulte [Depuração de histórico](../debugger/historical-debugging.md).  
  
    > [!NOTE]
    >  Você pode ver que algumas chamadas estão esmaecidas. Isso ocorre porque o IntelliTrace não registra dados dos módulos correspondentes. Para ver esses dados, com o IntelliTrace colete dados desses módulos. Para obter informações sobre como especificar módulos, consulte [Recursos do IntelliTrace](../debugger/intellitrace-features.md).  
  
## Próximas etapas