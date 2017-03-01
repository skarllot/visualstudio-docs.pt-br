---
title: Atributos condicionais de esquema XML VSCT | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSCT XML schema elements, conditional attributes
- conditional attributes (VSCT XML schema)
ms.assetid: 754d4f32-319b-44c9-915f-f7c60e53222e
caps.latest.revision: 5
ms.author: gregvanl
manager: ghogen
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
ms.openlocfilehash: 67b2f0cb5d2345f6bb6c37416f74acc4e3b8b833
ms.lasthandoff: 02/22/2017

---
# <a name="vsct-xml-schema-conditional-attributes"></a>Atributos condicionais de esquema XML VSCT
Atributos condicionais podem ser aplicados a todas as listas e itens. Operadores lógicos e expressões de expansão de símbolo avaliada como true ou false. Se verdadeiro, a lista associada ou o item é incluído na saída resultante.  
  
 Expansões token podem ser testados em outras expansões de token ou constantes. A função Defined é usada para testar se um determinado nome tiver sido definido, mesmo se ele não tem nenhum valor.  
  
 Quando um atributo de condição é aplicado a uma lista, a condição é aplicada a todos os elementos filho na lista. Se um elemento filho em si contém um atributo de condição, a condição é combinada com a expressão pai por uma operação AND.  
  
 Os valores 1, '1' e 'true' são avaliados como true e 0, '0' e 'false' são avaliadas como false.  
  
## <a name="operators"></a>Operadores  
 Os operadores a seguir podem ser usados para avaliar expressões condicionais.  
  
|Operador|Definição|  
|--------------|----------------|  
|(,)|Agrupamento|  
|!|Não lógico|  
|\<, >, \<=, >=, ==, !=|Relacionais e de igualdade|  
|e|Booleano|  
|ou|Booleano|  
  
## <a name="examples"></a>Exemplos  
  
```  
<Menu Condition="Defined(DEBUG)" …  
</Menu>  
  
<Menu Condition="%(SKU_MODE) = 'Demo'" …  
</Menu>  
  
<Menus Condition="Defined(DEBUG)">  
    <Menu …  
    </Menu>  
</Menus>  
  
<Menus Condition="Defined(DEMO_SKU)">  
    <Menus Condition="!Defined(DEBUG)">  
        <Menu …  
        </Menu>  
    </Menus>  
  
    <Menu …  
    </Menu>  
</Menus>  
  
<Menus Condition="(Defined(DEMO_SKU) or Defined(SAMPLE_SKU))   
and !Defined(DEBUG)">  
    <Menu …  
    </Menu>  
</Menus>  
```  
  
## <a name="see-also"></a>Consulte também  
 [Tabela de comando do Visual Studio (. Arquivos de VSCT)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
