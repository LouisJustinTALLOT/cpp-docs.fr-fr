---
title: -CLRSUPPORTLASTERROR (conserver dernier Code d’erreur pour les appels PInvoke) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /CLRSUPPORTLASTERROR
dev_langs:
- C++
helpviewer_keywords:
- /CLRSUPPORTLASTERROR linker option
- -CLRSUPPORTLASTERROR linker option
ms.assetid: b7057990-4154-4b1d-9fc9-6236f7be7575
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a80adfe34677c15a36af96ac412b7934747e68bc
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45707445"
---
# <a name="clrsupportlasterror-preserve-last-error-code-for-pinvoke-calls"></a>/CLRSUPPORTLASTERROR (Conserver le dernier code d'erreur pour les appels PInvoke)

**/CLRSUPPORTLASTERROR**, qui est activé par défaut, conserve le dernier code d’erreur des fonctions appelé via le mécanisme P/Invoke, ce qui vous permet d’appeler des fonctions natives dans des DLL, à partir du code compilé avec **/CLR**.

## <a name="syntax"></a>Syntaxe

```
/CLRSUPPORTLASTERROR{:NO | SYSTEMDLL}
```

## <a name="remarks"></a>Notes

Conservation du dernier code d’erreur implique une baisse des performances.  Si vous ne souhaitez pas subir l’impact sur les performances de la conservation du dernier code d’erreur, liez avec **/CLRSUPPORTLASTERROR:NO**.

Vous pouvez réduire l’impact sur les performances en liant avec **/CLRSUPPORTLASTERROR:SYSTEMDLL**, qui conserve uniquement le dernier code d’erreur pour les fonctions dans des DLL système.  Une DLL système est définie comme suit :

|||||
|-|-|-|-|
|INTERFACE ACLUI. DLL|ACTIVEDS. DLL|ADPTIF. DLL|ADVAPI32. DLL|
|ASYCFILT. DLL|AUTHZ. DLL|AVICAP32. DLL|AVIFIL32. DLL|
|FICHIER CAB. DLL|CLUSAPI. DLL|COMCTL32. DLL|COMDLG32. DLL|
|COMSVCS. DLL|CREDUI. DLL|CRYPT32. DLL|CRYPTNET. DLL|
|CRYPTUI. DLL|D3D8THK. DLL|DBGENG. DLL|DBGHELP. DLL|
|DCIMAN32. DLL|DNSAPI. DLL|DSPROP. DLL|DSUIEXT. DLL|
|GDI32. DLL|GLU32. DLL|HLINK. DLL|ICM32. DLL|
|IMAGEHLP. DLL|IMM32. DLL|IPHLPAPI. DLL|IPROP. DLL|
|KERNEL32. DLL|KSUSER. DLL|LOADPERF. DLL|LZ32. DLL|
|MAPI32. DLL|MGMTAPI. DLL|MOBSYNC. DLL|MPR. DLL|
|MPRAPI. DLL|MQRT. DLL|MSACM32. DLL|MSCMS. DLL|
|MSI. DLL|MSIMG32. DLL|MSRATING. DLL|MSTASK. DLL|
|MSVFW32. DLL|MSWSOCK. DLL|MTXEX. DLL|NDDEAPI. DLL|
|NETAPI32. DLL|NPPTOOLS. DLL|NTDSAPI. DLL|NTDSBCLI. DLL|
|NTMSAPI. DLL|ODBC32. DLL|ODBCBCP. DLL|OLE32. DLL|
|OLEACC. DLL|OLEAUT32. DLL|OLEDLG. DLL|OPENGL32. DLL|
|PDH. DLL|POWRPROF. DLL|QOSNAME. DLL|REQUÊTE. DLL|
|RASAPI32. DLL|RASDLG. DLL|RASSAPI. DLL|RESUTILS. DLL|
|RICHED20. DLL|RPCNS4. DLL|RPCRT4. DLL|RTM. DLL|
|RTUTILS. DLL|SCARDDLG. DLL|SECUR32. DLL|SENSAPI. DLL|
|SETUPAPI. DLL|SFC. DLL|SHELL32. DLL|SHFOLDER. DLL|
|SHLWAPI. DLL|SISBKUP. DLL|SNMPAPI. DLL|SRCLIENT. DLL|
|ICT. DLL|TAPI32. DLL|TRAFIC. DLL|URL. DLL|
|URLMON. DLL|USER32. DLL|USERENV. DLL|USP10. DLL|
|UXTHEME. DLL|VDMDBG. DLL|VERSION. DLL|WINFAX. DLL|
|WINHTTP. DLL|WININET. DLL|WINMM. DLL|WINSCARD. DLL|
|MICROSOFT. DLL|WLDAP32. DLL|WOW32. DLL|WS2_32.DLL|
|WSNMP32. DLL|WSOCK32.DLL|WTSAPI32. DLL|XOLEHLP. DLL|

> [!NOTE]
>  En conservant la dernière erreur n’est pas pris en charge pour les fonctions non managées qui sont consommées par du code CLR dans le même module.

- Pour plus d’informations, consultez l’article [/clr (Compilation pour le Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [définition des propriétés de projet Visual C++](../../ide/working-with-project-properties.md).

1. Cliquez sur le **l’éditeur de liens** dossier.

1. Cliquez sur la page de propriétés **Ligne de commande** .

1. Tapez l’option dans le **des Options supplémentaires** boîte.

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="example"></a>Exemple

L’exemple suivant définit une DLL native avec une fonction exportée qui modifie la dernière erreur.

```
// CLRSUPPORTLASTERROR_dll.cpp
// compile with: /LD
#include <windows.h>
#include <math.h>

#pragma unmanaged
__declspec(dllexport) double MySqrt(__int64 n) {
   SetLastError(DWORD(-1));
   return sqrt(double(n));
}
```

## <a name="example"></a>Exemple

L’exemple suivant utilise la DLL, qui montre comment utiliser **/CLRSUPPORTLASTERROR**.

```
// CLRSUPPORTLASTERROR_client.cpp
// compile with: /clr CLRSUPPORTLASTERROR_dll.lib /link /clrsupportlasterror:systemdll
// processor: x86
#include <windows.h>
#include <wininet.h>
#include <stdio.h>
#include <math.h>

#pragma comment(lib, "wininet.lib")

double MySqrt(__int64 n);

#pragma managed
int main() {
   double   d = 0.0;
   __int64 n = 65;
   HANDLE  hGroup = NULL;
   GROUPID groupID;
   DWORD   dwSet = 127, dwGet = 37;

   SetLastError(dwSet);
   d = MySqrt(n);
   dwGet = GetLastError();

   if (dwGet == DWORD(-1))
      printf_s("GetLastError for application call succeeded (%d).\n",
             dwGet);
   else
      printf_s("GetLastError for application call failed (%d).\n",
             dwGet);

   hGroup = FindFirstUrlCacheGroup(0, CACHEGROUP_SEARCH_ALL,
                           0, 0, &groupID, 0);
   dwGet = GetLastError();
   if (dwGet == 183)
      printf_s("GetLastError for system call succeeded (%d).\n",
             dwGet);
   else
      printf_s("GetLastError for system call failed (%d).\n",
             dwGet);
}
```

```Output
GetLastError for application call failed (127).
GetLastError for system call succeeded (183).
```

## <a name="see-also"></a>Voir aussi

[Définition des options de l’Éditeur de liens](../../build/reference/setting-linker-options.md)<br/>
[Options de l’éditeur de liens](../../build/reference/linker-options.md)