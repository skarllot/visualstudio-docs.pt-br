---
title: "CA1062: validar argumentos de m&#233;todos p&#250;blicos | Microsoft Docs"
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
  - "CA1062"
  - "ValidateArgumentsOfPublicMethods"
  - "Validate arguments of public methods"
helpviewer_keywords: 
  - "CA1062"
  - "ValidateArgumentsOfPublicMethods"
ms.assetid: db1f69ca-68f7-477e-94f3-d135cc5dfcbc
caps.latest.revision: 27
caps.handback.revision: 27
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1062: validar argumentos de m&#233;todos p&#250;blicos
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ValidateArgumentsOfPublicMethods|  
|CheckId|CA1062|  
|Categoria|Microsoft.Design|  
|Alteração Significativa|Sem Quebra|  
  
## Causa  
 Um método externamente visível cancelará um de seus argumentos de referência sem verificar se esse argumento é `null` \(`Nothing` no Visual Basic\).  
  
## Descrição da Regra  
 Todos os argumentos de referência que são passados para os métodos externamente visíveis devem ser verificados em `null`.  Se apropriado, lance <xref:System.ArgumentNullException> quando o argumento é `null`.  
  
 Se um método pode ser chamado de um assembly desconhecido porque é declarado público ou protegido, você deve validar todos os parâmetros do método.  Se o método é criado para ser chamado somente pelos assemblies conhecidos, você deve fazer o método interno e aplique o atributo de <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> o assembly que contém o método.  
  
## Como Corrigir Violações  
 Para corrigir uma violação desta regra, validar cada argumento de referência em `null`.  
  
## Quando Suprimir Alertas  
 Você pode suprimir um aviso dessa regra se você tiver certeza de que o parâmetro cancelado esteve validado por outra chamada do método na função.  
  
## Exemplo  
 O exemplo a seguir mostra um método que viola a regra e um método que satisfaça a regra.  
  
 [!code-cs[FxCop.Design.ValidateArguments#1](../code-quality/codesnippet/CSharp/ca1062-validate-arguments-of-public-methods_1.cs)]
 [!code-cs[FxCop.Design.ValidateArguments#1](../code-quality/codesnippet/CSharp/ca1062-validate-arguments-of-public-methods_1.cs)]
 [!code-vb[FxCop.Design.ValidateArguments#1](../code-quality/codesnippet/VisualBasic/ca1062-validate-arguments-of-public-methods_1.vb)]  
  
## Exemplo  
 Em [!INCLUDE[vsprvslong](../code-quality/includes/vsprvslong_md.md)], esta regra não detecta que os parâmetros estão sendo passados a outro método que faz a validação.  
  
 [!code-cs[FxCop.Design.ValidateArguments#2](../code-quality/codesnippet/CSharp/ca1062-validate-arguments-of-public-methods_2.cs)]
 [!code-cs[FxCop.Design.ValidateArguments#2](../code-quality/codesnippet/CSharp/ca1062-validate-arguments-of-public-methods_2.cs)]
 [!code-vb[FxCop.Design.ValidateArguments#2](../code-quality/codesnippet/VisualBasic/ca1062-validate-arguments-of-public-methods_2.vb)]  
  
## Exemplo  
 Copie os construtores que populam o campo ou as propriedades que são objetos de referência também podem violar a regra CA1062.  A violação ocorrer porque o objeto copiado transmitido ao construtor de cópia pode ser `null` \(`Nothing` no Visual Basic\).  Para resolver a violação, use compartilhado \(no Visual Basic\) um método estático para verificar se o objeto copiado não é nulo.  
  
 No exemplo da classe de `Person` , o objeto de `other` transmitido ao construtor de cópia de `Person` pode ser `null`.  
  
```  
  
public class Person  
{  
    public string Name { get; private set; }  
    public int Age { get; private set; }  
  
    public Person(string name, int age)  
    {  
        Name = name;  
        Age = age;  
    }  
  
    // Copy constructor CA1062 fires because other is dereferenced  
    // without being checked for null  
    public Person(Person other)  
        : this(other.Name, other.Age)  
    {  
    }  
}  
  
```  
  
## Exemplo  
 No exemplo revisado de `Person` , o objeto de `other` transmitido ao construtor de impressão é verificado principalmente para verificar se há um valor nulo no método de `PassThroughNonNull` .  
  
```  
public class Person  
{  
    public string Name { get; private set; }  
    public int Age { get; private set; }  
  
    public Person(string name, int age)  
    {  
        Name = name;  
        Age = age;  
    }  
  
    // Copy constructor  
    public Person(Person other)  
        : this(PassThroughNonNull(other).Name,   
          PassThroughNonNull(other).Age)  
    {   
    }  
  
    // Null check method  
    private static Person PassThroughNonNull(Person person)  
    {  
        if (person == null)  
            throw new ArgumentNullException("person");  
        return person;  
    }  
}  
  
```