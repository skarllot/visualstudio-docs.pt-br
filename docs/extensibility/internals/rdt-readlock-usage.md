---
title: Uso de RDT_ReadLock | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- RDT_ReadLock
- visible
- RDT_EditLock
- invisible
ms.assetid: b935fc82-9d6b-4a8d-9b70-e9a5c5ad4a55
caps.latest.revision: 8
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
ms.sourcegitcommit: e7575b914f0645882f3570bdbe29221f2f8130cc
ms.openlocfilehash: a8ea44ef2dea3b3c4ebd29cf95b1886e2028e2c3
ms.lasthandoff: 02/22/2017

---
# <a name="rdtreadlock-usage"></a>Uso de RDT_ReadLock

<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS>é um sinalizador que fornece a lógica para bloquear um documento no executando o documento tabela (RDT), que é a lista de todos os documentos abertos no momento no IDE do Visual Studio.</xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> Este sinalizador determina quando os documentos forem abertos e, se um documento está visível na interface do usuário ou mantido invisivelmente na memória.

Em geral, você usaria <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS>quando uma das seguintes opções for verdadeira:</xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS>

- Quando desejar abrir um documento de forma invisível e somente leitura, mas ele ainda não foi estabelecida que <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>devem seu proprietário.</xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>

- Quando você deseja que o usuário para ser solicitado a salvar um documento que foi aberto invisivelmente antes do usuário exibida na interface do usuário, ele e, em seguida, tentou fechá-lo.

## <a name="how-to-manage-visible-and-invisible-documents"></a>Gerenciar documentos visíveis e invisíveis

Quando um usuário abre um documento na interface do usuário, um <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>proprietário do documento deve ser estabelecido e um <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS>sinalizador deve ser definido.</xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> </xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> Se nenhum <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>proprietário pode ser estabelecido, em seguida, o documento não será salvo quando o usuário clica **Salvar tudo** ou fecha o IDE.</xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> Isso significa que se um documento está aberto invisivelmente onde ele é modificado na memória, e o usuário é solicitado a salvar o documento no desligamento ou salvo se **Salvar tudo** for escolhido, então um `RDT_ReadLock` não pode ser usado. Em vez disso, você deve usar um `RDT_EditLock` e registrar um <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder>quando um <xref:Microsoft.VisualStudio.Shell.Interop.__VSREGDOCLOCKHOLDER>sinalizador.</xref:Microsoft.VisualStudio.Shell.Interop.__VSREGDOCLOCKHOLDER> </xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder>

## <a name="rdteditlock-and-document-modification"></a>RDT_EditLock e modificação de documentos

O sinalizador anterior mencionado indica que produzirá a abertura invisível do documento seu `RDT_EditLock` quando o documento for aberto pelo usuário em um visível **DocumentWindow**. Quando isso ocorre, o usuário é apresentado com uma **salvar** Avisar quando o visível **DocumentWindow** está fechado. <xref:Microsoft.VisualStudio.Package.Automation.OAProject.CodeModel>as implementações que utilizam o <xref:Microsoft.VisualStudio.Shell.Interop.IVsInvisibleEditorManager>serviço inicialmente funciona quando somente um `RDT_ReadLock` é obtido (isto é, quando o documento for aberto invisivelmente analisar informações).</xref:Microsoft.VisualStudio.Shell.Interop.IVsInvisibleEditorManager></xref:Microsoft.VisualStudio.Package.Automation.OAProject.CodeModel> Posteriormente, se o documento deve ser modificado, em seguida, o bloqueio será atualizado para uma fraca **RDT_EditLock**. Se o usuário abre o documento em um visível **DocumentWindow**, o `CodeModel`do fraco `RDT_EditLock` é liberado.

Se o usuário fecha o **DocumentWindow** e escolhe **não** quando solicitado a salvar o documento aberto, o `CodeModel` implementação descarta todas as informações do documento e reabra o documento de disco invisivelmente na próxima vez em que mais informações são necessárias para o documento. O recurso desse comportamento é uma instância em que o usuário abre o **DocumentWindow** do documento aberto invisível, modifica, fechá-lo e, em seguida, escolhe **não** quando for solicitado a salvar o documento. Nesse caso, se o documento tem uma `RDT_ReadLock`, o documento não será fechado, na verdade, e o documento modificado permanecerá aberto invisivelmente na memória, mesmo que o usuário optou por não salvar o documento.

Se a abertura invisível do documento usa uma fraca `RDT_EditLock`, em seguida, ele gera o bloqueio quando o usuário abre o documento visivelmente e outros bloqueios não são mantidos. Quando o usuário fechar o **DocumentWindow** e escolhe **não** quando solicitado a salvar o documento, em seguida, o documento deve ser fechado da memória. Isso significa que o cliente invisível deve escutar eventos RDT acompanhar esta ocorrência. Na próxima vez em que o documento é necessário, o documento deverá ser reaberto.
