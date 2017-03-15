---
title: "Atualizando valores de propriedade na janela Propriedades | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Janela de propriedades, atualização de valores de propriedade"
  - "valores de propriedade, a atualização na janela Propriedades"
ms.assetid: 9358e8c3-b9d2-4fd4-aaab-cf48d1526db4
caps.latest.revision: 9
caps.handback.revision: 9
manager: "douge"
---
# Atualizando valores de propriedade na janela Propriedades
Há duas maneiras de manter o **propriedades** janela em sincronia com as alterações de valor de propriedade. A primeira é chamar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> interface, que fornece acesso à funcionalidade básica de janelas, incluindo acesso a e a criação de janelas de ferramenta e de documentos fornecidos pelo ambiente de. As etapas a seguir descrevem esse processo de sincronização.  
  
## Atualizando valores de propriedade usando IVsUIShell  
  
#### Para atualizar os valores de propriedade usando a interface IVsUIShell  
  
1.  Chamar <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> \(por meio de <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> service\) sempre que os VSPackages, projetos, ou editores precisam criar ou enumerar as janelas de ferramenta ou documento.  
  
2.  Implementar <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.RefreshPropertyBrowser%2A> para manter o **propriedades** janela em sincronia com alterações de propriedade de um projeto \(ou qualquer outro objeto selecionado que está sendo visitado o **propriedades** janela\) sem implementar <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> e disparando <xref:Microsoft.VisualStudio.OLE.Interop.IPropertyNotifySink.OnChanged%2A> eventos.  
  
3.  Implementar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> métodos <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.AdviseHierarchyEvents%2A> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.UnadviseHierarchyEvents%2A> para estabelecer e desativar, respectivamente, a notificação de cliente de eventos de hierarquia sem exigir a hierarquia para implementar <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>.  
  
## Atualizando valores de propriedade usando IConnection  
 A segunda maneira de manter o **propriedades** janela em sincronia com as alterações de valor de propriedade é implementar `IConnection` no objeto conectável para indicar a existência das interfaces de saída. Se você deseja localizar o nome da propriedade, derivar seu objeto de <xref:System.ComponentModel.ICustomTypeDescriptor>. O <xref:System.ComponentModel.ICustomTypeDescriptor> implementação pode modificar os descritores de propriedade retorna e altere o nome de uma propriedade. Para localizar a descrição, criar um atributo que deriva de <xref:System.ComponentModel.DescriptionAttribute> e substitui a propriedade Description.  
  
#### Considerações na implementação da interface IConnection  
  
1.  `IConnection` fornece acesso a um objeto de enumerador subdiretório com o <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints> interface. Ele também fornece acesso a conexão ponto subpropriedades objetos, cada um dos que implementa o <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> interface.  
  
2.  Qualquer objeto procurar é responsável por implementar uma <xref:Microsoft.VisualStudio.OLE.Interop.IPropertyNotifySink> eventos. O **propriedades** janela informará para o conjunto de eventos por meio de `IConnection`.  
  
3.  Um ponto de conexão controla quantas conexões \(uma ou mais\) permite em sua implementação de <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Advise%2A>. Um ponto de conexão que permite apenas uma interface pode retornar <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL> do <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.EnumConnections%2A> método.  
  
4.  Um cliente pode chamar o `IConnection` interface para obter acesso a um objeto de enumerador subdiretório com o <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints> interface. O <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints> interface pode então ser chamada para enumerar os pontos de conexão para cada interface de saída IID \(ID\).  
  
5.  `IConnection` também pode ser chamado para obter acesso aos objetos de subpropriedades de ponto de conexão com o <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> interface para cada saída IID. Por meio de <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> interface, um cliente inicia ou termina um loop comunicado com o objeto conectável e a sincronização do cliente. O cliente também pode chamar o <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> interface para obter um objeto enumerator com o <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnections> interface para enumerar as conexões que ele conhece.  
  
## Consulte também  
 [Anunciando a seleção da janela de propriedade de controle](/visual-cpp/misc/announcing-property-window-selection-tracking)   
 [Estendendo propriedades](../extensibility/internals/extending-properties.md)