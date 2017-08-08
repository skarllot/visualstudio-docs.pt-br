---
title: Live Unit Testing no Visual Studio | Microsoft Docs
ms.date: 2017-03-07
ms.suite: 
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio ALM
- Live Unit Testing
ms.assetid: 5b51fb96-94f4-4926-92b9-262156c05b85
author: rpetrusha
ms.author: ronpet
translation.priority.ht:
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
ms.translationtype: Human Translation
ms.sourcegitcommit: c559290c8e88c8b4e37feabc7014188fad15434d
ms.openlocfilehash: 0a939044b9806236cf55333c30bce24ae0fdb28a
ms.contentlocale: pt-br
ms.lasthandoff: 06/08/2017

---

# <a name="live-unit-testing-with-visual-studio-2017"></a>Live Unit Testing com o Visual Studio 2017

Durante o desenvolvimento de um aplicativo, o Live Unit Testing executa os testes de unidade afetados automaticamente em segundo plano e apresenta os resultados e a cobertura de código de forma dinâmica no IDE do Visual Studio em tempo real. Durante a modificação do código, o Live Unit Testing fornece comentários sobre como as alterações afetaram os testes existentes e se o novo código adicionado é abrangido por um ou mais testes existentes. Cuidadosamente, isso o lembrará de escrever testes de unidade durante as correções de bugs ou a adição novos recursos.

> [!NOTE]
> O Live Unit Testing está disponível para projetos do C# e do Visual Basic que se destinam ao .NET Core ou ao .NET Framework na Enterprise Edition do Visual Studio 2017.

## <a name="supported-test-frameworks"></a>Estruturas de teste com suporte
O Live Unit Testing funciona com as três estruturas de teste de unidade populares listadas na tabela a seguir. A versão mínima com suporte de seus adaptadores e suas estruturas também é listada na tabela. As estruturas de teste de unidade estão disponíveis em NuGet.org.
 
<table> 
<tr>
   <th>Estrutura de teste</th>
   <th>Versão mínima do Adaptador do Visual Studio</th>
   <th>Versão mínima da Estrutura</th>
</tr>
<tr>
   <td>xUnit.net</td>
   <td> xunit.runner.visualstudio versão 2.2.0-beta3-build1187</td>
   <td>xunit 2.0</td> 
</tr>
<tr>
   <td>NUnit</td>
   <td>NUnit3TestAdapter versão 3.5.1</td>  
   <td>NUnit versão 3.5.0</td>
</tr>
<tr>
   <td>MSTest</td>
   <td>MSTest.TestAdapter 1.1.11</td>
   <td>MSTest.TestFramework 1.1.11</td>
</tr>
</table>

Se você tiver referências mais antigas de adaptador e estrutura de teste dos projetos existentes, lembre-se de removê-las. (Lembre-se de remover a referência a `Microsoft.VisualStudio.QualityTools.UnitTestFramework` se estiver usando o MSTest.) Adicione as novas se o Live Unit Testing não estiver funcionando para você. 

Em alguns casos, talvez seja necessário restaurar explicitamente os pacotes NuGet referenciados pelos projetos na solução para que o Live Unit Testing funcione. Faça isso executando um build explícito da solução (selecione **Compilar**, **Recompilar Solução** no menu de nível superior do Visual Studio) ou restaurando pacotes da solução (clique com o botão direito do mouse na solução e selecione **Restaurar Pacotes NuGet**) antes de habilitar o Live Unit Testing. 

#   <a name="configuring-live-unit-testing"></a>Configurando o Live Unit Testing

É possível configurar o Live Unit Testing selecionando **Ferramentas**, **Opções** no menu de nível superior do Visual Studio e, em seguida, selecionando **Live Unit Testing** no painel esquerdo da caixa de diálogo **Opções**. A figura a seguir mostra as opções de configuração do Live Unit Testing disponíveis na caixa de diálogo.

  ![Image](./media/lut-options.png)

As opções configuráveis incluem:

- Se o Live Unit Testing é executado automaticamente quando uma solução é aberta.
- Se o Live Unit Testing é pausado quando uma solução é compilada e depurada ou quando a energia da bateria do sistema fica abaixo de um limite especificado.
- O intervalo após o qual um caso de teste atinge o tempo limite; o padrão é 30 segundos. 
- O número de processos de teste criados pelo Live Unit Testing. 
- O nível de informações gravadas na janela **Saída** do Live Unit Testing. As opções incluem sem log (Nenhum), somente mensagens de erro (Erro), mensagens de erro e mensagens informativas (Informações, o padrão) ou todos os detalhes (Detalhado).

Também é possível exibir a saída detalhada na janela **Saída** do Live Unit Testing atribuindo um valor igual a “1” a uma variável de ambiente em nível de usuário chamada `VS_UTE_DIAGNOSTICS` e reiniciando o Visual Studio. 

Para capturar mensagens de log detalhadas do MSBuild do Live Unit Testing em um arquivo, defina a variável de ambiente em nível de usuário `LiveUnitTesting_BuildLog` com o nome do arquivo que conterá o log.

## <a name="starting-pausing-and-stopping-live-unit-testing"></a>Iniciando, pausando e parando o Live Unit Testing

Habilite o Live Unit Testing selecionando **Teste**, **Live Unit Testing** e **Iniciar** no menu de nível superior do Visual Studio. Quando o Live Unit Testing é habilitado, as opções disponíveis no menu **Live Unit Testing** mudam de um único item, **Iniciar**, para **Pausar**, **Parar** e **Reiniciar**.

A qualquer momento, é possível pausar temporariamente ou parar por completo o Live Unit Testing. Talvez você deseje fazer isso, por exemplo, se estiver no meio de uma refatoração e souber que os testes serão interrompidos por algum tempo. As três opções de menu são:

- **Pausar**, que suspende o Live Unit Testing temporariamente. 
    Quando o Live Unit Testing está em pausa, a visualização de cobertura não é exibida no editor, mas todos os dados coletados são preservados. Para retomar o Live Unit Testing, selecione “Continuar” no menu Live Unit Testing. O Live Unit Testing fará o trabalho necessário para ficar atualizado com todas as edições que foram feitas durante sua pausa e atualizará os glifos de forma adequada. 
- **Parar**, para parar o Live Unit Testing por completo. O Live Unit Testing descarta todos os dados coletados
- **Reiniciar**, que é equivalente a selecionar **Parar** seguido por **Iniciar** no menu **Live Unit Testing**.

##  <a name="viewing-coverage-visualization-in-the-editor-as-you-type"></a>Exibindo a visualização de cobertura no editor durante a digitação

Depois de habilitado, o Live Unit Testing atualiza cada linha de código no editor do Visual Studio para mostrar se o código que está sendo escrito é abrangido por testes de unidade e se os testes que os abrangem são aprovados.  A figura a seguir mostra linhas de código com testes aprovados e não aprovados, bem como linhas de código que não são abrangidas por testes. As linhas decoradas com um "✓" verde são cobertas apenas por testes aprovados, as linhas decoradas com um "🞩" vermelho são cobertas por um ou mais testes com falha e as linhas decoradas por um "" azul não são cobertas por nenhum teste.

  ![Image](./media/lut-codewindow.png)

A visualização de cobertura do Live Unit Testing é atualizada imediatamente conforme o código é modificado no editor de código. Durante o processamento das edições, a visualização é alterada para indicar que os dados não estão atualizados, com a adição de uma imagem de temporizador redondo abaixo dos símbolos de aprovado, não aprovado e não abrangido, como mostra a figura a seguir.

  ![Image](./media/lut-codeupdating.png)
 
## <a name="getting-information-on-successful-or-failed-tests"></a>Obtendo informações sobre testes com êxito ou com falha

Ao focalizar o símbolo de êxito ou de falha na janela de código, é possível ver quantos testes estão atingindo essa linha. Se você clicar no símbolo, poderá ver o status dos testes individuais, como mostra a figura a seguir.
 
  ![Image](./media/lut-failedinfo.png) 

Ao focalizar o teste com falha na dica de ferramenta, ele é expandido para fornecer informações adicionais sobre a falha, conforme mostrado na imagem abaixo. Se você clicar no teste com falha na dica de ferramenta, poderá acessá-lo diretamente.

  ![Image](./media/lut-failedmsg.png) 

## <a name="diagnosing-and-correcting-test-failures"></a>Diagnosticando e corrigindo falhas de teste

No teste com falha, é possível depurar o código do produto com facilidade, fazer edições e continuar desenvolvendo o aplicativo. Como o Live Unit Testing é executado em segundo plano, você não precisa parar e reiniciá-lo durante o ciclo de depuração, edição e continuação.

Por exemplo, a falha de teste mostrada na figura anterior foi causada por uma suposição incorreta no método de teste de que caracteres não alfabéticos retornam `true` quando passados para o método [Char.IsLower](xref:System.Char.IsLower(System.Char)). Depois de corrigirmos o método de teste, descobrimos que todos os testes são aprovados. Enquanto estamos fazendo isso, não precisamos pausar nem parar o Live Unit Testing.

## <a name="live-unit-testing-and-test-explorer"></a>Live Unit Testing e o Gerenciador de Testes

Normalmente, o **Gerenciador de Testes** fornece a interface que permite executar, depurar e analisar os resultados de teste. O Live Unit Testing é integrado ao **Gerenciador de Testes**. Quando o Live Unit Testing não está habilitado ou está parado, o **Gerenciador de Testes** exibe o status dos testes de unidade na última vez que um teste foi executado. Alterações no código-fonte exigem uma nova execução dos testes. Por outro lado, quando o Live Unit Testing está habilitado, o status dos testes de unidade no **Gerenciador de Testes** é atualizado imediatamente. Não é mais necessário executar os testes de unidade explicitamente. 

No entanto, há algumas diferenças entre a execução e atualização automáticas dos resultados de teste do Live Unit Testing e a execução explícita de testes no **Gerenciador de Testes**. Elas incluem:

- A execução ou depuração de testes na janela Gerenciador de Testes executa binários regulares, ao passo que o Live Unit Testing executa binários instrumentados. 
- O Live Unit Testing não cria um novo domínio de aplicativo para executar testes; em vez disso, ele executa testes no domínio padrão. Os testes executados na janela **Gerenciador de Testes** criam um novo domínio de aplicativo.
- O Live Unit Testing executa testes em cada assembly de teste sequencialmente. Se você executar vários testes na janela **Gerenciador de Testes** e o botão **Executar Testes em Paralelo** estiver selecionado, os testes serão executados em paralelo.

## <a name="including-and-excluding-test-projects-and-test-methods"></a>Incluindo e excluindo projetos e métodos de teste

Para soluções com vários projetos de teste, é possível controlar quais projetos e quais métodos individuais em um projeto farão parte do Live Unit Testing. 

Por exemplo, se você tiver uma solução com centenas de projetos de teste, será possível selecionar um conjunto direcionado de projetos de teste para fazer parte do Live Unit Testing. Para selecionar os projetos individuais em testes de unidade, faça o seguinte após a inicialização do Live Unit Testing:

1.  Clique com o botão direito do mouse na solução, no Gerenciador de Soluções e escolha **Testes Dinâmicos**, **Excluir** para excluir toda a solução.
2.  Clique com o botão direito do mouse em cada projeto de teste que você deseja incluir nos testes e escolha **Testes Dinâmicos**, **Incluir**.
 
É possível usar a janela do editor de código para incluir ou excluir métodos de teste individuais. Clique com o botão direito do mouse na assinatura do método de teste na janela do editor de código e selecione **Testes Dinâmicos**, **Incluir** ou **Testes Dinâmicos**, **Excluir**. 

Como alternativa, também é possível aplicar o atributo [<ExcludeFromCodeCoverage>](https://msdn.microsoft.com/library/system.diagnostics.codeanalysis.excludefromcodecoverageattribute.aspx) para excluir, de forma programática, métodos, classes ou estruturas de relatar sua cobertura no Live Unit Testing.

O Live Unit Testing salva o estado de inclusão/exclusão como uma configuração de usuário e a memoriza quando uma solução é fechada e reaberta. 

## <a name="see-also"></a>Consulte também

[Blog do Live Unit Testing](https://go.microsoft.com/fwlink/?linkid=842514)   
[Perguntas frequentes sobre o Live Unit Testing](live-unit-testing-faq.md)    
[Vídeo do Channel 9: Live Unit Testing no Visual Studio 2017](https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T105)


