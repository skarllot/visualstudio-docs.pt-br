---
title: "Como definir o local de um arquivo de log personalizado para erros de implanta&#231;&#227;o do ClickOnce | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "implantação ClickOnce, log de erros"
  - "implantação ClickOnce, solucionando problemas"
  - "solucionando problemas de implantações ClickOnce"
ms.assetid: 77424414-7f0e-4b99-94bb-ea130de92d09
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como definir o local de um arquivo de log personalizado para erros de implanta&#231;&#227;o do ClickOnce
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]mantém os arquivos de log de ativação para todas as implantações.  Esses logs documentam todos os erros relacionados à instalação e inicializando um [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] implantação.  Por padrão, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] cria um arquivo de log para cada ativação de implantação.  Ele armazena esses arquivos de log na pasta Temporary Internet Files.  O arquivo de log para uma implantação será exibido para o usuário quando ocorrer uma falha de ativação e o usuário clica em  **detalhes** na caixa de diálogo de erro resultante.  
  
 Você pode alterar esse comportamento para um cliente específico usando o Editor do registro \(**regedit.exe**\) para definir um caminho de arquivo de log personalizado.  Nesse caso, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] registra êxitos de ativação e falhas de todas as implantações em um único arquivo.  
  
> [!CAUTION]
>  Se você usar o Editor do Registro incorretamente, você pode causar problemas sérios que podem exigir a reinstalação do sistema operacional.  Use o Editor do Registro e assuma os riscos.  
  
> [!NOTE]
>  Você precisará truncar ou excluir o arquivo de log ocasionalmente para impedir que ele fique muito grande.  
  
 O procedimento a seguir descreve como definir um local de arquivo de log personalizado para um único cliente.  
  
### Para definir um local de arquivo de log personalizado  
  
1.  Abra **Regedit.exe**.  
  
2.  Navegue até o nó  `HKCU\Software\Classes\Software\Microsoft\Windows\CurrentVersion\Deployment`.  
  
3.  Defina o valor de seqüência de caracteres  `LogFilePath` para o caminho completo e nome de arquivo do seu local preferido de log personalizado.  
  
     Esse local deve estar em um diretório ao qual o usuário tem acesso de gravação.  Por exemplo, no Windows Vista, crie a seguinte estrutura de pasta e defina  `LogFilePath` para C:\\Users\\ \<username\> \\Documents\\Logs\\ClickOnce\\installation.log.  
  
## Consulte também  
 [Solução de problemas de implantações do ClickOnce](../deployment/troubleshooting-clickonce-deployments.md)