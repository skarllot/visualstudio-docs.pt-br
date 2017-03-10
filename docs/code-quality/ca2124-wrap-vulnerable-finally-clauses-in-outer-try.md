---
title: "CA2124: encapsular cl&#225;usulas finalmente vulner&#225;veis em tentativa externa | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2124"
  - "WrapVulnerableFinallyClausesInOuterTry"
helpviewer_keywords: 
  - "CA2124"
  - "WrapVulnerableFinallyClausesInOuterTry"
ms.assetid: 82efd224-9e60-4b88-a0f5-dfabcc49a254
caps.latest.revision: 20
caps.handback.revision: 20
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2124: encapsular cl&#225;usulas finalmente vulner&#225;veis em tentativa externa
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|WrapVulnerableFinallyClausesInOuterTry|  
|CheckId|CA2124|  
|Categoria|Microsoft.Security|  
|Alteração Significativa|Sem Quebra|  
  
## Causa  
 Nas versões 1,0 e 1,1 de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], um público ou um método protegido contêm `try`\/`catch`\/bloco de`finally` .  O bloco de `finally` aparece para reiniciar o estado de segurança e não é incluído em um bloco de `finally` .  
  
## Descrição da Regra  
 Esta regra encontrar `try`\/blocos de`finally` no código que se destinam às versões 1,0 e 1,1 de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] que pode ser vulneráveis a filtros mal\-intencionados da exceção atual da pilha de chamadas.  Se as operações particulares como a representação ocorrem no bloco try, e uma exceção será gerada, o filtro pode executar antes que o bloco de `finally` .  Para o exemplo de representação, isso significa que o filtro executado como o usuário representado.  Os filtros são implementable atualmente apenas no Visual Basic.  
  
> [!WARNING]
>  **Observação** Nas versões 2,0 e posterior de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], o tempo de execução protege automaticamente `try`\/`catch`\/bloco de `finally` filtros mal\-intencionados de exceção, se a reinicialização ocorre diretamente dentro do método que contém o bloco de exceção.  
  
## Como Corrigir Violações  
 Colocar `try`desempacotado\/`finally` em um bloco CATCH da tentativa.  Consulte o segundo exemplo a seguir.  Isso força `finally` para executar antes de código de filtro.  
  
## Quando Suprimir Alertas  
 Não elimine um alerta desta regra.  
  
## Exemplo do pseudocódigo  
  
### Descrição  
 O pseudocódigo a seguir ilustra o padrão detectado por esta regra.  
  
### Código  
  
```  
try {  
   // Do some work.  
   Impersonator imp = new Impersonator("John Doe");  
   imp.AddToCreditCardBalance(100);  
}  
finally {  
   // Reset security state.  
   imp.Revert();  
}  
```  
  
## Exemplo  
 O pseudocódigo a seguir mostra o padrão que você pode usar para proteger seu código e para satisfazer essa regra.  
  
```  
try {  
     try {  
        // Do some work.  
     }  
     finally {  
        // Reset security state.  
     }  
}  
catch()  
{  
    throw;  
}  
```