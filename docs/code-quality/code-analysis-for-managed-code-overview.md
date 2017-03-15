---
title: "Vis&#227;o geral da an&#225;lise de c&#243;digo para c&#243;digo gerenciado | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.projectpropertypages.codeanalysis"
helpviewer_keywords: 
  - "análise de código, código gerenciado"
  - "código gerenciado, a análise de código"
ms.assetid: 12ec0dab-46a4-43d8-984a-440730ef37a9
caps.latest.revision: 35
caps.handback.revision: 35
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Vis&#227;o geral da an&#225;lise de c&#243;digo para c&#243;digo gerenciado
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

A análise de código para código gerenciado analisa os assemblies gerenciados e relata informações sobre assemblies, como violações das regras de programação e design definidas adiante nas diretrizes de design do Microsoft .NET Framework.  
  
 A ferramenta de análise representa as verificações que executa durante uma análise como mensagens de aviso.  As mensagens de aviso identificam os problemas relevantes de programação e design e, quando possível, fornecem as informações sobre como corrigir o problema.  
  
## Integração de IDE \(ambiente de desenvolvimento integrado\)  
 Como desenvolvedor, você pode executar a análise de código em seu projeto automaticamente ou você pode executá\-la manualmente.  
  
 Para executar análises de códigos sempre que você compilar um projeto, você seleciona **Ativar análise de código na compilação \(define a constante CODE\_ANALYSIS\)** na página Propriedades do projeto.  Para obter mais informações, consulte [Como habilitar e desabilitar análise de código automática](../Topic/How%20to:%20Enable%20and%20Disable%20Automatic%20Code%20Analysis%20for%20Managed%20Code.md).  
  
 Para executar manualmente a análise do código em um projeto, no menu de **Analisar** , clique em **Executar Análise do Código em** *ProjectName*.  Para obter mais informações, consulte [Como habilitar e desabilitar análise de código automática](../Topic/How%20to:%20Enable%20and%20Disable%20Automatic%20Code%20Analysis%20for%20Managed%20Code.md).  
  
## Conjuntos de regras  
 As regras de análise de código para código gerenciado são agrupadas em *conjuntos de regras*.  É possível usar um dos conjuntos padrão de regra da Microsoft ou criar uma regra personalizada definida para atender a uma necessidade específica.  Para obter mais informações, consulte [Usando conjuntos de regras para agrupar regras de análise de código](../code-quality/using-rule-sets-to-group-code-analysis-rules.md).  
  
## Exclusão de origem  
 Geralmente, é útil para indicar que um aviso não é aplicável.  Isso informa o desenvolvedor, e outras pessoas que podem examinar o código posteriormente, um aviso que foi investigado e então suprimido ou ignorado.  
  
 A exclusão de origem dos avisos é implementada com atributos personalizados.  Para suprimir um aviso, adicione o atributo `SuppressMessage` ao código\-fonte conforme mostrado no exemplo a seguir:  
  
 `[System.Diagnosis.CodeAnalysis.SuppressMessage("Microsoft.Design", "CA1039:ListsAreStrongTyped")]`  
  
 `Public class MyClass`  
  
 `{`  
  
 `// code`  
  
 `}`  
  
 Para obter mais informações, consulte [Suprimir avisos usando o atributo SuppressMessage](../code-quality/suppress-warnings-by-using-the-suppressmessage-attribute.md).  
  
## Executar a análise de código como parte de política de check\-in  
 Como uma organização, você pode desejar requerer que todos os check\-ins satisfaçam determinadas políticas.  Em particular, você deseja certificar\-se de seguir as seguintes políticas:  
  
-   Não houve nenhum erro na verificação do código.  
  
-   A análise de código foi executada como parte da compilação mais recente.  
  
 Você pode fazer isso especificando as políticas de check\-in.  Para obter mais informações, consulte [Melhorando a qualidade do código com políticas de check\-in do projeto da equipe](../code-quality/enhancing-code-quality-with-team-project-check-in-policies.md).  
  
## Integração da compilação da equipe  
 É possível usar os recursos integrados do sistema de compilação para executar a ferramenta de análise como parte do processo de compilação.  Para obter mais informações, consulte [Compilar o aplicativo](../Topic/Build%20the%20application.md).  
  
## Consulte também  
 [Usando conjuntos de regras para agrupar regras de análise de código](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)   
 [Como habilitar e desabilitar análise de código automática](../Topic/How%20to:%20Enable%20and%20Disable%20Automatic%20Code%20Analysis%20for%20Managed%20Code.md)