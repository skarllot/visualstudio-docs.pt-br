---
title: "Instru&#231;&#245;es passo a passo: analisando c&#243;digo gerenciado em busca de defeitos de c&#243;digo | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "análise de código, instruções passo a passo"
  - "código gerenciado, analisando"
  - "ferramenta de análise de código, instruções passo a passo"
ms.assetid: 22b99f49-1924-4fb5-a421-c8b23e5d5cd4
caps.latest.revision: 45
caps.handback.revision: 45
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Instru&#231;&#245;es passo a passo: analisando c&#243;digo gerenciado em busca de defeitos de c&#243;digo
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Neste passo a passo, você pode analisar um projeto para defeitos em código gerenciado usando a ferramenta de análise de código.  
  
 Este passo a passo guiará você pelo processo de uso da análise de código para analisar seus assemblies de código gerenciado do .NET para conformidade com as diretrizes de Design do Microsoft .NET Framework.  
  
 Neste passo a passo, você:  
  
-   Analisar e corrigir avisos de defeitos de código.  
  
## <a name="prerequisites"></a>Pré-requisitos  
  
-   [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)].  
  
## <a name="create-a-class-library"></a>Criar uma biblioteca de classe  
  
#### <a name="to-create-a-class-library"></a>Para criar uma biblioteca de classe  
  
1.  Sobre o **arquivo** menu de [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)], clique em **novo** e, em seguida, clique em **projeto**.  
  
2.  No **novo projeto** caixa de diálogo **tipos de projeto**, clique em **Visual C#**.  
  
3.  Em **modelos**, selecione **biblioteca de classes**.  
  
4.  No **nome** caixa de texto, digite **CodeAnalysisManagedDemo** e, em seguida, clique em **OK**.  
  
5.  Depois que o projeto é criado, abra o arquivo Class1. cs.  
  
6.  Substitua o texto existente em Class1. cs com o código a seguir:  
  
     `//CodeAnalysisManagedDemo //Class1.cs using System;  namespace testCode {          public class demo : Exception     {                  public static void Initialize(int size) { }         protected static readonly int _item;         public static int item { get { return _item; } }     } }`  
  
7.  Salve o arquivo Class1. cs.  
  
## <a name="analyze-the-project"></a>Analise o projeto  
  
#### <a name="to-analyze-a-managed-project-for-code-defects"></a>Para analisar um projeto para defeitos em código gerenciado  
  
1.  Selecione o projeto CodeAnalysisManagedDemo no **Solution Explorer**.  
  
2.  Sobre o **projeto** menu, clique em **propriedades**.  
  
     A página de propriedades CodeAnalysisManagedDemo é exibida.  
  
3.  Clique em **CodeAnalysis**.  
  
4.  Verifique se  **Enable Code Analysis na compilação (define a constante CODE_ANALYSIS**) é verificada.  
  
5.  Do **executar esse conjunto de regras** lista suspensa, selecione **todas as regras do Microsoft**.  
  
6.  Sobre o **arquivo** menu, clique em **Salvar itens selecionados**, e, em seguida, feche as páginas de propriedades ManagedDemo.  
  
7.  Sobre o **criar** menu, clique em **ManagedDemo criar**.  
  
     Os avisos de compilação de projeto CodeAnalysisManagedDemo são relatados no **da análise de código** e **saída** windows.  
  
     Se o **da análise de código** janela não aparecerem, no **Analisar** menu, escolha **Windows** e **Escolha Análise de código**.  
  
## <a name="correct-the-code-analysis-issues"></a>Corrija os problemas de análise de código  
  
#### <a name="to-correct-code-analysis-rule-violations"></a>Para corrigir violações de regra de análise de código  
  
1.  Sobre o **exibição** menu, clique em **lista de erros**.  
  
     Dependendo do perfil de desenvolvedor que você escolheu, talvez você precise aponte para **outras janelas** sobre o **exibição** menu e clique **Error List**.  
  
2.  Em **Solution Explorer**, clique em **Mostrar todos os arquivos**.  
  
3.  Em seguida, expanda o nó de propriedades e, em seguida, abra o arquivo AssemblyInfo.cs.  
  
4.  Use o seguinte para corrigir avisos:  
  
-   [CA1014: Marcar assemblies com CLSCompliantAttribute](../code-quality/ca1014-mark-assemblies-with-clscompliantattribute.md): Microsoft.Design: 'demonstração' deve ser marcada com CLSCompliantAttribute e seu valor deve ser true.  
  
    -   Adicione o código `using``System;` ao arquivo AssemblyInfo.cs.  
  
         Em seguida, adicione o código `[assembly: CLSCompliant(true)]` ao final do arquivo AssemblyInfo.cs.  
  
         Recompile o projeto.  
  
-   [CA1032: Implementar construtores de exceção padrão](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft.Design: Adicione o seguinte construtor para essa classe: demo(String) pública  
  
    -   Adicione o construtor `public demo (String s) : base(s) { }` à classe `demo`.  
  
-   [CA1032: Implementar construtores de exceção padrão](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft.Design: Adicione o seguinte construtor para essa classe: demonstração pública (String, exceção)  
  
    -   Adicione o construtor `public demo (String s, Exception e) : base(s, e) { }` à classe `demo`.  
  
-   [CA1032: Implementar construtores de exceção padrão](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft.Design: Adicione o seguinte construtor para essa classe: protegido demonstração (SerializationInfo, StreamingContext)  
  
    -   Adicione o código `using System.Runtime.Serialization;` para o início do arquivo Class1. cs.  
  
         Em seguida, adicione o construtor `protected demo (SerializationInfo info, StreamingContext context) : base(info, context) { } to the class demo.`  
  
         Recompile o projeto.  
  
-   [CA1032: Implementar construtores de exceção padrão](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft.Design: Adicione o seguinte construtor para essa classe: demo() pública  
  
    -   Adicione o construtor `public demo () : base() { }` à classe `demo`**.**  
  
         Recompile o projeto.  
  
-   [CA1709: Os identificadores devem ter maiusculas e minúsculas corretamente](../code-quality/ca1709-identifiers-should-be-cased-correctly.md): Microsoft.Naming: corrigir as maiusculas e minúsculas do nome do namespace 'testCode' alterando-a 'TestCode'.  
  
    -   Alterar as maiusculas e minúsculas do namespace `testCode` para `TestCode`.  
  
-   [CA1709: Os identificadores devem ter maiusculas e minúsculas corretamente](../code-quality/ca1709-identifiers-should-be-cased-correctly.md): Microsoft.Naming: Corrigir maiusculas e minúsculas de demonstração' nome do tipo' alterando-a para "Demonstração".  
  
    -   Alterar o nome do membro `Demo`.  
  
-   [CA1709: Os identificadores devem ter maiusculas e minúsculas corretamente](../code-quality/ca1709-identifiers-should-be-cased-correctly.md): Microsoft.Naming: corrigir as maiusculas e minúsculas do item' nome do membro' alterando-a para 'Item'.  
  
    -   Alterar o nome do membro `Item`.  
  
-   [CA1710: Os identificadores devem ter sufixo correto](../Topic/CA1710:%20Identifiers%20should%20have%20correct%20suffix.md): Microsoft.Naming: Renomear 'testCode.demo' para terminar em 'Exceção'.  
  
    -   Alterar o nome da classe e seus construtores para `DemoException`.  
  
-   [CA2210: Os Assemblies devem ter nomes fortes válidos](../Topic/CA2210:%20Assemblies%20should%20have%20valid%20strong%20names.md): assinar 'ManagedDemo' com uma chave de nome forte.  
  
    -   Sobre o **projeto** menu, clique em **ManagedDemo propriedades**.  
  
         As propriedades de projeto aparecem.  
  
         Clique em **assinatura**.  
  
         Selecione o **assinar o assembly** caixa de seleção.  
  
         No **Escolher um arquivo de chave de nome de cadeia de caracteres** lista, selecione **\< Novo … >**.  
  
         O **Create Strong Name Key** caixa de diálogo é exibida.  
  
         No **nome do arquivo de chave**, digite TestKey.  
  
         Digite uma senha e, em seguida, clique em **OK**.  
  
         Sobre o **arquivo** menu, clique em **Salvar itens selecionados**, e, em seguida, feche as páginas de propriedades.  
  
         Recompile o projeto.  
  
-   [CA2237: Marcar tipos ISerializable com SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md): Microsoft.Usage: adicionar um atributo [Serializable] para o tipo 'demonstração' como esse tipo implementa ISerializable.  
  
    -   Adicionar o `[Serializable ()]` à classe `demo`.  
  
         Recompile o projeto.  
  
 Depois de concluir as alterações, o arquivo Class1. cs deve parecer com o seguinte:  
  
```  
//CodeAnalysisManagedDemo  
//Class1.cs  
using System;  
using System.Runtime.Serialization;  
  
namespace TestCode  
{  
  
    [Serializable()]   
    public class DemoException : Exception  
    {  
        public DemoException () : base() { }  
        public DemoException(String s) : base(s) { }  
        public DemoException(String s, Exception e) : base(s, e) { }  
        protected DemoException(SerializationInfo info, StreamingContext context) : base(info, context) { }  
  
        public static void Initialize(int size) { }  
        protected static readonly int _item;  
        public static int Item { get { return _item; } }  
    }  
}  
```  
  
## <a name="exclude-code-analysis-warnings"></a>Excluir avisos da análise de código  
  
#### <a name="to-exclude-code-defect-warnings"></a>Para excluir os avisos de defeitos de código  
  
1.  Para cada um dos avisos restantes, faça o seguinte:  
  
    1.  Na janela de análise de código, selecione o aviso.  
  
    2.  Escolha **ações**, escolha **Suprimir a mensagem**, e, em seguida, escolha **no arquivo de supressão de projeto**.  
  
     Para obter mais informações, consulte [como: suprimir avisos usando o Item de Menu](../code-quality/how-to-suppress-warnings-by-using-the-menu-item.md)  
  
2.  Recompile o projeto.  
  
     O projeto é compilado sem erros ou avisos.