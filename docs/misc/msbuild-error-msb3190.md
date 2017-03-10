---
title: "Erro MSB3190 (MSBuild) | Microsoft Docs"
ms.custom: ""
ms.date: "11/23/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "GenerateManifest.InvalidRequestedExecutionLevel"
helpviewer_keywords: 
  - "MSB3190"
ms.assetid: 45b45688-9345-45db-adc8-3e200f1c17eb
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Erro MSB3190 (MSBuild)
**MSB3190: ClickOnce não oferece suporte para o nível de execução solicitado '\< nível \>'.**  
  
 Esse erro é gerado em computadores que executam o Windows Vista quando o manifesto inserido de controle de conta de usuário \(UAC\) do aplicativo especifica que um aplicativo ClickOnce executado com credenciais administrativas. ClickOnce e liberar o registro COM exigem um manifesto externo que especifica que o aplicativo é executado como o usuário atual.  
  
 ClickOnce não aceita os níveis de execução `requireAdministrator` ou `highestAvailable`. Se você especificar um desses níveis, você receberá esse erro. O ClickOnce exige `asInvoker`, mas também aceitarão nenhum `<requestedExecutionLevel>` nó, que especifica a virtualização de arquivo\/registro \(que significa que nenhum manifesto é gerado; isso é feito para compatibilidade com versões anteriores\).  
  
> [!NOTE]
>  Seu computador pode mostrar diferentes nomes ou locais para alguns dos elementos de interface do usuário do Visual Studio nas instruções a seguir. A edição do Visual Studio que você possui e as configurações que você usa determinam esses elementos. Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/pt-br/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### Para corrigir este erro  
  
-   Gerar um manifesto UAC externo \(App\) que especifica que o aplicativo é executado como o usuário atual \(`asInvoker`\).  
  
     Em projetos do Visual c\#, vá para o **aplicativo** página do Designer de projeto e clique em **Properties\\app.manifest** no **manifesto** lista. Para obter mais informações, consulte [Página Aplicativo, Designer de Projeto \(C\#\)](../ide/reference/application-page-project-designer-csharp.md).  
  
     Em projetos do Visual Basic, vá para o **aplicativo** página do Designer de projeto e clique o **Exibir configurações de UAC** botão. Isso abre o App para edição. Edite a seguinte marca no manifesto como segue:  
  
    ```  
    <requestedExecutionLevel level="asInvoker" />  
    ```  
  
     Para obter mais informações, consulte [Página de Aplicativo, Designer de Projeto \(Visual Basic\)](../ide/reference/application-page-project-designer-visual-basic.md).  
  
-   Para obter mais informações sobre como gerar um manifesto UAC e especificar o nível de execução, consulte [Implantação do ClickOnce no Windows Vista](../deployment/clickonce-deployment-on-windows-vista.md).  
  
## Consulte também  
 [Página Aplicativo, Designer de Projeto \(C\#\)](../ide/reference/application-page-project-designer-csharp.md)   
 [Página de Aplicativo, Designer de Projeto \(Visual Basic\)](../ide/reference/application-page-project-designer-visual-basic.md)   
 [Implantação do ClickOnce no Windows Vista](../deployment/clickonce-deployment-on-windows-vista.md)