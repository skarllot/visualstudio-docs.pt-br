---
title: "Usando controles HTML5 em testes de IU codificados | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2000b214-ae92-4334-b549-aa0eb4f45fe1
caps.latest.revision: 17
caps.handback.revision: 17
ms.author: "mlearned"
manager: "douge"
---
# Usando controles HTML5 em testes de IU codificados
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Os teste de IU codificados incluem suporte a alguns dos controles HTML5 incluídos no Internet Explorer 9 e no Internet Explorer 10.  
  
 **Requisitos**  
  
-   O Visual Studio Enterprise  
  
> [!WARNING]
>  Em versões anteriores ao Internet Explorer 10, era possível executar testes de UI codificados em um nível de privilégio mais alto comparado de processo do Internet Explorer.  Ao executar testes de UI codificados no Internet Explorer 10, o teste de IU codificado e o processo do Internet Explorer devem ser o mesmo nível de privilégio.  Isso é devido aos recursos de AppContainer mais seguros do Internet Explorer 10.  
  
> [!WARNING]
>  Se você criar um teste de IU codificado no Internet Explorer 10, ele não foi executado usando o Internet Explorer 9 ou Internet Explorer 8.  Isso ocorre porque o Internet Explorer 10 inclui controles HTML5, como áudio, vídeo, ProgressBar e Slider.  Esses controles HTML5 não são reconhecidos pelo Internet Explorer 9 ou pelo Internet Explorer 8.  Da mesma forma, seu teste de IU codificado usando o Internet Explorer 9 pode incluir alguns controles do HTML5 que também não serão reconhecidos pelo Internet Explorer 8.  
  
## Controles HTML5 com suporte  
 Testes de UI codificados incluem suporte para registro, reprodução e validação dos seguintes controles HTML5:  
  
-   [Controle de áudio](#UsingHTML5ControlsCodedUITestsAudio)  
  
-   [Controle de vídeo](#UsingHTML5ControlsCodedUITestsVideo)  
  
-   [Controle Deslizante](#UsingHTML5ControlsCodedUITestsSlider)  
  
-   [ProgressBar](#UsingHTML5ControlsCodedUITestsProgressBar)  
  
###  <a name="UsingHTML5ControlsCodedUITestsAudio"></a> Controle de áudio  
 **Controle de áudio:** ações no controle de áudio do HTML5 são registradas e reproduzidas corretamente.  
  
 ![Controle de áudio do HTML5](../test/media/codedui_html5_audio.png "CodedUI\_HTML5\_Audio")  
  
|Ação|Gravando|Código gerado|  
|----------|--------------|-------------------|  
|**Reproduzir áudio**<br /><br /> Diretamente do controle ou controles menu de contexto.|Reproduzir áudio \< nome \> de 00:00:00|HtmlAudio.Play\(TimeSpan\)|  
|**Buscar um momento específico no áudio**|Busca \< nome \> áudio como 00:01:48|HtmlAudio.Seek\(TimeSpan\)|  
|**Pausar o áudio**<br /><br /> Diretamente do controle ou controles menu de contexto.|Pausar \< nome \> áudio em 00:01:53|HtmlAudio.Pause\(TimeSpan\)|  
|**Desativar áudio**<br /><br /> Diretamente do controle ou controles menu de contexto.|Áudio de sem som \< nome \>|HtmlAudio.Mute\(\)|  
|**Áudio áudio**<br /><br /> Diretamente do controle ou controles menu de contexto.|Com áudio \< nome \> áudio|HtmlAudio.Unmute\(\)|  
|**Alterar o volume de áudio**|Definir o volume de \< nome \> áudio 79%|HtmlAudio.SetVolume\(float\)|  
  
 As propriedades a seguir estão disponíveis para HtmlAudio e você pode adicionar uma declaração em todos eles:  
  
```  
string AutoPlay  
string Controls  
string CurrentSrc  
string CurrentTime  
string CurrentTimeAsString  
string Duration  
string DurationAsString  
string Ended  
string Loop  
string Muted  
string Paused  
string PlaybackRate  
string ReadyState  
string Seeking  
string Src  
string Volume  
  
```  
  
 **Propriedades de pesquisa:** as propriedades de pesquisa `HtmlAudio` são `Id`, `Name` e `Title`.  
  
 **Propriedades de filtro:** as propriedades de filtro para `HtmlAudio` são `Src`, `Class`, `ControlDefinition` e `TagInstance`.  
  
> [!NOTE]
>  A quantidade de tempo de busca e Pause pode ser significativa.  Durante a reprodução, o teste de IU codificado aguardará até que o tempo especificado em `(TimeSpan)` antes de pausar o áudio.  Se por alguma circunstância especial, o tempo especificado tenha passado antes de atingir o comando Pause, uma exceção será gerada.  
  
###  <a name="UsingHTML5ControlsCodedUITestsVideo"></a> Controle de vídeo  
 **Controle de vídeo:** ações no controle de vídeo HTML5 são registradas e reproduzidas corretamente.  
  
 ![Controle de vídeo HTML5](../test/media/codedui_html5_video.png "CodedUI\_HTML5\_Video")  
  
|Ação|Gravando|Código gerado|  
|----------|--------------|-------------------|  
|**Reproduzir vídeo**<br /><br /> Diretamente do controle ou controles menu de contexto.|Reproduzir vídeo \< nome \> de 00:00:00|HtmlVideo.Play\(TimeSpan\)|  
|**Buscar um momento específico no vídeo**|Busca \< nome \> vídeo como 00:01:48|HtmlVideo.Seek\(TimeSpan\)|  
|**Pausar vídeo**<br /><br /> Diretamente do controle ou controles menu de contexto.|Pausar o vídeo \< nome \> em 00:01:53|HtmlVideo.Pause\(TimeSpan\)|  
|**Vídeo sem áudio**<br /><br /> Diretamente do controle ou controles menu de contexto.|Vídeo sem áudio \< nome \>|HtmlVideo.Mute\(\)|  
|**Vídeo de áudio**<br /><br /> Diretamente do controle ou controles menu de contexto.|Com áudio \< nome \> vídeo|HtmlVideo.Unmute\(\)|  
|**Alterar o volume do vídeo**|Definir o volume de \< nome \> vídeo 79%||  
  
 Todas as propriedades de HtmlAudio estão disponíveis para HtmlVideo.  Além disso, as três propriedades a seguintes também estão disponíveis.  Asserção pode ser adicionada em todos eles.  
  
```  
string Poster  
string VideoHeight  
string VideoWidth  
  
```  
  
 **Propriedades de pesquisa:** as propriedades de pesquisa `HtmlVideo` são `Id`, `Name` e `Title`.  
  
 **Propriedades de filtro:** as propriedades de filtro para `HtmlVideo` são `Src`, `Poster`, `Class`, `ControlDefinition` e `TagInstance`.  
  
> [!NOTE]
>  Se você Avançar ou retroceder rapidamente o vídeo usando rótulos\-30s ou \+30s, isso será agregado para buscar o momento adequado.  
  
###  <a name="UsingHTML5ControlsCodedUITestsSlider"></a> Controle Deslizante  
 **Controle deslizante:** ações no controle deslizante de HTML5 são registradas e reproduzidas corretamente.  
  
 ![Controle deslizante de HTML5](../test/media/codedui_html5_slider.png "CodedUI\_HTML5\_Slider")  
  
|Ação|Gravando|Código gerado|  
|----------|--------------|-------------------|  
|**Definir uma posição no controle deslizante**|Definir posição para \< x \> no controle deslizante \< name \>|HtmlSlider.ValueAsNumber\= \< x \>|  
  
 As propriedades a seguir estão disponíveis para HtmlSlider e asserção pode ser adicionada em todos eles:  
  
```  
string Disabled  
string Max  
string Min  
string Required  
string Step  
string ValueAsNumber  
```  
  
###  <a name="UsingHTML5ControlsCodedUITestsProgressbar"></a> Barra de Progresso  
 **ProgreesBar controle:** o ProgressBar é um controle não interactable.  Você pode adicionar asserções de `Value` e `Max` Propriedades desse controle.  
  
 ![Controle ProgressBar do HTML5](../test/media/codedui_html5_progressbar.png "CodedUI\_HTML5\_ProgressBar")  
  
## Consulte também  
 [Elementos HTML](http://go.microsoft.com/fwlink/?LinkID=232441)   
 [Usar automação de interface do usuário para testar código](../test/use-ui-automation-to-test-your-code.md)   
 [Criando testes de UI codificados](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate)   
 [Personalizando seu teste de IU codificado](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeCUITModify)   
 [Configurações e plataformas compatíveis para testes de IU codificados e gravações de ações](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)