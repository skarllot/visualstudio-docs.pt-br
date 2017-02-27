---
title: "Como analisar código JavaScript em páginas da Web | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- JavaScript performance profiling
- Profiling Tools,JavaScript
- web site performance profiling
ms.assetid: 37d02aad-ca4d-4eb0-bf66-ca3ecef31fbe
caps.latest.revision: 27
author: mikejo5000
ms.author: mikejo
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: 6c394dfcf1c0df0cb7d006592b3dc386da328876
ms.openlocfilehash: 40c90059930b16e081d7d46a24c1b93bdc34f98a

---
# <a name="how-to-profile-javascript-code-in-web-pages"></a>Como analisar código JavaScript em páginas da Web
As Ferramentas de Criação de Perfil do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] podem coletar dados de desempenho para o código JavaScript que é executado em um aplicativo Web do [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], em uma página da Web arbitrária ou em um aplicativo JavaScript usando o método de criação de perfil de instrumentação.  
  
 **Requisitos**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
-   Internet Explorer 8 ou posterior.  
  
> [!WARNING]
>  Para analisar JavaScript em aplicativos da Windows Store, consulte [Memória do JavaScript](../profiling/javascript-memory.md) 
  
 Você pode usar o Assistente de Criação de Perfil para criar uma sessão de desempenho. Especifique o método de instrumentação e, em seguida, especifique a opção de criação de perfil JavaScript na página de Instrumentação da caixa de diálogo de propriedades da sessão de desempenho.  
  
 Ao especificar criação de perfil JavaScript, o código JavaScript que é executado no navegador e o código do [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] que é executado no servidor serão analisados.  
  
-   Para um aplicativo Web do [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], o código JavaScript que é executado no navegador e o código do [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] que é executado no servidor serão analisados.  
  
-   Para uma página da Web arbitrária, o código JavaScript que é executado no navegador é analisado.  
  
### <a name="to-profile-javascript-in-an-aspnet-web-application-project"></a>Para analisar JavaScript em um projeto de aplicativo Web ASP .NET  
  
1.  No [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], abra o projeto Web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].  
  
2.  No menu **Analisar**, clique em **Iniciar o Assistente de Desempenho**.  
  
3.  Na primeira página do Assistente de Desempenho, especifique o método de criação de perfil **Instrumentação** e, em seguida, clique em **Avançar**.  
  
4.  Na segunda página do assistente, verifique se o projeto atual está selecionado na lista de destinos e, em seguida, clique em **Avançar.**  
  
5.  Na terceira página do assistente, selecione a caixa de seleção **Perfil JavaScript** e, em seguida, clique em **Avançar**.  
  
6.  Na quarta página do assistente, clique em **Concluir** para iniciar o aplicativo Web no navegador.  
  
7.  Execute a funcionalidade que você deseja analisar.  
  
8.  Para encerrar a sessão de criação de perfil, feche o navegador.  
  
### <a name="to-profile-javascript-in-individual-web-pages-or-a-javascript-applications"></a>Para analisar JavaScript em páginas da Web individuais ou em aplicativos JavaScript  
  
1.  Abra [!INCLUDE[vsPreShort](../code-quality/includes/vspreshort_md.md)].  
  
2.  No menu **Analisar**, clique em **Iniciar o Assistente de Desempenho**.  
  
3.  Na primeira página do Assistente de Desempenho, especifique o método de criação de perfil **Instrumentação** e, em seguida, clique em **Avançar**.  
  
4.  Na segunda página do assistente, clique em um aplicativo ASP.NET ou JavaScript e, em seguida, clique em **Avançar.**  
  
5.  Na terceira página do assistente:  
  
    1.  Digite a URL da página na caixa **Qual URL ou caminho executará seu aplicativo**.  
  
    2.  Selecione a caixa de seleção **Perfil JavaScript** e, em seguida, clique em **Avançar**.  
  
6.  Na quarta página do assistente, clique em **Concluir** para iniciar a página da Web no navegador.  
  
7.  Execute a funcionalidade que você deseja analisar.  
  
8.  Para encerrar a sessão de criação de perfil, feche o navegador.


<!--HONumber=Feb17_HO4-->


