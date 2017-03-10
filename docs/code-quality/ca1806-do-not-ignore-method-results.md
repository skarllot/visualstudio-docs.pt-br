---
title: "CA1806: n&#227;o ignore resultados do m&#233;todo | Microsoft Docs"
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
  - "CA1806"
  - "DoNotIgnoreMethodResults"
helpviewer_keywords: 
  - "CA1806"
  - "DoNotIgnoreMethodResults"
ms.assetid: fd805687-0817-481e-804e-b62cfb3b1076
caps.latest.revision: 27
caps.handback.revision: 27
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1806: n&#227;o ignore resultados do m&#233;todo
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotIgnoreMethodResults|  
|CheckId|CA1806|  
|Categoria|Microsoft.Usage|  
|Alteração Significativa|Sem Quebra|  
  
## Causa  
 Há várias razões possíveis para esse aviso:  
  
-   Um novo objeto é criado mas nunca usado.  
  
-   Um método que cria e retorna uma nova cadeia de caracteres é chamado e a nova cadeia de caracteres nunca seja usada.  
  
-   Um método de COM ou de P\/Invoke que retorna um HRESULT ou um código de erro que nunca sejam usados.  Descrição da Regra  
  
 A criação desnecessária do objeto e a coleta de lixo de objeto associado não usado degradam o desempenho.  
  
 As cadeias de caracteres são imutáveis e métodos como retornos de String.ToUpper uma nova instância de uma cadeia de caracteres em vez de modificar a instância de cadeia de caracteres no método de chamada.  
  
 Ignorar HRESULT ou código de erro pode resultar em um comportamento inesperado em condições de erro ou às condições de baixo recurso.  
  
## Como Corrigir Violações  
 Se o método Para criar uma nova instância do objeto de B que nunca será usado, passe a instância como um argumento para outro método ou atribuir a instância a uma variável.  Se a criação do objeto é desnecessária, \- ou removê\-lo.  
  
 Se o método A seguir chama o método B, mas não usa a nova instância da cadeia de caracteres que o método B retorna.  Passar a instância como um argumento para outro método, atribua a instância a uma variável.  Ou remover a chamada se for desnecessário.  
  
 \- ou \-  
  
 Se o método A seguir chama o método B, mas não usa o HRESULT ou o código de erro que o método retorna.  Use o resultado em uma instrução condicional, atribuir o resultado a uma variável, ou passá\-lo como um argumento para outro método.  
  
## Quando Suprimir Alertas  
 Não suprima um aviso desta regra a menos que o ato da criação do objeto para servir qualquer propósito.  
  
## Exemplo  
 O exemplo a seguir mostra uma classe que ignore o resultado de chamar String.Trim.  
  
 [!CODE [FxCop.Usage.DoNotIgnoreMethodResults#1](FxCop.Usage.DoNotIgnoreMethodResults#1)]  
  
## Exemplo  
 O exemplo a seguir corrige a violação anterior ao atribuir o resultado de String.Trim de volta para a variável que foi chamado.  
  
 [!CODE [FxCop.Usage.DoNotIgnoreMethodResults2#1](FxCop.Usage.DoNotIgnoreMethodResults2#1)]  
  
## Exemplo  
 O exemplo a seguir mostra um método que não use um objeto que cria.  
  
> [!NOTE]
>  Essa violação não pode ser reproduzida no Visual Basic.  
  
 [!code-cs[FxCop.Usage.DoNotIgnoreMethodResults3#1](../code-quality/codesnippet/CSharp/ca1806-do-not-ignore-method-results_1.cs)]
 [!code-vb[FxCop.Usage.DoNotIgnoreMethodResults3#1](../code-quality/codesnippet/VisualBasic/ca1806-do-not-ignore-method-results_1.vb)]
 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults3#1](../code-quality/codesnippet/CPP/ca1806-do-not-ignore-method-results_1.cpp)]  
  
## Exemplo  
 O exemplo a seguir corrige a violação anterior removendo desnecessária a criação de um objeto.  
  
 [!code-cs[FxCop.Usage.DoNotIgnoreMethodResults4#1](../code-quality/codesnippet/CSharp/ca1806-do-not-ignore-method-results_2.cs)]
 [!code-vb[FxCop.Usage.DoNotIgnoreMethodResults4#1](../code-quality/codesnippet/VisualBasic/ca1806-do-not-ignore-method-results_2.vb)]
 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults4#1](../code-quality/codesnippet/CPP/ca1806-do-not-ignore-method-results_2.cpp)]  
  
## Exemplo  
 O exemplo a seguir mostra um método que ignore o código de erro que o método nativo GetShortPathName retorna.  
  
 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults5#1](../code-quality/codesnippet/CPP/ca1806-do-not-ignore-method-results_3.cpp)]
 [!code-cs[FxCop.Usage.DoNotIgnoreMethodResults5#1](../code-quality/codesnippet/CSharp/ca1806-do-not-ignore-method-results_3.cs)]  
  
## Exemplo  
 O exemplo a seguir corrige a violação anterior verificando o código de erro e gerando uma exceção quando houver falha na chamada.  
  
 [!code-cs[FxCop.Usage.DoNotIgnoreMethodResults6#1](../code-quality/codesnippet/CSharp/ca1806-do-not-ignore-method-results_4.cs)]
 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults6#1](../code-quality/codesnippet/CPP/ca1806-do-not-ignore-method-results_4.cpp)]