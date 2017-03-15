---
title: "Limita&#231;&#245;es na depura&#231;&#227;o de script | Microsoft Docs"
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
  - "mapeamento de pontos de interrupção ASPX, limitações"
  - "mapeamento de pontos de interrupção, limitações"
  - "depuração de script, limitações"
ms.assetid: 280eead5-693c-47af-967f-dfe9d23f84db
caps.latest.revision: 22
caps.handback.revision: 22
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Limita&#231;&#245;es na depura&#231;&#227;o de script
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

O [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] suporta a depuração de script do lado do cliente, sujeito às restrições neste tópico.  
  
## Limitações do mapeamento de pontos de interrupção com script do lado do cliente  
 O [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] permite definir um ponto de interrupção em um ASPX de servidor ou arquivo HTML que seja transformado em um arquivo do lado do cliente em tempo de execução.  O [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] mapeia o ponto de interrupção do arquivo do servidor a um ponto de interrupção correspondente no arquivo do lado do cliente, sujeito às seguintes restrições:  
  
-   Os pontos de interrupção devem ser definidos dentro dos blocos de `<script>`.  Não é possível mapear pontos de interrupção em scripts embutidos ou em blocos de `<% %>`.  
  
-   A URL do navegador da página deve conter o nome da página.  Por exemplo, http:\/\/microsoft.com\/default.apsx.  O mapeamento de pontos de interrupção não pode reconhecer um redirecionamento de um endereço, por exemplo, http:\/\/microsoft.com para a página padrão.  
  
-   O ponto de interrupção deve ser definido na página especificada na URL do navegador, não em um arquivo de controle ASPX \(ascx\), uma página mestre ou outro arquivo incluído por essa página.  Não é possível mapear pontos de interrupção definidos em páginas incluídas.  
  
-   Não é possível mapear pontos de interrupção definidos em blocos de `<script defer=true>`.  
  
-   Para os pontos de interrupção definidos em blocos de `<script id="">`, o mapeamento de pontos de interrupção ignora o atributo `id`.  
  
## Mapeamento de pontos de interrupção e linhas duplicadas  
 Para encontrar o local correspondente no script do servidor e do lado do cliente, o algoritmo de mapeamento de pontos de interrupção examina o código em cada linha.  O algoritmo supõe que cada linha é única.  Se duas ou mais linhas contêm o mesmo código e você definiu um ponto de interrupção em uma dessas linhas duplicadas, o algoritmo de mapeamento de pontos de interrupção pode selecionar a duplicata incorreta no arquivo do lado do cliente.  Para evitar isso, adicione um comentário à linha na qual você definiu o ponto de interrupção.  Por exemplo:  
  
```  
i++ ;  
i ++; // I added a comment, so this line is now unique  
i ++;  
```