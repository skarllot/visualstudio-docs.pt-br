---
title: "Como: adicionar valida&#231;&#227;o a classes de entidade | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 61107da9-7fa3-4dba-b101-ae46536f52c4
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Como: adicionar valida&#231;&#227;o a classes de entidade
*Validando* classes de entidade é o processo que confirma que os valores inseridos em objetos de dados estão em conformidade com as restrições no esquema de um objeto e também as regras estabelecidas para o aplicativo. Validar dados antes de enviar atualizações para o banco de dados subjacente é uma boa prática que reduz erros. Ele também reduz o número potencial de processamentos entre um aplicativo e o banco de dados.  
  
 O [LINQ to SQL Tools no Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) fornece métodos parciais que permitem aos usuários para estender o código gerado pelo designer que é executado durante inserções, atualizações e exclusões de entidades completos e também durante e após as alterações de coluna individuais.  
  
> [!NOTE]
>  Este tópico fornece as etapas básicas para adicionar validação a classes de entidade usando o [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]. Porque ele pode ser difícil seguir essas etapas genéricos sem se referir a uma classe de entidade específica, foi fornecida um passo a passo que usa dados reais.  
  
## Adicionar validação para alterações ao valor em uma coluna específica  
 Este procedimento mostra como validar dados quando o valor em uma coluna é alterado. Porque a validação é executada dentro da definição de classe \(em vez de na interface do usuário\) uma exceção é lançada se o valor faz com que a validação falhar. Implementar o tratamento de erro para o código do aplicativo que tenta alterar os valores da coluna.  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
#### Para validar dados durante a alteração do valor da coluna  
  
1.  Abra ou crie um novo arquivo LINQ to SQL Classes \(**. dbml** arquivo\) no [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]. \(Clique duas vezes o **. dbml** arquivo **Solution Explorer**.\)  
  
2.  No Object Relational Designer, clique com botão direito a classe para a qual você deseja adicionar validação e, em seguida, clique em **Exibir código**.  
  
     O Editor de códigos abre com uma classe parcial para a classe de entidade selecionada.  
  
3.  Coloque o cursor na classe parcial.  
  
4.  Para projetos do Visual Basic:  
  
    1.  Expanda o **nome do método** lista.  
  
    2.  Localize o **na***COLUMNNAME***alterando** método para a coluna que você deseja adicionar validação para.  
  
    3.  Um `On`*COLUMNNAME*`Changing` método é adicionado à classe parcial.  
  
    4.  Adicione o seguinte código para primeiro verificar que um valor tenha sido inserido e, em seguida garantir que o valor inserido para a coluna é aceitável para seu aplicativo. O `value` argumento contém o valor proposto, para adicionar a lógica para confirmar se ele é um valor válido:  
  
        ```vb#  
        If value.HasValue Then  
            ' Add code to ensure that the value is acceptable.  
            ' If value < 1 Then  
            '    Throw New Exception("Invalid data!")  
            ' End If  
        End If  
        ```  
  
     Para projetos c\#:  
  
    1.  Como projetos c\# não gerar automaticamente os manipuladores de eventos, você pode usar o IntelliSense para criar os métodos parciais de alteração de coluna.  
  
         Tipo de `partial` e, em seguida, um espaço para acessar a lista de métodos parciais disponíveis. Clique no método de alteração de coluna para a coluna que você deseja adicionar validação para. O seguinte código lembra o código que é gerado quando você seleciona um método parcial de alteração de coluna:  
  
        ```c#  
        partial void OnCOLUMNNAMEChanging(COLUMNDATATYPE value)  
            {  
               throw new System.NotImplementedException();  
            }  
  
        ```  
  
## Adicionar validação para atualizações para uma classe de entidade  
 Além de verificar valores durante alterações, você também pode validar dados quando é feita uma tentativa de atualizar uma classe de entidade completa. Validação durante uma tentativa de atualização permite que você compare valores em várias colunas se regras comerciais exigem esta. O procedimento a seguir mostra como validar quando é feita uma tentativa de atualizar uma classe de entidade completa.  
  
> [!NOTE]
>  Código de validação para atualizações para concluir a classes de entidade é executado o parcial <xref:System.Data.Linq.DataContext> classe \(em vez de na classe parcial de uma classe de entidade específica\).  
  
#### Para validar dados durante uma atualização para uma classe de entidade  
  
1.  Abra ou crie um novo arquivo LINQ to SQL Classes \(**. dbml** arquivo\) no [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]. \(Clique duas vezes o **. dbml** arquivo **Solution Explorer**.\)  
  
2.  Clique em uma área vazia em Object Relational Designer e clique em **Exibir código**.  
  
     O Editor de códigos abre com uma classe parcial para o `DataContext`.  
  
3.  Coloque o cursor na classe parcial para o `DataContext`.  
  
4.  Para projetos do Visual Basic:  
  
    1.  Expanda o **nome do método** lista.  
  
    2.  Clique em **atualização***ENTITYCLASSNAME*.  
  
    3.  Um `Update`*ENTITYCLASSNAME* método é adicionado à classe parcial.  
  
    4.  Acessar valores de coluna individuais usando o `instance` argumento, conforme mostrado no código a seguir:  
  
        ```vb#  
        If (instance.COLUMNNAME = x) And (instance.COLUMNNAME = y) Then  
            Dim ErrorMessage As String = "Invalid data!"  
            Throw New Exception(ErrorMessage)  
        End If  
        ```  
  
     Para projetos c\#:  
  
    1.  Como projetos c\# não gerenciar automaticamente os manipuladores de eventos, você pode usar o IntelliSense para criar o parcial `Update`*CLASSNAME* método.  
  
    2.  Tipo de `partial` e, em seguida, um espaço para acessar a lista de métodos parciais disponíveis. Clique no método de atualização para a classe que você deseja adicionar validação para. O seguinte código lembra o código que é gerado quando você seleciona um `Update`*CLASSNAME* método parcial:  
  
        ```c#  
        partial void UpdateCLASSNAME(CLASSNAME instance)  
        {  
            if ((instance.COLUMNNAME == x) && (instance.COLUMNNAME = y))  
            {  
                string ErrorMessage = "Invalid data!";  
                throw new System.Exception(ErrorMessage);  
            }  
        }  
        ```  
  
## Consulte também  
 [LINQ to SQL Tools no Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ to SQL](../Topic/LINQ%20to%20SQL.md)   
 [Validando dados](../Topic/Validating%20Data.md)