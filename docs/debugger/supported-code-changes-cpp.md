---
title: "Altera&#231;&#245;es de c&#243;digo suportadas (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Editar e continuar, limitações"
  - "alterações de código com suporte"
  - "arquivos de objeto, limitações de editar e continuar"
  - "Linguagem c#, alterações de código suportadas"
  - "codificação, suporte para alterações de código"
  - "arquivos de recursos, limitações de editar e continuar"
  - "alterações de código, manipulando em Editar e continuar"
  - "o que há de novo [c#], alterações de código com suporte"
  - "alterações de código"
ms.assetid: f5754363-8a56-417b-b904-b05d9dd26d03
caps.latest.revision: 26
caps.handback.revision: 26
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Altera&#231;&#245;es de c&#243;digo suportadas (C++)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Editar e continuar do Visual C\+\+ trata a maioria dos tipos de alterações de código. No entanto, algumas alterações não podem ser aplicadas durante a execução do programa. Para aplicar essas alterações, você deve interromper a execução e criar uma versão atualizada do código.  
  
 Consulte [Editar e continuar \(Visual C\+\+\)](../debugger/edit-and-continue-visual-cpp.md) para obter informações sobre como trabalhar com editar e continuar do C\+\+ no Visual Studio.  
  
##  <a name="BKMK_Unsupported_changes"></a> Alterações sem suporte  
 As seguintes alterações C\/C\+\+ não podem ser aplicadas durante uma sessão de depuração:  
  
-   A maioria das alterações em dados globais ou estáticos.  
  
-   Alterações nos executáveis que são copiados de outro computador e não são criados localmente.  
  
-   Alterações para um tipo de dados que afetam o layout de um objeto, como os membros de dados de uma classe.  
  
-   Adicionando mais de 64K bytes de novo código ou dados.  
  
-   Adicionando variáveis que exigem um construtor em um ponto antes do ponteiro de instrução.  
  
-   Alterações que afetam o código que requer inicialização em tempo de execução.  
  
-   Adicionando manipuladores de exceção, em alguns casos.  
  
-   Alterações nos arquivos de recurso.  
  
-   Alterações no código em arquivos somente leitura.  
  
-   Alterações no código sem um arquivo PDB correspondente.  
  
-   Alterações no código com nenhum arquivo de objeto.  
  
 Se você fizer uma das alterações e depois tenta aplicar alterações de código, um erro ou mensagem de aviso aparece no **saída** janela.  
  
-   Editar e continuar não atualiza bibliotecas estáticas. Se você fizer uma alteração em uma biblioteca estática, a execução continua com a versão antiga e nenhum aviso é emitido.  
  
##  <a name="BKMK_Unsupported_scenarios"></a> Cenários sem suporte  
 Editar e continuar para C\/C\+\+ não está disponível nos seguintes cenários de depuração:  
  
-   Depuração de aplicativos nativos compilados com [\/Zo \(melhorar a otimização de depuração\)](/visual-cpp/build/reference/zo-enhance-optimized-debugging)  
  
-   Em versões do Visual Studio anterior a atualização 1 do Visual Studio 2015, depuração de aplicativos da Windows Store ou componentes. Iniciando na atualização 1 do Visual Studio 2015, você pode usar Editar e continuar em aplicativos da Windows Store C\+\+ e DirectX, porque ele agora oferece suporte a `/ZI` comutador de compilador com o  `/bigobj` Alternar. Você também pode usar Editar e continuar com os binários compilados com o `/FASTLINK` Alternar.  
  
-   Depuração no Windows 98.  
  
-   Depuração de modo misto \(nativo\/gerenciado\).  
  
-   Depuração de JavaScript.  
  
-   Depuração de SQL.  
  
-   Um arquivo de despejo de depuração.  
  
-   Edição do código após uma exceção não tratada, quando a **desenrolar a pilha de chamadas em exceções não tratadas** opção não estiver selecionada.  
  
-   Depurando um aplicativo usando **anexar a** em vez de executar o aplicativo escolhendo **Iniciar** sobre o **Depurar** menu.  
  
-   Depurando código otimizado.  
  
-   Depuração de uma versão antiga do seu código após uma nova versão falhar a compilação devido a erros de compilação.  
  
##  <a name="BKMK_Linking_limitations"></a> Limitações de vinculação  
  
###  <a name="BKMK_Linker_options_that_disable_Edit_and_Continue"></a> Opções do vinculador que desativam Editar e continuar  
 As seguintes opções do vinculador desativam Editar e continuar:  
  
-   Definindo **\/OPT: REF**, **\/OPT: ICF**, ou **\/INCREMENTAL** desabilita editar e continuar com o seguinte aviso:  
  
     LINK: aviso LNK4075: ignorando \/EDITANDCONTINUE devido a\/OPÇ  
  
     especificação  
  
-   Definindo **\/ORDER**, **\/versão**, ou **\/Force** desabilita editar e continuar com este aviso:  
  
     LINK: aviso LNK4075: ignorando \/incremental. devido a\/opção  
  
     especificação  
  
-   Configurar qualquer opção que impede a criação de um arquivo de banco de dados \(. PDB\) do programa desabilita editar e continuar sem qualquer aviso específico.  
  
###  <a name="BKMK_Auto_relinking_limitations"></a> Auto revinculação limitações  
 Por padrão, editar e continuar vincula novamente o programa no final de uma sessão de depuração para criar um executável atualizado.  
  
 Editar e continuar não podem vincular o programa novamente se você estiver depurando\-lo em um local diferente do local de compilação original. Uma mensagem informa que você precisa recompilar manualmente.  
  
 Editar e continuar não recompila bibliotecas estáticas. Se você fizer alterações em uma biblioteca estática usando editar e continuar, você precisa recompilar os aplicativos de biblioteca e vincular novamente usá\-lo manualmente.  
  
 Editar e continuar não invoca etapas de compilação personalizada. Se seu programa usa etapas de compilação personalizada, convém recriar manualmente para que as etapas de compilação personalizada podem ser invocadas. Nesse caso, você pode desabilitar nova vinculação após editar e continuar para garantir que você precisará recriar manualmente.  
  
 **Para desabilitar nova vinculação após editar e continuar**  
  
1.  Sobre o **Depurar** menu, escolha **Opções e configurações**.  
  
2.  No **opções** caixa de diálogo de **depuração** nó e selecione o **Editar e continuar** nó.  
  
3.  Limpar o **vincular novamente alterações de código após a depuração** caixa de seleção.  
  
##  <a name="BKMK_Precompiled_Header_Limitations"></a> Limitações de cabeçalho pré\-compilado  
 Por padrão, editar e continuar carrega e processa cabeçalhos pré\-compilados em segundo plano para acelerar o processamento de alterações de código. Carregar cabeçalhos pré\-compilados requer alocação de memória física, que pode ser um problema se você estiver compilando em uma máquina com RAM limitada. Você pode determinar se isso pode ser um problema usando o Gerenciador de tarefas do Windows para determinar a quantidade de memória física disponível enquanto você está depurando. Se o valor for maior que o tamanho dos cabeçalhos pré\-compilados, editar e continuar não terá problemas. Se o valor for menor que o tamanho dos cabeçalhos pré\-compilados, você pode impedir que editar e continuar carregue cabeçalhos pré\-compilados em segundo plano.  
  
 **Para desabilitar o carregamento de plano de fundo de cabeçalhos pré\-compilados para editar e continuar**  
  
1.  Sobre o **Depurar** menu, escolha **Opções e configurações**.  
  
2.  No **opções** caixa de diálogo de **depuração** nó e selecione o **Editar e continuar** nó.  
  
3.  Limpar o **Permitir pré\-compilação** caixa de seleção.  
  
##  <a name="BKMK_IDL_Attribute_Limitations"></a> Limitações de atributo IDL  
 Editar e continuar não restaure os arquivos de definição \(IDL\) de interface. Portanto, alterações em atributos IDL não serão refletidas enquanto você está depurando. Para ver o resultado de alterações em atributos IDL, você deve parar a depuração e recompilar seu aplicativo. Editar e continuar não gera um erro ou aviso se alterou atributos IDL. Para obter mais informações, consulte [atributos IDL](/visual-cpp/windows/idl-attributes).  
  
## Consulte também  
 [Editar e continuar \(Visual C\+\+\)](../debugger/edit-and-continue-visual-cpp.md)