---
title: "CA1305: especificar IFormatProvider | Microsoft Docs"
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
  - "SpecifyIFormatProvider"
  - "CA1305"
helpviewer_keywords: 
  - "CA1305"
  - "SpecifyIFormatProvider"
ms.assetid: fb34ed9a-4eab-47cc-8eef-3068a4a1397e
caps.latest.revision: 22
caps.handback.revision: 22
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1305: especificar IFormatProvider
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|SpecifyIFormatProvider|  
|CheckId|CA1305|  
|Categoria|Microsoft.Globalization|  
|Alteração Significativa|Sem quebra|  
  
## Causa  
 Um método ou um construtor chamam um ou mais membros que têm as sobrecargas que aceitam um parâmetro de <xref:System.IFormatProvider?displayProperty=fullName> , e o método ou o construtor não chama a sobrecarga que usa o parâmetro de <xref:System.IFormatProvider> .  Esta regra ignora chamadas para os métodos de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] que são documentados como ignorar o parâmetro de <xref:System.IFormatProvider> e adicionalmente os seguintes métodos:  
  
-   <xref:System.Activator.CreateInstance%2A?displayProperty=fullName>  
  
-   <xref:System.Resources.ResourceManager.GetObject%2A?displayProperty=fullName>  
  
-   <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=fullName>  
  
## Descrição da Regra  
 Quando um objeto de <xref:System.Globalization.CultureInfo?displayProperty=fullName> ou de <xref:System.IFormatProvider> não for fornecido, o valor padrão que é fornecido pelo membro sobrecarregado não pode ter o efeito desejado em todas as localidades.  Além disso, os membros de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] eles escolhem a cultura padrão e a formatação com base nas suposições que podem não estar corretas para seu código.  Para garantir que o código funciona conforme o esperado para seus cenários, você deve fornecer informações específicas à cultura específica de acordo com as seguintes diretrizes:  
  
-   Se o valor será exibido ao usuário, use a cultura atual.  Consulte <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName>.  
  
-   Se o valor será armazenado e acessado pelo software \(persistente em um arquivo ou em uma base de dados\), use a cultura invariável.  Consulte <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>.  
  
-   Se você não souber o destino do valor, tem o consumidor ou o provedor de dados especificar a cultura.  
  
 Observe que <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> é usado para recuperar apenas recursos encontrados usando uma instância da classe de <xref:System.Resources.ResourceManager?displayProperty=fullName> .  
  
 Se o comportamento padrão do membro sobrecarregado é apropriado para suas necessidades, é melhor chamar explicitamente a sobrecarga cultura específica para que seu código do seja documentando e mantido mais facilmente.  
  
## Como Corrigir Violações  
 Para corrigir uma violação desta regra, use a sobrecarga necessária <xref:System.Globalization.CultureInfo> ou <xref:System.IFormatProvider> e especifique o argumento de acordo com as diretrizes que foi listada anteriormente.  
  
## Quando Suprimir Alertas  
 É seguro suprimir um aviso desta regra quando você tiver certeza de que o provedor padrão de cultura\/formato é a escolha correta e onde a manutenibilidade de código não é uma prioridade importante de desenvolvimento.  
  
## Exemplo  
 No exemplo a seguir, `BadMethod` causa duas violações desta regra.  `GoodMethod` corrigir a primeira violação passando a cultura invariável a <xref:System.String.Compare%2A>, e corrigir a segunda violação passando a cultura atual a <xref:System.String.ToLower%2A> porque `string3` é exibido ao usuário.  
  
 [!code-cs[FxCop.Globalization.CultureInfo#1](../code-quality/codesnippet/CSharp/ca1305-specify-iformatprovider_1.cs)]  
  
## Exemplo  
 O exemplo a seguir mostra o efeito da cultura atual da opção <xref:System.IFormatProvider> que é selecionada pelo tipo de <xref:System.DateTime> .  
  
 [!code-cs[FxCop.Globalization.IFormatProvider#1](../code-quality/codesnippet/CSharp/ca1305-specify-iformatprovider_2.cs)]  
  
 O exemplo produz a seguinte saída.  
  
  **4\/6\/1900 12:15:12 PM**  
**06\/04\/1900 12:15:12**   
## Regras Relacionadas  
 [CA1304: especificar CultureInfo](../Topic/CA1304:%20Specify%20CultureInfo.md)  
  
## Consulte também  
 [NIB: Using the CultureInfo Class](http://msdn.microsoft.com/pt-br/d4329e34-64c3-4d1e-8c73-5b0ee626ba7a)