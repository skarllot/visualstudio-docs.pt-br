---
title: "Informa&#231;&#245;es de HRESULT em c&#243;digo gerenciado | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "HRESULT, VSPackages gerenciados"
  - "VSPackages, Informações de HRESULT"
ms.assetid: 0795ee94-17a8-4327-bf57-27cd5e312a4c
caps.latest.revision: 29
caps.handback.revision: 29
manager: "douge"
---
# Informa&#231;&#245;es de HRESULT em c&#243;digo gerenciado
A interação entre código gerenciado e COM pode causar problemas quando os valores de retorno HRESULT são encontrados.  
  
 Em uma interface COM um valor de retorno HRESULT pode executar estas funções:  
  
-   Fornecer informações de erro \(por exemplo, <xref:Microsoft.VisualStudio.VSConstants.E_INVALIDARG>\).  
  
-   Fornecer informações de status sobre o comportamento normal do programa.  
  
 Quando o COM chamar código gerenciado, HRESULTs podem causar esses problemas:  
  
-   Funções COM que retornam valores HRESULT menor que zero \(códigos de falha\) geram exceções.  
  
-   OS métodos que retornam regularmente dois ou mais códigos de sucesso diferentes, por exemplo, <xref:Microsoft.VisualStudio.VSConstants.S_OK> ou <xref:Microsoft.VisualStudio.VSConstants.S_FALSE>, não podem ser diferenciadas.  
  
 Porque muitas do [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] funções COM retornam valores HRESULT menor que zero ou retornam códigos de sucesso diferentes, o [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] assemblies de interoperabilidade foram gravados para que as assinaturas de método são preservadas. Todos os [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] são métodos de interoperabilidade do `int` tipo. A camada de interoperabilidade sem alteração e sem gerar exceções são passados valores HRESULT.  
  
 Como uma função COM retorna um HRESULT para o método gerenciado que faz a chamada, o método de chamada deve verificar o HRESULT e lançar exceções conforme necessário.  
  
## Manipulando HRESULTs retornados ao código gerenciado de COM  
 Quando você chama uma interface COM de código gerenciado, examine o valor HRESULT e lançar uma exceção se necessário. O <xref:Microsoft.VisualStudio.ErrorHandler> classe contém o <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> método que lança uma exceção de COM, dependendo do valor de HRESULT é passado para ele.  
  
 Por padrão, <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> gera uma exceção sempre que é passado um HRESULT que tem um valor menor que zero. Em casos onde tais HRESULTs são valores aceitáveis e nenhuma exceção deve ser lançada, os valores de HRESULTS adicionais devem ser passados para <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> depois que os valores são testados. Se o HRESULT que está sendo testado corresponde todos explicitamente passados para os valores HRESULT <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>, nenhuma exceção é lançada.  
  
> [!NOTE]
>  O <xref:Microsoft.VisualStudio.VSConstants> classe contém constantes para HRESULTS comuns, por exemplo, <xref:Microsoft.VisualStudio.VSConstants.S_OK> e <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL>, e [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] HRESULTS, por exemplo, <xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA> e <xref:Microsoft.VisualStudio.VSConstants.VS_E_UNSUPPORTEDFORMAT>.<xref:Microsoft.VisualStudio.VSConstants> também fornece a <xref:Microsoft.VisualStudio.ErrorHandler.Succeeded%2A> e <xref:Microsoft.VisualStudio.ErrorHandler.Failed%2A> métodos que correspondem às macros êxito e falha no COM.  
  
 Por exemplo, considere a seguinte chamada de função, na qual <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL> é um valor de retorno aceitável, mas qualquer outro HRESULT menor que zero representa um erro.  
  
 [!code-vb[VSSDKHRESULTInformation#1](../extensibility/internals/codesnippet/VisualBasic/hresult-information-in-managed-code_1.vb)]
 [!code-cs[VSSDKHRESULTInformation#1](../extensibility/internals/codesnippet/CSharp/hresult-information-in-managed-code_1.cs)]  
  
 Se existir mais de um retorno dos valores aceitáveis, valores adicionais de HRESULT apenas podem ser acrescentados à lista na chamada para <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>.  
  
 [!code-vb[VSSDKHRESULTInformation#2](../extensibility/internals/codesnippet/VisualBasic/hresult-information-in-managed-code_2.vb)]
 [!code-cs[VSSDKHRESULTInformation#2](../extensibility/internals/codesnippet/CSharp/hresult-information-in-managed-code_2.cs)]  
  
## Retornando HRESULTS para COM a partir do código gerenciado  
 Se nenhuma exceção ocorrer, gerenciados código retorna <xref:Microsoft.VisualStudio.VSConstants.S_OK> para a função COM que o chamou. Interoperabilidade COM oferece suporte a exceções comuns que são fortemente tipadas em código gerenciado. Por exemplo, um método que recebe um inaceitável `null` argumento lança um <xref:System.ArgumentNullException>.  
  
 Se não tiver certeza de qual exceção a ser lançada, mas você sabe o HRESULT você deseja retornar ao COM, você pode usar o <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> método lançar uma exceção apropriada. Isso funciona mesmo com um erro diferente do padrão, por exemplo, <xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA>.<xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> tenta mapear o HRESULT é passado para ele a uma exceção com rigidez de tipos. Se não for possível, ele lança uma exceção COM genéricos em vez disso. O resultado final é que o HRESULT que você passe a <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> do código gerenciado é retornado para a função COM que o chamou.  
  
> [!NOTE]
>  Exceções de comprometer o desempenho e servem para indicar as condições de programa anormal. Condições que ocorrem com freqüência devem ser tratada embutidas, em vez de uma exceção gerada.  
  
## Consulte também  
 [VSPackages gerenciados](../misc/managed-vspackages.md)   
 [Interoperação com código não gerenciado](../Topic/Interoperating%20with%20Unmanaged%20Code.md)   
 [Como mapear HRESULTs e exceções](../Topic/How%20to:%20Map%20HRESULTs%20and%20Exceptions.md)   
 [Compilando componentes COM para interoperação](http://msdn.microsoft.com/pt-br/7a2c657a-cfef-40f0-bed3-7c2c0ac4abdf)   
 [VSPackages gerenciados](../misc/managed-vspackages.md)