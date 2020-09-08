---
title: _getch_nolock, _getwch_nolock
description: Informations de référence sur les API pour _getch_nolock et _getwch_nolock ; qui récupèrent un caractère de la console sans écho et sans verrouiller le thread.
ms.date: 4/2/2020
api_name:
- _getwch_nolock
- _getch_nolock
- _o__getch_nolock
- _o__getwch_nolock
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
- api-ms-win-crt-conio-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _getch_nolock
- getwch_nolock
- getch_nolock
- _getwch_nolock
- _gettch_nolock
- gettch_nolock
helpviewer_keywords:
- characters, getting from console
- _getwch_nolock function
- _getch_nolock function
- getwch_nolock function
- _gettch_nolock function
- console, reading from
- getch_nolock function
- gettch_nolock function
ms.assetid: 9d248546-26ca-482c-b0c6-55812a987e83
ms.openlocfilehash: 36a50f215a9250b23d4dc25db2e1f1c764a085ce
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89555031"
---
# <a name="_getch_nolock-_getwch_nolock"></a>_getch_nolock, _getwch_nolock

Obtient un caractère de la console sans l’afficher et sans verrouiller le thread.

> [!IMPORTANT]
> Cette API ne peut pas être utilisée dans les applications qui s'exécutent dans le Windows Runtime. Pour plus d’informations, consultez [Fonctions CRT non prises en charge dans les applications de la plateforme Windows universelle](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
int _getch_nolock( void );
wint_t _getwch_nolock( void );
```

## <a name="return-value"></a>Valeur de retour

Retourne le caractère lu. Il n’y a pas d’erreur de retour.

## <a name="remarks"></a>Notes

les **_getch_nolock** et les **_getwch_nolock** sont identiques à **_getch** et **_getchw** , sauf qu’ils ne sont pas protégés contre les interférences par d’autres threads. Elles peuvent être plus rapides, car elles n'entraînent pas la charge du verrouillage des autres threads. Utilisez ces fonctions uniquement dans les contextes thread-safe, tels que les applications à un seul thread ou lorsque la portée appelante gère déjà l'isolation des threads.

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine Tchar.h|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_gettch_nolock**|**_getch_nolock**|**_getch_nolock**|**_getwch_nolock**|

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_getch_nolock**|\<conio.h>|
|**_getwch_nolock**|\<conio.h> ou \<wchar.h>|

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// crt_getch_nolock.c
// compile with: /c
// This program reads characters from
// the keyboard until it receives a 'Y' or 'y'.

#include <conio.h>
#include <ctype.h>

int main( void )
{
   int ch;

   _cputs( "Type 'Y' when finished typing keys: " );
   do
   {
      ch = _getch_nolock();
      ch = toupper( ch );
   } while( ch != 'Y' );

   _putch_nolock( ch );
   _putch_nolock( '\r' );    // Carriage return
   _putch_nolock( '\n' );    // Line feed
}
```

```Input
abcdefy
```

```Output
Type 'Y' when finished typing keys: Y
```

## <a name="see-also"></a>Voir aussi

[E/s de console et de port](../../c-runtime-library/console-and-port-i-o.md)<br/>
[_getche, _getwche](getche-getwche.md)<br/>
[_cgets, _cgetws](../../c-runtime-library/cgets-cgetws.md)<br/>
[getc, getwc](getc-getwc.md)<br/>
[_ungetch, _ungetwch, _ungetch_nolock, _ungetwch_nolock](ungetch-ungetwch-ungetch-nolock-ungetwch-nolock.md)<br/>
