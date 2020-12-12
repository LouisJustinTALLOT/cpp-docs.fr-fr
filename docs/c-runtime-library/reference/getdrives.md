---
description: 'En savoir plus sur : _getdrives'
title: _getdrives
ms.date: 4/2/2020
api_name:
- _getdrives
- _o__getdrives
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
- api-ms-win-crt-filesystem-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- getdrives
- _getdrives
helpviewer_keywords:
- _getdrives function
- getdrives function
- disk drives
ms.assetid: 869bb51f-4209-4328-846e-3aadebaceb9c
ms.openlocfilehash: 77e73b1d63238b5f558fffdef0344fa5180c84ab
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97289151"
---
# <a name="_getdrives"></a>_getdrives

Retourne un masque de bits qui représente les lecteurs de disque actuellement disponibles.

> [!IMPORTANT]
> Cette API ne peut pas être utilisée dans les applications qui s'exécutent dans le Windows Runtime. Pour plus d’informations, consultez [Fonctions CRT non prises en charge dans les applications de la plateforme Windows universelle](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
unsigned long _getdrives( void );
```

## <a name="return-value"></a>Valeur de retour

Si la fonction aboutit, la valeur de retour est un masque de bits qui représente les lecteurs de disque actuellement disponibles. La position de bit 0 (bit de poids faible) est le lecteur A, la position de bit 1 est le lecteur B, la position de bit 2 est le lecteur C, et ainsi de suite. Si la fonction échoue, la valeur de retour est égale à zéro. Pour obtenir des informations détaillées sur l’erreur, appelez **GetLastError**.

## <a name="remarks"></a>Notes

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_getdrives**|\<direct.h>|

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// crt_getdrives.c
// This program retrieves and lists out
// all the logical drives that are
// currently mounted on the machine.

#include <windows.h>
#include <direct.h>
#include <stdio.h>
#include <tchar.h>

TCHAR g_szDrvMsg[] = _T("A:\n");

int main(int argc, char* argv[]) {
   ULONG uDriveMask = _getdrives();

   if (uDriveMask == 0)
   {
      printf( "_getdrives() failed with failure code: %d\n",
              GetLastError());
   }
   else
   {
      printf("The following logical drives are being used:\n");

      while (uDriveMask) {
         if (uDriveMask & 1)
            printf(g_szDrvMsg);

         ++g_szDrvMsg[0];
         uDriveMask >>= 1;
      }
   }
}
```

```Output
The following logical drives are being used:
A:
C:
D:
E:
```

## <a name="see-also"></a>Voir aussi

[Contrôle de répertoire](../../c-runtime-library/directory-control.md)<br/>
