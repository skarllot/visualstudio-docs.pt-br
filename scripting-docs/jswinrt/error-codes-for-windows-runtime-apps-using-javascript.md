---
title: "Códigos de erro dos aplicativos Windows Runtime usando JavaScript | Microsoft Docs"
ms.custom: 
ms.date: 05/10/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- javascript
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- JavaScript, Windows Runtime error codes
- VS.WebClient.Help.APPHOST9601
- VS.WebClient.Help.APPHOST9602
- VS.WebClient.Help.APPHOST9603
- VS.WebClient.Help.APPHOST9604
- VS.WebClient.Help.APPHOST9605
- VS.WebClient.Help.APPHOST9606
- VS.WebClient.Help.APPHOST9607
- VS.WebClient.Help.APPHOST9608
- VS.WebClient.Help.APPHOST9610
- VS.WebClient.Help.APPHOST9611
- VS.WebClient.Help.APPHOST9613
- VS.WebClient.Help.APPHOST9614
- VS.WebClient.Help.APPHOST9615
- VS.WebClient.Help.APPHOST9616
- VS.WebClient.Help.APPHOST9617
- VS.WebClient.Help.APPHOST9618
- VS.WebClient.Help.APPHOST9619
- VS.WebClient.Help.APPHOST9620
- VS.WebClient.Help.APPHOST9623
- VS.WebClient.Help.APPHOST9624
- VS.WebClient.Help.APPHOST9626
ms.assetid: 4c6d4e90-602a-4b56-ae74-3458929da442
caps.latest.revision: 1
author: erikadoyle
ms.author: edoyle
manager: jken
ms.translationtype: HT
ms.sourcegitcommit: 47057e9611b824c17077b9127f8d2f8b192d6eb8
ms.openlocfilehash: 89b91a3246d0a6e2980459c2c35c7361168bccd4
ms.contentlocale: pt-br
ms.lasthandoff: 08/11/2017

---
# <a name="error-codes-for-windows-runtime-apps-using-javascript"></a>Códigos de erro dos aplicativos Windows Runtime usando JavaScript
Aqui estão os códigos de erro exibidos pelo console do Microsoft Visual Studio ao desenvolver aplicativos do Windows Runtime usando JavaScript.
  
Erro | Comentários
----- | -------
APPHOST9601: "Não é possível carregar *remoteURI*. Um aplicativo não é capaz de carregar conteúdo da Web remoto no contexto local." | Para obter mais informações sobre o que é permitido no contexto da Web, consulte [Recursos e restrições por contexto](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh465373.aspx).
APPHOST9602: "'javascript:' é um valor de atributo inválido e será ignorado. Não use URIs do ' javascript:' no contexto local." | Por motivos de segurança, não é possível usar URIs 'javascript:' no contexto local. Para obter mais informações sobre o que é permitido no contexto local, consulte [Recursos e restrições por contexto](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh465373.aspx).
APPHOST9603: "não é possível carregar o plug-in ActiveX que tem a ID de classe *classID*.  Os aplicativos não são capazes de carregar controles ActiveX." | Aplicativos do Windows Runtime usando JavaScript não dão suporte a controles personalizados do Microsoft ActiveX. Se você precisar de um controle de interface do usuário, use um controle da Web padrão, uma biblioteca de controles ou então crie seu próprio controle personalizado. Se você precisa executar lógica personalizada, crie um objeto personalizado do Windows Runtime em vez disso. Para obter informações sobre outras diferenças entre HTML, CSS e JavaScript, consulte [Recursos e diferenças entre HTML, CSS e JavaScript](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh465380.aspx).
APPHOST9604: "não é possível navegar para *uri* porque ele usa uma codificação de caracteres inválida.  Um aplicativo pode navegar somente para arquivos codificados em UTF8." | Todo o HTML, JavaScript e CSS acessado por um Windows Runtime deve ser codificado como UTF-8 (formato de transformação Unicode de 8 bits). Para obter informações sobre outras diferenças entre HTML, CSS e JavaScript, consulte [Recursos e diferenças entre HTML, CSS e JavaScript](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh465380.aspx).
APPHOST9605: "Não é possível navegar para *targetURI* de *sourceURI* porque o URI de destino está em uma zona de segurança mais alta. Você não pode navegar de uma zona com segurança inferior a uma zona com segurança mais alta, a menos que você esteja navegando para um URI de contexto local de um URI de contexto da Web e você já tenha registrado o URI de contexto local com o método MSApp.addPublicLocalApplicationUri." | Para obter mais informações, consulte [MSApp.addPublicLocalApplicationUri](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh465759.aspx).
APPHOST9606: "não é possível carregar *uri* porque ele usa uma conexão HTTP e o metaelemento ms-https-connections-only está presente. Apenas conexões HTTPS são permitidas quando você usa o metaelemento ms-https-connections-only. Use uma conexão HTTPS ou, se você não precisar de uma conexão segura, remova o metaelemento." | Para obter mais informações, consulte [Como exigir uma conexão HTTPS](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh452771.aspx).
APPHOST9607: "O aplicativo não é capaz de iniciar o URI em *uri* devido a este erro: *failureCode*." | Um recurso ausente ou um arquivo inválido são causas comuns desse erro.
APPHOST9608: "O aplicativo não foi capaz de navegar para a página about:blank por causa deste erro: *errorCode*." | 
APPHOST9610: "o aplicativo encontrou um erro ao se preparar para navegar até uma página de erro personalizada: *errorCode*." |
APPHOST9611: "O aplicativo não foi capaz de navegar para a página de erro personalizada por causa deste erro: *errorCode*." |
APPHOST9613: "O aplicativo não foi capaz de navegar para * uri* devido a este erro: *errorCode*." | 
APPHOST9614: "Um documento em um iframe solicitou o modo de documento *requestedDocMode*, mas o sistema impõe o modo de documento *currentDocMode*. O Iframe usará o modo de documento *currentDocMode*." | Para obter mais informações sobre como exibir o conteúdo da Web remoto, consulte [Como vincular a páginas da Web externas](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh780594.aspx).
APPHOST9615: "O aplicativo não consegue baixar o arquivo em *uri* porque ele foi invocado programaticamente fora do contexto local." | Ocorre quando o conteúdo no contexto da Web tenta baixar um arquivo programaticamente.
APPHOST9616: "Esse URI não é capaz de usar APIs de geolocalização.  APIs de geolocalização podem ser chamadas apenas de um URI que faz parte do pacote ou está incluído no elemento ApplicationContentUris do manifesto." | Para obter mais informações sobre o que é permitido no contexto da Web, consulte [Recursos e restrições por contexto](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh465373.aspx).
APPHOST9617: "Esse URI não é capaz de usar APIs de área de transferência.  As APIs de área de transferência podem ser chamadas apenas de um URI que faz parte do pacote ou está incluído no elemento ApplicationContentUris do manifesto." | Para obter mais informações sobre o que é permitido no contexto da Web, consulte [Recursos e restrições por contexto](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh465373.aspx).
APPHOST9618: "Esse URI não pode usar window.close.  O método window.close pode ser invocado apenas de conteúdo do pacote que foi carregado com um esquema de URI do ms-appx." | Para obter mais informações sobre o que é permitido no contexto da Web, consulte [Recursos e restrições por contexto](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh465373.aspx).
APPHOST9619: "O aplicativo não pode navegar para *uri* porque uma página no contexto da Web não pode ser o documento de nível superior do aplicativo. Em vez disso, carregue a página em um iframe." | Você não pode navegar sua página de nível superior para uma página da Web remota, mas o aplicativo pode exibir uma página da Web em um [iframe](https://msdn.microsoft.com/en-us/library/ms535258(v=vs.85).aspx). Para obter mais informações sobre como exibir o conteúdo da Web remoto, consulte [Como vincular a páginas da Web externas](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh780594.aspx).
APPHOST9620: "Este aplicativo foi fechado porque ele usou uma conexão HTTP e o metaelemento ms-https-connections-only está presente. Apenas conexões HTTPS são permitidas quando você usa o metaelemento ms-https-connections-only. Use uma conexão HTTPS ou, se você não precisar de uma conexão segura, remova o metaelemento." | Para obter mais informações, consulte [Como exigir uma conexão HTTPS](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh452771.aspx).
APPHOST9623: "O aplicativo não foi capaz de resolver *url* devido a este erro: *errorCode*." | Uma causa comum desse erro é um arquivo ausente.  
APPHOST9624: "o aplicativo não pode usar o script para carregar a URL de *url* porque a URL inicia outro aplicativo. Somente a interação direta do usuário pode iniciar outro aplicativo." | Os aplicativos não podem iniciar outros aplicativos diretamente. Outros aplicativos podem ser iniciados pelo usuário quando o aplicativo implementa certos contratos. Para obter mais informações, consulte [Contratos e extensões de aplicativos](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh464906.aspx).
APPHOST9626: "Uma referência direta ao arquivo de recurso `ms-appx://1d33240b-0b00-40e4-a416-a4750c48787f/ja-jp\images\logo.scale-140.png` foi detectada. Essa referência causa falhas quando usada fora do ambiente de depuração." | Devido ao caminho do arquivo `logo.scale-140.png`, esse arquivo PNG é tratado como um recurso localizado, causando o erro em que os recursos localizados não podem ser referenciados diretamente. Consulte [Globalizando seu aplicativo (HTML)](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh465006.aspx) se você pretende usar esse arquivo como um recurso de linguagem. Caso contrário, tente renomear o diretório problemático.
  
## <a name="see-also"></a>Consulte também  
 [Usar o Windows Runtime em JavaScript](../jswinrt/using-the-windows-runtime-in-javascript.md)
