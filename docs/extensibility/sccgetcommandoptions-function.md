---
title: "Função SccGetCommandOptions | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SccGetCommandOptions
helpviewer_keywords:
- SccGetCommandOptions function
ms.assetid: bbe4aa4e-b4b0-403e-b7a0-5dd6eb24e5a9
caps.latest.revision: 14
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
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: df497de98463d728b5cd040415924a40fb6717b8
ms.contentlocale: pt-br
ms.lasthandoff: 09/06/2017

---
# <a name="sccgetcommandoptions-function"></a>Função SccGetCommandOptions
Essa função solicita ao usuário para as opções avançadas para um determinado comando.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
SCCRTN SccGetCommandOptions(  
   LPVOID pvContext,  
   HWND hWnd,  
   enum SCCCOMMAND iCommand,  
   LPCMDOPTS* ppvOptions  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 pvContext  
 [in] A estrutura de contexto de plug-in de controle de origem.  
  
 hWnd  
 [in] Um identificador para a janela do IDE que o plug-in de controle de origem pode usar como um pai para todas as caixas de diálogo que ele oferece.  
  
 iCommand  
 [in] O comando para a qual as opções avançadas são solicitadas (consulte [comando código](../extensibility/command-code-enumerator.md) possíveis valores).  
  
 ppvOptions  
 [in] A estrutura de opção (também pode ser `NULL`).  
  
## <a name="return-value"></a>Valor de retorno  
 A implementação de plug-in de controle de origem dessa função deve retornar um dos seguintes valores:  
  
|Valor|Descrição|  
|-----------|-----------------|  
|SCC_OK|Êxito.|  
|SCC_I_ADV_SUPPORT|O plug-in de controle de origem dá suporte a opções avançadas para o comando.|  
|SCC_I_OPERATIONCANCELED|O usuário cancelou o origem controle do plug-in **opções** caixa de diálogo.|  
|SCC_E_OPTNOTSUPPORTED|O plug-in de controle de origem não oferece suporte a esta operação.|  
|SCC_E_ISCHECKEDOUT|Não é possível executar esta operação em um arquivo que está sendo verificado.|  
|SCC_E_ACCESSFAILURE|Houve um problema ao acessar o sistema de controle de origem, provavelmente devido a problemas de rede ou de contenção. Recomenda-se uma nova tentativa.|  
|SCC_E_NONSPECIFICERROR|Falha não específica.|  
  
## <a name="remarks"></a>Comentários  
 O IDE chama esta função pela primeira vez com `ppvOptions` = `NULL` para determinar se o plug-in de controle de origem suporta o recurso de opções avançadas para o comando especificado. Se o plug-in oferece suporte ao recurso para o comando, o IDE chama essa função novamente quando o usuário solicita opções avançadas (geralmente é implementado como um **avançado** botão em uma caixa de diálogo) e fornece um ponteiro não nula para `ppvOptions` que aponta para um `NULL` ponteiro. O plug-in armazena quaisquer opções avançadas especificadas pelo usuário em uma estrutura em particular e retorna um ponteiro para a estrutura no `ppvOptions`. Essa estrutura é passada para todas as outras funções de API de plug-in de controle de origem que precisa saber sobre ele, incluindo as chamadas subsequentes para o `SccGetCommandOptions` função.  
  
 Um exemplo pode ajudar a esclarecer essa situação.  
  
 Um usuário escolhe o **obter** comando e o IDE exibe um **obter** caixa de diálogo. O IDE chama o `SccGetCommandOptions` funcionar com `iCommand` definida como `SCC_COMMAND_GET` e `ppvOptions` definido como `NULL`. Isso é interpretado pelo controle de origem de plug-in como a pergunta, "Você tem as opções avançadas para este comando?" Se o plug-in retorna `SCC_I_ADV_SUPPORT`, o IDE exibe um **avançado** botão no seu **obter** caixa de diálogo.  
  
 Na primeira vez que o usuário clica o **avançado** botão, o IDE novamente chama o `SccGetCommandOptions` funcionar, dessa vez com não`NULL``ppvOptions` que aponta para um `NULL` ponteiro. O plug-in exibe seu próprio **obter opções de** caixa de diálogo solicita ao usuário para obter informações, coloca essa informação em sua própria estrutura e retorna um ponteiro para a estrutura no `ppvOptions`.  
  
 Se o usuário clica em **avançado** novamente na caixa de diálogo, o IDE chama o `SccGetCommandOptions` função novamente sem alterar `ppvOptions`, de modo que a estrutura é passada de volta para o plug-in. Isso permite que o plug-in reinicializar sua caixa de diálogo para os valores que o usuário tiver sido definida anteriormente. O plug-in modifica a estrutura em vigor antes de retornar.  
  
 Finalmente, quando o usuário clica **Okey** no IDE do **obter** caixa de diálogo, o IDE chama o [SccGet](../extensibility/sccget-function.md), passando a estrutura retornada em `ppvOptions` que contém o Opções avançadas.  
  
> [!NOTE]
>  O comando `SCC_COMMAND_OPTIONS` é usado quando o IDE exibe um **opções** caixa de diálogo que permite ao usuário definir preferências que controlam como a integração funciona. Se quiser que o plug-in de controle de origem fornecer sua própria caixa de diálogo de preferências, ele pode exibi-lo de um **avançado** botão na caixa de diálogo de preferências do IDE. O plug-in é responsável pela obtenção e a manter esta informação. o IDE não usá-lo ou modificá-lo.  
  
## <a name="see-also"></a>Consulte também  
 [Funções de API de plug-in de controle de origem](../extensibility/source-control-plug-in-api-functions.md)   
 [Código de comando](../extensibility/command-code-enumerator.md)
