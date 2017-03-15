---
title: "Valores de m&#233;tricas do c&#243;digo | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "métricas de código"
  - "análise de código"
  - "medir qualidade do código"
ms.assetid: bc38831e-2083-4ea4-8527-ee41499a342f
caps.latest.revision: 20
caps.handback.revision: 20
author: "erickson-doug"
ms.author: "douge"
manager: "douge"
---
# Valores de m&#233;tricas do c&#243;digo
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Métricas de código é um conjunto de medidas de software que fornecem desenvolvedores melhor informações no código que está desenvolvendo.  Usufruindo a métrica de código, os desenvolvedores podem entender quais digita e\/ou os métodos devem ser reworked ou mais minuciosamente sers.  As equipes de desenvolvimento pode identificar potenciais, riscos entender o estado atual de um projeto, e rastrear o progresso durante a programação de software.  
  
## Medidas de software  
 A lista a seguir mostra a métrica de código resultados que calcula [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]:  
  
-   **Índice de manutenibilidade** – Calcula um valor de índice entre 0 e 100 que representa a facilidade relativa de manter o código.  Um valor alto significa a melhor manutenibilidade.  As estimativas codificadas cor podem ser usadas para identificar rapidamente pontos de conflito em seu código.  Uma estimativa verde estiver entre 20 e 100 e indica que o código tem boa a manutenibilidade.  Uma estimativa amarela estiver entre 10 e 19 e indica que o código é sustentável moderadamente.  Uma estimativa vermelha é uma estimativa entre 0 e 9 e indica pouca manutenibilidade.  
  
-   **Complexidade de Cyclomatic** – Medidas a complexidade estrutural de código.  É criado para calcular o número de diferentes caminhos de código no fluxo do programa.  Um programa que tem o fluxo de controle complexo exigir mais testes obter uma boa cobertura de código e será menor sustentável.  
  
    > [!NOTE]
    >  Em alguns casos, o cálculo de complexidade cyclomatic para um método em  [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] difere das versões anteriores.  Para obter mais informações, consulte “as alterações na seção de cálculos da complexidade do código do Visual Studio 2010” de [Solucionando problemas de métricas do código](../code-quality/troubleshooting-code-metrics-issues.md).  
  
-   **Profundidade de herança** – Indica o número de definições de classe que estendem à raiz da hierarquia da classe.  Mais profunda a hierarquia pode ser mais difícil entender onde os métodos específicos e os campos é definida e\/ou redefinido.  
  
-   **Acoplamento da classe** – Medidas o envolvimento às classes exclusivas com os parâmetros, as variáveis locais, os tipos de retorno, as chamadas de método, as instanciações genéricas ou do modelo, as classes base, as implementações da interface, os campos definidos em tipos externos, e a decoração do atributo.  O bom design de software que determina os tipos e os métodos devem ter a coesão alto e baixo acoplamento.  O envolvimento alto indica um design que é difícil de reutilizar e manter devido às suas muitas interdependências em outros tipos.  
  
-   **Linhas de código** – Indica o número aproximado de linhas no código.  A pontuação é baseada em código de IL e não em virtude disso é o número exato de linhas no arquivo de origem.  Uma quantidade muito grande pode indicar que um tipo ou um método estão tentando fazer muito trabalho e deve ser dividida acima.  Também pode indicar que o tipo ou o método podem ser difícil de manter.  
  
## Métodos anônimas  
 *Um método anônimo* é apenas um método que não tem nenhum nome.  Os métodos anônimas com mais frequência são usadas para passar um bloco de código como um parâmetro de delegação.  Métricas resultados para um método anônima que é declarada em um membro, como um método ou um acessador, é associado ao membro que declara o método.  Não são associados ao membro que chama o método.  
  
 Para obter mais informações sobre como as métricas de código trata métodos anônimas, consulte [Métodos anônimos e análise de código](../code-quality/anonymous-methods-and-code-analysis.md).  
  
## Código gerado  
 Algumas ferramentas e os compiladores de software gerenciem o código que são adicionados a um projeto e que o desenvolvedor do projeto não consulta ou não deve ser alterado.  Na maior parte, a métrica de código ignora o código gerado quando o calcular os valores das métricas.  Isso permite que os valores das métricas para refletir o que o desenvolvedor pode consultar e alterar.  
  
 O código gerado para windows forms não é ignorado, porque é o código que o desenvolvedor pode consultar e alterar.  
  
## Consulte também  
 [Medindo complexidade e facilidade de manutenção do código gerenciado](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)