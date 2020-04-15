---
title: /CLRSUPPORTLASTERROR (Conserver le dernier code d'erreur pour les appels PInvoke)
ms.date: 11/04/2016
f1_keywords:
- /CLRSUPPORTLASTERROR
helpviewer_keywords:
- /CLRSUPPORTLASTERROR linker option
- -CLRSUPPORTLASTERROR linker option
ms.assetid: b7057990-4154-4b1d-9fc9-6236f7be7575
ms.openlocfilehash: 19930591c2d0406c68b1a408622a49c9e8b1d551
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81322273"
---
# <a name="clrsupportlasterror-preserve-last-error-code-for-pinvoke-calls"></a>/CLRSUPPORTLASTERROR (Conserver le dernier code d'erreur pour les appels PInvoke)

**/CLRSUPPORTLASTERROR**, qui est activé par défaut, préserve le dernier code d’erreur des fonctions appelées via le mécanisme P/Invoke, qui vous permet d’appeler des fonctions indigènes dans DLLS, à partir du code compilé avec **/clr**.

## <a name="syntax"></a>Syntaxe

```
/CLRSUPPORTLASTERROR{:NO | SYSTEMDLL}
```

## <a name="remarks"></a>Notes

Préserver le dernier code d’erreur implique une diminution des performances.  Si vous ne souhaitez pas encourir l’impact sur les performances de la préservation du dernier code d’erreur, lien avec **/CLRSUPPORTLASTERROR:NO**.

Vous pouvez minimiser l’impact sur les performances en vous liant à **/CLRSUPPORTLASTERROR:SYSTEMDLL**, qui ne conserve que le dernier code d’erreur pour les fonctions dans les DLL système.  Un système DLL est défini comme l’un des éléments suivants :

|||||
|-|-|-|-|
|ACLUI. DLL DLL|ACTIFS. DLL DLL|ADPTIF. DLL DLL|ADVAPI32. DLL DLL|
|C’EST L’ASYCFILT. DLL DLL|AUTHZ. DLL DLL|AVICAP32. DLL DLL|AVIFIL32. DLL DLL|
|Cabinet. DLL DLL|CLUSAPI. DLL DLL|COMCTL32. DLL DLL|COMDLG32. DLL DLL|
|COMSVCS. DLL DLL|C’EST CREDUI. DLL DLL|CRYPT32. DLL DLL|CRYPTNET. DLL DLL|
|CRYPTUI. DLL DLL|D3D8THK. DLL DLL|DBGENG. DLL DLL|DBGHELP. DLL DLL|
|DCIMAN32. DLL DLL|DNSAPI. DLL DLL|DSPROP. DLL DLL|DSUIEXT. DLL DLL|
|GDI32. DLL DLL|GLU32. DLL DLL|HLINK. DLL DLL|ICM32. DLL DLL|
|IMAGEHLP. DLL DLL|IMM32. DLL DLL|IPHLPAPI. DLL DLL|IPROP. DLL DLL|
|LE NOYAU32. DLL DLL|Ksuser. DLL DLL|CHARGEURF. DLL DLL|LZ32. DLL DLL|
|MAPI32. DLL DLL|Mgmtapi. DLL DLL|MOBSYNC. DLL DLL|Mpr. DLL DLL|
|MPRAPI. DLL DLL|MQRT. DLL DLL|MSACM32. DLL DLL|MSCMS. DLL DLL|
|Msi. DLL DLL|MSIMG32. DLL DLL|MSRATING. DLL DLL|MSTASK. DLL DLL|
|MSVFW32. DLL DLL|MSWSOCK. DLL DLL|MTXEX. DLL DLL|NDDEAPI. DLL DLL|
|NETAPI32. DLL DLL|NPPTOOLS. DLL DLL|NTDSAPI. DLL DLL|NTDSBCLI. DLL DLL|
|NTMSAPI. DLL DLL|ODBC32. DLL DLL|ODBCBCP. DLL DLL|OLE32. DLL DLL|
|OLEACC. DLL DLL|OLEAUT32. DLL DLL|OLEDLG. DLL DLL|OPENGL32. DLL DLL|
|Pdh. DLL DLL|POWRPROF. DLL DLL|QOSNAME. DLL DLL|Requête. DLL DLL|
|RASAPI32. DLL DLL|RASDLG. DLL DLL|C’EST RASSAPI. DLL DLL|DES RESUTILS. DLL DLL|
|RICHED20. DLL DLL|RPCNS4. DLL DLL|RPCRT4. DLL DLL|Rtm. DLL DLL|
|LES RTUTILS. DLL DLL|SCARDDLG. DLL DLL|LA SÉCUR32. DLL DLL|SENSAPI. DLL DLL|
|SETUPAPI. DLL DLL|Sfc. DLL DLL|SHELL32. DLL DLL|DES ER4E FOIS. DLL DLL|
|SHLWAPI. DLL DLL|SISBKUP. DLL DLL|SNMPAPI. DLL DLL|SRCLIENT. DLL DLL|
|Les ITS. DLL DLL|TAPI32. DLL DLL|Trafic. DLL DLL|Url. DLL DLL|
|URLMON. DLL DLL|UTILISATEUR32. DLL DLL|USERENV. DLL DLL|L’USP10. DLL DLL|
|Uxtheme. DLL DLL|VDMDBG. DLL DLL|Version. DLL DLL|Winfax. DLL DLL|
|LE WINHTTP. DLL DLL|Wininet. DLL DLL|LE WINMM. DLL DLL|WINSCARD. DLL DLL|
|WINTRUST. DLL DLL|WLDAP32. DLL DLL|WOW32. DLL DLL|WS2_32.DLL|
|WSNMP32. DLL DLL|WSOCK32.DLL|WTSAPI32. DLL DLL|XOLEHLP. DLL DLL|

> [!NOTE]
> La préservation de la dernière erreur n’est pas prise en charge pour les fonctions non gestion qui sont consommées par le code CLR, dans le même module.

- Pour plus d’informations, voir [/clr (Common Language Runtime Compilation)](clr-common-language-runtime-compilation.md).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Cliquez sur le dossier **Éditeur de liens**.

1. Cliquez sur la page de propriétés **Ligne de commande** .

1. Tapez l’option dans la boîte **Options supplémentaires.**

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="example"></a>Exemple

L’échantillon suivant définit un DLL indigène avec une fonction exportée qui modifie la dernière erreur.

```cpp
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

L’échantillon suivant consomme le DLL, démontrant comment utiliser **/CLRSUPPORTLASTERROR**.

```cpp
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

[Informations de référence sur l’éditeur de liens MSVC](linking.md)<br/>
[Options de l’éditeur de liens MSVC](linker-options.md)
