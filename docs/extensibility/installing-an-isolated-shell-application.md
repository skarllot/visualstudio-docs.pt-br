---
title: "Instalação de um aplicativo de Shell isolado | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Shell [Visual Studio], deploying shell-based applications
- Visual Studio shell, deploying shell-based applications
ms.assetid: 33416226-9083-41b5-b153-10d2bf35c012
caps.latest.revision: 40
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
ms.openlocfilehash: a10da2f771d71e1cbb3997307b3a2b5b614ec502
ms.lasthandoff: 02/22/2017

---
# <a name="installing-an-isolated-shell-application"></a>Instalação de um aplicativo de Shell isolado
Para instalar um aplicativo do Shell, você deve executar as etapas a seguir.  
  
-   Prepare a sua solução.  
  
-   Crie um pacote do Windows Installer (MSI) para seu aplicativo.  
  
-   Crie um bootstrapper de instalação.  
  
 Todo o código de exemplo neste documento proveniente do [exemplo de implantação do Shell](http://go.microsoft.com/fwlink/?LinkId=262245), que pode ser baixado da Galeria de código no site do MSDN. O exemplo mostra os resultados da execução de cada uma dessas etapas.  
  
## <a name="prerequisites"></a>Pré-requisitos  
 Para executar os procedimentos descritos neste tópico, as ferramentas a seguir devem ser instaladas em seu computador.  
  
-   O SDK do Visual Studio  
  
-   O [conjunto de ferramentas XML do Windows Installer](http://go.microsoft.com/fwlink/?LinkId=82720) versão 3.6  
  
 O exemplo também requer o Microsoft Visualization e o SDK de modelagem, que nem todos os shells exigem.  
  
## <a name="preparing-your-solution"></a>Preparando sua solução  
 Por padrão, criar modelos de Shell para pacotes VSIX, mas esse comportamento é destinado principalmente para fins de depuração. Quando você implanta um aplicativo do Shell, você deve usar pacotes MSI para permitir que o acesso ao registro e reinicializações durante a instalação. Para preparar o aplicativo para implantação MSI, execute as etapas a seguir.  
  
#### <a name="to-prepare-a-shell-application-for-msi-deployment"></a>Para preparar um aplicativo de Shell para implantação MSI  
  
1.  Edite cada arquivo .vsixmanifest em sua solução.  
  
     No `Identifier` elemento, adicione um `InstalledByMSI` elemento e um `SystemComponent` elemento e, em seguida, defina seus valores como `true`.  
  
     Esses elementos que impeçam o instalador VSIX de instalar os componentes e o usuário de desinstalá-los usando o **extensões e atualizações** caixa de diálogo.  
  
2.  Para cada projeto que contém um manifesto VSIX, edite as tarefas de compilação para o conteúdo para o local do qual irá instalar o MSI de saída. Incluir o manifesto VSIX na saída da compilação, mas não criar um arquivo. VSIX.  
  
## <a name="creating-an-msi-for-your-shell"></a>Criando um MSI para o Shell  
 Para criar o pacote do MSI, é recomendável que você use o [conjunto de ferramentas XML do Windows Installer](http://go.microsoft.com/fwlink/?LinkId=82720) porque ele oferece maior flexibilidade do que um projeto de instalação padrão.  
  
 No arquivo Product. wxs, defina blocos de detecção e o layout dos componentes do Shell.  
  
 Crie entradas do registro, no arquivo. reg para sua solução e em ApplicationRegistry.wxs.  
  
### <a name="detection-blocks"></a>Blocos de detecção  
 Consiste em um bloco de detecção de um `Property` elemento que especifica um pré-requisito para detectar e um `Condition` elemento que especifica uma mensagem a ser retornada se o pré-requisito não estiver presente no computador. Por exemplo, seu aplicativo de Shell exigirá redistribuível do Microsoft Visual Studio Shell e o bloco de detecção será semelhante a marcação a seguir.  
  
```xml  
<Property Id="ISOSHELLSFX">  
  <RegistrySearch Id="IsoShellSfx" Root="HKLM" Key="Software\Microsoft\DevDiv\vs\Servicing\\$(var.ShellVersion)\IsoShell\$(var.ProductLanguage)" Name="Install" Type="raw" />  
</Property>  
<Property Id="INTSHELLSFX">  
  <RegistrySearch Id="IntShellSfx" Root="HKLM" Key="SOFTWARE\Microsoft\DevDiv\vs\Servicing\$(var.ShellVersion)\devenv\$(var.ProductLanguage)" Name="Install" Type="raw" />  
</Property>  
  
<Condition Message="This application requires $(var.IsoShellName).  Please install $(var.IsoShellName) then run this installer again.">  
  <![CDATA[Installed OR ISOSHELLSFX]]>  
</Condition>  
<Condition Message="This application requires $(var.IntShellName).  Please install $(var.IntShellName) then run this installer again.">  
  <![CDATA[Installed OR INTSHELLSFX]]>  
</Condition>  
  
```  
  
### <a name="layout-of-shell-components"></a>Layout de componentes de Shell  
 Você deve adicionar elementos para identificar a estrutura do diretório de destino e os componentes a serem instalados.  
  
##### <a name="to-set-the-layout-of-shell-components"></a>Para definir o layout dos componentes do Shell  
  
1.  Criar uma hierarquia de `Directory` elementos para representar todos os diretórios para criar no sistema de arquivos no computador de destino, como mostra o exemplo a seguir.  
  
    ```xml  
    <Directory Id="TARGETDIR" Name="SourceDir">  
      <Directory Id="ProgramFilesFolder">  
        <Directory Id="CompanyDirectory" Name="$(var.CompanyName)">  
          <Directory Id="INSTALLDIR" Name="$(var.FullProductName)">  
            <Directory Id="ExtensionsFolder" Name="Extensions" />  
            <Directory Id="Folder1033" Name="1033" />  
          </Directory>  
        </Directory>  
      </Directory>  
      <Directory Id="ProgramMenuFolder">  
        <Directory Id="ApplicationProgramsFolder" Name="$(var.FullProductName)"/>  
      </Directory>  
    </Directory>  
    ```  
  
     Esses diretórios são referidos por `Id` quando os arquivos que devem ser instalados são especificados.  
  
2.  Identifique os componentes que requerem o Shell e o seu aplicativo de Shell, como mostra o exemplo a seguir.  
  
    > [!NOTE]
    >  Alguns elementos podem consultar definições em outros arquivos .wxs.  
  
    ```xml  
    <Feature Id="ProductFeature" Title="$(var.ShortProductName)Shell" Level="1">  
      <ComponentGroupRef Id="ApplicationGroup" />  
      <ComponentGroupRef Id="HelpAboutPackage" />  
      <ComponentRef Id="GeneralProfile" />  
      <ComponentGroupRef Id="EditorAdornment"/>        
      <ComponentGroupRef Id="SlideShowDesignerGroup"/>  
  
      <!-- Note: The following ComponentGroupRef is required to pull in generated authoring from project references. -->  
      <ComponentGroupRef Id="Product.Generated" />  
    </Feature>  
    ```  
  
    1.  O `ComponentRef` elemento refere-se a outro arquivo .wxs que identifica os arquivos que requer o componente atual. Por exemplo, GeneralProfile tem a seguinte definição na HelpAbout.wxs.  
  
        ```xml  
        <Fragment Id="FragmentProfiles">  
          <DirectoryRef Id="INSTALLDIR">  
            <Directory Id="ProfilesFolder" Name="Profiles">  
              <Component Id='GeneralProfile' Guid='*'>  
                <File Id='GeneralProfile' Name='General.vssettings' DiskId='1' Source='$(var.BuildOutputDir)Profiles\General.vssettings' KeyPath='yes' />  
              </Component>  
            </Directory>  
          </DirectoryRef>  
        </Fragment>  
        ```  
  
         O `DirectoryRef` elemento Especifica onde esses arquivos no computador do usuário. O `Directory` elemento Especifica que ele será instalado em um subdiretório e cada `File` elemento representa um arquivo que é compilado ou que existe como parte da solução e identifica onde esse arquivo pode ser encontrado quando o arquivo MSI é criado.  
  
    2.  O `ComponentGroupRef` elemento se refere a um grupo de outros componentes (ou componentes e grupos de componentes). Por exemplo, `ComponentGroupRef` em ApplicationGroup é definida da seguinte forma no Application.wxs.  
  
        ```xml  
        <ComponentGroup Id="ApplicationGroup">  
          <ComponentGroupRef Id="DebuggerProxy" />  
          <ComponentRef Id="MasterPkgDef" />  
          <ComponentRef Id="SplashResource" />  
          <ComponentRef Id="IconResource" />  
          <ComponentRef Id="WinPrfResource" />  
          <ComponentRef Id="AppExe" />  
          <ComponentRef Id="AppConfig" />  
          <ComponentRef Id="AppPkgDef" />  
          <ComponentRef Id="AppPkgDefUndef" />  
          <ComponentRef Id="$(var.ShortProductName)UI1033" />  
          <ComponentRef Id="ApplicationShortcut"/>  
          <ComponentRef Id="ApplicationRegistry"/>  
        </ComponentGroup>  
        ```  
  
    > [!NOTE]
    >  Necessário para dependências de aplicativos do Shell (isolado) são: DebuggerProxy, MasterPkgDef, recursos (especialmente o arquivo .winprf), aplicativos e PkgDefs.  
  
### <a name="registry-entries"></a>Entradas do registro  
 O modelo de projeto do Shell (isolado) inclui um *ProjectName*. reg para chaves do registro mesclar na instalação. Essas entradas do registro devem ser parte do MSI para fins de limpeza e de instalação. Você também deve criar blocos de registro correspondentes em ApplicationRegistry.wxs.  
  
##### <a name="to-integrate-registry-entries-into-the-msi"></a>Para integrar as entradas do registro no MSI  
  
1.  No **personalização do Shell** pasta, abra *ProjectName*. reg.  
  
2.  Substitua todas as instâncias de símbolo $ $RootFolder com o caminho do diretório de instalação de destino.  
  
3.  Adicione todas as outras entradas do registro que seu aplicativo requer.  
  
4.  Abra ApplicationRegistry.wxs.  
  
5.  Para cada entrada do registro *ProjectName*. reg, adicionar um bloco de registro correspondentes, como mostram os exemplos a seguir.  
  
    |*ProjectName*. reg|ApplicationRegisty.wxs|  
    |-----------------------|----------------------------|  
    |[HKEY_CLASSES_ROOT\CLSID\\{bb431796-a179-4df7-b65d-c0df6bda7cc6}]<br /><br /> @= "Objeto DTE PhotoStudio"|\<RegistryKey Id = 'DteClsidRegKey' Root = 'HKCR' Key =' $(var. DteClsidRegKey)' Ação = 'createAndRemoveOnUninstall' ><br /><br /> \<Tipo de RegistryValue = 'string' nome =' @' valor =' $(var. Objeto ShortProductName) DTE' / ><br /><br /> \</ RegistryKey >|  
    |[HKEY_CLASSES_ROOT\CLSID\\\LocalServer32 {bb431796-a179-4df7-b65d-c0df6bda7cc6}]<br /><br /> @= "$RootFolder$\PhotoStudio.exe"|\<RegistryKey Id = 'DteLocSrv32RegKey' Root = 'HKCR' Key =' $(var. DteClsidRegKey) \LocalServer32' Ação = 'createAndRemoveOnUninstall' ><br /><br /> \<Tipo de RegistryValue = 'string' nome =' @' valor ='[INSTALLDIR] $(var. ShortProductName) .exe ' / ><br /><br /> \</ RegistryKey >|  
  
     Neste exemplo, Var.DteClsidRegKey resolve a chave do registro na linha superior. Resolve Var.ShortProductName `PhotoStudio`.  
  
## <a name="creating-a-setup-bootstrapper"></a>Criando um Bootstrapper de instalação  
 MSI concluído será instalado somente se todos os pré-requisitos estão instalados primeiro. Para facilitar a experiência do usuário final, crie um programa de instalação que coleta e instala todos os pré-requisitos antes de instalar o aplicativo. Para garantir uma instalação bem-sucedida, execute estas ações:  
  
-   Forçar a instalação pelo administrador.  
  
-   Detecte se o Shell do Visual Studio (isolado) está instalado.  
  
-   Execute um ou ambos os instaladores de Shell na ordem.  
  
-   Lidar com solicitações de reinício.  
  
-   Execute o MSI.  
  
### <a name="enforcing-installation-by-administrator"></a>Impondo instalação pelo administrador  
 Esse procedimento é necessário para habilitar o programa de instalação acessar os diretórios necessários como \Program Files\\.  
  
##### <a name="to-enforce-installation-by-administrator"></a>Para forçar a instalação pelo administrador  
  
1.  Abra o menu de atalho para o projeto de instalação e, em seguida, escolha **propriedades**.  
  
2.  Em **arquivo de configuração do vinculador/propriedades/manifesto**, defina **o nível de execução UAC** para **requireAdministrator**.  
  
     Essa propriedade coloca o atributo que exige que o programa a ser executado como administrador no arquivo de manifesto inserido.  
  
### <a name="detecting-shell-installations"></a>Detectar instalações de Shell  
 Para determinar se o Shell do Visual Studio (isolado) deve ser instalado, primeiro determine se ele já está instalado, verificando o valor do registro de HKLM\Software\Microsoft\DevDiv\vs\Servicing\ShellVersion\isoshell\LCID\Install.  
  
> [!NOTE]
>  Esses valores também são lidos pelo bloco de detecção de Shell em Product. wxs.  
  
 HKLM\Software\Microsoft\AppEnv\14.0\ShellFolder Especifica o local onde o Shell do Visual Studio foi instalado e você pode procurar arquivos.  
  
 Para obter um exemplo de como detectar uma instalação do Shell, consulte o `GetProductDirFromReg` função de Utilities.cpp no exemplo de implantação de Shell.  
  
 Se um ou ambos dos Shells Visual Studio que requer o pacote não estiver instalado no computador, você deve adicioná-los à lista de componentes a serem instalados. Para obter um exemplo, consulte o `ComponentsPage::OnInitDialog` função de ComponentsPage.cpp no exemplo de implantação de Shell.  
  
### <a name="running-the-shell-installers"></a>Executando os instaladores de Shell  
 Para executar os instaladores de Shell, chame os redistribuíveis do Shell do Visual Studio usando os argumentos de linha de comando corretos. No mínimo, você deve usar os argumentos de linha de comando **/q /norestart** e observe o código de retorno determinar o que deve ser feito em seguida. O exemplo a seguir executa o Shell (isolado) redistribuível.  
  
```  
dwResult = ExecCmd("Vs_IsoShell.exe /norestart /q", TRUE);  
```  
  
### <a name="running-the-shell-language-pack-installers"></a>Executando os instaladores de pacote de idiomas do Shell  
 Se em vez disso, você descobrir que o shell ou shells foram instalados e apenas precisam de um pacote de idiomas, você pode instalar os pacotes de idiomas como mostra o exemplo a seguir.  
  
```  
dwResult = ExecCmd("Vs_IsoShellLP.exe /norestart /q", TRUE);  
  
```  
  
### <a name="deciphering-return-values"></a>Valores de retorno decifrar  
 Em alguns sistemas operacionais, uma reinicialização será necessária para a instalação do Visual Studio Shell (isolado). Essa condição pode ser determinada pelo código de retorno da chamada para `ExecCmd`.  
  
|Valor de retorno|Descrição|  
|------------------|-----------------|  
|ERROR_SUCCESS|Instalação foi concluída. Agora você pode instalar o aplicativo.|  
|ERROR_SUCCESS_REBOOT_REQUIRED|Instalação foi concluída. Você pode instalar seu aplicativo depois que o computador for reiniciado.|  
|3015|Instalação está em andamento. É necessário reiniciar o computador para continuar a instalação.|  
  
### <a name="handling-restarts"></a>Tratamento de reinicializações  
 Ao executar o instalador do Shell usando o **/norestart** argumento, você especificou que ele não reiniciar o computador ou peça para o computador ser reiniciado. No entanto, talvez seja necessário reiniciar, e você deve garantir que seu instalador continuará depois que o computador for reiniciado.  
  
 Para lidar com reinicializações corretamente, certifique-se de que apenas um programa de instalação é definido como retomar e que o processo de continuação será manipulado corretamente.  
  
 Se ERROR_SUCCESS_REBOOT_REQUIRED ou 3015 for retornado, seu código deverá reiniciar o computador antes de continua a instalação.  
  
 Para lidar com reinicializações, faça o seguinte:  
  
-   Defina o registro para continuar a instalação do Windows é iniciado.  
  
-   Execute uma reinicialização dupla do bootstrapper.  
  
-   Exclua a chave de ResumeData de instalador do Shell.  
  
-   Reinicie o Windows.  
  
-   Redefina o caminho inicial do MSI.  
  
### <a name="setting-the-registry-to-resume-setup-when-windows-starts"></a>Definir o registro para continuar a instalação ao iniciar o Windows  
 A chave de registro HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\RunOnce\ executa na inicialização do sistema com permissões administrativas e, em seguida, é apagada. HKEY_CURRENT_USER contém uma chave semelhante, mas ele é executado como um usuário normal e não é adequado para instalações. Você pode continuar a instalação, colocando um valor de cadeia de caracteres na chave do RunOnce que chama o instalador. No entanto, recomendamos que você chama o instalador usando um **/reiniciar** ou parâmetro semelhante para notificar o aplicativo que ele está continuando em vez de começar. Você também pode incluir parâmetros para indicar onde você está no processo de instalação, que é especialmente útil em instalações que podem exigir várias reinicializações.  
  
 O exemplo a seguir mostra um valor de chave de registro RunOnce para retomar uma instalação.  
  
 `"c:\MyAppInstaller.exe /restart /SomeOtherDataFlag"`  
  
### <a name="installing-double-restart-of-bootstrapper"></a>Reinicialização dupla do Bootstrapper de instalação  
 Se a configuração é usada diretamente do RunOnce, a área de trabalho não poderá ser completamente carregada. Para disponibilizar a interface do usuário completa, você deve criar outro execução da instalação e encerrar a instância RunOnce.  
  
 Você deverá executar novamente o programa de instalação para que ele obtém as permissões corretas, e você deve fornecer informações suficientes para saber onde você parou antes da reinicialização, como mostra o exemplo a seguir.  
  
```  
if (_cmdLineInfo.IsRestart())  
{  
    TCHAR path[MAX_PATH]={0};  
    GetModuleFileName(NULL, path, MAX_PATH * sizeof(TCHAR));      
    ShellExecute( NULL, _T( "open" ), path, _T("/install"), 0, SW_SHOWNORMAL );  
}  
  
```  
  
### <a name="deleting-the-shell-installer-resumedata-key"></a>Excluir a chave do Shell Installer ResumeData  
 O instalador do Shell define a chave de registro HKLM\Software\Microsoft\VisualStudio\14.0\Setup\ResumeData com os dados para continuar a instalação após a reinicialização. Como seu aplicativo, não o instalador do Shell, está continuando, exclua chave do registro, como mostra o exemplo a seguir.  
  
```  
CString resumeSetupPath(MAKEINTRESOURCE("SOFTWARE\\Microsoft\\VisualStudio\\14.0\\Setup\\ResumeData"));  
RegDeleteKey(HKEY_LOCAL_MACHINE, resumeSetupPath);  
```  
  
### <a name="restarting-windows"></a>Reinicialização do Windows  
 Depois de definir as chaves de registro necessárias, você pode reiniciar o Windows. O exemplo a seguir invoca os comandos de reinicialização para diferentes sistemas operacionais Windows.  
  
```  
OSVERSIONINFO ov;  
HANDLE htoken ;  
//Ask for the SE_SHUTDOWN_NAME token as this is needed by the thread calling for a system shutdown.  
if (OpenProcessToken(GetCurrentProcess(), TOKEN_ADJUST_PRIVILEGES | TOKEN_QUERY, &htoken))  
{  
    LUID luid ;  
    LookupPrivilegeValue(NULL, SE_SHUTDOWN_NAME, &luid) ;  
    TOKEN_PRIVILEGES    privs ;  
    privs.Privileges[0].Luid = luid ;  
    privs.PrivilegeCount = 1 ;  
    privs.Privileges[0].Attributes = SE_PRIVILEGE_ENABLED ;  
    AdjustTokenPrivileges(htoken, FALSE, &privs, 0, (PTOKEN_PRIVILEGES) NULL, 0) ;  
}   
  
//Use InitiateSystemShutdownEx to avoid unexpected restart message box  
try  
{              
    if ( (ov.dwMajorVersion > 5) || ( (ov.dwMajorVersion == 5) && (ov.dwMinorVersion  > 0) ))  
    {  
        bExitWindows = InitiateSystemShutdownEx(0, _T(""), 0, TRUE, TRUE, REASON_PLANNED_FLAG);  
    }  
    else  
    {  
#pragma prefast(suppress:380,"ignore warning about legacy api")  
        bExitWindows = InitiateSystemShutdown(0, _T(""), 0, TRUE, TRUE);  
    }  
}  
catch(...)  
{  
    //advapi32.dll call not available! Will not restart!  
}  
  
```  
  
### <a name="resetting-the-start-path-of-msi"></a>Redefinindo o caminho inicial do MSI  
 Antes de reiniciar, o diretório atual é o local do seu programa de instalação mas, após a reinicialização, o local se tornará o diretório system32. O programa de instalação deve redefinir o diretório atual antes de cada chamada MSI, como mostra o exemplo a seguir.  
  
```  
CString GetSetupPath()  
{  
    TCHAR file[MAX_PATH];  
    GetModuleFileName(NULL, file, MAX_PATH * sizeof(TCHAR));  
    CString path(file);  
    int fpos = path.ReverseFind('\\');  
    if (fpos != -1)  
    {  
        path = path.Left(fpos + 1);  
    }  
  
    return path;  
}  
  
```  
  
### <a name="running-the-application-msi"></a>Executando o aplicativo MSI  
 Depois que o instalador do Shell do Visual Studio retorna ERROR_SUCCESS, você pode executar o MSI para seu aplicativo. Como o programa de instalação está fornecendo a interface do usuário, iniciar o MSI no modo silencioso (**/q**) e com o log (**/L**), como mostra o exemplo a seguir.  
  
```cpp#  
TCHAR temp[MAX_PATH];  
GetTempPath(MAX_PATH, temp);  
  
CString boutiqueInstallCmd, msi, log;  
CString cmdLine(MAKEINTRESOURCE("msiexec /q /I %s /L*vx %s REBOOT=ReallySuppress"));  
CString name(MAKEINTRESOURCE("PhotoStudioIntShell.msi"));  
log.Format(_T("\"%s%s.log\""), temp, name);  
msi.Format(_T("\"%s%s\""), GetSetupPath(), name);  
boutiqueInstallCmd.Format(cmdLine, msi, log);  
  
//TODO: You can use MSI API to gather and present install progress feedback from your MSI.  
dwResult = ExecCmd(boutiqueInstallCmd, FALSE);  
```  
  
## <a name="see-also"></a>Consulte também  
 [Passo a passo: Criando um aplicativo básico Shell isolado](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)
