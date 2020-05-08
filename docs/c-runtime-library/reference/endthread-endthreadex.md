---
title: _endthread, _endthreadex
ms.date: 4/2/2020
api_name:
- _endthread
- _endthreadex
- _o__endthread
- _o__endthreadex
api_location:
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: a3889adcc90bd62e766102b72aae68577915e55b
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82915081"
---
# <a name="_endthread-_endthreadex"></a>_endthread, _endthreadex

Termine un thread ; **_endthread** met fin à un thread créé par **_beginthread** et **_endthreadex** met fin à un thread créé par **_beginthreadex**.

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

Vous pouvez appeler **_endthread** ou **_endthreadex** explicitement pour terminer un thread ; Toutefois, **_endthread** ou **_endthreadex** est appelé automatiquement lorsque le thread retourne de la routine passée en tant que paramètre à **_beginthread** ou **_beginthreadex**. L’arrêt d’un thread à l’aide d’un appel à **endthread** ou **_endthreadex** permet de garantir une récupération correcte des ressources allouées pour le thread.

> [!NOTE]
> Pour un fichier exécutable lié à Libcmt.lib, n’appelez pas l’API [ExitThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-exitthread) Win32, car elle empêche le système runtime de récupérer les ressources allouées. **_endthread** et **_endthreadex** récupérer les ressources de thread allouées, puis appeler **ExitThread**.

**_endthread** ferme automatiquement le handle de thread. (Ce comportement diffère de l’API **ExitThread** Win32.) Par conséquent, lorsque vous utilisez **_beginthread** et **_endthread**, ne fermez pas explicitement le handle du thread en appelant l’API [CloseHandle](/windows/win32/api/handleapi/nf-handleapi-closehandle) Win32.

À l’instar de l’API **ExitThread** Win32, **_endthreadex** ne ferme pas le handle de thread. Par conséquent, lorsque vous utilisez **_beginthreadex** et **_endthreadex**, vous devez fermer le handle du thread en appelant l’API **CloseHandle** Win32.

> [!NOTE]
> **_endthread** et **_endthreadex** entraînent la non-appel des destructeurs C++ en attente dans le thread.

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Function|En-tête requis|
|--------------|---------------------|
|**_endthread**|\<process.h>|
|**_endthreadex**|\<process.h>|

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliothèques

Uniquement les versions multithread des [bibliothèques Runtime C](../../c-runtime-library/crt-library-features.md) .

## <a name="example"></a> Exemple

Voir l’exemple pour [_beginthread](beginthread-beginthreadex.md).

## <a name="see-also"></a>Voir aussi

[Contrôle de processus et d’environnement](../../c-runtime-library/process-and-environment-control.md)<br/>
[_beginthread, _beginthreadex](beginthread-beginthreadex.md)<br/>
