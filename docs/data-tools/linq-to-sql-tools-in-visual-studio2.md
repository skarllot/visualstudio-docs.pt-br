---
title: "LINQ to SQL Tools no Visual Studio2 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 45e477c0-5c6b-41f9-b2d0-2808fb4f6537
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# LINQ to SQL Tools no Visual Studio
O LINQ to SQL foi a primeira tecnologia de mapeamento relacional de objeto lançada pela Microsoft. Ele funciona bem em cenários básicos e continua a ter suporte no Visual Studio, mas ele não está mais sob desenvolvimento ativo. Use o LINQ to SQL durante a manutenção de um aplicativo herdado que já está usando ou em aplicativos simples que usam o SQL Server e não requerem mapeamento de várias tabela. Em geral, novos aplicativos devem usar o Entity Framework quando uma camada mapeador relacional de objetos é necessária.  
  
 No Visual Studio, você cria classes LINQ to SQL que representam tabelas SQL usando o [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
 O [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] tem duas áreas distintas na superfície de design: o painel de entidades à esquerda e o painel de métodos à direita. O painel de entidades é a principal superfície de design que exibe as classes de entidade, associações e hierarquias de herança. O painel de métodos é a superfície de design que exibe o <xref:System.Data.Linq.DataContext> métodos que são mapeados para procedimentos armazenados e funções.  
  
 O [!INCLUDE[vs_ordesigner_long](../data-tools/includes/vs_ordesigner_long_md.md)] ([!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]) fornece uma superfície de design visual para criar [LINQ to SQL](../Topic/LINQ%20to%20SQL.md) classes de entidade e associações (relações) que são baseadas em objetos em um banco de dados. Ou seja, o [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] é usado para criar um modelo de objeto em um aplicativo que mapeia para objetos em um banco de dados. Ele também gera um tipo mais acentuado <xref:System.Data.Linq.DataContext> que é usado para enviar e receber dados entre as classes de entidade e o banco de dados. O [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] também fornece funcionalidade para mapear procedimentos armazenados e funções para <xref:System.Data.Linq.DataContext> métodos para retornar dados e preencher classes de entidade. Finalmente, o [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] fornece a capacidade de criar relações de herança entre classes de entidade.  
  
## <a name="opening-the-or-designer"></a>Abrindo o Object Relational Designer  
 Para adicionar um LINQ no modelo de entidade SQL ao seu projeto, escolha **projeto &#124; Adicionar Novo Item** e, em seguida, escolha  **Classes LINQ to SQL** da lista de itens de projeto:  
  
 ![Classes LINQ to SQL](../data-tools/media/raddata-linq-to-sql-classes.png "raddata LINQ to SQL Classes")  
  
 Visual Studio cria um arquivo. dbml e adiciona à sua solução. Este é o arquivo de mapeamento XML e seus arquivos de código relacionadas.  
  
 ![Classes LINQ to SQL no Solution Explorer](../data-tools/media/raddata-linq-to-sql-classes-in-solution-explorer.png "raddata LINQ to SQL classes in Solution Explorer")  
  
 Quando você seleciona o arquivo. dbml, o Visual Studio mostra a superfície de Object Relational designer que permite que você crie visualmente o modelo. A ilustração a seguir mostra o designer após tem sido arrastadas as tabelas Northwind Customers e Orders no Gerenciador de servidores. Observe a relação entre as tabelas.  
  
 ![LINQ to SQL Designer](../data-tools/media/raddata-linq-to-sql-designer.png "raddata LINQ to SQL Designer")  
  
> [!IMPORTANT]
>  O [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] é um mapeador relacional de objeto simples, pois suporta apenas as relações de mapeamento 1:1. Em outras palavras, uma classe de entidade pode ter apenas uma relação de mapeamento 1:1 com uma exibição ou tabela de banco de dados. Não há suporte para o mapeamento complexo, como o mapeamento de uma classe de entidade para uma tabela unida, Use o Entity Framework para mapeamento complexo. Além disso, o designer é um gerador de código unidirecional. Isso significa que somente as alterações feitas à superfície de designer são refletidas no arquivo de código. Alterações manuais no arquivo de código não são refletidas no [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]. Quaisquer alterações feitas manualmente no arquivo de código são substituídas quando o designer é salvo e o código for gerado novamente. Para obter informações sobre como adicionar código de usuário e estender as classes geradas pelo [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], consulte [como: estender o código gerado por Object Relational Designer](../Topic/How%20to:%20Extend%20Code%20Generated%20by%20the%20O-R%20Designer.md).  
  
## <a name="creating-and-configuring-the-datacontext"></a>Criando e configurando o DataContext  
 Depois de adicionar um **Classes LINQ to SQL** item a um projeto e abrir o [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], a superfície de design vazio representa vazia <xref:System.Data.Linq.DataContext> pronto para ser configurado. o <xref:System.Data.Linq.DataContext> está configurado com as informações de conexão fornecida pelo primeiro item que é arrastado para a superfície de design... Portanto, o <xref:System.Data.Linq.DataContext> é configurado usando as informações de conexão do primeiro item descartado na superfície de design. Para obter mais informações sobre o <xref:System.Data.Linq.DataContext> consulte classe [métodos de DataContext (Object Relational Designer)](../data-tools/datacontext-methods-o-r-designer.md).  
  
## <a name="creating-entity-classes-that-map-to-database-tables-and-views"></a>Criando Classes de entidade que mapeiam para tabelas de banco de dados e exibições  
 Você pode criar classes de entidade mapeadas para tabelas e modos de exibição arrastando tabelas de banco de dados e modos de exibição de **Server Explorer**/**Database Explorer** até o [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]. Conforme indicado na seção anterior a <xref:System.Data.Linq.DataContext> está configurado com as informações de conexão fornecida pelo primeiro item que é arrastado para a superfície de design. Se um item subsequente que usa uma conexão diferente é adicionado para o [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], você pode alterar a conexão para o <xref:System.Data.Linq.DataContext>. Para obter mais informações, consulte [como: criar classes LINQ to SQL mapeadas para tabelas e exibições (Object Relational Designer)](../Topic/How%20to:%20Create%20LINQ%20to%20SQL%20classes%20mapped%20to%20tables%20and%20views%20\(O-R%20Designer\).md).  
  
## <a name="creating-datacontext-methods-that-call-stored-procedures-and-functions"></a>Criando métodos DataContext que chamam procedimentos armazenados e funções  
 Você pode criar <xref:System.Data.Linq.DataContext> métodos que chamam (são mapeados) procedimentos armazenados e funções arrastando-as da **Server Explorer**/**Database Explorer** até o [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]. Procedimentos armazenados e funções são adicionadas para o [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] como métodos do <xref:System.Data.Linq.DataContext>.  
  
> [!NOTE]
>  Quando você arrasta procedimentos armazenados e funções de **Server Explorer**/**Database Explorer** até o [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], o tipo de retorno de gerado <xref:System.Data.Linq.DataContext> método difere dependendo de onde você solta o item. Para obter mais informações, consulte [métodos de DataContext (Object Relational Designer)](../data-tools/datacontext-methods-o-r-designer.md).  
  
## <a name="configuring-a-datacontext-to-use-stored-procedures-to-save-data-between-entity-classes-and-a-database"></a>Configurando um DataContext para usar procedimentos armazenados para salvar dados entre Classes de entidade e um banco de dados  
 Conforme mencionado anteriormente, você pode criar <xref:System.Data.Linq.DataContext> métodos que chamam procedimentos armazenados e funções. Além disso, você também pode atribuir procedimentos armazenados que podem ser usados para o comportamento padrão de tempo de execução de [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] que executa inserções, atualiza, e exclui as. Para obter mais informações, consulte [como: atribuir procedimentos armazenados para executar atualizações, inserções e exclusões (Object Relational Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).  
  
## <a name="inheritance-and-the-or-designer"></a>Herança e Object Relational Designer  
 Como outros objetos, classes de [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] podem usar a herança e ser derivadas de outras classes. Em um banco de dados, as relações de herança são criadas de várias maneiras. 
          [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] suporta o conceito de herança de tabela única como geralmente é implementado em sistemas relacionais. Para obter mais informações, consulte [como: configurar a herança usando Object Relational Designer](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md).  
  
## <a name="linq-to-sql-queries"></a>Consultas LINQ to SQL  
 As classes de entidade criadas pelo [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] são projetados para uso com [LINQ (consulta integrada à linguagem)](../Topic/LINQ%20\(Language-Integrated%20Query\).md). Para obter mais informações, consulte [como: consultar informações](../Topic/How%20to:%20Query%20for%20Information.md).  
  
## <a name="separating-the-generated-datacontext-and-entity-class-code-into-different-namespaces"></a>Separando o DataContext gerado e o código da classe de entidade em Namespaces diferentes  
 O [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] fornece a **Namespace do contexto** e **Namespace da entidade** Propriedades de <xref:System.Data.Linq.DataContext>. Essas propriedades determinam o namespace do <xref:System.Data.Linq.DataContext> e código de classe de entidade é gerado. Por padrão, essas propriedades são vazios e <xref:System.Data.Linq.DataContext> e classes de entidade são gerados no namespace do aplicativo. Para gerar o código em um namespace diferente do namespace do aplicativo, insira um valor para o **Namespace do contexto** e/ou **Namespace da entidade** Propriedades.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Métodos de DataContext (Object Relational Designer)](../data-tools/datacontext-methods-o-r-designer.md)  
 Explica o que <xref:System.Data.Linq.DataContext> métodos são e como criá-los.  
  
 [Herança de classe de dados (Object Relational Designer)](../data-tools/data-class-inheritance-o-r-designer.md)  
 Descreve o conceito de herança de tabela única e como ela é implementada no [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
 [Como: criar LINQ to SQL classes mapeadas para tabelas e exibições (Object Relational Designer)](../Topic/How%20to:%20Create%20LINQ%20to%20SQL%20classes%20mapped%20to%20tables%20and%20views%20\(O-R%20Designer\).md)  
 Descreve como criar classes de entidade que são mapeadas para tabelas e exibições em um banco de dados.  
  
 [Como: criar uma associação (relação) entre classes LINQ to SQL (Object Relational Designer)](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md)  
 Descreve como criar uma relação entre classes de entidade do [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)].  
  
 [Como: criar métodos DataContext mapeados para procedimentos armazenados e funções (Object Relational Designer)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)  
 Descreve como criar <xref:System.Data.Linq.DataContext> métodos que executam procedimentos armazenados ou funções quando são chamados.  
  
 [Como: atribuir procedimentos armazenados para executar atualizações, inserções e exclusões (Object Relational Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)  
 Descreve como configurar um <xref:System.Data.Linq.DataContext> usar procedimentos armazenados ao salvar dados de entidade classes de volta para um banco de dados.  
  
 [Como: alterar o tipo de retorno de um método DataContext (Object Relational Designer)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md)  
 Descreve como definir o tipo de retorno de um <xref:System.Data.Linq.DataContext> método a ser o tipo de uma classe de entidade ou um tipo gerado automaticamente criado pelo Object Relational Designer.  
  
 [Como: adicionar validação a classes de entidade](../data-tools/how-to-add-validation-to-entity-classes.md)  
 Descreve como gerar métodos parciais que permitem a adição de código durante alterações de propriedade e atualizações de classe de entidade.  
  
 [Como: ative em pluralization e off (Object Relational Designer)](../data-tools/how-to-turn-pluralization-on-and-off-o-r-designer.md)  
 Descreve como ativar e desativar o renomeamento automático de classes que são adicionadas ao [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
 [Como: configurar a herança usando Object Relational Designer](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md)  
 Descreve como configurar classes de entidade usando herança de tabela única com o [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
 [Como: estender o código gerado por Object Relational Designer](../Topic/How%20to:%20Extend%20Code%20Generated%20by%20the%20O-R%20Designer.md)  
 Descreve como e onde adicionar código que não será substituído quando as alterações em objetos no Object Relational Designer regenerarem o código.  
  
 [Passo a passo: Criando Classes LINQ to SQL usando a herança de tabela única (Object Relational Designer)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)  
 Fornece instruções passo a passo para configurar classes de entidade usando a herança de tabela única com o [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
 [Passo a passo: Personalizando a inserção, atualização e exclusão de comportamento de classes de entidade](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md)  
 Fornece instruções passo a passo para configurar um <xref:System.Data.Linq.DataContext> usar procedimentos armazenados ao salvar dados de entidade classes de volta para um banco de dados.  
  
## <a name="reference-content"></a>Conteúdo de referência  
 <xref:System.Linq>  
  
 <xref:System.Data.Linq>  
  
## <a name="see-also"></a>Consulte também  
 [Ferramentas de dados do Visual Studio para .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)   
 [Perguntas frequentes](../Topic/Frequently%20Asked%20Questions.md)   
 [LINQ to SQL](../Topic/LINQ%20to%20SQL.md)   
 [Acessando dados no Visual Studio](../data-tools/accessing-data-in-visual-studio.md)