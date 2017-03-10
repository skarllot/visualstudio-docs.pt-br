---
title: "Exce&#231;&#245;es de solu&#231;&#227;o de problemas: System.InvalidOperationException | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Classe InvalidOperationException"
ms.assetid: db3400e5-62d7-4d65-897d-387e7edcb7cf
caps.latest.revision: 33
caps.handback.revision: 33
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Exce&#231;&#245;es de solu&#231;&#227;o de problemas: System.InvalidOperationException
Um <xref:System.InvalidOperationException?displayProperty=fullName> é lançada quando um método de um objeto é chamado quando o estado do objeto não oferece suporte para a chamada do método. A exceção também é lançada quando um método tenta manipular a interface do usuário do thread de interface do usuário ou por um thread que não é o principal.  
  
> [!IMPORTANT]
>  Porque <xref:System.InvalidOperationException>s pode ser gerada em uma ampla variedade de circunstâncias, é importante ler e entender o <xref:System.Exception.Message%2A> que é exibida no Assistente de exceção.  
  
##  <a name="BKMK_In_this_article"></a> Neste artigo  
 [Um método em execução em um segmento sem interface do usuário atualiza a interface do usuário](#BKMK_A_method_running_on_a_non_UI_thread_updates_the_UI)  
  
 [Uma instrução em um bloco foreach (For Each no Visual Basic) altera a coleção que está iterando](#BKMK_A_statement_in_a_foreach_For_Each_in_Visual_Basic_block_changes_the_collection_it_is_iterating)  
  
 [Uma propriedade Nullable &lt; T &gt; Nulo é convertida em T](#BKMK_A_Nullable_T_that_is_null_is_cast_to_T)  
  
 [Um método System.Linq.Enumerable é chamado em uma coleção vazia](#BKMK_A_System_Linq_Enumerable_method_is_called_on_an_empty_collection)  
  
 [Artigos relacionados](#BKMK_Related_articles)  
  
 Os exemplos de código neste artigo mostram como algumas comuns <xref:System.InvalidOperationException> poderão ocorrer exceções em seu aplicativo. Como lidar com os problemas depende da situação específica. Se a exceção for fatal para a funcionalidade do seu aplicativo, você talvez queira usar um [try... catch](/dotnet/csharp/language-reference/keywords/exception-handling-statements) \([Try... Catch](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement) no Visual Basic\) construção para capturar a exceção e limpar o estado do aplicativo antes de sair. Mas outras <xref:System.InvalidOperationException>s pode ser prevista e evitados. Os exemplos de método revisados mostram algumas dessas técnicas.  
  
##  <a name="BKMK_A_method_running_on_a_non_UI_thread_updates_the_UI"></a> Um método em execução em um segmento sem interface do usuário atualiza a interface do usuário  
 [Causando uma InvalidOperationException com uma atualização da interface do usuário de um thread sem interface do usuário](#BKMK_Causing_an_InvalidOperationException_with_a_UI_update_from_a_non_UI_thread)  **&#124;**  [Evitando InvalidOperationExceptions em threads sem interface do usuário](#BKMK_Avoiding_InvalidOperationExceptions_on_non_UI_threads)  
  
 A maioria das estruturas de aplicativo .NET GUI \(interface gráfica do usuário\), como o Windows Forms e Windows Presentation Foundation \(WPF\), permitem que você acesse objetos de GUI somente do thread que cria e gerencia a interface do usuário \(o **principal** ou **UI** thread\). Um <xref:System.InvalidOperationException> é lançada quando você tenta acessar um elemento de interface do usuário de um thread que não seja o thread da interface do usuário.  
  
###  <a name="BKMK_Causing_an_InvalidOperationException_with_a_UI_update_from_a_non_UI_thread"></a> Causando uma InvalidOperationException com uma atualização da interface do usuário de um thread sem interface do usuário  
  
> [!NOTE]
>  Os exemplos a seguir usam o [Task\-based Asynchronous Pattern \(TAP\)](../Topic/Task-based%20Asynchronous%20Pattern%20\(TAP\).md) criar threads sem interface do usuário. No entanto, os exemplos também são relevantes para todos os .NET [Asynchronous Programming Patterns](../Topic/Asynchronous%20Programming%20Patterns.md).  
  
 Nestes exemplos, o `ThreadsExampleBtn_Click` chamadas de manipulador de eventos de `DoSomeWork` método duas vezes. A primeira chamada para o método \(`DoSomeWork(20);` é executada simultaneamente e tiver êxito. Mas a segunda chamada \(`Task.Run( () => { DoSomeWork(1000);});`\) é executado em um thread do aplicativo em [pool de threads](http://msdn.microsoft.com/en-us/library/system.threading.threadpool.aspx). Porque essa chamada tenta atualizar a interface do usuário de um thread sem interface do usuário, a instrução gera uma <xref:System.InvalidOperationException>  
  
 **Aplicativos WPF e Store**  
  
> [!NOTE]
>  Em aplicativos de telefone da loja, um <xref:System.Exception> será lançado em vez do mais específico <xref:System.InvalidOperationException>.  
  
 **Mensagens de exceção:**  
  
|||  
|-|-|  
|Aplicativos WPF|Informações adicionais: O thread de chamada não pode acessar este objeto porque possui um thread diferente.|  
|Aplicativos da Store|Informações adicionais: O aplicativo chamou uma interface que foi tratada por um thread diferente. \(Exceção de HRESULT: 0x8001010E \(RPC\_E\_WRONG\_THREAD\)\)|  
  
```c#  
private async void ThreadsExampleBtn_Click(object sender, RoutedEventArgs e) { TextBox1.Text = String.Empty; TextBox1.Text = "Simulating work on UI thread.\n"; DoSomeWork(20); TextBox1.Text += "Simulating work on non-UI thread.\n"; await Task.Run(() => DoSomeWork(1000)); TextBox1.Text += "ThreadsExampleBtn_Click completes. "; } private void DoSomeWork(int msOfWork) { // simulate work var endTime = DateTime.Now.AddMilliseconds(msOfWork); while (DateTime.Now < endTime) { // spin }; // report completion var msg = String.Format("Some work completed in {0} ms on UI thread. \n", msOfWork); TextBox1.Text += msg; }  
```  
  
 **Aplicativos do Windows Forms**  
  
 **Mensagem de exceção:**  
  
-   Informações adicionais: operação entre threads inválida: controle 'TextBox1' acessado de um thread diferente do thread que foi criado.  
  
```c#  
private async void ThreadsExampleBtn_Click(object sender, EventArgs e) { TextBox1.Text = String.Empty; var tbLinesList = new List<string>() {"Simulating work on UI thread."}; TextBox1.Lines = tbLinesList.ToArray(); DoSomeWork(20, tbLinesList); tbLinesList.Add("Simulating work on non-UI thread."); TextBox1.Lines = tbLinesList.ToArray(); await Task.Run(() => DoSomeWork(1000, tbLinesList)); tbLinesList.Add("ThreadsExampleBtn_Click completes."); TextBox1.Lines = tbLinesList.ToArray(); } private void DoSomeWork(int msOfWork, List<string> tbLinesList) { // simulate work var endTime = DateTime.Now.AddMilliseconds(msOfWork); while (DateTime.Now < endTime) { }; { // spin }; // report completion var msg = String.Format("Some work completed in {0} ms on UI thread. \n", msOfWork); tbLinesList.Add(msg); TextBox1.Lines = tbLinesList.ToArray(); }  
```  
  
 ![Back to top](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Neste artigo](#BKMK_In_this_article) ![In this section](../misc/media/pcs_backtotopmid.png "PCS\_BackToTopMid") [Um método em execução em um segmento sem interface do usuário atualiza a interface do usuário](#BKMK_A_method_running_on_a_non_UI_thread_updates_the_UI)  
  
###  <a name="BKMK_Avoiding_InvalidOperationExceptions_on_non_UI_threads"></a> Evitando InvalidOperationExceptions em threads sem interface do usuário  
 Estruturas de interface do usuário Windows implementam um *dispatcher* padrão que inclui um método para verificar se uma chamada a um membro de um elemento de interface do usuário está sendo executada no thread da interface do usuário e outros métodos para agendar a chamada no thread da interface do usuário.  
  
 **Aplicativos WPF**  
  
 Em aplicativos WPF, use um dos <xref:System.Windows.Threading.Dispatcher.Invoke%2A?displayProperty=fullName> métodos para executar um delegado no thread da interface do usuário. Se necessário, use o <xref:System.Windows.Threading.Dispatcher.CheckAccess%2A?displayProperty=fullName> método para determinar se um método está sendo executado em um segmento sem interface do usuário.  
  
```c#  
private void DoSomeWork(int msOfWork) { var endTime = DateTime.Now.AddMilliseconds(msOfWork); while (DateTime.Now < endTime) { // spin }; // report completion var msgFormat = "Some work completed in {0} ms on {1}UI thread.\n"; var msg = String.Empty; if (TextBox1.Dispatcher.CheckAccess()) { msg = String.Format(msgFormat, msOfWork, String.Empty); TextBox1.Text += msg; } else { msg = String.Format(msgFormat, msOfWork, "non-"); Action act = ()=> {TextBox1.Text += msg;}; TextBox1.Dispatcher.Invoke(act); } }  
  
```  
  
 **Aplicativos do Windows Forms**  
  
 Em aplicativos do Windows Form, use o <xref:System.Windows.Forms.Control.Invoke%2A?displayProperty=fullName> método para executar um delegado que atualiza o thread da interface do usuário. Se necessário, use o <xref:System.Windows.Forms.Control.InvokeRequired%2A?displayProperty=fullName> para determinar se um método está sendo executado em um segmento sem interface do usuário.  
  
```c#  
private void DoSomeWork(int msOfWork, List<string> tbLinesList) { // simulate work var endTime = DateTime.Now.AddMilliseconds(msOfWork); while (DateTime.Now < endTime) { // spin }; // report completion var msgFormat = "Some work completed in {0} ms on {1}UI thread.\n"; var msg = String.Empty; if (TextBox1.InvokeRequired) { msg = String.Format(msgFormat, msOfWork, "non-"); tbLinesList.Add(msg); Action act = () => TextBox1.Lines = tbLinesList.ToArray(); TextBox1.Invoke( act ); } else { msg = String.Format(msgFormat, msOfWork, String.Empty); tbLinesList.Add(msg); TextBox1.Lines = tbLinesList.ToArray(); } }  
```  
  
 **Aplicativos da Store**  
  
 Em aplicativos de armazenamento, use o <xref:Windows.UI.Core.CoreDispatcher.RunAsync%2A?displayProperty=fullName> método para executar um delegado que atualiza o thread da interface do usuário. Se necessário, use o <xref:Windows.UI.Core.CoreDispatcher.HasThreadAccess%2A> para determinar se um método está sendo executado em um segmento sem interface do usuário.  
  
```c#  
private void DoSomeWork(int msOfWork) { // simulate work var endTime = DateTime.Now.AddMilliseconds(msOfWork); while (DateTime.Now < endTime) { // spin }; // report completion var msgFormat = "Some work completed in {0} ms on {1}UI thread.\n"; var msg = String.Empty; if (TextBox1.Dispatcher.HasThreadAccess) { msg = String.Format(msgFormat, msOfWork, String.Empty); TextBox1.Text += msg; } else { msg = String.Format(msgFormat, msOfWork, "non-"); TextBox1.Dispatcher.RunAsync(Windows.UI.Core.CoreDispatcherPriority.Normal,()=> {TextBox1.Text += msg;}); } }  
```  
  
 ![Back to top](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Neste artigo](#BKMK_In_this_article) ![In this section](../misc/media/pcs_backtotopmid.png "PCS\_BackToTopMid") [Um método em execução em um segmento sem interface do usuário atualiza a interface do usuário](#BKMK_A_method_running_on_a_non_UI_thread_updates_the_UI)  
  
##  <a name="BKMK_A_statement_in_a_foreach_For_Each_in_Visual_Basic_block_changes_the_collection_it_is_iterating"></a> Uma instrução em um bloco foreach \(For Each no Visual Basic\) altera a coleção que está iterando  
 [Causando uma InvalidOperationException com foreach](#BKMK_Causing_an_InvalidOperationException_with_foreach)  **&#124;**  [Evitando InvalidOperationExceptions em loops](#BKMK_Avoiding_InvalidOperationExceptions_in_loops)  
  
 Um [foreach](/dotnet/csharp/language-reference/keywords/foreach-in) instrução \([para cada](/dotnet/visual-basic/language-reference/statements/for-each-next-statement) no Visual Basic\) repete um grupo de instruções inseridos para cada elemento em uma matriz ou coleção que implementa o <xref:System.Collections.IEnumerable?displayProperty=fullName> ou <xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName> interface. O `foreach` instrução é usada para iterar pela coleção para ler e modificar os elementos, mas ele não pode ser usado para adicionar ou remover itens da coleção. Um <xref:System.InvalidOperationException> é lançada se você adicionar ou remove itens da coleção de origem em uma instrução foreach.  
  
###  <a name="BKMK_Causing_an_InvalidOperationException_with_foreach"></a> Causando uma InvalidOperationException com foreach  
 Neste exemplo, um <xref:System.InvalidOperationException> é gerada quando o `numList.Add(5);` declaração tenta modificar lista no bloco foreach.  
  
 **Mensagem de exceção:**  
  
-   Informações adicionais: a coleção foi modificada; não pode executar a operação de enumeração.  
  
<CodeContentPlaceHolder>5</CodeContentPlaceHolder>  
 ![Back to top](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Neste artigo](#BKMK_In_this_article) ![In this section](../misc/media/pcs_backtotopmid.png "PCS\_BackToTopMid") [Uma instrução em um bloco foreach (For Each no Visual Basic) altera a coleção que está iterando](#BKMK_A_statement_in_a_foreach_For_Each_in_Visual_Basic_block_changes_the_collection_it_is_iterating)  
  
###  <a name="BKMK_Avoiding_InvalidOperationExceptions_in_loops"></a> Evitando InvalidOperationExceptions em loops  
  
> [!IMPORTANT]
>  Adicionando ou removendo elementos de uma lista enquanto você está iterando a coleção pode ter não intencionais e difícil de prever os efeitos colaterais. Se possível, você deve mover a operação para fora da iteração.  
  
<CodeContentPlaceHolder>6</CodeContentPlaceHolder>  
 Se sua situação exigir que você adicionar ou remover elementos de uma lista que itera uma coleção, use um [para](/dotnet/csharp/language-reference/keywords/for) \([para](/dotnet/visual-basic/language-reference/statements/for-next-statement) no Visual Basic\) loop:  
  
<CodeContentPlaceHolder>7</CodeContentPlaceHolder>  
 ![Back to top](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Neste artigo](#BKMK_In_this_article) ![In this section](../misc/media/pcs_backtotopmid.png "PCS\_BackToTopMid") [Uma instrução em um bloco foreach (For Each no Visual Basic) altera a coleção que está iterando](#BKMK_A_statement_in_a_foreach_For_Each_in_Visual_Basic_block_changes_the_collection_it_is_iterating)  
  
##  <a name="BKMK_A_Nullable_T_that_is_null_is_cast_to_T"></a> Uma propriedade Nullable \< T \> Nulo é convertida em T  
 [Causando uma InvalidOperationException com uma conversão inválida](#BKMK_Causing_an_InvalidOperationException_with_an_invalid_cast)  **&#124;**  [Evitando InvalidOperationException de uma conversão inválida](#BKMK_Avoiding_InvalidOperationException_from_a_bad_cast)  
  
 Se você converter um <xref:System.Nullable%601> estrutura `null` \(`Nothing` no Visual Basic\) para seu tipo subjacente, um <xref:System.InvalidOperationException> exceção é lançada.  
  
###  <a name="BKMK_Causing_an_InvalidOperationException_with_an_invalid_cast"></a> Causando uma InvalidOperationException com uma conversão inválida  
 Nesse método, um <xref:System.InvalidOperationException> é lançada quando o método Select projeta um elemento nulo de dbQueryResults em um int.  
  
 **Mensagem de exceção:**  
  
-   Informações adicionais: o objeto nulo deve ter um valor.  
  
```c#  
private void MapQueryResults() { var dbQueryResults = new int?[] { 1, 2, null, 4 }; var ormMap = dbQueryResults.Select(nullableInt => (int)nullableInt); //display map list foreach (var num in ormMap) { Console.Write("{0} ", num); } Console.WriteLine(); }  
  
```  
  
 ![Back to top](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Neste artigo](#BKMK_In_this_article) ![In this section](../misc/media/pcs_backtotopmid.png "PCS\_BackToTopMid") [Uma propriedade Nullable &lt; T &gt; Nulo é convertida em T](#BKMK_A_Nullable_T_that_is_null_is_cast_to_T)  
  
###  <a name="BKMK_Avoiding_InvalidOperationException_from_a_bad_cast"></a> Evitando InvalidOperationException de uma conversão inválida  
 Para evitar <xref:System.InvalidOperationException>:  
  
-   Use o <xref:System.Nullable%601.HasValue%2A?displayProperty=fullName> propriedade para selecionar apenas os elementos que não são nulos.  
  
-   Use um dos sobrecarregados <xref:System.Nullable%601.GetValueOrDefault%2A?displayProperty=fullName> métodos para fornecer um valor padrão para um item nulo.  
  
 **Nullable \< T \>. Exemplo de HasValue**  
  
```c#  
private void MapQueryResults() { var dbQueryResults = new int?[] { 1, 2, null, 4 }; var ormMap = dbQueryResults .Where(nulllableInt => nulllableInt.HasValue) .Select(num => (int)num); //display map list foreach (var num in ormMap) { Console.Write("{0} ", num); } Console.WriteLine(); // handle nulls Console.WriteLine("{0} nulls encountered in dbQueryResults", dbQueryResults.Where(nullableInt => !nullableInt.HasValue).Count()); }  
```  
  
 **Nullable \< T \>. Exemplo de GetValueOrDefault**  
  
 Neste exemplo, usamos <xref:System.Nullable%601.GetValueOrDefault%28%600%29> para especificar um padrão que está fora dos valores esperados retornados por `dbQueryResults`.  
  
```c#  
private void MapQueryResults() { var dbQueryResults = new int?[] { 1, 2, null, 4 }; var nullFlag = int.MinValue; var ormMap = dbQueryResults.Select(nullableInt => nullableInt.GetValueOrDefault(nullFlag)); // handle nulls Console.WriteLine("'{0}' indicates a null database value.", nullFlag); foreach (var num in ormMap) { Console.Write("{0} ", num); } Console.WriteLine(); }  
  
```  
  
 ![Back to top](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Neste artigo](#BKMK_In_this_article) ![In this section](../misc/media/pcs_backtotopmid.png "PCS\_BackToTopMid") [Uma propriedade Nullable &lt; T &gt; Nulo é convertida em T](#BKMK_A_Nullable_T_that_is_null_is_cast_to_T)  
  
##  <a name="BKMK_A_System_Linq_Enumerable_method_is_called_on_an_empty_collection"></a> Um método System.Linq.Enumerable é chamado em uma coleção vazia  
 O <xref:System.Linq.Enumerable> métodos <xref:System.Linq.Enumerable.Aggregate%2A>, <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Last%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>, <xref:System.Linq.Enumerable.First%2A>, <xref:System.Linq.Enumerable.Single%2A>, e <xref:System.Linq.Enumerable.SingleOrDefault%2A> executar operações em uma sequência e retornar um único resultado.  
  
 Algumas sobrecargas desses métodos lançar um <xref:System.InvalidOperationException> uma exceção quando a sequência está vazia \(outras sobrecargas retornam `null` \(`Nothing` no Visual Basic\).<xref:System.Linq.Enumerable.SingleOrDefault%2A> também gera <xref:System.InvalidOperationException> quando a sequência contém mais de um elemento.  
  
> [!TIP]
>  A maioria do <xref:System.Linq.Enumerable> métodos discutidos nesta seção são sobrecarregados. Certifique\-se de que entender o comportamento da sobrecarga que você escolher.  
  
 **Mensagens de exceção:**  
  
 [Agregação, métodos de média, Last, Max e Min](#BKMK_Aggregate_Average_Last_Max_and_Min_methods)  **&#124;**  [Métodos First e FirstOrDefault](#BKMK_First_and_FirstOrDefault_methods)  **&#124;**  [Métodos Single e SingleOrDefault](#BKMK_Single_and_SingleOrDefault_methods)  
  
###  <a name="BKMK_Aggregate_Average_Last_Max_and_Min_methods"></a> Agregação, métodos de média, Last, Max e Min  
  
-   Informações adicionais: sequência não contém elementos  
  
 **Causando uma InvalidOperationException com média**  
  
 Nesse exemplo, o seguinte método lança um <xref:System.InvalidOperationException> quando ele chama o <xref:System.Linq.Enumerable.Average%2A> método porque a expressão Linq retorna uma seqüência que não contém elementos que são maiores do que 4.  
  
```c#  
private void FindAverageOfNumbersGreaterThan4() { var dbQueryResults = new[] { 1, 2, 3, 4 }; var avg = dbQueryResults.Where(num => num > 4).Average(); Console.WriteLine("The average value numbers greater than 4 in the returned records is {0}", avg); }  
```  
  
 Quando você usa um desses métodos sem verificar se há uma sequência vazia, está implicitamente supondo que a sequência não está vazia e uma sequência vazia é uma ocorrência inesperada. Capturar ou gerar a exceção é apropriado quando você assumir que a seqüência será vazio.  
  
 **Evitando InvalidOperationException causado por uma sequência vazia**  
  
 Use um dos <xref:System.Linq.Enumerable.Any%2A?displayProperty=fullName> métodos para verificar se a seqüência for vazia.  
  
> [!TIP]
>  Usando <xref:System.Linq.Enumerable.Any%2A> pode melhorar o desempenho da verificação se a sequência de média pode conter um grande número de elementos ou se a operação que gera a sequência for cara.  
  
```c#  
private void FindAverageOfNumbersGreaterThan4() { var dbQueryResults = new[] { 1, 2, 3, 4 }; var moreThan4 = dbQueryResults.Where(num => num > 4); if(moreThan4.Any()) { var msgFormat = "The average value numbers greater than 4 in the returned records is {0}"; Console.WriteLine(msgFormat, moreThan4.Average()); } else { // handle empty collection Console.WriteLine("There are no values greater than 4 in the ecords."); } }  
  
```  
  
 ![Back to top](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Neste artigo](#BKMK_In_this_article) ![In this section](../misc/media/pcs_backtotopmid.png "PCS\_BackToTopMid") [Um método System.Linq.Enumerable é chamado em uma coleção vazia](#BKMK_A_System_Linq_Enumerable_method_is_called_on_an_empty_collection)  
  
###  <a name="BKMK_First_and_FirstOrDefault_methods"></a> Métodos First e FirstOrDefault  
 <xref:System.Linq.Enumerable.First%2A> Retorna o primeiro item em uma sequência ou gera uma <xref:System.InvalidOperationException> se a seqüência for vazia.  Você pode chamar o <xref:System.Linq.Enumerable.FirstOrDefault%2A> método em vez de <xref:System.Linq.Enumerable.First%2A> para retornar um especificado ou valor em vez de lançar a exceção padrão.  
  
> [!NOTE]
>  No .NET Framework, os tipos têm um conceito de valores padrão. Por exemplo, para qualquer referência tipo o valor padrão é null, e para um tipo inteiro é zero. Consulte [Tabela de valores padrão](/dotnet/csharp/language-reference/keywords/default-values-table).  
  
 **Causando uma InvalidOperationException com First**  
  
 O <xref:System.Linq.Enumerable.First%2A> é um método de otimização que retorna o primeiro elemento em uma sequência que satisfazem uma condição especificada. Se um elemento que satisfaça a condição não for encontrado, os métodos gerarão um <xref:System.InvalidOperationException> exceção.  
  
 Neste exemplo, o `First` método lança a exceção porque `dbQueryResults` não contém um elemento que é maior do que 4.  
  
 **Mensagem de exceção:**  
  
-   Informações adicionais: sequência não contém elementos correspondentes  
  
```c#  
private void FindANumbersGreaterThan4() { var dbQueryResults = new[] { 1, 2, 3, 4 }; var firstNum = dbQueryResults.First(n=> n > 4); var msgFormat = "{0} is an element of dbQueryResults that is greater than 4"; Console.WriteLine(msgFormat, firstNum); }  
  
```  
  
 **Evitando uma exceção com FirstOrDefault**  
  
 Você pode usar um o   <xref:System.Linq.Enumerable.FirstOrDefault%2A> métodos no lugar de  <xref:System.Linq.Enumerable.First%2A> para verificar se o `firstNum` seqüência contém pelo menos um elemento. Se a consulta não encontrar um elemento que satisfaça a condição, ele retorna um especificado ou valor padrão. Você pode verificar o valor retornado para determinar se os elementos forem encontrados.  
  
> [!NOTE]
>  Usando <xref:System.Linq.Enumerable.FirstOrDefault%2A> pode ser mais difícil de implementar se o valor padrão do tipo é um elemento válido na sequência.  
  
```c#  
private void FindANumbersGreaterThan4() { var dbQueryResults = new[] { 1, 2, 3, 4 }; // default(object) == null var firstNum = dbQueryResults.FirstOrDefault(n => n > 4); if (firstNum != 0) { var msgFormat = "{0} is an element of dbQueryResults that is greater than 4"; Console.WriteLine(msgFormat, firstNum); } else { // handle default case Console.WriteLine("No element of dbQueryResults is greater than 4."); } }  
  
```  
  
 ![Back to top](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Neste artigo](#BKMK_In_this_article) ![In this section](../misc/media/pcs_backtotopmid.png "PCS\_BackToTopMid") [Um método System.Linq.Enumerable é chamado em uma coleção vazia](#BKMK_A_System_Linq_Enumerable_method_is_called_on_an_empty_collection)  
  
###  <a name="BKMK_Single_and_SingleOrDefault_methods"></a> Métodos Single e SingleOrDefault  
 O <xref:System.Linq.Enumerable.Single%2A?displayProperty=fullName> métodos retornam o único elemento de uma seqüência ou o único elemento de uma sequência que atende a um teste especificado.  
  
 Se não há nenhum elemento na sequência ou há mais de um elemento em t sequência, o método gerará uma <xref:System.InvalidOperationException> exceção.  
  
 Você pode usar <xref:System.Linq.Enumerable.SingleOrDefault%2A> para retornar um especificado ou valor em vez de lançar a exceção quando a sequência não contém elementos padrão. No entanto, <xref:System.Linq.Enumerable.SingleOrDefault%2A> ainda lança um <xref:System.InvalidOperationException> quando a sequência contém mais de um elemento que corresponde ao predicado da seleção.  
  
> [!NOTE]
>  No .NET Framework, os tipos têm um conceito de valores padrão. Por exemplo, para qualquer referência tipo o valor padrão é null, e para um tipo inteiro é zero. Consulte [Tabela de valores padrão](/dotnet/csharp/language-reference/keywords/default-values-table).  
  
 **Causando InvalidOperationExceptions Single**  
  
 Neste exemplo, `singleObject` lança um <xref:System.InvalidOperationException> porque `dbQueryResults` não contém um elemento maior que 4.  
  
 **Mensagem de exceção:**  
  
-   Informações adicionais: sequência não contém elementos correspondentes  
  
```c#  
private void FindTheOnlyNumberGreaterThan4() { var dbQueryResults = new[] { (object)1, (object)2, (object)3, (object)4 }; var singleObject = dbQueryResults.Single(obj => (int)obj > 4); // display results var msgFormat = "{0} is the only element of dbQueryResults that is greater than 4"; Console.WriteLine(msgFormat, singleObject); }  
  
```  
  
 **Causando InvalidOperationExceptions com Single ou SingleOrDefault**  
  
 Neste exemplo, `singleObject` lança um <xref:System.InvalidOperationException> porque `dbQueryResults` contém mais de um elemento maior que 2.  
  
 **Mensagem de exceção:**  
  
-   Informações adicionais: sequência contém mais de um elemento correspondente  
  
```c#  
private void FindTheOnlyNumberGreaterThan2() { var dbQueryResults = new[] { (object)1, (object)2, (object)3, (object)4 }; var singleObject = dbQueryResults.SingleOrDefault(obj => (int)obj > 2); if (singleObject != null) { var msgFormat = "{0} is the only element of dbQueryResults that is greater than 2"; Console.WriteLine(msgFormat, singleObject); } else { // handle empty collection Console.WriteLine("No element of dbQueryResults is greater than 2."); } }  
  
```  
  
 **Evitando InvalidOperationExceptions com Single**  
  
 Usando <xref:System.Linq.Enumerable.Single%2A> e <xref:System.Linq.Enumerable.SingleOrDefault%2A> também serve como documentação de suas intenções.<xref:System.Linq.Enumerable.Single%2A> implica fortemente que você espera que um e somente um resultado a ser retornado da condição.<xref:System.Linq.Enumerable.SingleOrDefault%2A> declara que você espera um ou zero resultados, mas não mais. Quando essas condições são inválidas, gerar ou capturar a <xref:System.InvalidOperationException> é apropriado. No entanto, se você espera que condições inválidas ocorram com alguma frequência, considere usar outros <xref:System.Linq.Enumerable> métodos, tais como <xref:System.Linq.Enumerable.First%2A> ou <xref:System.Linq.Enumerable.Where%2A>, para gerar os resultados.  
  
 Durante o desenvolvimento, você pode usar um dos <xref:System.Diagnostics.Debug.Assert%2A> métodos para verificar suas suposições. Neste exemplo, o código realçado faz com que o depurador interrompa e exibe uma caixa de diálogo assert durante o desenvolvimento. A declaração é removida no código da versão e quaisquer <xref:System.Linq.Enumerable.Single%2A> lançará se os resultados são inválidos.  
  
> [!NOTE]
>  Usando <xref:System.Linq.Enumerable.Take%2A> e definindo seu `count` parâmetro para 2 limita a sequência retornada a no máximo dois elementos. Esta sequência inclui todas as ocorrências que você precisa verificar \(0, 1 e elementos de mais de 1\) e pode melhorar o desempenho da verificação de quando a sequência contiver um grande número de elementos ou se a operação que gera a sequência for cara.  
  
```c#  
private void FindTheOnlyNumberGreaterThan4() { var dbQueryResults = new[] { (object)1, (object)2, (object)3, (object)4 }; var moreThan4 = dbQueryResults.Where(obj => (int)obj > 4).Take(2); System.Diagnostics.Debug.Assert(moreThan4.Count() == 1,String.Format("moreThan4.Count() == 1; Actual count: {0}", moreThan4.Count())); // do not handle exceptions in release code Console.WriteLine("{0} is the only element of dbQueryResults that is greater than 4", moreThan4.Single()); }  
  
```  
  
 Se você quiser evitar a exceção, mas ainda manipular estados inválidos no código da versão, você pode modificar a técnica descrita acima. Neste exemplo, o método responde ao número de elementos retornados por `moreThan2` na instrução switch.  
  
```c#  
private void FindTheOnlyNumberGreaterThan2() { var dbQueryResults = new[] { (object)1, (object)2, (object)3, (object)4 }; var moreThan2 = dbQueryResults.TakeWhile(obj => (int)obj > 2).Take(2); switch(moreThan2.Count()) { case 1: // success var msgFormat = "{0} is the only element of dbQueryResults that is greater than 2"; Console.WriteLine(msgFormat, moreThan2.Single()); break; case 0: // handle empty collection Console.WriteLine("No element of the dbQueryResults are greater than 4."); break; default: // count > 1 // handle more than one element Console.WriteLine("More than one element of dbQueryResults is greater than 4"); break; } }  
  
```  
  
 ![Back to top](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Neste artigo](#BKMK_In_this_article) ![In this section](../misc/media/pcs_backtotopmid.png "PCS\_BackToTopMid") [Um método System.Linq.Enumerable é chamado em uma coleção vazia](#BKMK_A_System_Linq_Enumerable_method_is_called_on_an_empty_collection)  
  
##  <a name="BKMK_Related_articles"></a> Artigos relacionados  
 [Diretrizes de design para exceções \(diretrizes de Design do .NET Framework\)](http://msdn.microsoft.com/library/ms229014)  
  
 [Manipulando e lançando exceções \(Fundamentos de aplicativo do .NET Framework\)](http://msdn.microsoft.com/library/5b2yeyab)  
  
 [Como: receber notificações de exceções de primeira Chance \(guia de desenvolvimento do .NET Framework\)](http://msdn.microsoft.com/library/Dd997368)  
  
 [Como: manipular exceções em uma consulta PLINQ \(guia de desenvolvimento do .NET Framework\)](http://msdn.microsoft.com/library/Dd460712)  
  
 [Exceções em Threads gerenciados \(guia de desenvolvimento do .NET Framework\)](http://msdn.microsoft.com/library/ms228965)  
  
 [Exceções e manipulação de exceções \(Guia de Programação em C\#\)](http://msdn.microsoft.com/library/ms173160)  
  
 [Instruções para manipulação de exceções \(Referência de C\#\)](http://msdn.microsoft.com/library/s7fekhdy)  
  
 [Instrução Try...Catch...Finally \(Visual Basic\)](http://msdn.microsoft.com/library/fk6t46tz)  
  
 [Tratamento de exceções \(F\#\)](http://msdn.microsoft.com/library/Dd233223)  
  
 [Exceções em C\+\+\/CLI](http://msdn.microsoft.com/library/Hh875008)  
  
 [Tratamento de exceções \(biblioteca de tarefas paralelas\)](http://msdn.microsoft.com/library/Dd997415)  
  
 [Tratamento de exceções \(depuração\)](http://msdn.microsoft.com/library/x85tt0dd)  
  
 [Passo a passo: Manipulando uma exceção de simultaneidade \(como acessar dados no Visual Studio\)](http://msdn.microsoft.com/library/ms171936)  
  
 [Como: manipular erros e exceções que ocorrem com ligação de dados \(Windows Forms\)](http://msdn.microsoft.com/library/k26k86tb)  
  
 [Tratamento de exceções em aplicativos de rede \(XAML\) \(Windows\)](http://msdn.microsoft.com/library/Dn263240)  
  
 ![Back to top](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Neste artigo](#BKMK_In_this_article)