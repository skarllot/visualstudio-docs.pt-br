---
title: Propriedades de armazenamento calculadas e personalizadas | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language, programming domain properties
ms.assetid: 42b785f9-2b0f-4f13-a6b4-246e5e0d477a
caps.latest.revision: 19
author: alancameronwills
ms.author: awills
manager: douge
translation.priority.mt:
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
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 928398ad2a863e0c4aa0447d179b1077329e244e
ms.lasthandoff: 02/22/2017

---
# <a name="calculated-and-custom-storage-properties"></a>Propriedades calculadas e de armazenamento personalizado
Todas as propriedades de domínio em uma linguagem específica do domínio (DSL) podem ser exibidas para o usuário no diagrama e no seu Gerenciador de linguagens e podem ser acessadas pelo código do programa. No entanto, as propriedades diferem da maneira que seus valores são armazenados.  
  
## <a name="kinds-of-domain-properties"></a>Tipos de propriedades de domínio  
 Na definição de DSL, você pode definir o **tipo** de uma propriedade de domínio, conforme listado na tabela a seguir:  
  
|Tipo de propriedade de domínio|Descrição|  
|--------------------------|-----------------|  
|**Padrão** (padrão)|Uma propriedade de domínio que é salvo o *armazenar* e serializado para o arquivo.|  
|**Calculado**|Uma propriedade de domínio somente leitura que não é salvas no repositório, mas é calculada a partir de outros valores.<br /><br /> Por exemplo, `Person.Age` pode ser calculado do `Person.BirthDate`.<br /><br /> Você deve fornecer o código que executa o cálculo. Normalmente, você calcular o valor de outras propriedades de domínio. No entanto, você também pode usar os recursos externos.|  
|**Armazenamento personalizado**|Uma propriedade de domínio que não é salvas diretamente no armazenamento, mas pode ser get e set.<br /><br /> Você precisa fornecer os métodos que obtém e definir o valor.<br /><br /> Por exemplo, `Person.FullAddress` podem ser armazenados em `Person.StreetAddress`, `Person.City`, e `Person.PostalCode`.<br /><br /> Você também pode acessar recursos externos, por exemplo, para obter e definir valores de um banco de dados.<br /><br /> Seu código não deve definir valores no repositório quando `Store.InUndoRedoOrRollback` é verdadeiro. Consulte [transações e Setters personalizados](#setters).|  
  
## <a name="providing-the-code-for-a-calculated-or-custom-storage-property"></a>Fornecendo o código para uma propriedade de armazenamento calculado ou personalizado  
 Se você definir o tipo de uma propriedade de domínio calculado ou armazenamento personalizado, você precisa fornecer métodos de acesso. Quando você cria sua solução, um relatório de erro informará o que é necessário.  
  
#### <a name="to-define-a-calculated-or-custom-storage-property"></a>Para definir uma calculado ou propriedade de armazenamento personalizado  
  
1.  Em Dsldefinition, selecione a propriedade de domínio no diagrama ou no **Gerenciador de DSL**.  
  
2.  No **propriedades** janela, defina a **tipo** campo **calculado** ou **armazenamento personalizado**.  
  
     Certifique-se de que você também configurou seu **tipo** ao que você deseja.  
  
3.  Clique em **transformar todos os modelos** na barra de ferramentas de **Solution Explorer**.  
  
4.  No menu **Compilar**, clique em **Compilar Solução**.  
  
     A seguinte mensagem de erro: "*YourClass* não contém uma definição para Get*YourProperty*."  
  
5.  Clique duas vezes a mensagem de erro.  
  
     Dsl\GeneratedCode\DomainClasses.cs ou DomainRelationships.cs é aberto. Acima a chamada do método realçado, um comentário solicita que você forneça uma implementação para Get*YourProperty*().  
  
    > [!NOTE]
    >  Este arquivo é gerado de Dsldefinition. Se você editar esse arquivo, as alterações serão perdidas na próxima vez que você clicar em **transformar todos os modelos**. Em vez disso, adicione o método necessário em um arquivo separado.  
  
6.  Criar ou abrir um arquivo de classe em uma pasta separada, por exemplo Códigopersonalizado\\*YourDomainClass*. cs.  
  
     Certifique-se de que o namespace é o mesmo do código gerado.  
  
7.  No arquivo de classe, escreva uma implementação parcial da classe de domínio. Na classe, escreva uma definição para o ausente `Get` método semelhante ao exemplo a seguir:  
  
    ```  
    namespace Company.FamilyTree  
    {  public partial class Person  
       {  int GetAgeValue()  
          { return System.DateTime.Today.Year - this.BirthYear; }  
    }  }  
    ```  
  
8.  Se você definir **tipo** para **armazenamento personalizado**, também será necessário fornecer um `Set` método. Por exemplo:  
  
    ```  
    void SetAgeValue(int value)  
    { if (!Store.InUndoRedoOrRollback)  
        this.BirthYear =   
            System.DateTime.Today.Year - value; }  
    ```  
  
     Seu código não deve definir valores no repositório quando `Store.InUndoRedoOrRollback` é verdadeiro. Consulte [transações e Setters personalizados](#setters).  
  
9. Criar e executar a solução.  
  
10. Teste a propriedade. Certifique-se de que você tente **desfazer** e **Refazer**.  
  
##  <a name="a-namesettersa-transactions-and-custom-setters"></a><a name="setters"></a>Transações e Setters personalizados  
 No método conjunto de propriedade personalizado de armazenamento, você não precisa abrir uma transação, porque o método geralmente é chamado dentro de uma transação ativa.  
  
 No entanto, o método Set também pode ser chamado se o usuário invoca desfazer ou refazer, ou se uma transação está sendo revertida. Quando <xref:Microsoft.VisualStudio.Modeling.Store.InUndoRedoOrRollback%2A>for true, o método Set deve se comportar da seguinte maneira:</xref:Microsoft.VisualStudio.Modeling.Store.InUndoRedoOrRollback%2A>  
  
-   Ele não deve fazer alterações no repositório, como atribuindo valores a outras propriedades do domínio. O Gerenciador de desfazer definirá seus valores.  
  
-   No entanto, ele deve atualizar todos os recursos externos, como banco de dados de conteúdo do arquivo ou objetos fora do repositório. Isso irá assegurar que elas são mantidas na synchronism com os valores no repositório.  
  
 Por exemplo:  
  
```  
void SetAgeValue(int value)  
{   
  // If we are in Undo, no changes to Store objects:  
  if (!this.Store.InUndoRedoOrRollback)  
  {   
    this.BirthYear = System.DateTime.Today.Year - value;   
  }  
  // But always update external objects:  
  System.IO.File.WriteAllText(AgeFile, value);  
}  
```  
  
 Para obter mais informações sobre transações, consulte [Navegando e atualizando um modelo no código do programa](../modeling/navigating-and-updating-a-model-in-program-code.md).  
  
## <a name="see-also"></a>Consulte também  
 [Navegando e atualizando um modelo no código de programa](../modeling/navigating-and-updating-a-model-in-program-code.md)   
 [Propriedades de domínio](../modeling/properties-of-domain-properties.md)   
 [Como definir uma linguagem específica de domínio](../modeling/how-to-define-a-domain-specific-language.md)
