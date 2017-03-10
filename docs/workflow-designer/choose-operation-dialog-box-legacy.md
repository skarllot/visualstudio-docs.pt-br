---
title: "Choose Operation Dialog Box (Legacy) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Workflow.Activities.Design.OperationPickerDialog.UI"
ms.assetid: bc3ec902-7797-494e-af48-e70c97eb6779
caps.latest.revision: 10
caps.handback.revision: 10
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Choose Operation Dialog Box (Legacy)
Este tópico descreve como usar a caixa de diálogo **Escolher Operação** em [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)]herdado.  Use [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] herdado quando você precisa definir como alvo [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] ou [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].  
  
 A caixa de diálogo **Escolher Operação** é usada para selecionar uma operação para associar uma atividade de <xref:System.Workflow.Activities.ReceiveActivity> ou uma atividade de <xref:System.Workflow.Activities.SendActivity> .  Para obter mais informações sobre como usar esta caixa de diálogo com as atividades, consulte [How to: Implement a WCF Contract Operation \(Legacy\)](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md) e [How to: Invoke a WCF Contract Operation \(Legacy\)](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md).  
  
 A tabela a seguir descreve os elementos de \(UI\) de interface de usuário da caixa de diálogo **Escolher Operação** .  
  
|Elemento da Interface do Usuário|Descrição|  
|--------------------------------------|---------------|  
|**Adicionar Contrato**|Cria um novo contrato para você.  Você pode definir novos operações no contrato.  \(Isso é usado com <xref:System.Workflow.Activities.ReceiveActivity> somente.\)|  
|**Adicionar Operação**|Adicionar novos operações para um novo contrato que você crie na caixa de diálogo **Escolher Operação** . **Note:**  Você pode adicionar novos operações somente a contratos que você criou através da caixa de diálogo **Escolher Operação** . <br /><br /> \(Isso é usado com <xref:System.Workflow.Activities.ReceiveActivity> somente.\)|  
|**Importação…**|Importa um contrato definido anteriormente e permite que você selecione uma operação do contrato.|  
|**Operação Nome**|Nome da operação selecionada.  Esta caixa de texto disponível para editar apenas se você criou uma operação através da caixa de diálogo **Escolher Operação** .|  
|**Parâmetros**|Catalogue para conter as definições de parâmetro para a operação selecionada. **Note:**  As definições de parâmetro podem ser alteradas somente se você criou uma operação através da caixa de diálogo **Escolher Operação** .|  
|**Propriedades**|Catalogue para conter configurações de <xref:System.Net.Security.ProtectionLevel> para as mensagens enviadas entre o cliente e o serviço. **Note:**  Este guia é ativado somente se você criou uma operação através da caixa de diálogo **Escolher Operação** .|  
|**Permissões**|Catalogue para conter propriedades de <xref:System.Workflow.Activities.OperationInfoBase.PrincipalPermissionName%2A> e de <xref:System.Workflow.Activities.OperationInfoBase.PrincipalPermissionRole%2A> de usuários são permitidos que chamar a operação.  Por exemplo, se apenas foram permitidos para usuários do grupo administradores chamar a operação, então você escreveria “administradores” na caixa de texto **Função** .<br /><br /> Este guia é habilitado para ambas as operações criadas pela caixa de diálogo **Escolher Operação** e operações que foram importados através de botão de **Importar** .|  
  
> [!NOTE]
>  Contratos ou operações mostra a caixa de diálogo **Escolher Operação** somente que são usados por outras atividades de <xref:System.Workflow.Activities.SendActivity> no fluxo de trabalho.  Da mesma forma, a caixa de diálogo **Escolher Operação** para contratos mostra as atividades de <xref:System.Workflow.Activities.ReceiveActivity> ou somente operações que são usadas por outras atividades de **ReceiveActivity** no fluxo de trabalho.  
  
## Consulte também  
 [How to: Implement a WCF Contract Operation \(Legacy\)](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md)   
 [How to: Invoke a WCF Contract Operation \(Legacy\)](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md)   
 [Legacy Designer for Windows Workflow Foundation UI Help](../workflow-designer/legacy-designer-for-windows-workflow-foundation-ui-help.md)