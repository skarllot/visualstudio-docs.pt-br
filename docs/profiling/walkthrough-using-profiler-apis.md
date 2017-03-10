---
title: "Instru&#231;&#245;es passo a passo: usando APIs do criador de perfil | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ferramentas de desempenho, explicações passo a passo"
  - "ferramentas de criação de perfil, explicações passo a passo"
ms.assetid: c2ae0b3e-a0ca-4967-b4df-e319008f520e
caps.latest.revision: 16
caps.handback.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Instru&#231;&#245;es passo a passo: usando APIs do criador de perfil
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

O passo a passo usa um aplicativo C\# demonstrar como usar as APIs de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Ferramentas de Criação de Perfil.  Você usará as APIs do profiler para limitar a quantidade de dados coletados durante a criação da instrumentação.  
  
 As etapas deste passo a passo geralmente se aplicam ao aplicativo c. criando \/C  Para cada idioma, você terá que configurar adequadamente seu ambiente de criação.  
  
 Normalmente, você iniciará para analisar o desempenho do aplicativo usando analisar de exemplo.  Se a criação de perfil de exemplo não fornece informações que localiza um afunilamento, analisar a instrumentação pode fornecer um nível de detalhe maior.  Analisar a instrumentação é muito útil para investigar a interação do thread.  
  
 No entanto, um nível de detalhe maior significa que mais dados são coletados.  Você pode descobrir que analisar a instrumentação cria arquivos de dados grandes.  Além disso, a instrumentação é mais provável que afete o desempenho do aplicativo.  Para obter mais informações, consulte [Noções básicas sobre valores de dados de instrumentação](../profiling/understanding-instrumentation-data-values.md) e [Noções básicas sobre valores de dados de amostragem](../profiling/understanding-sampling-data-values.md)  
  
 O profiler do Visual Studio permite que você limite a coleção de dados.  Este passo a passo oferece um exemplo de como limitar a coleção de dados usando as APIs do profiler.  O profiler do Visual Studio fornece uma API para a coleta de dados de controle do aplicativo.  
  
 Para o código nativo, as APIs do profiler do Visual Studio estiverem em VSPerf.dll.  O arquivo de cabeçalho, VSPerf.h, e a biblioteca de importação, VSPerf.lib, está localizado diretórios das ferramentas do Microsoft Visual Studio 9 team em \\ \\ ferramentas de desempenho.  
  
 Para código gerenciado, as APIs do profiler estão no Microsoft.VisualStudio.Profiler.dll.  Este DLL for localizado diretórios das ferramentas do Microsoft Visual Studio 9 team em \\ \\ ferramentas de desempenho.  Para obter mais informações, consulte <xref:Microsoft.VisualStudio.Profiler>.  
  
## Pré-requisitos  
 Este passo a passo pressupõe que sua escolha do ambiente de desenvolvimento é configurado para oferecer suporte à depuração e a amostragem.  Os tópicos a seguir fornecem uma visão geral desses pré\-requisitos:  
  
 [Como escolher métodos de coleção](../profiling/how-to-choose-collection-methods.md)  
  
 [Como fazer referência a informações de símbolo do Windows](../profiling/how-to-reference-windows-symbol-information.md)  
  
 Por padrão, quando o profiler for iniciado, o profiler coleta dados no nível global.  O código a seguir no início do programa gerencia analisar global.  
  
```  
DataCollection.StopProfile(  
ProfileLevel.Global,  
DataCollection.CurrentId);  
```  
  
 Você pode desativar a coleta de dados na linha de comando sem o uso de uma chamada ao API.  As etapas a seguir pressupõem a linha de comando o ambiente de criação que é configurado para executar as ferramentas para analisar e como suas ferramentas de desenvolvimento.  Isso inclui configurações necessárias para VSInstr e VSPerfCmd.  Consulte a linha de comando Ferramentas de Criação de Perfil.  
  
## Limitando a coleta de dados usando APIs do profiler  
  
#### Para criar o código para analisar  
  
1.  Crie um novo projeto C\# no Visual Studio, ou use uma construção de linha de comando, dependendo de sua preferência.  
  
    > [!NOTE]
    >  A construção deve fazer referência a biblioteca de Microsoft.VisualStudio.Profiler.dll, localizada diretórios das ferramentas do Microsoft Visual Studio 9 team em \\ \\ ferramentas de desempenho.  
  
2.  Copie e cole o código a seguir em seu projeto:  
  
    ```  
    using System;  
    using System.Collections.Generic;  
    using System.Text;  
    using Microsoft.VisualStudio.Profiler;  
  
    namespace ConsoleApplication2  
    {  
        class Program  
        {  
            public class A  
            {  
             private int _x;  
  
             public A(int x)  
             {  
              _x = x;  
             }  
  
             public int DoNotProfileThis()  
             {  
              return _x * _x;  
             }  
  
             public int OnlyProfileThis()  
             {  
              return _x + _x;  
             }  
  
             public static void Main()  
             {  
            DataCollection.StopProfile(  
            ProfileLevel.Global,  
            DataCollection.CurrentId);  
              A a;  
              a = new A(2);  
              int x;      
              Console.WriteLine("2 square is {0}", a.DoNotProfileThis());  
              DataCollection.StartProfile(  
                  ProfileLevel.Global,  
                  DataCollection.CurrentId);  
              x = a.OnlyProfileThis();  
              DataCollection.StopProfile(  
                  ProfileLevel.Global,   
                  DataCollection.CurrentId);  
              Console.WriteLine("2 doubled is {0}", x);  
             }  
            }  
  
        }  
    }  
    ```  
  
#### Para coletar e exibir dados no Visual Studio industry  
  
1.  Abra [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE.  No menu de **Analisar** , aponte para **Criador de Perfis**, e selecione **Nova sessão de desempenho.**  
  
2.  Adicionar seu binário compilado à lista de **Destinos** na janela de **Desempenho Explorer** .  Clique com o botão direito do mouse em **Destinos**, e selecione **Adicionar binário de destino**.  Localize binário na caixa de diálogo de **Adicionar binário de destino** , e clique em **Abrir**.  
  
3.  **Instrumentação** Selecione na lista de **Método** na barra de ferramentas de **Desempenho Explorer** .  
  
4.  Clique em **Iniciar a análise**.  
  
     O profiler proverá e executará binários e criará um arquivo de relatório de desempenho.  O arquivo de relatório de desempenho aparecerá no nó de **Relatórios** de **Desempenho Explorer**.  
  
5.  Abra o arquivo de relatório resultante de desempenho.  
  
 Por padrão, quando o profiler for iniciado, o profiler coletará dados no nível global.  O código a seguir no início do programa gerencia analisar global.  
  
```  
DataCollection.StopProfile(  
ProfileLevel.Global,  
DataCollection.CurrentId);  
```  
  
#### Para coletar e exibir dados na linha de comando  
  
1.  Criar uma versão de depuração do código de exemplo criado em “criando o código para analisar o procedimento”, anteriormente neste passo a passo.  
  
2.  Para analisar um aplicativo gerenciado, digite o seguinte comando para definir as variáveis de ambiente apropriadas:  
  
     VsPefCLREnv \/traceon  
  
3.  Digite o seguinte comando: VSInstr \<filename\>.exe  
  
4.  Digite o seguinte comando: VSPerfCmd \/start:trace \/output:\<filename\>.vsp  
  
5.  Digite o seguinte comando: VSPerfCmd \/globaloff  
  
6.  Execute o programa.  
  
7.  Digite o seguinte comando: VSPerfCmd \/shutdown  
  
8.  Digite o seguinte comando: VSPerfReport \/calltrace:\<filename\>.vsp  
  
     Um arquivo .csv será criado no diretório atual com os dados de desempenho resultantes.  
  
## Consulte também  
 <xref:Microsoft.VisualStudio.Profiler>   
 [Referência da API do Visual Studio Profiler \(nativo\)](../profiling/visual-studio-profiler-api-reference-native.md)   
 [Guia de Introdução](../profiling/getting-started-with-performance-tools.md)   
 [Criando perfil a partir da linha de comando](../profiling/using-the-profiling-tools-from-the-command-line.md)