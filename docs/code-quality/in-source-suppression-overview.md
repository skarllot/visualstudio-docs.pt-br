---
title: "Vis&#227;o geral de supress&#227;o na origem | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Supressão da fonte, a análise de código"
  - "análise de código, a supressão de origem"
ms.assetid: f1a2dc6a-a9eb-408c-9078-2571e57d207d
caps.latest.revision: 40
caps.handback.revision: 40
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Vis&#227;o geral de supress&#227;o na origem
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

a exclusão em origem é a capacidade de suprimir ou ignorar violações de análise de código em código gerenciado adicionando o atributo de **SuppressMessage** aos segmentos de código que fazem com que as violações.  O atributo é um atributo de **SuppressMessage** condicional que está incluído nos metadados de IL de seu assembly de código gerenciado apenas se o símbolo de compilação de CODE\_ANALYSIS é definido em tempo de compilação.  
  
 Em C\+\+\/CLI, use as macros CA\_SUPPRESS\_MESSAGE ou CA\_GLOBAL\_SUPPRESS\_MESSAGE no arquivo de cabeçalho, adicione o atributo.  
  
 Você não deve usar exclusões em origem em construções de versão para evitar enviar os metadados de exclusão em origem acidentalmente.  Devido à despesa o custo de processamento de exclusão em origem, o desempenho de seu aplicativo também pode ser desatualizado incluindo os metadados de exclusão em origem.  
  
> [!NOTE]
>  Você não precisa fornecer o código esses atributos você mesmo.  Para obter mais informações, consulte [Como suprimir avisos usando o item de menu](../code-quality/how-to-suppress-warnings-by-using-the-menu-item.md).  O item de menu não estará disponível para o código C\+\+.  
  
## Atributo de SuppressMessage  
 Quando você clica com o botão direito do mouse em um aviso de análise de código em **Lista de Erros** e clique em **Suprimir Mensagem**, um atributo de **SuppressMessage** é adicionado ou em seu código ou ao projeto exclusões globais arquivo.  
  
 O atributo de **SuppressMessage** tem o seguinte formato:  
  
```vb  
<Scope:SuppressMessage("Rule Category", "Rule Id", Justification = "Justification", MessageId = "MessageId", Scope = "Scope", Target = "Target")>  
```  
  
```c#  
[Scope:SuppressMessage("Rule Category", "Rule Id", Justification = "Justification", MessageId = "MessageId", Scope = "Scope", Target = "Target")]  
  
```  
  
 \[C\+\+\]  
  
```  
CA_SUPPRESS_MESSAGE("Rule Category", "Rule Id", Justification = "Justification", MessageId = "MessageId", Scope = "Scope", Target = "Target")  
  
```  
  
 Where:  
  
-   **Categoria de regra** \- A categoria na qual a regra é definida.  Para obter mais informações sobre categorias da regra de análise de código, consulte [Avisos da análise de código para código gerenciado](../code-quality/code-analysis-for-managed-code-warnings.md).  
  
-   **Use a ID** \- O identificador da regra.  O suporte inclui um nome curto e longo para o identificador da regra.  O nome curto é CAXXXX; o nome longo é CAXXXX:FriendlyTypeName.  
  
-   **Justificação** \- O texto usado para documentar a razão para suprimir a mensagem.  
  
-   **ID de mensagem** \- Identificador exclusivo de um problema para cada mensagem.  
  
-   **Escopo** \- O destino em que o aviso está sendo suprimido.  Se o destino não for especificado, será definido como o destino do atributo.  Os escopos com suporte incluem o seguinte:  
  
    -   Module  
  
    -   Namespace  
  
    -   Recurso  
  
    -   Tipo  
  
    -   Membro  
  
-   **Destino** \- Um identificador que é usado para especificar o destino em que o aviso está sendo suprimido.  Deve conter um nome totalmente qualificada do item.  
  
## Uso de SuppressMessage  
 Os avisos da análise do código são suprimidos no nível a que uma instância do atributo de **SuppressMessage** é aplicada.  O objetivo dessa é acoplar com segurança informações de exclusão ao código onde a violação ocorrer.  
  
 O formato geral de exclusão inclui a categoria de regra e um identificador da regra que contém uma representação legível opcional do nome da regra.  Por exemplo,  
  
 `[SuppressMessage("Microsoft.Design", "CA1039:ListsAreStrongTyped")]`  
  
 Se houver motivo de desempenho restringidas para minimizar metadados de exclusão em origem, o próprio nome da regra pode ficar fora.  A categoria de regra e o ID da regra suficientemente juntos constituem um identificador exclusivo da regra.  Por exemplo,  
  
 `[SuppressMessage("Microsoft.Design", "CA1039")]`  
  
 Esse formato não é recomendada devido a problemas de manutenibilidade.  
  
## Suprimindo mais violações em um corpo do método  
 Os atributos só podem ser se aplicados a um método e não podem ser inseridas no corpo do método.  No entanto, você pode especificar o identificador como a ID de mensagem para distinguir várias ocorrências de uma violação dentro de um método.  
  
 [!code-cpp[InSourceSuppression#1](../code-quality/codesnippet/CPP/in-source-suppression-overview_1.cpp)]
 [!code-vb[InSourceSuppression#1](../code-quality/codesnippet/VisualBasic/in-source-suppression-overview_1.vb)]
 [!code-cs[InSourceSuppression#1](../code-quality/codesnippet/CSharp/in-source-suppression-overview_1.cs)]  
  
## Código gerado  
 Os compiladores de código gerenciado e algumas ferramentas de terceiros gerenciem o código para facilitar o desenvolvimento rápido de código.  o código gerado completo que aparecem nos arquivos de origem é marcado normalmente com o atributo de **GeneratedCodeAttribute** .  
  
 Você pode escolher se deseja suprimir avisos e erros de análise de código para o código gerado.  Para obter informações sobre como suprimir esses avisos e erros, consulte [Como suprimir avisos para código gerenciado](../code-quality/how-to-suppress-code-analysis-warnings-for-generated-code.md).  
  
 Observe que a análise de código ignora **GeneratedCodeAttribute** quando é aplicada a um assembly inteiro ou um único parâmetro.  Essas situações raramente ocorrem.  
  
## Exclusões de Global\- nível  
 A ferramenta análise de código gerenciado examina os atributos de **SuppressMessage** que são aplicados ao assembly, módulo, tipo, membro ou nível do parâmetro.  Também será acionado violações em recursos e namespaces.  Essas violações devem ser aplicadas no nível global e têm escopo e pretendido.  Por exemplo, a seguinte mensagem suprime uma violação de namespace:  
  
 `[module: SuppressMessage("Microsoft.Design", "CA1020:AvoidNamespacesWithFewTypes", Scope = "namespace", Target = "MyNamespace")]`  
  
> [!NOTE]
>  Quando você suprime um aviso com escopo do namespace, suprime o aviso no namespace próprio.  Não suprime o aviso em tipos no namespace.  
  
 Qualquer exclusão pode ser expressada especificando um escopo explícito.  Essas exclusões devem viver no nível global.  Você não pode especificar a exclusão de membros de nível decorando um tipo.  
  
 Exclusões de Global\- nível é a única maneira de suprimir as mensagens que fazem referência ao código gerado completo que não é mapeado para a origem explicitamente fornecidas do usuário.  Por exemplo, o seguinte código suprime uma violação em um construtor completo emissor:  
  
 `[module: SuppressMessage("Microsoft.Design", "CA1055:AbstractTypesDoNotHavePublicConstructors", Scope="member", Target="Microsoft.Tools.FxCop.Type..ctor()")]`  
  
> [!NOTE]
>  O destino sempre contém o nome totalmente qualificada do item.  
  
## Excluir Arquivo global  
 O arquivo global de exclusão mantém as exclusões que são exclusões de global\- nível ou exclusões que não especificam um destino.  Por exemplo, as exclusões para violações no nível de assembly são armazenadas no arquivo.  Além disso, algumas exclusões do ASP.NET são armazenadas no arquivo como as configurações de nível de projeto não estão disponíveis para o código atrás de um formulário.  Uma exclusão global é criada e adicionada a seu projeto na primeira vez que você seleciona a opção de **Na exclusão Arquivo de projeto** de comando de **Suprimir Mensagem** na janela da Lista de erros.  Para obter mais informações, consulte [Como suprimir avisos usando o item de menu](../code-quality/how-to-suppress-warnings-by-using-the-menu-item.md).  
  
## Consulte também  
 <xref:System.Diagnostics.CodeAnalysis>