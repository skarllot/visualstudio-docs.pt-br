---
title: "Como: criar categorias personalizadas de listas de tarefas | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Lista de tarefas, categorias personalizadas"
ms.assetid: 5e4ac1b1-9afb-46c5-9dcc-6cab9c5ceee8
caps.latest.revision: 9
caps.handback.revision: 9
manager: "douge"
---
# Como: criar categorias personalizadas de listas de tarefas
Categorias personalizadas de tarefas fornecem controle sobre como as tarefas são exibidas na  **Lista de tarefas** janela.  
  
 Implemente uma categoria personalizada de tarefas pelos seguintes motivos:  
  
-   Deseja controlar onde suas categorias são exibidas \(classificado\) na lista de categorias.  
  
-   Você tem várias subcategorias de tarefas que você deseja classificar em uma categoria sem outras tarefas de classificação entre eles.  
  
-   Você deseja criar uma exibição personalizada na qual somente suas tarefas são exibidas.  
  
    > [!NOTE]
    >  Você pode conseguir efeitos semelhantes a categorias personalizadas sem realmente implementar uma categoria personalizada.  Por exemplo, você pode exibir um bitmap para uma categoria ou subcategoria implementando <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider2.ImageList%2A> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskItem2.ImageListIndex%2A>.  O provedor de tarefas fornece a lista e cada tarefa apresenta um índice para a lista.  
  
 Para criar uma categoria personalizada na  **Lista de tarefas**, registrá\-lo com o  **Lista de tarefas** usando o procedimento a seguir.  
  
### Para registrar uma categoria da lista de tarefas personalizado  
  
-   Chame <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList.RegisterCustomCategory%2A> para registrar uma categoria personalizada com a lista de tarefas.  
  
     Cada categoria personalizada deve ter seu próprio GUID, que é especificada na `guidCat` parâmetro.  No `dwSortOrder` parâmetro, forneça o local onde deseja que esta categoria para classificar \(quando a lista é classificada por categorias\).  Este método retorna o posicionamento de classificação real da categoria personalizada dentro da lista de categorias maior.  
  
     Classificar as ordens para as categorias de tarefas interno, que são definidas na <xref:Microsoft.VisualStudio.Shell.Interop.VSTASKCATEGORY> enumeração, estão na tabela a seguir.  
  
    |\<strong\>Categoria\<\/strong\>|Valor|Descrição|  
    |-------------------------------------|-----------|---------------|  
    |CAT\_ALL|1|Não é uma categoria real.  Usado para permitir que um modo de exibição de lista de tarefas mostrar todas as tarefas do  **Lista de tarefas**.|  
    |CAT\_BUILDCOMPILE|10|Construir erros, avisos e possivelmente erros de implantação.|  
    |CAT\_COMMENTS|20|Tarefas geradas por comentários especiais, como, por exemplo, "TODO", "Desfazer" ou "HACK".|  
    |CAT\_CODESENSE|30|Erros gerados conforme você digita o código\-fonte.|  
    |CAT\_SHORTCUTS|40|Atalhos para o código.|  
    |CAT\_USER|50|Tarefas inseridas pelo usuário.|  
    |CAT\_MISC|60|Tarefas diversas que VSPackages talvez queira adicionar o  **Lista de tarefas**.|  
    |CAT\_HTML|70|Tarefas relacionados ao desenvolvimento de página da Web.|  
  
     Por exemplo, para incluir uma categoria entre CAT\_CODESENSE e CAT\_SHORTCUTS, você pode passar um valor de 31 para sua ordem de classificação.  No entanto, porque um valor igual a 31 já pode ser usado por outro provedor de categoria de tarefas personalizado, o  **Lista de tarefas** atribui a você a categoria de tarefa para o próximo slot vazio.  Esse valor é passado de volta para você na `pCat` parâmetro.  
  
### Para cancelar o registro de uma categoria da lista de tarefas personalizado  
  
-   Chame <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList.UnregisterCustomCategory%2A> para cancelar o registro de sua categoria personalizada.  
  
## Consulte também  
 [Criando modos de exibição de lista de tarefas personalizados](/visual-cpp/misc/creating-custom-task-list-views)