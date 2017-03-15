---
title: "Rule Set Editor Dialog Box (Legacy) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Workflow.Activities.Rules.Design.RuleSetDialog.UI"
helpviewer_keywords: 
  - "Rule Set Editor dialog box"
ms.assetid: 7cfd5df1-1115-4e5c-9b72-121f39419e83
caps.latest.revision: 7
caps.handback.revision: 7
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Rule Set Editor Dialog Box (Legacy)
Este tópico descreve como usar a caixa de diálogo **Editor de Conjunto de Regras** em [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)]herdado.  Use [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] herdado quando você precisa definir como alvo [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] ou [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].  
  
 O **Rule Set Editor** caixa de diálogo é usada para criar e modificar [PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019) conjuntos de regra, que são serializados em um arquivo. rules.  
  
> [!NOTE]
>  Se você deseja abrir o arquivo de .rules com **Editor XML com codificação**, você deve primeiro feche a janela de designer associado para o fluxo de trabalho ou a atividade.  
  
 Para obter informações sobre como acessar a caixa de diálogo **Editor de Conjunto de Regras** , consulte [How to: Create a PolicyActivity Rule Set \(Legacy\)](../workflow-designer/how-to-create-a-policyactivity-rule-set-legacy.md).  
  
> [!WARNING]
>  O editor das regras de novas [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] que é usado para direcionar [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] ou [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)] não oferece suporte Multitargeting.  
  
 A tabela a seguir descreve os elementos de \(UI\) de interface de usuário da caixa de diálogo **Editor de Conjunto de Regras** .  
  
|Elemento da Interface do Usuário|Descrição|  
|--------------------------------------|---------------|  
|**Adicione a regra**|Adicione uma nova definição de regra ao conjunto de regras.|  
|**Excluir**|Exclui a regra selecionada do conjunto de regras.|  
|**Encadeamento**|Especifica que tipo de encadeamento frente para usar com o conjunto de regras.  As opções disponíveis são:<br /><br /> -   **Encadeando completamente**, que especifica usar todos mecanismos encadeando dianteiros: método implícito, atribuindo, e explícito usando uma função de **Update** .<br />-   **Sequencial**, que especifica para não usar qualquer encadeamento frente.<br />-   **Atualização explícita apenas**, que especifica para executar somente encadeamento frente em ações de **Atualizar** .<br /><br /> Para obter mais informações sobre o encadeamento, consulte [usando a atividade PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65004).|  
|**Nome**|Regra título da coluna da lista.  Clique para classificar por nome a lista de regras.|  
|**Prioridade**|Regra título da coluna da lista.  Clique para classificar a lista de regras por prioridade.|  
|**Reavaliação**|Regra título da coluna da lista.  Clique para classificar a lista de regras pelo tipo de reavaliação.|  
|**Visualização de Regra**|Regra título da coluna da lista.  Clique para classificar a lista de regras por visualização de condição e ações de uma regra.|  
|**Nome:**|Digite o nome da regra.|  
|**Prioridade:**|Insira uma prioridade para a regra.  A prioridade padrão é 0.|  
|**Reavaliação:**|Especifica que tipo de reavaliação de regras para usar com a regra.  As opções disponíveis são:<br /><br /> -   **Sempre**, que faz com que a regra ser reavaliada quando necessário.<br />-   **Nunca**, que faz com que a regra ser reavaliada nunca.  Neste caso uma regra executa somente uma vez.|  
|**Ativo**|Verifique para fazer a regra ativo.|  
|**Condição:**|Digite uma expressão para a condição de regra.  Para obter informações sobre a sintaxe de expressão, consulte a seção “inserindo de expressões de condição e a ação” nessa página.|  
|**Ações:**|Insira a expressão para ações.  Para obter informações sobre a sintaxe de expressão, consulte a seção “inserindo de expressões de condição e a ação” nessa página.|  
|**Outras ações:**|Insira a expressão para outras ações.  Para obter informações sobre a sintaxe de expressão, consulte a seção “inserindo de expressões de condição e a ação” nessa página.|  
|**OK**|Clique para salvar a regra definida como um arquivo de .rules.|  
  
 Para obter mais informações sobre conjuntos de regras, consulte [usando a atividade PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65004).  
  
## Inserindo expressões de condição e de ação  
 Você inserir expressões para a condição e as ações de seguida e outras como texto em suas respectivas caixas de texto na caixa de diálogo **Editor de Conjunto de Regras** .  Você pode digitar **this.** no editor a campos, a métodos e propriedades de referência usados no fluxo de trabalho, usando um IntelliSense\- tipo de menu.  Ou você pode digitar um nome de membro de fluxo de trabalho diretamente.  Você pode chamar métodos estáticos em tipos referenciados digitando o nome da classe seguida do nome do método.  
  
 Você pode adicionar operadores lógicos a condição, como AND, OU, e NOT.  Você também pode adicionar predicados.  Um predicado é um operador binário e dois operandos.  Os operadores binários suportados são \= \=, \>, \<\>, \=, e \< \=.  Os operandos são suportados valor constante, função aritmética, e membros públicos o escopo.  
  
 Você pode especificar o tipo para comparação, e você pode comparar a **null** ou cadeia de caracteres vazia.  Você pode aninhar chamadas aos membros em uma variável que contém um tipo complexo, por exemplo, `this.Address.State == "WA"`.  
  
 As expressões dão suporte aos seguintes operadores:  
  
-   Operadores relacionais: \=\=, \=\! \=  
  
-   Operadores de comparação: \<, \< \=, \>, \> \=  
  
-   Operadores aritméticos: \+, \-, \*,\/, MODIFICAÇÃO  
  
-   Operadores lógicos: E, & &, OR, &#124; &#124;, não\!  
  
-   Operadores bit a bit: &, &#124;  
  
 Precedência de operadores de expressão segue regras de precedência de operador C\#.  
  
 Para obter mais informações sobre as circunstâncias, consulte [Using Conditions in Workflows](http://msdn.microsoft.com/pt-br/541211f5-d382-4810-894f-71f00b34fa77).  
  
### Interromper e atualizar funções  
 **Ações:** e suporte **Halt** expressões de **Outras ações:** e funções de **Update** .  Para usar a função de **Halt** , digite **Halt** em uma caixa de texto de **Em ação:** ou de **Outra ação:** .  A ação de **Halt** faz com que a regra a execução de parar imediatamente, e controla retorna para o código de chamada.  Você usa a função de **Update** com o encadeamento frente.  
  
 Uma declaração de **Update** pode ser expressa no editor em um dos dois formulários; ambos os formulários são mostrados no exemplo a seguir:  
  
```  
Update(this.Address.State)  
Update("this/Address/State")  
```  
  
 Para obter mais informações sobre como usar **Update** com o encadeamento de encaminhamento, consulte [usando a atividade PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65004).  
  
## Consulte também  
 [PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019)   
 [Select Rule Set Dialog Box \(Legacy\)](../workflow-designer/select-rule-set-dialog-box-legacy.md)   
 [Usando a atividade PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65004)   
 [Usando condições em fluxos de trabalho](http://go.microsoft.com/fwlink?LinkID=65009)