---
title: "CA2202: n&#227;o descartar objetos v&#225;rias vezes | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2202"
  - "Do not dispose objects multiple times"
  - "DoNotDisposeObjectsMultipleTimes"
helpviewer_keywords: 
  - "CA2202"
ms.assetid: fa85349a-cf1e-42c8-a86b-eacae1f8bd96
caps.latest.revision: 20
caps.handback.revision: 20
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2202: n&#227;o descartar objetos v&#225;rias vezes
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotDisposeObjectsMultipleTimes|  
|CheckId|CA2202|  
|Categoria|Microsoft.Usage|  
|Alteração Significativa|Sem Quebra|  
  
## Causa  
 Uma implementação do método contém os caminhos de código que poderiam causar várias chamadas para <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> ou a um equivalente de disposição, como um \(\) próximo método em alguns tipos, no mesmo objeto.  
  
## Descrição da Regra  
 Um método corretamente implementado de <xref:System.IDisposable.Dispose%2A> pode ser chamado várias vezes sem gerar uma exceção.  No entanto, isso não é garantido e para evitar gerar <xref:System.ObjectDisposedException?displayProperty=fullName> que você não deve chamar <xref:System.IDisposable.Dispose%2A> mais de uma vez em um objeto.  
  
## Regras Relacionadas  
 [CA2000: descartar objetos antes de perder o escopo](../code-quality/ca2000-dispose-objects-before-losing-scope.md)  
  
## Como Corrigir Violações  
 Para corrigir uma violação desta regra, altere a implementação de modo que independentemente do caminho de código, <xref:System.IDisposable.Dispose%2A> é chamado apenas uma vez para o objeto.  
  
## Quando Suprimir Alertas  
 Não elimine um alerta desta regra.  Se <xref:System.IDisposable.Dispose%2A> para o objeto é conhecido para ser acessível com segurança várias vezes, a implementação pode ser alterada no futuro.  
  
## Exemplo  
 As instruções aninhadas de `using` \(`Using` no Visual Basic\) podem causar violações de aviso CA2202.  Se o recurso IDisposable da instrução aninhada interna de `using` contém o recurso da instrução exterior de `using` , o método de `Dispose` de recursos aninhado libera o recurso independente.  Quando essa situação acontece, o método de `Dispose` da instrução exterior de `using` tentar descartar seu recurso pela segunda vez.  
  
 No exemplo a seguir, um objeto de <xref:System.IO.Stream> criado em uma instrução de utilização exterior é liberado no final da instrução de utilização interna no método dispose do objeto de <xref:System.IO.StreamWriter> que contém o objeto de `stream` .  No final da instrução exterior de `using` , o objeto de `stream` é liberado em uma segunda vez.  A segunda versão é uma violação de CA2202.  
  
```  
using (Stream stream = new FileStream("file.txt", FileMode.OpenOrCreate))  
{  
    using (StreamWriter writer = new StreamWriter(stream))  
    {  
        // Use the writer object...  
    }  
}  
  
```  
  
## Exemplo  
 Para resolver esse problema, use um bloco de `try`\/`finally` em vez da instrução exterior de `using` .  No bloco de `finally` , verifique se o recurso de `stream` não for nulo.  
  
```  
Stream stream = null;  
try  
{  
    stream = new FileStream("file.txt", FileMode.OpenOrCreate);  
    using (StreamWriter writer = new StreamWriter(stream))  
    {  
        stream = null;  
        // Use the writer object...  
    }  
}  
finally  
{  
    if(stream != null)  
        stream.Dispose();  
}  
  
```  
  
## Consulte também  
 <xref:System.IDisposable?displayProperty=fullName>   
 [Padrão de descarte](../Topic/Dispose%20Pattern.md)