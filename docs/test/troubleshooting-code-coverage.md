---
title: "Solu&#231;&#227;o de problemas de cobertura de c&#243;digo | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 26de91b8-45e3-4976-a20e-a3bd1942ddcb
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "mlearned"
manager: "douge"
---
# Solu&#231;&#227;o de problemas de cobertura de c&#243;digo
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

A ferramenta de análise da cobertura de código no Visual Studio coleta dados para assemblies nativos e gerenciados \(arquivos .dll ou .exe\).  No entanto, em alguns casos, a janela Resultados de Cobertura de Código exibe um erro semelhante a "Esvaziar resultados gerados: ...." Existem vários motivos possíveis pelos quais isso pode acontecer.  Este tópico deve ajudar a resolver esses problemas.  
  
## O que você deve ver  
 Se escolher um comando **Analisar Cobertura de Código** no menu Teste e se a compilação e os testes forem executados com êxito, você deverá ver uma lista de resultados na janela Cobertura de Código.  Você talvez tenha que expandir os itens para ver os detalhes.  
  
 ![Resultados de cobertura de código com cores](../test/media/codecoverage1.png "CodeCoverage1")  
  
 Para obter mais informações, consulte [Usando cobertura de código para determinar quanto código está sendo testado](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md).  
  
## Possíveis motivos para não ver resultados ou ver resultados anteriores  
  
### Você tem a edição certa do Visual Studio?  
 É necessário o Visual Studio Enterprise.  
  
### Nenhum teste foi executado  
 Análise  
 Verifique a janela de saída.  Na lista suspensa **Mostrar Saída de**, escolha **Testes**.  Verifique se existe algum aviso ou erro registrado em log.  
  
 Explicação  
 A análise de cobertura de código é feita durante a execução de testes.  Ela inclui apenas assemblies carregados na memória durante a execução dos testes.  Se nenhum dos testes for executado, não haverá nada para a cobertura de código a ser reportado.  
  
 Resolução  
 No Gerenciador de Testes, escolha **Executar Tudo** para verificar se os testes foram executados com êxito.  Corrija todas as falhas antes de usar **Analisar Cobertura de Código**.  
  
### Você está observou um resultado anterior  
 Quando você modificar e reexecutar os testes, um resultado anterior da cobertura de código poderá permanecer visível, inclusive a coloração de código com base nessa execução anterior.  
  
1.  Executar Analisar Cobertura de Código.  
  
2.  Não se esqueça de selecionar o conjunto de resultados mais recente na janela de resultados Cobertura de Código.  
  
### Os arquivos .pdb \(símbolo\) não estão disponíveis  
 Análise  
 Abra a pasta de destino de compilação \(normalmente bin\\debug\) e verifique se, para cada assembly, existe um arquivo .pdb no mesmo diretório do arquivo .dll ou .exe.  
  
 Explicação  
 O mecanismo de cobertura de código exige que todo assembly tenha seu arquivo .pdb associado acessível durante a execução do teste.  Se não houver arquivo .pdb para um determinado assembly, ele não será analisado.  
  
 O arquivo .pdb deve ser gerado com base na mesma compilação dos arquivos .dll ou .exe.  
  
 Resolução  
 Verifique se as configurações de compilação geram o arquivo .pdb.  Se os arquivos .pdb não forem atualizados quando o projeto for compilado, abra as propriedades do projeto, selecione a página **Compilação**, escolha **Avançado** e inspecione **Informações de Depuração**.  
  
 Se os arquivos .pdb e .dll ou .exe estiverem em locais diferentes, copie o arquivo .pdb para o mesmo diretório.  Também é possível configurar o mecanismo de cobertura de código para procurar arquivos .pdb em outro local.  Para obter mais informações, consulte [Personalizando análise de cobertura de código](../test/customizing-code-coverage-analysis.md).  
  
### Usando um binário instrumentado ou otimizado  
 Análise  
 Determine se o binário passou por algum formulário de otimização avançada como, por exemplo, Otimização Guiada por Perfil, ou foi instrumentado por uma ferramenta de criação de perfil como vsinstr.exe ou vsperfmon.exe.  
  
 Explicação  
 Se um assembly já tiver sido instrumentado ou otimizado por outra ferramenta de criação de perfil, o assembly será omitido da análise de cobertura de código.  
  
 A análise de cobertura de código não pode ser realizada nesses assemblies.  
  
 Resolução  
 Desative a otimização e use uma nova compilação.  
  
### O código é não gerenciado \(.NET\) ou nativo \(C\+\+\)  
 Análise  
 Verifique se você está executando alguns testes em código gerenciado ou do C\+\+.  
  
 Explicação  
 A análise de cobertura de código no Visual Studio está disponível apenas no código gerenciado e nativo \(C\+\+\).  Se você estiver trabalhando com ferramentas de terceiros, um ou todo o código poderá ser executado em uma plataforma diferente.  
  
 Resolução  
 Nenhum disponível.  
  
### O assembly foi instalado por NGen  
 Análise  
 Verifique se o assembly não é carregado com base no cache de imagem nativa.  
  
 Explicação  
 Por motivos de desempenho, os assemblies de imagem nativa não são analisados.  Para obter mais informações, consulte [Ngen.exe \(Gerador de Imagens Nativas\)](../Topic/Ngen.exe%20\(Native%20Image%20Generator\).md).  
  
 Resolução  
 Use uma versão MSIL do assembly.  Não o processe com NGen.  
  
### Arquivo .runsettings personalizado com sintaxe incorreta  
 Análise  
 Se você estiver usando um arquivo .runsettings personalizado, ele poderá conter um erro de sintaxe.  
  
 Isso resulta na ausência de execução de cobertura de código.  A janela de cobertura de código não é aberta ao final da execução de teste ou mostra resultados anteriores.  
  
 Explicação  
 É possível executar testes de unidade com um arquivo .runsettings personalizado para configurar opções de cobertura de código.  As opções permitem incluir ou excluir arquivos.  Para obter mais informações, consulte [Personalizando análise de cobertura de código](../test/customizing-code-coverage-analysis.md).  
  
 Resolução  
 Existem dois tipos possíveis de falhas:  
  
-   **Erro de XML**  
  
     Abra o arquivo .runsettings no editor XML do Visual Studio.  Procure indicações de erro.  
  
-   **Erro na expressão regular**  
  
     Cada cadeia de caracteres no arquivo é uma expressão regular.  Revise cada um em busca de erros e, em especial, procure:  
  
    -   Incompatíveis parênteses \(...\) ou parênteses sem escape \\ \(...  \\\).  Se quiser corresponder um parêntese na cadeia de pesquisa, você deverá usar o escape.  Por exemplo, para corresponder a uma função, use: `.*MyFunction\(double\)`  
  
    -   Asterisco ou sinal de adição no início de uma expressão.  Para comparar qualquer cadeia de caracteres, use um ponto seguido de um asterisco: `.*`  
  
### Arquivo .runsettings personalizado com exclusões incorretas  
 Análise  
 Se você estiver usando um arquivo .runsettings personalizado, verifique se ele inclui o assembly.  
  
 Explicação  
 É possível executar testes de unidade com um arquivo .runsettings personalizado para configurar opções de cobertura de código.  As opções permitem incluir ou excluir arquivos.  Para obter mais informações, consulte [Personalizando análise de cobertura de código](../test/customizing-code-coverage-analysis.md).  
  
 Resolução  
 Remova todos os nós `Include` do arquivo .runsettings e, em seguida, descarte todos os nós `Exclude`.  Se isso corrigir o problema, recoloque\-os em estágios.  
  
 Verifique se o nó DataCollectors especifica a Cobertura de Código.  Compare\-o com o exemplo no [Personalizando análise de cobertura de código](../test/customizing-code-coverage-analysis.md).  
  
## Um código é sempre mostrado como não coberto  
  
### O código de inicialização em DLLs nativas é executado antes da instrumentação  
 Análise  
 No código nativo vinculado estaticamente, a função de inicialização **DllMain** e o código chamado às vezes são mostrados como não cobertos, mesmo que o código tenha sido executado.  
  
 Explicação  
 A ferramenta de cobertura de código funciona inserindo\-se a instrumentação em um assembly pouco antes do início da execução do aplicativo.  Em qualquer assembly carregado antes, o código de inicialização em **DllMain** é executado assim que o assembly é carregado e antes da execução do aplicativo.  Esse código aparentemente não estará coberto.  
  
 Normalmente, isso se aplica aos assemblies carregados estaticamente.  
  
 Resolução  
 Nenhum.  
  
## Consulte também  
 [Usando cobertura de código para determinar quanto código está sendo testado](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)