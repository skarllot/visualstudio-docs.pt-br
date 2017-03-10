---
title: "Erro MSB3783 (MSBuild) | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSBuild.ResolveSDKReference.MaxPlatformVersionLessThanTargetPlatformVersion"
ms.assetid: 847fc96e-73d3-4aa5-927a-ef8cebc8d3f6
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Erro MSB3783 (MSBuild)
**Msb3783 \(\): Não foi possível resolver o SDK "{0}" porque ele tem o atributo MaxPlatformVersion com o valor "\\ {1 \\", que é menor que o valor de TargetPlatformVersion "\\ {2 \\".**  
  
 MSBuild gera este erro quando o projeto tem uma dependência que é incompatível com a plataforma que seu projeto está definido. Contar com dependências incompatíveis pode causar falhas ou comportamento inesperado de aplicativo em tempo de execução.  
  
### Para corrigir esse erro para referências de projeto  
  
1.  Destino de projetos do Visual Basic, c\#, C\+\+ e JavaScript [!INCLUDE[win81](../debugger/includes/win81_md.md)] repositório não fazem referências a projetos C\+\+ Windows Store destinados [!INCLUDE[win8](../debugger/includes/win8_md.md)] porque ele causará problemas de tempo de execução. Se qualquer projeto em seus destinos de aplicativo [!INCLUDE[win81](../debugger/includes/win81_md.md)] e seu aplicativo consiste em um projeto C \+ \+ Windows Store, você precisará executar as seguintes etapas:  
  
2.  Redirecionar todos os projetos em seu aplicativo para [!INCLUDE[win81](../debugger/includes/win81_md.md)]. Você pode fazer isso clicando em cada projeto em seu aplicativo, selecionando o **Redirecionar para o Windows 8.1** de comando e, em seguida, clicando em **OK** no **Revisar alterações de projeto e solução** caixa de diálogo.  
  
3.  Com o botão direito em cada Visual Basic, c\# e JavaScript projeto que depende de um projeto da Windows Store em C\+\+, escolha **Adicionar referência**, vá para o **Windows** guia, o **extensões** subguia, desmarque **v 11.0 do pacote de tempo de execução do Microsoft Visual C\+\+** e verifique **v 12.0 do pacote de tempo de execução do Microsoft Visual C\+\+**, em seguida, clique em **OK**.  
  
4.  Projetos do Visual Basic, c\# e JavaScript da Windows Store destinados [!INCLUDE[win81](../debugger/includes/win81_md.md)] pode consultar o Visual Basic e c\# da Windows Store projetos destinados [!INCLUDE[win8](../debugger/includes/win8_md.md)] desde que o [!INCLUDE[win8](../debugger/includes/win8_md.md)] repositório projetos não usem APIs que foram substituídos no [!INCLUDE[win81](../debugger/includes/win81_md.md)]. Consulte [aplicativos Migrando do Windows 8 para Windows 8.1 Preview](http://msdn.microsoft.com/library/windows/apps/dn263113.aspx) para determinar se o [!INCLUDE[win8](../debugger/includes/win8_md.md)] projetos de armazenamento continuará a se comportar conforme o esperado quando referenciado de um [!INCLUDE[win81](../debugger/includes/win81_md.md)] projeto.  
  
     [!INCLUDE[win8](../debugger/includes/win8_md.md)] Projetos de armazenamento não dependem de projetos da Windows Store ou binários destino [!INCLUDE[win81](../debugger/includes/win81_md.md)].  
  
### Para corrigir esse erro para referências de SDK de extensão  
  
1.  Projetos do Visual Basic, c\#, C\+\+ e JavaScript da Windows Store destinados [!INCLUDE[win81](../debugger/includes/win81_md.md)] não é possível referenciar os SDKs de extensão que dependem do pacote do Microsoft Visual C\+\+ Runtime v 11.0, pois isso causará problemas de tempo de execução. Você pode descobrir se um SDK de extensão depende v 11.0 do pacote de tempo de execução do Microsoft Visual C\+\+, criando um novo projeto do c\# da Windows Store, clicando duas vezes no projeto e escolha **Adicionar referência**, indo para o **Windows** guia, o **extensões** subguia, selecionando o SDK de extensão e ver se o painel direito no **Gerenciador de referências** lista **Microsoft.VCLibs, versão \= 11.0** como uma dependência.  
  
     Projetos do Visual Basic, c\# e JavaScript da Windows Store destinados [!INCLUDE[win81](../debugger/includes/win81_md.md)] pode fazer referência a SDKs de extensão que não dependem de pacote de tempo de execução do Microsoft Visual C\+\+ v 11.0, desde que estes SDKs de extensão não usa APIs que foram substituídos no [!INCLUDE[win81](../debugger/includes/win81_md.md)]. Verifique o site do fornecedor do SDK de extensão para determinar se ele pode ser referenciado por loja projetos destinados [!INCLUDE[win81](../debugger/includes/win81_md.md)].  
  
     Se você determinar que não há suporte para o SDK de extensão que está sendo referenciado por seu aplicativo, você precisa executar as seguintes etapas:  
  
2.  Observe o nome do projeto que está causando o erro. A plataforma de que seu projeto está definido é indicada entre parênteses ao lado do nome do projeto. Por exemplo, **MyProjectName \(Windows 8.1\)** significa que seu projeto **MyProjectName** está voltada para a versão da plataforma [!INCLUDE[win81](../debugger/includes/win81_md.md)].  
  
3.  Vá para o site do fornecedor que possui o SDK de extensão sem suporte e instale a versão do SDK de extensão com dependências que são compatíveis com a versão da plataforma do que seu projeto está definido.  
  
4.  Se o SDK de extensão instalado anteriormente tiver dependências em outros SDKs de extensão, vá para o site \(s\) de fornecedor \(es\) que possuem as dependências e instala as versões dessas dependências que são compatíveis com a versão da plataforma do que seu projeto está definido.  
  
    > [!NOTE]
    >  Se seu projeto está definido [!INCLUDE[win81](../debugger/includes/win81_md.md)] e o SDK de extensão instalada anteriormente tem uma dependência no pacote de tempo de execução do Microsoft Visual C\+\+, a versão do pacote Microsoft Visual C\+\+ Runtime que é compatível com o Windows 8.1 é v 12.0 e é instalada com [!INCLUDE[vs_dev12](../data-tools/includes/vs_dev12_md.md)].  
  
    > [!NOTE]
    >  Para descobrir se o SDK de extensão instalada anteriormente possui dependências em outros SDKs de extensão é reiniciar o Visual Studio, crie um novo projeto do c\# da Windows Store, clique com botão direito no projeto e escolha **Adicionar referência**, vá para o **Windows** tab, vá para o **extensões** subguia, selecione o SDK de extensão e examine o painel direito no **Gerenciador de referências**. Se ele possui dependências, eles serão listados lá.  
  
5.  Reinicie o Visual Studio e abra seu aplicativo.  
  
6.  Clique com botão direito no projeto que está causando o erro e escolha **Adicionar referência** no caso do Visual Basic, c\# ou projetos de JavaScript, ou **referências** no caso de projetos do C\+\+. Para projetos do C\+\+, em seguida, clique no **Adicionar nova referência** botão.  
  
7.  Clique o **Windows** guia e, em seguida, o **extensões** subguia. Desmarque as caixas de seleção ao lado de SDKs de extensão do antigo e marque as caixas de seleção ao lado de novos SDKs de extensão. Clique em **OK**.