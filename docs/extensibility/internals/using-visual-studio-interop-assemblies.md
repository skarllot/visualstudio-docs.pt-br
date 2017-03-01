---
title: Usando Assemblies de interoperabilidade do Visual Studio | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio, interop assemblies
- interop assemblies, Visual Studio
- managed VSPackages, interop assemblies
ms.assetid: 1043eb95-4f0d-4861-be21-2a25395b3b3c
caps.latest.revision: 33
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
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: 9762ba0404e739c167cadc3e9d3106c7f3ee14e8
ms.lasthandoff: 02/22/2017

---
# <a name="using-visual-studio-interop-assemblies"></a>Usando Assemblies de interoperabilidade do Visual Studio
Assemblies de interoperabilidade Visual Studio permitem que aplicativos gerenciados acessar as interfaces COM que fornecem a extensibilidade do Visual Studio. Existem algumas diferenças entre retas COM interfaces e suas versões de interoperabilidade. Por exemplo, HRESULTs são geralmente representados como valores int e precisam ser manipulados da mesma forma como exceções e parâmetros (especialmente os parâmetros de saída) são tratados de maneira diferente.  
  
## <a name="handling-hresults-returned-to-managed-code-from-com"></a>Manipulando HRESULTs retornados ao código gerenciado de COM  
 Quando você chama uma interface COM de código gerenciado, examine o valor HRESULT e lançar uma exceção se necessário. A <xref:Microsoft.VisualStudio.ErrorHandler>classe contém o <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>método que lança uma exceção de COM, dependendo do valor de HRESULT passado para o proprietário.</xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> </xref:Microsoft.VisualStudio.ErrorHandler>  
  
 Por padrão, <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>gera uma exceção sempre que é passado um HRESULT que tem um valor menor que zero.</xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> Em casos onde tais HRESULTs são valores aceitáveis e nenhuma exceção deve ser lançada, os valores de HRESULTS adicionais devem ser passados para <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>depois que os valores são testados.</xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> Se o HRESULT que está sendo testado corresponde todos explicitamente passados para os valores HRESULT <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>, nenhuma exceção é lançada.</xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>  
  
> [!NOTE]
>  O <xref:Microsoft.VisualStudio.VSConstants>classe contém constantes para HRESULTS comuns, por exemplo, <xref:Microsoft.VisualStudio.VSConstants.S_OK>e <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL>, e [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] HRESULTS, por exemplo, <xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA>e <xref:Microsoft.VisualStudio.VSConstants.VS_E_UNSUPPORTEDFORMAT>.</xref:Microsoft.VisualStudio.VSConstants.VS_E_UNSUPPORTEDFORMAT> </xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA> </xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL> </xref:Microsoft.VisualStudio.VSConstants.S_OK> </xref:Microsoft.VisualStudio.VSConstants> <xref:Microsoft.VisualStudio.VSConstants>também fornece os <xref:Microsoft.VisualStudio.ErrorHandler.Succeeded%2A> <xref:Microsoft.VisualStudio.ErrorHandler.Failed%2A>métodos, que correspondem às macros êxito e falha no COM.</xref:Microsoft.VisualStudio.ErrorHandler.Failed%2A> e</xref:Microsoft.VisualStudio.ErrorHandler.Succeeded%2A></xref:Microsoft.VisualStudio.VSConstants>  
  
 Por exemplo, considere a seguinte chamada de função, na qual <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL>é um valor de retorno aceitável, mas qualquer outro HRESULT menor que zero representa um erro.</xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL>  
  
 [!code-vb[&#1; VSSDKHRESULTInformation](../../extensibility/internals/codesnippet/VisualBasic/using-visual-studio-interop-assemblies_1.vb) ] 
 [!code-cs [VSSDKHRESULTInformation n º&1;](../../extensibility/internals/codesnippet/CSharp/using-visual-studio-interop-assemblies_1.cs)]  
  
 Se existir mais de um retorno dos valores aceitáveis, valores adicionais de HRESULT apenas podem ser acrescentados à lista na chamada para <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>.</xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>  
  
 [!code-vb[N º&2; VSSDKHRESULTInformation](../../extensibility/internals/codesnippet/VisualBasic/using-visual-studio-interop-assemblies_2.vb) ] 
 [!code-cs [VSSDKHRESULTInformation n º&2;](../../extensibility/internals/codesnippet/CSharp/using-visual-studio-interop-assemblies_2.cs)]  
  
## <a name="returning-hresults-to-com-from-managed-code"></a>Retornando HRESULTS para COM a partir do código gerenciado  
 Se nenhuma exceção ocorrer, o código gerenciado retorna <xref:Microsoft.VisualStudio.VSConstants.S_OK>para a função COM que chamado proprietário.</xref:Microsoft.VisualStudio.VSConstants.S_OK> Interoperabilidade COM oferece suporte a exceções comuns que são fortemente tipadas em código gerenciado. Por exemplo, um método que recebe um inaceitável `null` argumento lança um <xref:System.ArgumentNullException>.</xref:System.ArgumentNullException>  
  
 Se não tiver certeza de qual exceção a ser lançada, mas você sabe o HRESULT você deseja retornar ao COM, você pode usar o <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A>método lançar uma exceção apropriada.</xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> Isso funciona mesmo com um erro diferente do padrão, por exemplo, <xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA>.</xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA> <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A>tenta mapear o HRESULT é passado para ele a uma exceção com rigidez de tipos.</xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> Se não for possível, ele lança uma exceção COM genéricos em vez disso. O resultado final é que o HRESULT que você passe a <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A>partir do código gerenciado é retornado para a função COM que chamado proprietário.</xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A>  
  
> [!NOTE]
>  Exceções de comprometer o desempenho e servem para indicar as condições de programa anormal. Condições que ocorrem com frequência devem ser tratada embutidas, em vez de uma exceção gerada.  
  
## <a name="iunknown-parameters-passed-as-type-void"></a>IUnknown parâmetros passados como tipo void * *  
 Procure [os parâmetros são definidos como tipo out] `void **` no COM a interface, mas que são definidos como `[``iid_is``]` no [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] protótipo do método assembly de interoperabilidade.  
  
 Às vezes, uma interface COM gera um `IUnknown` objeto e a interface COM transmiti-la como tipo `void **`. Essas interfaces são especialmente importantes porque se a variável for definida como [out] no IDL, então o `IUnknown` objeto é a contagem de referência com o `AddRef` método. Um vazamento de memória ocorre se o objeto não é tratado corretamente.  
  
> [!NOTE]
>  Um `IUnknown` objeto criado pela interface COM e retornados em uma variável [out] faz com que um vazamento de memória se não for explicitamente liberado.  
  
 Gerenciado métodos que manipulam esses objetos devem ser tratadas <xref:System.IntPtr>como um ponteiro para um `IUnknown` de objeto e chamar o <xref:System.Runtime.InteropServices.Marshal.GetObjectForIUnknown%2A>método para obter o objeto.</xref:System.Runtime.InteropServices.Marshal.GetObjectForIUnknown%2A> </xref:System.IntPtr> O chamador deve, em seguida, converter o valor de retorno para qualquer tipo é apropriado. Quando o objeto não é necessária, plano <xref:System.Runtime.InteropServices.Marshal.Release%2A>de liberada.</xref:System.Runtime.InteropServices.Marshal.Release%2A>  
  
 A seguir está um exemplo de chamar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A>método e manipulação o `IUnknown` objeto corretamente:</xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A>  
  
```  
MyClass myclass;  
Object object;  
IntPtr pObj;  
Guid iid = Typeof(MyClass).Guid;  
int hr = windowFrame.QueryViewInterface(ref iid, out pObj);     
if (NativeMethods.Succeeded(hr))   
{  
    try   
    {  
        object = Marshal.GetObjectForIUnknown(pObj);  
        myclass = object;  
    }  
    finally   
    {  
        Marshal.Release(pObj);  
    }  
}  
else   
{  
    // error calling QueryViewInterface  
}  
```  
  
> [!NOTE]
>  Os métodos a seguir são conhecidos para transmitir `IUnknown` ponteiros de objeto como tipo <xref:System.IntPtr>.</xref:System.IntPtr> Tratá-los conforme descrito nesta seção.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.InitializeForOwner%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.InitializeForOwner%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetNestedHierarchy%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetNestedHierarchy%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.CreateProject%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.CreateProject%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2.get_CfgType%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2.get_CfgType%2A>  
  
## <a name="optional-out-parameters"></a>Opcional [parâmetros out]  
 Procure os parâmetros que são definidos como [out] o tipo de dados (`int`, `object`, e assim por diante) no COM a interface, mas que são definidos como matrizes de tipo de dados no [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] protótipo do método assembly de interoperabilidade.  
  
 Alguns COM interfaces, como <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A>, tratam [parâmetros opcionais out].</xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A> Se um objeto não é necessário, essas interfaces COM retornam um `null` ponteiro como o valor desse parâmetro, em vez de criar o objeto [out]. Esse comportamento é esperado. Para essas interfaces, `null` ponteiros são considerados como parte do comportamento correto do VSPackage e nenhum erro será retornado.  
  
 Como o CLR não permite o valor de um parâmetro [out] para ser `null`, parte do comportamento padrão dessas interfaces não está disponível diretamente no código gerenciado. O [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] métodos do assembly de interoperabilidade para interfaces afetados contornar o problema definindo os parâmetros relevantes como matrizes, como o CLR permite a passagem de `null` matrizes.  
  
 Implementações gerenciadas desses métodos devem colocar um `null` matriz para o parâmetro quando não há nada a ser retornado. Caso contrário, crie uma matriz de um elemento do tipo correto e colocar o valor de retorno na matriz.  
  
 Gerenciado por métodos que recebem informações de interfaces com [out] opcional parâmetros recebem o parâmetro como uma matriz. Basta examine o valor do primeiro elemento da matriz. Se não for `null`, trate o primeiro elemento como se fosse o parâmetro original.  
  
## <a name="passing-constants-in-pointer-parameters"></a>Constantes de passar parâmetros de ponteiro  
 Procure os parâmetros que são definidas como [in] ponteiros na interface COM, mas que são definidos como um <xref:System.IntPtr>Digite o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] protótipo do método assembly de interoperabilidade.</xref:System.IntPtr>  
  
 Um problema semelhante ocorre quando passa de uma interface COM um valor especial, como 0, -1 ou – 2, em vez de um ponteiro de objeto. Ao contrário de [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)], o CLR não permite constantes ser convertido como objetos. Em vez disso, o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] assembly de interoperabilidade define o parâmetro como um <xref:System.IntPtr>tipo.</xref:System.IntPtr>  
  
 Implementações gerenciadas desses métodos devem tirar proveito do fato de que o <xref:System.IntPtr>classe tem ambos `int` e `void *` construtores para criar um <xref:System.IntPtr>de um objeto ou uma constante de inteiro, conforme apropriado.</xref:System.IntPtr> </xref:System.IntPtr>  
  
 Gerenciado por métodos que recebem <xref:System.IntPtr>parâmetros desse tipo devem usar o <xref:System.IntPtr>Digite operadores de conversão para lidar com os resultados.</xref:System.IntPtr> </xref:System.IntPtr> Primeiro converter o <xref:System.IntPtr>para `int` e testá-lo em constantes de inteiro relevantes.</xref:System.IntPtr> Se não há valores correspondentes, convertê-lo em um objeto do tipo necessário e continue.  
  
 Para exemplos, consulte <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>e <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenSpecificEditor%2A>.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenSpecificEditor%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>  
  
## <a name="ole-return-values-passed-as-out-parameters"></a>OLE retornar valores passados como [parâmetros out]  
 Procure métodos que têm um `retval` o valor de retorno na interface COM, mas que têm um `int` retornar valor e um [parâmetro de matriz em out] adicional a [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] protótipo do método assembly de interoperabilidade. Deve ficar claro que esses métodos exigem tratamento especial, pois o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] protótipos de método do assembly de interoperabilidade tem um parâmetro a mais que os métodos de interface COM.  
  
 Várias interfaces COM que lidam com a atividade OLE enviar informações sobre o status OLE voltar ao programa de chamada armazenado no `retval` retornar o valor da interface. Em vez de usar um valor de retorno correspondente [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] métodos do assembly de interoperabilidade enviam as informações de volta para o programa de chamada armazenado em [out] o parâmetro de matriz.  
  
 Implementações gerenciadas desses métodos devem criar uma matriz de elemento único do mesmo tipo como o parâmetro [out] e colocá-lo no parâmetro. O valor do elemento da matriz deve ser o mesmo que o apropriada COM `retval`.  
  
 Métodos gerenciados que chamam as interfaces desse tipo devem receber o primeiro elemento da matriz [out]. Esse elemento pode ser tratado como se fosse um `retval` retornar o valor da interface COM correspondente.  
  
## <a name="see-also"></a>Consulte também  
 [Interoperação com código não gerenciado](http://msdn.microsoft.com/Library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)
