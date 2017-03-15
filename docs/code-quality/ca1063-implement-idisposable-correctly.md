---
title: "CA1063: implementar IDisposable corretamente | Microsoft Docs"
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
  - "ImplementIDisposableCorrectly"
  - "CA1063"
helpviewer_keywords: 
  - "CA1063"
  - "ImplementIDisposableCorrectly"
ms.assetid: 12afb1ea-3a17-4a3f-a1f0-fcdb853e2359
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1063: implementar IDisposable corretamente
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ImplementIDisposableCorrectly|  
|CheckId|CA1063|  
|Categoria|Microsoft.Design|  
|Alteração Significativa|Sem quebra|  
  
## Causa  
 `IDisposable` não é implementado corretamente.  Algumas razões para esse problema são listadas aqui:  
  
-   IDisposable novamente é implementado na classe.  
  
-   Encerre novamente é substituída.  
  
-   Dispose é substituída.  
  
-   Dispose\(\) não é público, selado, ou nomeada descartado.  
  
-   Bool descartado \(\) não é protegido, virtual, nem unsealed.  
  
-   Em tipos não lacrados, Dispose\(\) deve chamar descartado \(retifique\).  
  
-   Para tipos não lacrados, a implementação de finalizacão não chama ou para descartar \(bool\) ou o finalizador da classe dos casos.  
  
 A violação de qualquer um desses padrões disparará esse aviso.  
  
 Cada tipo não lacrado IDisposable raiz deve fornecer seu próprio void virtual protegido método dispose de bool \(\).  Dispose\(\) deve chamar Dipose \(true\) e Termina deve chamar descartado \(false\).  Se você estiver criando um tipo não lacrado IDisposable raiz, você deve definir descartado \(bool\) e chame.  Para obter mais informações, consulte [Cleaning Up Unmanaged Resources](../Topic/Cleaning%20Up%20Unmanaged%20Resources.md) na seção de [Diretrizes de Design de estrutura](../Topic/Framework%20Design%20Guidelines.md) da documentação do.NET Framework.  
  
## Descrição da Regra  
 Todos os tipos de IDisposable devem implementar o padrão de disposição corretamente.  
  
## Como Corrigir Violações  
 Examine o código e determine quais das seguintes resoluções corrigirá essa violação.  
  
-   Remover IDisposable da lista de interfaces que são implementadas por {0} e substituir a classe base disposto a implementação em vez disso.  
  
-   Remova o finalizador do tipo {0}, substituição descartado \(bool que descartado\), e coloca a lógica de acabamento no caminho de código onde “descartar” é falsa.  
  
-   Remover {0}, substituição descartado \(bool que descartado\), e coloca a lógica de disposição no caminho de código onde “descartar” for verdadeira.  
  
-   Verifique se {0} ser declarado como públicas e selado.  
  
-   Renomear {0} “descartado” e ter certeza de que esteja declarado como públicas e selado.  
  
-   Certifique\-se de que {0} é declarado como protegido, virtual, e unsealed.  
  
-   Modifique {0} de modo que chama descartado \(retifique\), então chama GC.SuppressFinalize na instância atual do objeto \(“a” ou “i” em [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\), e retorna em.  
  
-   Modifique {0} de modo que chama descartado \(false\) e retorne em.  
  
-   Se você estiver escrevendo uma classe não lacrada IDisposable raiz, certifique\-se de que a implementação IDisposable segue o padrão descrito anteriormente nesta seção.  
  
## Quando Suprimir Alertas  
 Não elimine um alerta desta regra.  
  
## Exemplo do pseudocódigo  
 O pseudocódigo a seguir fornece um exemplo geral de como descartado \(bool\) deve ser implementada em uma classe que usa os recursos gerenciados e nativos.  
  
```  
public class Resource : IDisposable   
{  
    private IntPtr nativeResource = Marshal.AllocHGlobal(100);  
    private AnotherResource managedResource = new AnotherResource();  
  
// Dispose() calls Dispose(true)  
    public void Dispose()  
    {  
        Dispose(true);  
        GC.SuppressFinalize(this);  
    }  
    // NOTE: Leave out the finalizer altogether if this class doesn't   
    // own unmanaged resources itself, but leave the other methods  
    // exactly as they are.   
    ~Resource()   
    {  
        // Finalizer calls Dispose(false)  
        Dispose(false);  
    }  
    // The bulk of the clean-up code is implemented in Dispose(bool)  
    protected virtual void Dispose(bool disposing)  
    {  
        if (disposing)   
        {  
            // free managed resources  
            if (managedResource != null)  
            {  
                managedResource.Dispose();  
                managedResource = null;  
            }  
        }  
        // free native resources if there are any.  
        if (nativeResource != IntPtr.Zero)   
        {  
            Marshal.FreeHGlobal(nativeResource);  
            nativeResource = IntPtr.Zero;  
        }  
    }  
}  
```