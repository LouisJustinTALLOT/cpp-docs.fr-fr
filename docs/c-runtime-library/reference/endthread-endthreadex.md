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
ms.openlocfilehash: 5afbc907356d4c5b14b749de5de0c8d36280891e
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69499960"
---
# <a name="_endthread-_endthreadex"></a>_endthread, _endthreadex

Termine un thread; _ **endthread** termine un thread créé par _ **BeginThread** et _ **endthreadex** met fin à un thread créé par _ **beginthreadex**.

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

Vous pouvez appeler _ **endthread** ou _ **endthreadex** explicitement pour terminer un thread; Toutefois, _ **endthread** ou _ **endthreadex** est appelé automatiquement lorsque le thread retourne de la routine passée en tant que paramètre à _ **BeginThread** ou _ **beginthreadex**. L’arrêt d’un thread avec un appel à **endthread** ou _ **endthreadex** permet de garantir une récupération correcte des ressources allouées pour le thread.

> [!NOTE]
> Pour un fichier exécutable lié à Libcmt.lib, n’appelez pas l’API [ExitThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-exitthread) Win32, car elle empêche le système runtime de récupérer les ressources allouées. _ **endthread** et _ **endthreadex** récupèrent les ressources de thread allouées, puis appellent **ExitThread**.

_ **endthread** ferme automatiquement le handle de thread. (Ce comportement diffère de l’API **ExitThread** Win32.) Par conséquent, lorsque vous utilisez _ **BeginThread** et _ **endthread**, ne fermez pas explicitement le handle du thread en appelant l’API [CloseHandle](/windows/win32/api/handleapi/nf-handleapi-closehandle) Win32.

À l’instar de l’API **ExitThread** Win32, _ **endthreadex** ne ferme pas le handle de thread. Par conséquent, lorsque vous utilisez _ **beginthreadex** et _ **endthreadex**, vous devez fermer le handle du thread en appelant l’API **CloseHandle** Win32.

> [!NOTE]
> _ **endthread** et _ C++ **endthreadex** entraînent la non-appel des destructeurs en attente dans le thread.

## <a name="requirements"></a>Configuration requise

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
