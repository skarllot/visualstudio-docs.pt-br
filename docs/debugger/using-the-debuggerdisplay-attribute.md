---
title: "Usando o atributo DebuggerDisplay | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "atributos [c#], o depurador"
  - "Atributo DebuggerDisplay"
  - "Classe DebuggerDisplayAttribute"
ms.assetid: f4eb7c76-af4e-493b-9ab6-9cb05949d9b3
caps.latest.revision: 47
caps.handback.revision: 47
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Usando o atributo DebuggerDisplay
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

O [DebuggerDisplayAttribute Classe](../Topic/DebuggerDisplayAttribute%20Class.md) controla como um objeto, propriedade ou campo é exibido nas janelas de variáveis do depurador. Esse atributo pode ser aplicado a tipos, delegados, propriedades, campos e assemblies.  
  
 O `DebuggerDisplay` atributo tem um único argumento, que é uma cadeia de caracteres a ser exibida na coluna valor para instâncias do tipo. Essa seqüência pode conter chaves \(`{` e `}`\). Texto dentro de um par de chaves será avaliado como um campo, propriedade ou método.  
  
 Se uma classe tem um substituído `ToString()` método, o depurador usa o método substituído em vez do padrão `{<typeName>}`. Portanto, se você tiver substituído o `ToString()` método, o depurador usa o método substituído em vez do padrão`{<typeName>}`, e você não precisa usar `DebuggerDisplay`. Se você usar ambos, o `DebuggerDisplay` atributo tem precedência sobre a substituição `ToString()` método.  
  
 Se o depurador avalia nesse implícita `ToString()` chamada depende de uma configuração de usuário na **Ferramentas \/ opções \/ depuração** caixa de diálogo. Visual Basic não implementa implícita neste `ToString()` avaliação.  
  
> [!IMPORTANT]
>  Se o **Mostrar estrutura bruta de objetos em janelas variáveis** caixa de seleção é marcada no **Ferramentas\/opções \/ depuração** caixa de diálogo, o `DebuggerDisplay` atributo é ignorado.  
  
 A tabela a seguir mostra algumas utilizações possíveis do `DebuggerDisplay` atributo e saídas de exemplo.  
  
|Atributo|Saída aparecendo no **valor** coluna\)|  
|--------------|--------------------------------------------|  
|`[DebuggerDisplay("x = {x} y = {y}")]`<br /><br /> Usado em um tipo com campos `x` e `y`.|`x = 5 y = 18`|  
|`[DebuggerDisplay("String value is {getString()}")]`Sintaxe do parâmetro pode variar entre linguagens. Portanto, usá\-lo com cuidado.|`String value is [5, 6, 6]`|  
  
 `DebuggerDisplay` também pode aceitar parâmetros nomeados.  
  
|Parâmetros|Finalidade|  
|----------------|----------------|  
|`Name`, `Type`|Esses parâmetros afetam o **nome** e **tipo** colunas das janelas de variável. \(Eles podem ser definidos em cadeias de caracteres usando a mesma sintaxe do construtor.\) Usar esses parâmetros demais ou usá\-los incorretamente, poderá causar uma saída confusa.|  
|`Target`, `TargetTypeName`|Especifica o tipo de destino quando o atributo é usado no nível do assembly.|  
  
 O arquivo autoexp.cs usa o atributo DebuggerDisplay no nível do assembly. O arquivo autoexp.cs determina as expansões padrão que o Visual Studio usa para objetos .NET. Você pode examinar o arquivo autoexp.cs para obter exemplos de como usar o atributo DebuggerDisplay, ou você pode modificar e compilar o arquivo autoexp.cs para alterar as expansões padrão. Certifique\-se de fazer backup do arquivo autoexp.cs antes de modificá\-lo.  
  
 Para criar autoexp.cs, abra um Prompt de comando o desenvolvedor para VS2015 e execute os seguintes comandos  
  
```  
cd <directory containing autoexp.cs>  
csc /t:library autoexp.cs  
```  
  
 As alterações autoexp.dll serão selecionadas na próxima sessão de depuração.  
  
## Usando expressões em DebuggerDisplay  
 Embora você possa usar uma expressão geral entre as chaves em um atributo DebuggerDisplay, essa prática não é recomendada.  
  
 Uma expressão geral em DebuggerDisplay tem acesso implícito ao `this` ponteiro para a instância atual do tipo de destino somente. A expressão não tem acesso para aliases, locais ou ponteiros. Se a expressão fizer referência a propriedades, atributos nessas propriedades não são processados. Por exemplo, o código c\# `[DebuggerDisplay("Object {count - 2}"`  exibiria `Object 6` se o campo `count` foi 8.  
  
 Usando expressões em DebuggerDisplay pode levar a problemas a seguir:  
  
-   Avaliar expressões é a operação mais cara no depurador e a expressão é avaliada toda vez que ele é exibido. Isso pode causar problemas de desempenho ao depurar o código. Por exemplo, uma expressão complexa que é usada para exibir os valores em uma coleção ou uma lista pode ser muito lenta quando o número de elementos é grande.  
  
-   Expressões são avaliadas pelo avaliador de expressão da linguagem do quadro de pilhas atual e não pelo avaliador da linguagem na qual a expressão foi gravada. Isso pode causar resultados imprevisíveis quando os idiomas são diferentes.  
  
-   Avaliar uma expressão pode alterar o estado do aplicativo. Por exemplo, uma expressão que define o valor de uma propriedade muda o valor da propriedade no código em execução.  
  
 Uma maneira de reduzir os possíveis problemas de avaliação da expressão é criando uma propriedade privada que executa a operação e retorna uma cadeia de caracteres. O atributo DebuggerDisplay pode exibir o valor da propriedade privada. O exemplo a seguir implementa esse padrão:  
  
```c#  
[DebuggerDisplay("{DebuggerDisplay,nq}")]  
public sealed class MyClass   
{      
    public int count { get; set; }      
    public bool flag { get; set; }      
    private string DebuggerDisplay  
   {         
        get  
        {  
             return string.Format("("Object {0}", count - 2);  
        }      
    }  
}  
```  
  
## Exemplo  
 O exemplo de código a seguir mostra como usar `DebuggerDisplay`, juntamente com `DebuggerBrowseable` e `DebuggerTypeProxy`. Quando exibido em uma janela de variáveis do depurador, como o **inspeção** janela, ela produz uma expansão parecida com esta:  
  
|**Nome**|**Valor**|**Tipo**|  
|--------------|---------------|--------------|  
|Key|"três"|objeto {string}|  
|Valor|3|objeto {int}|  
  
```c#  
[DebuggerDisplay("{value}", Name = "{key}")]  
internal class KeyValuePairs  
{  
    private IDictionary dictionary;  
    private object key;  
    private object value;  
    public KeyValuePairs(IDictionary dictionary, object key, object value)  
    {  
        this.value = value;  
        this.key = key;  
        this.dictionary = dictionary;  
    }  
  
    public object Key  
    {  
        get { return key; }  
        set  
        {  
            object tempValue = dictionary[key];  
            dictionary.Remove(key);  
            key = value;  
            dictionary.Add(key, tempValue);  
        }  
    }  
  
    public object Value  
    {  
        get { return this.value; }  
        set  
        {  
            this.value = value;  
            dictionary[key] = this.value;  
        }  
    }  
}  
  
[DebuggerDisplay("{DebuggerDisplay,nq}")]  
[DebuggerTypeProxy(typeof(HashtableDebugView))]  
class MyHashtable  
{  
    public Hashtable hashtable;  
  
    public MyHashtable()  
    {  
        hashtable = new Hashtable();    
    }    private string DebuggerDisplay    {        get { return "Count = " + hashtable.Count); }    }  
  
    private class HashtableDebugView  
    {  
        private MyHashtable myhashtable;  
        public HashtableDebugView(MyHashtable myhashtable)  
        {  
            this.myhashtable = myhashtable;  
        }  
  
        [DebuggerBrowsable(DebuggerBrowsableState.RootHidden)]  
        public KeyValuePairs[] Keys  
        {  
            get  
            {  
                KeyValuePairs[] keys = new KeyValuePairs[myhashtable.hashtable.Count];  
  
                int i = 0;  
                foreach (object key in myhashtable.hashtable.Keys)  
                {  
                    keys[i] = new KeyValuePairs(myhashtable.hashtable, key, myhashtable.hashtable[key]);  
                    i++;  
                }  
                return keys;  
            }  
        }  
    }  
}  
```  
  
## Consulte também  
 [Usando o atributo DebuggerTypeProxy](../debugger/using-debuggertypeproxy-attribute.md)   
 [Exibindo tipos de dados personalizados](../debugger/create-custom-views-of-dot-managed-objects.md)   
 [Melhorando a depuração com os atributos de exibição do depurador](../Topic/Enhancing%20Debugging%20with%20the%20Debugger%20Display%20Attributes.md)