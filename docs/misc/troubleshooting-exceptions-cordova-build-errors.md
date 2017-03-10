---
title: "Exce&#231;&#245;es de solu&#231;&#227;o de problemas: Erros de compila&#231;&#227;o de Cordova | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BLD102"
  - "BLD10205"
  - "BLD301"
  - "BLD401"
  - "BLDErr_Build_NodeMissing"
  - "BLDErr_BLD_Win8Required"
ms.assetid: 781c09e3-0704-4b30-9230-036cbdb2dff9
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
---
# Exce&#231;&#245;es de solu&#231;&#227;o de problemas: Erros de compila&#231;&#227;o de Cordova
Este tópico descreve algumas das mensagens de erro mais comuns que você pode ver ao usando o Visual Studio Tools for Apache Cordova.  
  
-   [MSBUILD: erro de compilação cordova BLD102: sem esse arquivo ou diretório 'config'](#BLD102)  
  
-   [MSBUILD: erro de compilação cordova BLD301: um agente de compilação do iOS remoto não foi configurado](#BLD301)  
  
-   [MSBUILD: erro de compilação cordova BLD401: não foi possível localizar o módulo &lt; modulename &gt;](#BLD401)  
  
-   [MSBUILD: erro de compilação cordova BLD10205: Instale o destino Android](#BLD10205)  
  
-   [Não foi possível determinar o caminho BLDErr_Build_NodeMissing executável do Node. js.](#BLDErr_Build_NodeMissing)  
  
-   [BLDErr_Build_Win8Required](#BLDErr_Build_Win8Required)  
  
 Se precisar de ajuda geral mais erros no seu aplicativo Cordova de solução de problemas, consulte [Resolvendo erros de compilação](https://taco.visualstudio.com/en-us/docs/resolving-build-errors/).  
  
##  <a name="BLD102"></a> MSBUILD: erro de compilação cordova BLD102: sem esse arquivo ou diretório 'config'  
 Se você vir esse erro, certifique\-se de que o projeto inclui um arquivo config. XML na raiz do projeto e certifique\-se de que seu projeto está no computador local e não que residem em um compartilhamento de rede.  
  
 Para obter mais informações, consulte [de StackOverflow](http://stackoverflow.com/questions/27134007/new-cordova-project-gives-the-error-bld00102-no-such-file-or-directory-confi).  
  
##  <a name="BLD301"></a> MSBUILD: erro de compilação cordova BLD301: um agente de compilação do iOS remoto não foi configurado  
 é a cadeia de caracteres de erro completa:  
  
-   MSBUILD: erro de compilação cordova BLD301: um agente de compilação do iOS remoto não foi configurado. Configure um em Ferramentas \> Opções \> Ferramentas para Apache Cordova \> Configuração do agente remoto. Para obter detalhes e alternativas, consulte http:\/\/go.microsoft.com\/fwlink\/?LinkID\=511904  
  
 Para obter informações sobre como instalar e configurar o agente remotebuild para iOS, consulte [guia de configuração do iOS.](http://taco.visualstudio.com/en-us/docs/ios-guide/)  
  
##  <a name="BLD401"></a> MSBUILD: erro de compilação cordova BLD401: não foi possível localizar o módulo \< modulename \>  
 É a cadeia de caracteres de erro completa:  
  
-   MSBUILD: erro de compilação cordova BLD401: erro: BLD00401: não foi possível localizar o módulo \< modulename. Por favor, vá para Ferramentas\-\-\> Opções\-\-\> Ferramentas para Apache Cordova\-\-\> Ferramentas do Cordova\-\-\> Limpar Cordova Cache e tente compilar novamente.  
  
 Talvez seja necessário limpar o cache e reinstale o tac vs. Para obter mais informações, consulte [reinstalar vs tac](http://taco.visualstudio.com/en-us/docs/configure-vs-tools-apache-cordova#vstac).  
  
 Depois de limpar o cache, exclua a pasta plataformas no projeto. Em seguida, tente criar novamente.  
  
##  <a name="BLD10205"></a> MSBUILD: erro de compilação cordova BLD10205: Instale o destino Android  
 Se você vir esse erro, certifique\-se de que instalar as dependências necessárias para o dispositivo de destino selecionado usando o Gerenciador de SDK do Android \(Manager.exe SDK\).  
  
 Para obter mais informações sobre o nível necessário de API e outros componentes do SDK do Android, consulte [instalar as dependências manualmente](http://taco.visualstudio.com/en-us/docs/configure-vs-tools-apache-cordova#ThirdParty).  
  
 Você também deve verificar o local em que o Visual Studio usa para encontrar o SDK do Android. Para fazer isso, consulte [Substituir variáveis de ambiente do sistema](http://taco.visualstudio.com/en-us/docs/configure-vs-tools-apache-cordova#env-var).  
  
 Para obter mais informações sobre como instalar os componentes corretos para usar as ferramentas, consulte [Ferramentas de terceiros](http://taco.visualstudio.com/en-us/docs/install-vs-tools-apache-cordova#choose).  
  
##  <a name="BLDErr_Build_NodeMissing"></a> Não foi possível determinar o caminho BLDErr\_Build\_NodeMissing executável do Node. js.  
 Se o Node. js foi instalado em um local não padrão, o Visual Studio não pode localizá\-lo. Reinstale o Node. js para o local padrão. Para obter mais informações, consulte [StackOverflow últimos](http://stackoverflow.com/questions/32203992/vs2015-cordova-apps-blderr-build-nodemissing) e este artigo em [atualizar com segurança o Node. js](http://taco.visualstudio.com/en-us/docs/change-node-version/).  
  
##  <a name="BLDErr_Build_Win8Required"></a> BLDErr\_Build\_Win8Required  
 Windows 8.1 é necessário para Windows de destino em um aplicativo criado usando o Visual Studio Tools for Apache Cordova.