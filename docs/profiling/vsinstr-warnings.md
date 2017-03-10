---
title: "Avisos de VSInstr | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "implementação, ferramenta VSInstr"
  - "ferramentas de desempenho, ferramenta VSInstr"
  - "ferramenta VSInstr"
  - "avisos"
  - "avisos, ferramenta VSInstr"
ms.assetid: 47512bc9-a8e9-4628-883a-d9888edab786
caps.latest.revision: 20
caps.handback.revision: 20
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Avisos de VSInstr
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

A tabela a seguir lista os avisos emitidos pela ferramenta de VSInstr.exe.  Você pode usar a opção de NOWARN junto com os números de aviso para suprimir o aviso aparecessem.  
  
|Número de aviso|Descrição|  
|---------------------|---------------|  
|**VSP2000**|Erro interno.  Não é possível obter o nome de arquivo do módulo para esse executável.|  
|**VSP2001**|\<o nome do assembly\> é um assembly altamente nomeada.  Deve ser assinada novamente antes que possa ser executado.<br /><br /> Esse aviso ocorre quando um assembly assinado é provido.  Você pode usar a ferramenta de sn.exe para renunciar binário ou desativar temporariamente o requisito de nome forte.  Para obter mais informações, consulte [Sn.exe \(Ferramenta de Nome Forte\)](../Topic/Sn.exe%20\(Strong%20Name%20Tool\).md).|  
|**VSP2002**|Não foi possível localizar o funcname \<da função\> no nome \<do arquivo\><br /><br /> Esse aviso ocorrerá se uma função não poderá ser localizada no arquivo especificado.|  
|**VSP2003**|Não foi possível encontrar nenhum saltos cruzadas ao funcname \<da\> função no \<nome do arquivo\>.<br /><br /> Esse aviso ocorrerá se VSInstr não pode anular saltos cruzadas.  Os saltos de dados são usados para a otimização de código.|  
|**VSP2004**|O funcname \<da função\> foi excluído usando a opção de linha de comando de EXCLUSÃO mas necessário porque contém um salto cruzada.<br /><br /> Esse aviso ocorrerá se a função foi excluída usando a opção de EXCLUSÃO, mas é necessário durante o processo de instrumentação.  O profiler inclui automaticamente a função necessário.|  
|**VSP2005**|Texto interno do \<erro de WMI\><br /><br /> Esse aviso é emitido se a instrumentação não pode ser executada.  Revise o texto de erro para determinar se o pode ser corrigido.|  
|**VSP2006**|Não foi possível localizar o PDB para \<o nome\><br /><br /> Esse aviso ocorrerá se o arquivo PDB não existe no caminho de pesquisa ou não corresponde ao binário.|  
|**VSP2007**|\<o nome\> de arquivo não contém nenhum código instrumentable.<br /><br /> Esse aviso é emitido se todas as funções do arquivo binário que foram excluídas ou se o arquivo especificado contém apenas os recursos.|  
|**VSP2008**|Não é possível obter atributos de segurança \<do nome\>.  Código \<do código de erro\><br /><br /> Esse aviso ocorrerá se o usuário não tem permissão de READ\_DAC.  Durante o processo de instrumentação profiler, o tenta preservar DACL original para binário.  Como binário original é substituído por um novo binário, DACL de binário original deve ser copiado e aplicado ao novo binário.  Isso pode falhar se o usuário tem acesso de READ\_DAC em binário original.|  
|**VSP2009**|Não é possível definir atributos de segurança \<no nome\>.  Número \<de erro do código de erro\><br /><br /> Esse aviso ocorrerá se o usuário não tem permissão de WRITE\_DAC.  Durante o processo de instrumentação profiler, o tenta preservar DACL original para binário.  Como binário original é substituído por um novo binário, DACL de binário original deve ser copiado e aplicado ao novo binário.  Isso pode falhar se o usuário tem acesso de WRITE\_DAC no novo binário.|  
|**VSP2010**|Nenhuma função for selecionada especificamente para a instrumentação \- devido às opções de INCLUDE\/\-EXCLUDE|  
|**VSP2011**|Inclua\/excluir o nome \<de funcspec\> não corresponde a nenhuma função|  
|**VSP2012**|A imagem não contém nenhum código que pode ser provido para a cobertura de código.<br /><br /> O profiler não provê o seguinte tipo de código:<br /><br /> -   Funções estáticas de CRT<br />-   Métodos gerenciados atribuídos com NonUserCodeAttribute<br />-   Métodos gerenciados atribuídos com DebuggerHiddenAttribute<br />-   Blocos de MASM<br /><br /> Esse aviso será gerado se, depois dessa filtragem, não há nenhum código esquerda.|  
|**VSP2013**|A esta imagem requer ser executado como um processo de 32 bits.  Os sinalizadores de cabeçalho de CLR foram atualizados para refletir isso.<br /><br /> O profiler altera o binário de modo que os sistemas operacionais de 64 bits possam abrir o processo de 32 bits emulador o WOW64.  Para bibliotecas \(DLL\) isso pode falhar se são carregados em um processo de 64 bits existente.  Esse aviso notifica o usuário de dependência.|  
|**VSP2014**|A imagem instrumentada resultante parece ser inválida, e não pode executar.<br /><br /> Essa mensagem ocorre quando o assembly provido final tem um cabeçalho inválido de PE.|  
  
## Consulte também  
 [VSInstr](../profiling/vsinstr.md)