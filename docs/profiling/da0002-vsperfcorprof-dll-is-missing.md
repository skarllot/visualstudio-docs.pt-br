---
title: "DA0002: VSPerfCorProf.dll n&#227;o foi encontrado | Microsoft Docs"
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
  - "vs.performance.DA0002"
  - "vs.performance.2"
  - "vs.performance.rules.DAVsPerfCorProfMissing"
  - "vs.performance.rules.DA0002"
ms.assetid: 76e614b3-ad7e-4b92-b7be-88dc1329be1d
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# DA0002: VSPerfCorProf.dll n&#227;o foi encontrado
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|Identificação da Regra|DA0002|  
|Categoria|Uso de Ferramentas de Criação de Perfil|  
|Analisando métodos|Analisar usando ferramentas de linha de comando de VSPerfCmd e de VSPerfASPNETCmd|  
|Message \(Mensagem\)|Parece que o arquivo esteve coletado sem corretamente definir as variáveis de ambiente com VSPerfCLREnv.cmd.  Os símbolos de binários não gerenciados podem resolver.|  
|Tipo de regra|Informações|  
  
## Causa  
 O profiler não pôde localizar VSPerfCorProf.dll durante analisar executado.  Esse aviso ocorre quando as ferramentas de linha de comando para a coleção de dados do criador de perfil são usadas sem usar a ferramenta de VSPerfCLREnv.cmd para inicializar as variáveis de ambiente necessário.  O aviso também pode ser disparado se outro profiler estiver em execução quando o início de Ferramentas de Criação de Perfil.  
  
## Descrição da Regra  
 As variáveis de ambiente específicos devem ser definidos antes de analisar executado para que o profiler resolve os símbolos em binários do.NET Framework.  Esse aviso sugeridas que a ferramenta de VSPerfCLREnv.cmd não foi executado antes que os dados de perfil foram coletados.  Os símbolos de binários não gerenciados podem resolver.  Para obter mais informações sobre como usar as Ferramentas de Criação de Perfil da linha de comando, consulte [Criando perfil a partir da linha de comando](../profiling/using-the-profiling-tools-from-the-command-line.md)  
  
## Como Corrigir Violações  
 Quando você estiver analisando aplicativos gerenciados usando as ferramentas de linha de comando em [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Ferramentas de Criação de Perfil, execute a ferramenta de linha de comando [VSPerfCLREnv](../profiling/vsperfclrenv.md) antes de começar a coletar dados.