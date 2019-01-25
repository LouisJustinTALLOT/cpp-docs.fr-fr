---
title: _endthread, _endthreadex
ms.date: 11/04/2016
apiname:
- _endthread
- _endthreadex
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _endthread
- endthreadex
- _endthreadex
- endthread
helpviewer_keywords:
- _endthread function
- endthread function
- terminating threads
- endthreadex function
- _endthreadex function
- threading [C++], terminating threads
ms.assetid: 18a91f2f-659e-40b4-b266-ec12dcf2abf5
ms.openlocfilehash: 2f54ca9c4cd5e863ca960f1d9c3634b85e7896dd
ms.sourcegitcommit: c85c8a1226d8fbbaa29f4691ed719f8e6cc6575c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2019
ms.locfileid: "54893299"
---
# <a name="endthread-endthreadex"></a>_endthread, _endthreadex

Termine un thread ; **_endthread** termine un thread créé par **_beginthread** et **_endthreadex** termine un thread créé par **_beginthreadex**.

## <a name="syntax"></a>Syntaxe

```C
void _endthread( void );
void _endthreadex(
   unsigned retval
);
```

### <a name="parameters"></a>Paramètres

*retval*<br/>
Code de sortie de thread.

## <a name="remarks"></a>Notes

Vous pouvez appeler **_endthread** ou **_endthreadex** explicitement pour terminer un thread ; Toutefois, **_endthread** ou **_endthreadex** est appelée automatiquement lorsque le thread retourne de la routine passée en tant que paramètre à **_beginthread** ou **_beginthreadex**. Arrêt d’un thread avec un appel à **endthread** ou **_endthreadex** vous aide à garantir une récupération correcte des ressources allouées pour le thread.

> [!NOTE]
> Pour un fichier exécutable lié à Libcmt.lib, n’appelez pas l’API [ExitThread](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-exitthread) Win32, car elle empêche le système runtime de récupérer les ressources allouées. **_endthread** et **_endthreadex** récupèrent les ressources de thread allouées, puis appellent **ExitThread**.

**_endthread** ferme automatiquement le handle du thread. (Ce comportement diffère de Win32 **ExitThread** API.) Par conséquent, lorsque vous utilisez **_beginthread** et **_endthread**, ne fermez pas explicitement le handle du thread en appelant Win32 [CloseHandle](/windows/desktop/api/handleapi/nf-handleapi-closehandle) API.

Comme Win32 **ExitThread** API, **_endthreadex** ne ferme pas le handle du thread. Par conséquent, lorsque vous utilisez **_beginthreadex** et **_endthreadex**, vous devez fermer le handle du thread en appelant Win32 **CloseHandle** API.

> [!NOTE]
> **_endthread** et **_endthreadex** provoquer des destructeurs C++ en attente dans le thread d’appel.

## <a name="requirements"></a>Spécifications

|Fonction|En-tête requis|
|--------------|---------------------|
|**_endthread**|\<process.h>|
|**_endthreadex**|\<process.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliothèques

Uniquement les versions multithread des [bibliothèques Runtime C](../../c-runtime-library/crt-library-features.md) .

## <a name="example"></a>Exemple

Voir l'exemple pour [_beginthread](beginthread-beginthreadex.md).

## <a name="see-also"></a>Voir aussi

[Contrôle de processus et d’environnement](../../c-runtime-library/process-and-environment-control.md)<br/>
[_beginthread, _beginthreadex](beginthread-beginthreadex.md)<br/>
