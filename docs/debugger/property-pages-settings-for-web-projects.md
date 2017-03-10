---
title: "Configura&#231;&#245;es das p&#225;ginas de propriedade para projetos Web | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "depurar compilações, configurações de projeto"
  - "depurar configurações, Projetos da Web"
  - "depurando [Visual Studio], aplicativos da Web"
  - "depurando aplicativos da Web, configurações de projeto"
  - "configurações do projeto [Visual Studio], depurar configurações"
  - "projetos [Visual Studio], depurar configurações"
ms.assetid: 8ec5160a-6408-4f47-8d41-f0e20e79a3b9
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Configura&#231;&#245;es das p&#225;ginas de propriedade para projetos Web
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Você pode alterar as configurações de propriedade para uma configuração de depuração do site na caixa de diálogo **Páginas de Propriedades**, conforme discutido em [Configurações de depuração e lançamento](../debugger/how-to-set-debug-and-release-configurations.md).  As tabelas a seguir mostram onde localizar configurações relacionadas ao depurador na caixa de diálogo **Páginas de Propriedades**.  
  
### A pasta propriedades de configuração \(Opções de Inicialização\)  
  
|**Configuração**|**Descrição**|  
|----------------------|-------------------|  
|**Iniciar ação**|Cabeçalho que agrupa as opções relacionadas à inicialização do aplicativo.|  
|**Usar página atual**|Especifica a página atual como o ponto de inicialização para depuração.|  
|**Página específica:**|Especifica a página da Web onde você deseja iniciar a depuração.|  
|**Iniciar programa externo:**|Especifica o comando para iniciar o programa que você deseja depurar.|  
|**Argumentos de linha de comando:**|Especifica argumentos para o comando especificado acima.|  
|**Diretório de trabalho:**|Especifica o diretório de trabalho do programa que está sendo depurado.  No [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)], o diretório de trabalho é o diretório a partir do qual o aplicativo é iniciado de \\bin\\debug por padrão.|  
|**URL inicial**|Especifica o local do aplicativo Web que você deseja depurar.|  
|**Não abra a página.  Aguardar solicitação de um aplicativo externo**|Diz para aguardar solicitação de um aplicativo externo.  Essa opção não inicia o Internet Explorer ou outro aplicativo.  Ela apenas prepara para depuração quando for chamada por um aplicativo.|  
|**Servidor**|Cabeçalho que agrupa as opções relacionadas ao servidor a ser usado.|  
|**Usar servidor Web padrão**|Informa para usar o servidor Web padrão.|  
|**Usar servidor personalizado**|Permite inserir uma URL base para usar como o servidor.|  
|**Depuradores**|Cabeçalho que agrupa as opções relacionadas ao tipo de depuração a ser feito.|  
|**Depuração de ASP.NET**|Permite a depuração das páginas do servidor escritas para a plataforma de desenvolvimento do [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].  Você deve especificar uma URL em **URL Inicial**.|  
|**Depuração de código nativo**|Permite depurar chamadas para código Win32 nativo \(não gerenciado\) a partir do seu aplicativo gerenciado.|  
|**Depuração SQL Server**|Permite depuração de objetos de banco de dados do SQL Server.|  
|**Depuração do Silverlight**|Permite depuração de componentes do Silverlight.|  
  
## Consulte também  
 [Configurações de depuração e preparação](../debugger/debugger-settings-and-preparation.md)