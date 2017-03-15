---
title: "Escrevendo código para personalizar uma linguagem específica do domínio | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language, programming
ms.assetid: a4a17f5b-9c97-4575-b2d1-3182c1896b72
caps.latest.revision: 29
author: alancameronwills
ms.author: awills
manager: douge
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 9bce101e19df3da66891cb78f55db8bc5477fa2d
ms.lasthandoff: 02/22/2017

---
# <a name="writing-code-to-customise-a-domain-specific-language"></a>Escrevendo código para personalizar uma linguagem específica do domínio
Esta seção mostra como usar código personalizado para acessar, modificar ou criar um modelo em uma linguagem específica do domínio.  
  
 Há vários contextos em que você pode escrever código que funciona com uma DSL:  
  
-   **Comandos personalizados.** Você pode criar um comando que os usuários podem chamar clicando no diagrama, e que pode modificar o modelo. Para obter mais informações, consulte [como: adicionar um comando ao Menu de atalho](../modeling/how-to-add-a-command-to-the-shortcut-menu.md).  
  
-   **Validação.** Você pode escrever código que verifica se o modelo está no estado correto. Para obter mais informações, consulte [validação em uma linguagem específica do domínio](../modeling/validation-in-a-domain-specific-language.md).  
  
-   **Substituindo o comportamento padrão.** Você pode modificar vários aspectos do código que é gerado a partir de Dsldefinition. Para obter mais informações, consulte [substituindo e estendendo as Classes geradas por](../modeling/overriding-and-extending-the-generated-classes.md).  
  
-   **Transformação de texto.** Você pode escrever modelos de texto que contêm código que acessa um modelo e gera um arquivo de texto, por exemplo, para gerar o código do programa. Para obter mais informações, consulte [código de geração de uma linguagem específica do domínio](../modeling/generating-code-from-a-domain-specific-language.md).  
  
-   **Outras extensões do Visual Studio.** Você pode escrever extensões VSIX separadas que ler e modificar modelos. Para obter mais informações, consulte [como: abrir um modelo de arquivo no código do programa](../modeling/how-to-open-a-model-from-file-in-program-code.md)  
  
 Instâncias de classes que você define no Dsldefinition são mantidas em uma estrutura de dados chamada a *repositório na memória* (IMS) ou *repositório*. As classes que definem uma DSL sempre levam um repositório como um argumento para o construtor. Por exemplo, se sua DSL define uma classe chamada de exemplo:  
  
 `Example element = new Example (theStore);`  
  
 Manter objetos no armazenamento (em vez de objetos apenas tão comuns) oferece vários benefícios.  
  
-   **Transações**. Você pode agrupar uma série de alterações relacionadas em uma transação:  
  
     `using (Transaction t = store.TransactionManager.BeginTransaction("updates"))`  
  
     `{`  
  
     `// make several changes to Store elements here`  
  
     `t.Commit();`  
  
     `}`  
  
     Se uma exceção ocorrer durante as alterações, para que o final Commit () não é executada, o repositório será redefinido para seu estado anterior. Isso ajuda a garantir que os erros não deixar o modelo em um estado inconsistente. Para obter mais informações, consulte [Navegando e atualizando um modelo no código do programa](../modeling/navigating-and-updating-a-model-in-program-code.md).  
  
-   **Relações binárias**. Se você definir uma relação entre duas classes, as instâncias em ambas as extremidades têm uma propriedade que navega para a outra. As duas extremidades são sempre sincronizadas. Por exemplo, se você definir uma relação de parenthood com funções nomeadas pais e filhos, você poderia escrever:  
  
     `John.Children.Add(Mary)`  
  
     Ambas as expressões a seguir forem verdadeiras:  
  
     `John.Children.Contains(Mary)`  
  
     `Mary.Parents.Contains(John)`  
  
     Você também pode obter o mesmo efeito escrevendo:  
  
     `Mary.Parents.Add(John)`  
  
     Para obter mais informações, consulte [Navegando e atualizando um modelo no código do programa](../modeling/navigating-and-updating-a-model-in-program-code.md).  
  
-   **Regras e eventos**. Você pode definir regras que são acionados sempre que forem feitas alterações especificadas. Regras são usadas, por exemplo, para se manter atualizado com os elementos de modelo que apresentam as formas no diagrama. Para obter mais informações, consulte [propagando alterações e responder a](../modeling/responding-to-and-propagating-changes.md).  
  
-   **Serialização**. O armazenamento fornece uma maneira padrão para serializar objetos que ela contém um arquivo. Você pode personalizar as regras de serialização e desserialização. Para obter mais informações, consulte [Personalizando o armazenamento de arquivos e a serialização XML](../modeling/customizing-file-storage-and-xml-serialization.md).  
  
## <a name="see-also"></a>Consulte também  
 [Personalizando e estendendo uma linguagem específica de domínio](../modeling/customizing-and-extending-a-domain-specific-language.md)
