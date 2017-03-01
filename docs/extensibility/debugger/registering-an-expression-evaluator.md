---
title: "Registrando um avaliador de expressão | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluators, registering
ms.assetid: 236be234-e05f-4ad8-9200-24ce51768ecf
caps.latest.revision: 13
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
ms.openlocfilehash: c96edd48b36bdabb5b74e2b913630d4630ca32e8
ms.lasthandoff: 02/22/2017

---
# <a name="registering-an-expression-evaluator"></a>Registrando um avaliador de expressão
> [!IMPORTANT]
>  No Visual Studio 2015, essa forma de implementar os avaliadores de expressão foi preterida. Para obter informações sobre como implementar os avaliadores de expressão do CLR, consulte [avaliadores de expressão de CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [amostra do avaliador de expressão gerenciado](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 O avaliador de expressão (EE) deve ser registrado como uma fábrica de classes com o ambiente COM Windows e o Visual Studio. Um EE é implementado como uma DLL para que ele pode ser injetado no espaço de endereço debug engine (DE) ou o espaço de endereço do Visual Studio, dependendo de qual entidade instancia o EE.  
  
## <a name="managed-code-expression-evaluator"></a>Avaliador de expressão de código gerenciado  
 Um código gerenciado EE é implementado como uma biblioteca de classe, que é uma DLL que se registra com o ambiente COM, normalmente iniciado com uma chamada para o Programa VSIP, **regpkg.exe**. O processo de escrever as chaves do registro para o ambiente COM é manipulado automaticamente.  
  
 Um método da classe principal é marcado com a <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute>indicando que o método é chamado quando a DLL está sendo registrada com COM.</xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute> Esse método de registro, geralmente chamado `RegisterClass`, executa a tarefa de registrar a DLL com o Visual Studio. Um correspondente `UnregisterClass` (marcados com o <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute>), desfazer os efeitos da `RegisterClass` quando a DLL é desinstalada.</xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute>  
  
 As mesmas entradas de registro são feitas para um EE escrito em código não gerenciado; a única diferença é que não há nenhuma função auxiliar como `SetEEMetric` para fazer o trabalho para você. Um exemplo desse processo de registro/cancelamento de registro tem esta aparência:  
  
### <a name="example"></a>Exemplo  
 Essa função mostra como um código gerenciado EE registra e cancela o registro em si com o Visual Studio.  
  
```c#  
namespace EEMC  
{  
    [GuidAttribute("462D4A3D-B257-4AEE-97CD-5918C7531757")]  
    public class EEMCClass : IDebugExpressionEvaluator  
    {  
        #region Register and unregister.  
        private static Guid guidMycLang = new Guid("462D4A3E-B257-4AEE-97CD-5918C7531757");  
        private static string languageName = "MyC";  
        private static string eeName = "MyC Expression Evaluator";  
  
        private static Guid guidMicrosoftVendor = new Guid("994B45C4-E6E9-11D2-903F-00C04FA302A1");  
        private static Guid guidCOMPlusOnlyEng = new Guid("449EC4CC-30D2-4032-9256-EE18EB41B62B");  
        private static Guid guidCOMPlusNativeEng = new Guid("92EF0900-2251-11D2-B72E-0000F87572EF");  
  
        /// <summary>  
        /// Register the expression evaluator.  
        /// Set "project properties/configuration properties/build/register for COM interop" to true.  
        /// </summary>  
         [ComRegisterFunctionAttribute]  
        public static void RegisterClass(Type t)  
        {  
            // Get Visual Studio version (set by regpkg.exe)  
            string hive = Environment.GetEnvironmentVariable("EnvSdk_RegKey");  
            string s = @"SOFTWARE\Microsoft\VisualStudio\"  
                        + hive  
                        + @"\AD7Metrics\ExpressionEvaluator";  
  
            RegistryKey rk = Registry.LocalMachine.CreateSubKey(s);  
            if (rk == null)  return;  
  
            rk = rk.CreateSubKey(guidMycLang.ToString("B"));  
            rk = rk.CreateSubKey(guidMicrosoftVendor.ToString("B"));  
            rk.SetValue("CLSID", t.GUID.ToString("B"));  
            rk.SetValue("Language", languageName);  
            rk.SetValue("Name", eeName);  
  
            rk = rk.CreateSubKey("Engine");  
            rk.SetValue("0", guidCOMPlusOnlyEng.ToString("B"));  
            rk.SetValue("1", guidCOMPlusNativeEng.ToString("B"));  
        }  
        /// <summary>  
        /// Unregister the expression evaluator.  
        /// </summary>  
         [ComUnregisterFunctionAttribute]  
        public static void UnregisterClass(Type t)  
        {  
            // Get Visual Studio version (set by regpkg.exe)  
            string hive = Environment.GetEnvironmentVariable("EnvSdk_RegKey");  
            string s = @"SOFTWARE\Microsoft\VisualStudio\"  
                        + hive  
                        + @"\AD7Metrics\ExpressionEvaluator\"  
                        + guidMycLang.ToString("B");  
            RegistryKey key = Registry.LocalMachine.OpenSubKey(s);  
            if (key != null)  
            {  
                key.Close();  
                Registry.LocalMachine.DeleteSubKeyTree(s);  
            }  
        }  
    }  
}  
```  
  
## <a name="unmanaged-code-expression-evaluator"></a>Avaliador de expressão de código não gerenciado  
 A DLL EE implementa o `DllRegisterServer` função ao se registrar com o ambiente COM, bem como o Visual Studio.  
  
> [!NOTE]
>  O código de registro de exemplo de código MyCEE pode ser encontrado no dllentry.cpp arquivo, que está localizado na instalação do VSIP em EnVSDK\MyCPkgs\MyCEE.  
  
### <a name="dll-server-process"></a>Processo de DLL do servidor  
 Ao registrar EE, o servidor DLL:  
  
1.  Registra sua fábrica de classes `CLSID` de acordo com as convenções de COM normal.  
  
2.  Chama a função auxiliar `SetEEMetric` para registrar com o Visual Studio, as métricas EE mostradas na tabela a seguir. A função `SetEEMetric` e as métricas especificadas abaixo são parte da biblioteca dbgmetric.lib. Consulte [SDK auxiliares para depuração](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) para obter detalhes.  
  
    |Métrica|Descrição|  
    |------------|-----------------|  
    |`metricCLSID`|`CLSID`da fábrica de classe EE|  
    |`metricName`|Nome do EE como uma cadeia de caracteres de exibição|  
    |`metricLanguage`|O nome do idioma que o EE é projetado para avaliar|  
    |`metricEngine`|`GUID`s dos mecanismos de depuração (DE) que funcionam com esse EE|  
  
    > [!NOTE]
    >  O `metricLanguage``GUID` identifica o idioma por nome, mas ele é o `guidLang` argumento `SetEEMetric` que seleciona o idioma. Quando o compilador gera o arquivo de informações de depuração, deve gravar apropriado `guidLang` para que o DE saiba qual EE usar. O DE geralmente solicita que o provedor de símbolo para esse idioma `GUID`, que é armazenado no arquivo de informações de depuração.  
  
3.  Registra com o Visual Studio criando chaves em HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\*x. y*, onde *x. y* é a versão do Visual Studio para registrar.  
  
### <a name="example"></a>Exemplo  
 Essa função mostra como um código não gerenciado (C++) EE registra e cancela o registro em si com o Visual Studio.  
  
```cpp#  
/*---------------------------------------------------------  
  Registration  
-----------------------------------------------------------*/  
#ifndef LREGKEY_VISUALSTUDIOROOT  
    #define LREGKEY_VISUALSTUDIOROOT L"Software\\Microsoft\\VisualStudio\\8.0"  
#endif  
  
static HRESULT RegisterMetric( bool registerIt )  
{  
    // check where we should register  
    const ULONG cchBuffer = _MAX_PATH;  
    WCHAR wszRegistrationRoot[cchBuffer];  
    DWORD cchFreeBuffer = cchBuffer - 1;  
    wcscpy(wszRegistrationRoot, LREGKEY_VISUALSTUDIOROOT_NOVERSION);  
    wcscat(wszRegistrationRoot, L"\\");  
  
    // this is Environment SDK specific  
    // we check for  EnvSdk_RegKey environment variable to  
    // determine where to register  
    DWORD cchDefRegRoot = lstrlenW(LREGKEY_VISUALSTUDIOROOT_NOVERSION) + 1;  
    cchFreeBuffer = cchFreeBuffer - cchDefRegRoot;  
    DWORD cchEnvVarRead = GetEnvironmentVariableW(  
        /* LPCTSTR */ L"EnvSdk_RegKey", // environment variable name  
        /* LPTSTR  */ &wszRegistrationRoot[cchDefRegRoot],// buffer for variable value  
        /* DWORD   */ cchFreeBuffer);// size of buffer  
    if (cchEnvVarRead >= cchFreeBuffer)  
        return E_UNEXPECTED;  
    // If the environment variable does not exist then we must use   
    // LREGKEY_VISUALSTUDIOROOT which has the version number.  
    if (0 == cchEnvVarRead)  
        wcscpy(wszRegistrationRoot, LREGKEY_VISUALSTUDIOROOT);  
  
    if (registerIt)  
    {  
        SetEEMetric(guidMycLang,  
                    guidMicrosoftVendor,  
                    metricCLSID,  
                    CLSID_MycEE,  
                    wszRegistrationRoot );  
        SetEEMetric(guidMycLang,  
                    guidMicrosoftVendor,  
                    metricName,  
                    GetString(IDS_INFO_MYCDESCRIPTION),  
                    wszRegistrationRoot );  
        SetEEMetric(guidMycLang,  
                    guidMicrosoftVendor,  
                    metricLanguage, L"MyC",  
                    wszRegistrationRoot);  
  
        GUID engineGuids[2];  
        engineGuids[0] = guidCOMPlusOnlyEng;  
        engineGuids[1] = guidCOMPlusNativeEng;  
        SetEEMetric(guidMycLang,  
                    guidMicrosoftVendor,  
                    metricEngine,  
                    engineGuids,  
                    2,  
                    wszRegistrationRoot);  
    }  
    else  
    {  
        RemoveEEMetric( guidMycLang,  
                        guidMicrosoftVendor,  
                        metricCLSID,  
                        wszRegistrationRoot);  
        RemoveEEMetric( guidMycLang,  
                        guidMicrosoftVendor,  
                        metricName,  
                        wszRegistrationRoot );  
        RemoveEEMetric( guidMycLang,  
                        guidMicrosoftVendor,  
                        metricLanguage,  
                        wszRegistrationRoot );  
        RemoveEEMetric( guidMycLang,  
                        guidMicrosoftVendor,  
                        metricEngine,  
                        wszRegistrationRoot );  
    }  
  
    return S_OK;  
}  
```  
  
## <a name="see-also"></a>Consulte também  
 [Escrevendo um avaliador de expressão de CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [Auxiliares do SDK para depuração](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
