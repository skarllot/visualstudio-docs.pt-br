---
title: "Tipados versus datasets n&#227;o tipados | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c83ba0bb-5425-4d47-8891-6b4dbf937701
caps.latest.revision: 5
caps.handback.revision: 2
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Tipados versus datasets n&#227;o tipados
Um dataset tipado é um conjunto de dados é primeiro derivado da base <xref:System.Data.DataSet> classe e, em seguida, usa as informações do **Dataset Designer**, que é armazenado em um arquivo. xsd, para gerar uma nova classe de conjunto de dados fortemente tipados. Informações do esquema \(tabelas, colunas e assim por diante\) são geradas e compiladas essa nova classe de conjunto de dados como um conjunto de objetos de primeira classe e propriedades. Como um dataset tipado herda da base <xref:System.Data.DataSet> classe, a classe tipada pressupõe que todas as funcionalidades do <xref:System.Data.DataSet> de classe e pode ser usado com métodos que usam uma instância de um <xref:System.Data.DataSet> classe como um parâmetro  
  
 Um conjunto de dados não tipado, por outro lado, não tem nenhum esquema interna correspondente. Como em um dataset tipado, um dataset não tipado contém tabelas, colunas e assim por diante — mas esses são expostos apenas como coleções. \(No entanto, depois de criar manualmente as tabelas e outros elementos de dados em um dataset não tipado, você pode exportar estrutura do conjunto de dados como um esquema usando o conjunto de dados <xref:System.Data.DataSet.WriteXmlSchema%2A> método.\)  
  
## Ao contrário de acesso a dados em Datasets tipados e não tipados  
 A classe de um dataset tipado tem um modelo de objeto em que suas propriedades assumir os nomes reais das tabelas e colunas. Por exemplo, se você estiver trabalhando com um dataset tipado, você pode referenciar uma coluna usando um código como o seguinte:  
  
 [!CODE [VbRaddataDatasets#4](../CodeSnippet/VS_Snippets_VBCSharp/VbRaddataDatasets#4)]  
  
 Por outro lado, se você estiver trabalhando com um conjunto de dados não tipado, o código equivalente é:  
  
 [!CODE [VbRaddataDatasets#5](../CodeSnippet/VS_Snippets_VBCSharp/VbRaddataDatasets#5)]  
  
 Acesso digitado não é apenas mais fácil de ler, mas é totalmente suportado pelo IntelliSense no [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] **Editor de códigos**.  Além de ser mais fácil trabalhar com, a sintaxe para o conjunto de dados tipado fornece verificação de tipo em tempo de compilação, reduzindo significativamente a possibilidade de erros em atribuir valores aos membros do conjunto de dados. Se você alterar o nome de uma coluna em sua <xref:System.Data.DataSet> e, em seguida, compilar o aplicativo, você receberá um erro de compilação. Clicando duas vezes o erro de compilação no **lista de tarefas**, você poderá ir diretamente para a linha ou linhas de código que referenciam o nome da coluna anterior. Acesso a tabelas e colunas em um conjunto de dados também é ligeiramente mais rápido em tempo de execução porque o acesso é determinado em tempo de compilação, não por meio de coleções em tempo de execução.  
  
 Embora os conjuntos de dados tipados têm muitas vantagens, há uma variedade de circunstâncias sob as quais um dataset não tipado é útil. O cenário mais óbvio é quando nenhum esquema está disponível para o conjunto de dados. Isso pode ocorrer, por exemplo, se seu aplicativo está interagindo com um componente que retorna um conjunto de dados, mas você não sabe com antecedência qual sua estrutura. Da mesma forma, há vezes quando você estiver trabalhando com dados que não tem uma estrutura estática, previsível; Nesse caso, é impraticável para usar um dataset tipado, porque você precisa gerar a classe de conjunto de dados tipado com cada alteração na estrutura de dados.  
  
 Normalmente, há muitas vezes quando você pode criar um conjunto de dados dinamicamente sem ter um esquema disponível. Nesse caso, o conjunto de dados é simplesmente uma estrutura conveniente no qual você pode manter informações, como os dados podem ser representados de forma relacional. Ao mesmo tempo, você pode tirar proveito dos recursos do conjunto de dados, como a capacidade de serializar as informações para passar para outro processo ou para gravar um arquivo XML.