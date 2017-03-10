---
title: "Essas configura&#231;&#245;es de projeto est&#227;o desatualizadas: &lt; configuration &gt;. Voc&#234; gostaria de cri&#225;-los? | Microsoft Docs"
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
  - "VS.Message.BuildOutOfDateProjects"
ms.assetid: d0711f3b-3a2e-4247-afad-9e6468f9df96
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Essas configura&#231;&#245;es de projeto est&#227;o desatualizadas: &lt; configuration &gt;. Voc&#234; gostaria de cri&#225;-los?
Você está editando um projeto do Visual Studio ou tenha selecionado um projeto no Solution Explorer, e você optou por iniciar \(F5\) do projeto ou iniciar sem depuração \(CTRL \+ F5\). Um ou mais projetos permitem a depuração sem recriar, mesmo se o projeto tiver sido modificado desde a última compilação.  
  
 O ambiente de desenvolvimento integrado \(IDE\) pergunta se reconstruir projetos que permitem a depuração sem recriar ou não.  
  
### Para responder a esta mensagem  
  
-   Selecione um dos botões na parte inferior da mensagem. As opções são:  
  
|Termo|Definição|  
|-----------|---------------|  
|**Sim**|Você recriará projetos desatualizados. Isso significa que:<br /><br /> -   Se o projeto ainda não foi criado, o projeto é criado.<br />-   Se o projeto tiver sido modificado desde a última compilação, o projeto será reconstruído.<br />-   O projeto é depurado ou iniciado sem depuração.|  
|**Não**|Você recriará somente os projetos desatualizados que devem ser recriados antes de depurar. Isso significa que:<br /><br /> -   Se o projeto permitir depuração sem recompilar \(por exemplo, um projeto de aplicativo do MFC do Visual C\+\+\), o projeto não será recriado.<br />-   Se o projeto deve ser recriado antes de depuração \(por exemplo, um projeto do Visual Basic\), o projeto será reconstruído.<br />-   O projeto é depurado ou iniciar sem depuração.|  
|**Cancelar**|A operação atual está parada. Nenhum projeto é compilado, iniciado ou depurado.|  
  
## Consulte também  
 [Caixa de diálogo Gerenciador de configuração](http://msdn.microsoft.com/pt-br/fa182dca-282e-4ae5-bf37-e155344ca18b)   
 [How to: Create Solution and Project Build Configurations](../Topic/How%20to:%20Create%20Solution%20and%20Project%20Build%20Configurations.md)   
 [Como criar e remover dependências de projeto](../Topic/How%20to:%20Create%20and%20Remove%20Project%20Dependencies.md)   
 [Project Dependencies Dialog Box](http://msdn.microsoft.com/pt-br/d66e48c3-3722-40dd-99b4-53d93cac128e)   
 [Project Dependencies, Common Properties, Solution Property Pages Dialog Box](http://msdn.microsoft.com/pt-br/2ba638fc-719c-4a79-b166-3455a4374e31)   
 [Compilando aplicativos no Visual Studio](../ide/compiling-and-building-in-visual-studio.md)   
 [Noções sobre configurações de compilação](../ide/understanding-build-configurations.md)   
 [NIB: projetos como contêineres](http://msdn.microsoft.com/pt-br/87d40f63-f487-4767-8963-64beec27ba1b)   
 [Gerenciamento de PONTA: itens em projetos](http://msdn.microsoft.com/pt-br/762e606b-7f44-4b66-97a1-e30a703654a0)