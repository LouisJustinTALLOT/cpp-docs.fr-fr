---
title: Fonctions obsolètes | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp
- devlang-cpp
ms.topic: conceptual
f1_keywords:
- is_wctype
- _loaddll
- _unloaddll
- _getdllprocaddr
- _seterrormode
- _beep
- _sleep
- _getsystime
- corecrt_wctype/is_wctype
- process/_loaddll
- process/_unloaddll
- process/_getdllprocaddr
- stdlib/_seterrormode
- stdlib/_beep
- stdlib/_sleep
- time/_getsystime
- time/_setsystime
dev_langs:
- C++
helpviewer_keywords:
- obsolete functions
- _beep function
- _sleep function
- _seterrormode function
ms.assetid: 8e14c2d4-1481-4240-8586-47eb43db02b0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 259bd5f5fd458d11c104aa3b9c141d049ad3fa96
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46016596"
---
# <a name="obsolete-functions"></a>Fonctions obsolètes

Certaines fonctions de la bibliothèque sont obsolètes et ont des équivalents plus récents. Nous vous recommandons d’utiliser les versions mises à jour. D’autres fonctions obsolètes ont été supprimées du CRT. Cette rubrique répertorie les fonctions déconseillées comme obsolètes et celles qui ont été supprimées d’une version particulière de Visual Studio.

## <a name="deprecated-as-obsolete-in-visual-studio-2015"></a>Déconseillées comme obsolètes dans Visual Studio 2015

|Fonction obsolète|Alternative|
|-----------------------|-----------------|
|`is_wctype`|[iswctype](../c-runtime-library/reference/isctype-iswctype-isctype-l-iswctype-l.md)|
|`_loaddll`|[LoadLibrary](https://msdn.microsoft.com/library/windows/desktop/ms684175\(v=vs.85\).aspx), [LoadLibraryEx](/windows/desktop/api/libloaderapi/nf-libloaderapi-loadlibraryexa) ou [LoadPackagedLibrary](/windows/desktop/api/winbase/nf-winbase-loadpackagedlibrary)|
|`_unloaddll`|[FreeLibrary](https://msdn.microsoft.com/library/windows/desktop/ms683152\(v=vs.85\).aspx)|
|`_getdllprocaddr`|[GetProcAddress](../build/getprocaddress.md)|
|`_seterrormode`|[SetErrorMode](https://msdn.microsoft.com/en-us/library/windows/desktop/ms680621\(v=vs.85\).aspx)|
|`_beep`|[Beep](https://msdn.microsoft.com/library/windows/desktop/ms679277\(v=vs.85\).aspx)|
|`_sleep`|[Sleep](/windows/desktop/api/synchapi/nf-synchapi-sleep)|
|`_getsystime`|[GetLocalTime](https://msdn.microsoft.com/library/windows/desktop/ms724338\(v=vs.85\).aspx)|
|`_setsystime`|[SetLocalTime](https://msdn.microsoft.com/library/windows/desktop/ms724936\(v=vs.85\).aspx)|

## <a name="removed-from-the-crt-in-visual-studio-2015"></a>Supprimées du CRT dans Visual Studio 2015

|Fonction obsolète|Alternative|
|-----------------------|-----------------|
|[_cgets, _cgetws](../c-runtime-library/cgets-cgetws.md)|[_cgets_s, _cgetws_s](../c-runtime-library/reference/cgets-s-cgetws-s.md)|
|[gets, _getws](../c-runtime-library/gets-getws.md)|[gets_s, _getws_s](../c-runtime-library/reference/gets-s-getws-s.md)|
|[_get_output_format](../c-runtime-library/get-output-format.md)|Aucun.|
|[_heapadd](../c-runtime-library/heapadd.md)|Aucun.|
|[_heapset](../c-runtime-library/heapset.md)|Aucun.|
|[inp, inpw](../c-runtime-library/inp-inpw.md)|Aucun.|
|[_inp, _inpw, _inpd](../c-runtime-library/inp-inpw-inpd.md)|Aucun.|
|[outp, outpw](../c-runtime-library/outp-outpw.md)|Aucun.|
|[_outp, _outpw, _outpd](../c-runtime-library/outp-outpw-outpd.md)|Aucun.|
|[_set_output_format](../c-runtime-library/set-output-format.md)|Aucun.|

## <a name="removed-from-the-crt-in-earlier-versions-of-visual-studio"></a>Supprimées du CRT dans les versions antérieures de Visual Studio

[_lock](../c-runtime-library/lock.md)

[_unlock](../c-runtime-library/unlock.md)