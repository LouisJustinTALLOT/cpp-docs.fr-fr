---
title: _getpid
description: Référence d’API pour _getpid, qui obtient l’identification du processus.
ms.date: 11/04/2016
api_name:
- _getpid
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _getpid
helpviewer_keywords:
- getpid function
- _getpid function
- process identification numbers
ms.assetid: d3e13bae-9a0c-4f33-86d3-ec9df9519285
ms.openlocfilehash: fc2de8e0b6e87d04bd9ae29ce3a945c048af00e2
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89556487"
---
# <a name="_getpid"></a>_getpid

Obtient l’identification du processus.

> [!IMPORTANT]
> Cette API ne peut pas être utilisée dans les applications qui s'exécutent dans le Windows Runtime. Pour plus d’informations, consultez [Fonctions CRT non prises en charge dans les applications de la plateforme Windows universelle](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
int _getpid( void );
```

## <a name="return-value"></a>Valeur de retour

Retourne l’ID de processus obtenu auprès du système. Il n’y a pas d’erreur de retour.

## <a name="remarks"></a>Notes

La fonction **_getpid** obtient l’ID de processus à partir du système. L’ID de processus identifie de façon univoque le processus appelant.

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_getpid**|\<process.h>|

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// crt_getpid.c
// This program uses _getpid to obtain
// the process ID and then prints the ID.

#include <stdio.h>
#include <process.h>

int main( void )
{
   // If run from command line, shows different ID for
   // command line than for operating system shell.

   printf( "Process id: %d\n", _getpid() );
}
```

```Output
Process id: 3584
```

## <a name="see-also"></a>Voir aussi

[Contrôle de processus et d’environnement](../../c-runtime-library/process-and-environment-control.md)<br/>
[_mktemp, _wmktemp](mktemp-wmktemp.md)<br/>
