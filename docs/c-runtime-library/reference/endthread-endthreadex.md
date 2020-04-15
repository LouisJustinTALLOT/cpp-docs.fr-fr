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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: c76f479255080400e07678ef5dbde572b7a9dffc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81348034"
---
# <a name="_endthread-_endthreadex"></a>_endthread, _endthreadex

Termine un fil; **_endthread** met fin à un fil qui est créé par **_beginthread** et **_endthreadex** met fin à un fil qui est créé par **_beginthreadex**.

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

Vous pouvez appeler **_endthread** ou **_endthreadex** explicitement pour mettre fin à un thread; cependant, **_endthread** ou **_endthreadex** est appelé automatiquement lorsque le thread revient de la routine passée comme un paramètre à **_beginthread** ou **_beginthreadex**. La fin d’un thread avec un appel pour **mettre fin** ou **_endthreadex** permet d’assurer une récupération adéquate des ressources allouées au thread.

> [!NOTE]
> Pour un fichier exécutable lié à Libcmt.lib, n’appelez pas l’API [ExitThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-exitthread) Win32, car elle empêche le système runtime de récupérer les ressources allouées. **_endthread** et **_endthreadex** récupérer les ressources de thread allouées, puis appeler **ExitThread**.

**_endthread** ferme automatiquement le manche du thread. (Ce comportement diffère de l’API Win32 **ExitThread.)** Par conséquent, lorsque vous utilisez **_beginthread** et **_endthread**, ne fermez pas explicitement le manche de thread en appelant l’API Win32 [CloseHandle.](/windows/win32/api/handleapi/nf-handleapi-closehandle)

Comme l’API Win32 **ExitThread,** **_endthreadex** ne ferme pas la poignée de fil. Par conséquent, lorsque vous utilisez **_beginthreadex** et **_endthreadex,** vous devez fermer la poignée de thread en appelant l’API Win32 **CloseHandle.**

> [!NOTE]
> **_endthread** et **_endthreadex** causent que les destructeurs de CMD en attente dans le fil ne soient pas appelés.

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Fonction|En-tête requis|
|--------------|---------------------|
|**_endthread**|\<process.h>|
|**_endthreadex**|\<process.h>|

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliothèques

Uniquement les versions multithread des [bibliothèques Runtime C](../../c-runtime-library/crt-library-features.md) .

## <a name="example"></a>Exemple

Voir l’exemple pour [_beginthread](beginthread-beginthreadex.md).

## <a name="see-also"></a>Voir aussi

[Contrôle des processus et de l’environnement](../../c-runtime-library/process-and-environment-control.md)<br/>
[_beginthread, _beginthreadex](beginthread-beginthreadex.md)<br/>
