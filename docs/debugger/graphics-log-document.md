---
title: "Documentos de log de gr&#225;fico | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.graphics.vsglog.error"
  - "vs.graphics.experiment"
  - "vs.graphics.vsglog"
ms.assetid: 6ccb1269-d55f-49c4-920d-baedf7de2888
caps.latest.revision: 31
caps.handback.revision: 31
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Documentos de log de gr&#225;fico
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

O documento de Log de gráficos é o registro de eventos de gráficos que ocorreu enquanto seu aplicativo estava sendo executado em uma sessão de diagnóstico de gráficos.  Após ser gravado, você pode examinar o log no Visual Studio gráficos Analyzer para diagnosticar problemas de desempenho e de renderização.  
  
 Isso é o que um documento de log gráficos é semelhante no analisador de gráficos:  
  
 ![Um log de gráficos contendo dois quadros capturados.](~/debugger/graphics/media/gfx_diag_demo_graphics_log_orientation.png "gfx\_diag\_demo\_graphics\_log\_orientation")  
  
## Entendendo os documentos de log de gráficos  
 Usando o analisador de gráficos para examinar um documento de log de gráficos, você pode visualizar os efeitos de eventos do Direct3D no destino de renderização que ocorreram durante a captura.  É possível indicar as áreas exatas do destino de renderização com saídas inesperadas.  Ao selecionar um pixel na área afetada, você pode usar os diagnósticos gráficos para inspecioná\-la e inspecionar seus sombreadores, os eventos do Direct3D que a afetaram, a pilha de chamadas do aplicativo que resultou nesses eventos e os objetos do DirectX compatíveis com esses eventos.  Você pode usar essas informações para diagnosticar problemas de renderização em seu jogo ou aplicativo.  
  
 A parte superior da janela \(**Graphics Experiment.vsglog**\) exibe a saída do destino de renderização atual do quadro selecionado. A parte inferior exibe uma **Lista de Quadros** com miniaturas dos quadros capturados.  
  
#### Para inspecionar um quadro  
  
-   Na **Lista de Quadros**, selecione o quadro que você quer inspecionar.  A saída do destino de renderização que aparece na parte superior do documento de log de gráficos é atualizada para exibir o quadro selecionado.  
  
#### Para inspecionar um pixel  
  
-   Na parte superior do documento de log de gráficos, selecione o pixel desejado da saída do destino de renderização.  Com um pixel selecionado, você pode usar a janela **Histórico de Pixel de Gráficos** para exibir informações detalhadas sobre o pixel selecionado.  Para obter mais informações, consulte [Histórico de Pixel](../debugger/graphics-pixel-history.md).  
  
## Máquina de reprodução  
 No canto superior direito da **Lista de Quadros** fica a **Máquina de Reprodução**.  O computador de reprodução é um computador ou dispositivo usado para reproduzir eventos de gráficos de um arquivo de log de gráficos em uma sessão de diagnóstico posterior.  Ao usar outro dispositivo para reproduzir eventos capturados no lugar de seu computador de desenvolvimento, você pode reproduzir com mais precisão o ambiente de execução no qual o problema ocorreu. Por exemplo, você pode usar um computador com drivers ou hardwares gráficos que seu computador de desenvolvimento não usa ou outros tipos de dispositivos, como um tablet Windows RT baseado em ARM ou um dispositivo com Windows Phone.  
  
 Para obter informações sobre como especificar um computador de reprodução, consulte [Como alterar a máquina de reprodução de diagnóstico do gráfico](../debugger/how-to-change-the-graphics-diagnostics-playback-machine.md).  
  
## Informações de resumo do log de elementos gráficos  
 Quando o arquivo do log de elementos gráficos está ativo, a janela **Propriedades** exibe informações sobre o ambiente que hospedou a sessão de captura dos diagnósticos gráficos.  Essa janela exibe informações de diversas categorias.  
  
 **Informações do Direct3D**  
 Apresenta informações sobre os recursos de hardware e driver da placa de vídeo usada durante a sessão de captura.  
  
|Propriedade|Descrição|  
|-----------------|---------------|  
|**Formato XR High Color de 10 bits**|**True** se o formato XR High Color de 10 bits for compatível; caso contrário, **False**.|  
|**DirectCompute CS 4.x**|**True** se Compute Shader 4.0 for compatível; caso contrário, **False**.|  
|**Sombreadores de precisão dupla**|**True** se a placa de vídeo for compatível com valores de ponto flutuante com precisão dupla \(64 bits\); caso contrário, **False**.|  
|**Listas de Comando do Driver**|**True** se o driver for compatível com as listas de comando; caso contrário, **False**.|  
|**Driver com Criações Concorrentes**|**True** se o driver for compatível com criação concorrente \(assíncrona\); caso contrário, **False**.|  
|**Formatos Estendidos \(BGRA, etc.\)**|**True** se formatos estendidos como BGRA forem compatíveis; caso contrário, **False**.|  
|**Nível máximo de Recursos de Hardware**|Exibe o mais alto nível de recursos permitido pela placa de vídeo.|  
  
 **Exibir informações**  
 Apresenta informações sobre a placa de vídeo usada durante a sessão de captura.  
  
|Propriedade|Descrição|  
|-----------------|---------------|  
|**Descrição**|A cadeia de caracteres de descrição da placa de vídeo.|  
|**Memória de Vídeo**|A quantidade de memória instalada no adaptador gráfico.|  
|**Nome do Driver**|O nome do driver do adaptador gráfico.|  
|**Versão do Driver**|A versão do driver do adaptador gráfico.|  
|**Nome**|O nome do adaptador gráfico.|  
  
 **Arquivo de experimento**  
 Apresenta informações sobre o arquivo de experimento associado à sessão de captura.  
  
|Propriedade|Descrição|  
|-----------------|---------------|  
|**Caminho**|O caminho do arquivo .vsglog. **Note:**  Essa propriedade não é usada em capturas herdadas.|  
  
 **Informações do módulo**  
 Apresenta o nome e a versão das DLLs \(bibliotecas de vínculo dinâmico\) que foram carregadas pelo aplicativo durante a sessão de captura.  
  
 **Informações do sistema**  
 Apresenta informações sobre o hardware e o sistema operacional que hospedou o aplicativo durante a sessão de captura.  
  
|Propriedade|Descrição|  
|-----------------|---------------|  
|**Memória**|A quantidade de memória instalada no computador.|  
|**Arquitetura do Sistema Operacional**|A arquitetura da CPU de destino do sistema operacional.|  
|**Versão do Sistema Operacional**|A versão do sistema operacional.|  
|**Processador**|O processador instalado no computador.|  
|**Arquitetura do Aplicativo de Destino**|A arquitetura da CPU de destino do aplicativo.  As informações presentes nesse campo podem ser diferentes das do campo **Arquitetura do Sistema Operacional**.|  
  
 **Aplicativo de destino**  
 Apresenta informações sobre o aplicativo que passou pela sessão de captura.  
  
|Propriedade|Descrição|  
|-----------------|---------------|  
|**Data\/hora da última modificação**|A data e hora em que o aplicativo foi compilado.|  
|**Caminho**|O caminho do aplicativo.|  
|**ID do Processo**|A ID do processo atribuída ao aplicativo.|  
|**Versão**|A versão do aplicativo.|  
  
 **Arquivo de log VSG**  
 Apresenta informações sobre o documento de log de gráficos.  
  
|Propriedade|Descrição|  
|-----------------|---------------|  
|**Criado por**|O nome do aplicativo que criou o documento de log de gráficos.  Por exemplo, se a sessão de captura foi iniciada no [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] \(captura manual\), o valor dessa propriedade será [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].|  
|**Hora de Início da Sessão**|A data e hora em que a sessão de captura começou.|  
|**Tamanho**|O tamanho do documento de log de gráficos.|  
  
## Consulte também  
 [Instruções passo a passo: objetos ausentes devido ao sombreamento de vértice](../debugger/walkthrough-missing-objects-due-to-vertex-shading.md)   
 [Instruções passo a passo: depurando erros de renderização devido ao sombreamento](../debugger/walkthrough-debugging-rendering-errors-due-to-shading.md)