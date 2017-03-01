---
title: "Definindo uma política de bloqueio para criar segmentos somente leitura | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fa549c71-2bf6-4b08-b7b2-7756dd6f1dc8
caps.latest.revision: 12
author: alancameronwills
ms.author: awills
manager: douge
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 3d07f82ea737449fee6dfa04a61e195654ba35fa
ms.openlocfilehash: d1fd809760a5a3a77db961aedf32b0c0e4e36693
ms.lasthandoff: 02/22/2017

---
# <a name="defining-a-locking-policy-to-create-read-only-segments"></a>Definindo uma política de bloqueio para criar segmentos somente leitura
A API de imutabilidade do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] SDK de visualização e modelagem permite que um programa para bloqueio parte ou todo um modelo de linguagem específica do domínio (DSL) para que ele pode ser lido mas não alterado. Essa opção somente leitura pode ser usada, por exemplo, para que um usuário pode solicitar que seus colegas para anotar e analisar um modelo DSL, mas pode impedir alterar o original.  
  
 Além disso, como autor de uma DSL, você pode definir um *política de bloqueio.* Uma política de bloqueio define quais bloqueios são permitidos, não permitidos ou obrigatórios. Por exemplo, quando você publica uma DSL, você pode incentivar os desenvolvedores de terceiros para estendê-lo com novos comandos. Mas você também pode usar uma política de bloqueio para impedir que alterar o status somente leitura de partes específicas do modelo.  
  
> [!NOTE]
>  Uma política de bloqueio pode ser evitada por meio de reflexão. Ele fornece um limite claro para os desenvolvedores de terceiros, mas não fornecem alta segurança.  
  
 Mais informações e exemplos estão disponíveis na [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] [SDK de visualização e modelagem](http://go.microsoft.com/fwlink/?LinkId=186128) site da Web.  

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
  
## <a name="setting-and-getting-locks"></a>Definindo e Obtendo bloqueios  
 Você pode definir os bloqueios no repositório, em uma partição ou em um elemento individual. Por exemplo, esta instrução impedirá que um elemento de modelo que está sendo excluído e também impedirá que suas propriedades sejam alteradas:  
  
```  
using Microsoft.VisualStudio.Modeling.Immutability; ...  
element.SetLocks(Locks.Delete | Locks.Property);  
```  
  
 Outros valores de bloqueio podem ser usados para impedir alterações em relações, criação de elemento, a movimentação entre partições e links de ordenação novamente em uma função.  
  
 Os bloqueios se aplicam às ações do usuário e ao código de programa. Se o código do programa tenta fazer uma alteração, um `InvalidOperationException` será lançada. São ignorados os bloqueios em uma operação de desfazer ou refazer.  
  
 Você pode descobrir se um elemento tem um qualquer bloqueio em um determinado conjunto usando `IsLocked(Locks)` e você pode obter o conjunto atual de bloqueios em um elemento usando `GetLocks()`.  
  
 Você pode definir um bloqueio sem usar uma transação. O banco de dados de bloqueio não é parte do armazenamento. Se você definir um bloqueio em resposta a uma alteração de um valor no armazenamento, por exemplo em OnValueChanged, você deve permitir alterações que fazem parte de uma operação de desfazer.  
  
 Esses métodos são métodos de extensão são definidos na <xref:Microsoft.VisualStudio.Modeling.Immutability>namespace.</xref:Microsoft.VisualStudio.Modeling.Immutability>  
  
### <a name="locks-on-partitions-and-stores"></a>Bloqueios em partições e repositórios  
 Bloqueios também podem ser aplicados para partições e o armazenamento. Um bloqueio é definido em uma partição se aplica a todos os elementos na partição. Portanto, por exemplo, a instrução a seguir impedirá todos os elementos em uma partição que está sendo excluído, independentemente dos Estados de seus próprios bloqueios. No entanto, outros bloqueios como `Locks.Property` ainda pode ser definida em elementos individuais:  
  
```  
partition.SetLocks(Locks.Delete);  
```  
  
 Um bloqueio é definido no repositório se aplica a todos os seus elementos, independentemente das configurações de bloqueio em partições e os elementos.  
  
### <a name="using-locks"></a>Uso de bloqueios  
 Você pode usar bloqueios para implementar esquemas, como os exemplos a seguir:  
  
-   Não permitir alterações para todos os elementos e relações, exceto aqueles que representam os comentários. Isso permite aos usuários anotar um modelo sem alterá-lo.  
  
-   Não permitir alterações na partição padrão, mas permitir alterações na partição do diagrama. O usuário pode reorganizar o diagrama, mas não é possível alterar o modelo subjacente.  
  
-   Não permitir alterações no armazenamento, exceto um grupo de usuários que são registrados em um banco de dados separado. Para outros usuários, o diagrama e o modelo são somente leitura.  
  
-   Não permitir alterações para o modelo se uma propriedade booleana do diagrama é definida como true. Forneça um comando de menu para alterar essa propriedade. Isso ajuda a garantir que os usuários que não fazem com que as alterações acidentalmente.  
  
-   Não permitir a adição e exclusão de elementos e relações de classes específicas, mas permitir alterações de propriedade. Isso fornece aos usuários uma forma fixa no qual eles podem preencher as propriedades.  
  
## <a name="lock-values"></a>Valores de bloqueio  
 Bloqueios podem ser definidos em um repositório, partição ou ModelElement individual. Bloqueios é um `Flags` enumeração: você pode combinar seus valores usando ' |'.  
  
-   Bloqueios de depósito sempre incluem os bloqueios de sua partição.  
  
-   Bloqueios de uma partição sempre incluem os bloqueios do armazenamento.  
  
 Você não pode definir um bloqueio em uma partição ou armazenar e ao mesmo tempo, desabilite o bloqueio em um elemento individual.  
  
|Valor|Isso significa se `IsLocked(Value)` for true|  
|-----------|------------------------------------------|  
|Nenhum|Nenhuma restrição.|  
|Propriedade|Propriedades do domínio de elementos não podem ser alteradas. Isso não se aplica às propriedades que são geradas pela função de uma classe de domínio em uma relação.|  
|Adicionar|Novos elementos e links não pode ser criados em uma partição ou armazenar.<br /><br /> Não aplicável a `ModelElement`.|  
|Mover|Elemento não pode ser movido entre partições se `element.IsLocked(Move)` for true, ou se `targetPartition.IsLocked(Move)` for true.|  
|Excluir|Um elemento não pode ser excluído se esse bloqueio é definido no próprio elemento ou em qualquer um dos elementos que seria Propagar exclusão, como formas e elementos incorporados.<br /><br /> Você pode usar `element.CanDelete()` para descobrir se um elemento pode ser excluído.|  
|Reordenar|A ordem dos links em um roleplayer não pode ser alterada.|  
|RolePlayer|O conjunto de links que são originados nesse elemento não pode ser alterado. Por exemplo, novos elementos não podem ser inseridos nesse elemento. Isso não afeta os links para o qual este elemento é o destino.<br /><br /> Se este elemento é um link, sua origem e destino não são afetados.|  
|Todos|OR bit a bit dos outros valores.|  
  
## <a name="locking-policies"></a>Políticas de bloqueio  
 Como o autor de uma DSL, você pode definir um *política de bloqueio*. Uma política de bloqueio moderates a operação de SetLocks(), para que possa evitar bloqueios específicos sejam definidas ou exige que os bloqueios específicos devem ser definidos. Normalmente, você poderia usar uma política de bloqueio para evitar que usuários ou desenvolvedores de contravening acidentalmente o uso pretendido de uma DSL, da mesma maneira que você pode declarar uma variável `private`.  
  
 Você também pode usar uma política de bloqueio para definir bloqueios em todos os elementos depende do tipo do elemento. Isso ocorre porque `SetLocks(Locks.None)` é sempre chamado quando um elemento é criado ou desserializado de arquivos.  
  
 No entanto, você não pode usar uma política para variar os bloqueios em um elemento durante sua vida. Para obter esse efeito, você deve usar chamadas para `SetLocks()`.  
  
 Para definir uma política de bloqueio, você precisa:  
  
-   Crie uma classe que implemente <xref:Microsoft.VisualStudio.Modeling.Immutability.ILockingPolicy>.</xref:Microsoft.VisualStudio.Modeling.Immutability.ILockingPolicy>  
  
-   Adicione essa classe para os serviços que estão disponíveis por meio de DocData da DSL.  
  
### <a name="to-define-a-locking-policy"></a>Para definir uma política de bloqueio  
 <xref:Microsoft.VisualStudio.Modeling.Immutability.ILockingPolicy>tem a seguinte definição:</xref:Microsoft.VisualStudio.Modeling.Immutability.ILockingPolicy>  
  
```  
public interface ILockingPolicy  
{  
  Locks RefineLocks(ModelElement element, Locks proposedLocks);  
  Locks RefineLocks(Partition partition, Locks proposedLocks);  
  Locks RefineLocks(Store store, Locks proposedLocks);  
}  
```  
  
 Esses métodos são chamados quando uma chamada é feita para `SetLocks()` em uma loja, uma partição ou um ModelElement. Cada método, você receberá um conjunto proposto de bloqueios. Você pode retornar o conjunto de proposta, ou você pode adicionar e subtrair bloqueios.  
  
 Por exemplo:  
  
```  
using Microsoft.VisualStudio.Modeling;  
using Microsoft.VisualStudio.Modeling.Immutability;  
namespace Company.YourDsl.DslPackage // Change  
{  
  public class MyLockingPolicy : ILockingPolicy  
  {  
    /// <summary>  
    /// Moderate SetLocks(this ModelElement target, Locks locks)  
    /// </summary>  
    /// <param name="element">target</param>  
    /// <param name="proposedLocks">locks</param>  
    /// <returns></returns>  
    public Locks RefineLocks(ModelElement element, Locks proposedLocks)  
    {  
      // In my policy, users can never delete an element,  
      // and other developers cannot easily change that:  
      return proposedLocks | Locks.Delete);  
    }  
    public Locks RefineLocks(Store store, Locks proposedLocks)  
    {  
      // Only one user can change this model:  
      return Environment.UserName == "aUser"   
           ? proposedLocks : Locks.All;  
    }  
  
```  
  
 Para certificar-se de que os usuários sempre podem excluir elementos, mesmo que outro código chama`SetLocks(Lock.Delete):`  
  
 `return proposedLocks & (Locks.All ^ Locks.Delete);`  
  
 Para impedir alterações em todas as propriedades de cada elemento de MyClass:  
  
 `return element is MyClass ? (proposedLocks | Locks.Property) : proposedLocks;`  
  
### <a name="to-make-your-policy-available-as-a-service"></a>Para fazer sua política disponível como um serviço  
 No seu `DslPackage` projeto, adicione um novo arquivo que contém o código que é semelhante ao exemplo a seguir:  
  
```  
using Microsoft.VisualStudio.Modeling;  
using Microsoft.VisualStudio.Modeling.Immutability;  
namespace Company.YourDsl.DslPackage // Change  
{   
  // Override the DocData GetService() for this DSL.  
  internal partial class YourDslDocData // Change  
  {  
    /// <summary>  
    /// Custom locking policy cache.  
    /// </summary>  
    private ILockingPolicy myLockingPolicy = null;  
  
    /// <summary>  
    /// Called when a service is requested.  
    /// </summary>  
    /// <param name="serviceType">Service requested</param>  
    /// <returns>Service implementation</returns>  
    public override object GetService(System.Type serviceType)  
    {  
      if (serviceType == typeof(SLockingPolicy)   
       || serviceType == typeof(ILockingPolicy))  
      {  
        if (myLockingPolicy == null)  
        {  
          myLockingPolicy = new MyLockingPolicy();  
        }  
        return myLockingPolicy;  
      }  
      // Request is for some other service.  
      return base.GetService(serviceType);  
    }  
}  
```

