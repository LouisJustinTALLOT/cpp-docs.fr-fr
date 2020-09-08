---
title: _getche, _getwche
description: Informations de référence sur les API pour _getche et _getwche ; qui obtient un caractère de la console avec ECHO.
ms.date: 4/2/2020
api_name:
- _getwche
- _getche
- _o__getche
- _o__getwche
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
- getwche
- _getche
- _getwche
helpviewer_keywords:
- characters, getting from console
- _getwche function
- getche function
- console, reading from
- getwche function
- _getche function
ms.assetid: eac978a8-c43a-4130-938f-54f12e2a0fda
ms.openlocfilehash: 228251a34c3f9829f2ef7c39561af4118649e158
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89556067"
---
# <a name="_getche-_getwche"></a>_getche, _getwche

Obtient un caractère à partir de la console et l’affichent.

> [!IMPORTANT]
> Cette API ne peut pas être utilisée dans les applications qui s'exécutent dans le Windows Runtime. Pour plus d’informations, consultez [Fonctions CRT non prises en charge dans les applications de la plateforme Windows universelle](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
int _getche( void );
wint_t _getwche( void );
```

## <a name="return-value"></a>Valeur de retour

Retourne le caractère lu. Il n’y a pas d’erreur de retour.

## <a name="remarks"></a>Notes

Les fonctions **_getche** et **_getwche** lisent un caractère unique à partir de la console avec ECHO, ce qui signifie que le caractère s’affiche sur la console. Aucune de ces fonctions ne peut être utilisée pour lire Ctrl+C. Pour la lecture d’une touche de fonction ou de direction, chaque fonction doit être appelée deux fois ; le premier appel retourne 0 ou 0xE0, tandis que le second retourne le code de la touche.

Ces fonctions verrouillent le thread appelant et sont donc thread-safe. Pour les versions sans verrouillage, consultez [_getche_nolock, _getwche_nolock](getche-nolock-getwche-nolock.md).

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine Tchar.h|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_getche**|**_getche**|**_getch**|**_getwche**|

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_getche**|\<conio.h>|
|**_getwche**|\<conio.h> ou \<wchar.h>|

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// crt_getche.c
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
      ch = _getche();
      ch = toupper( ch );
   } while( ch != 'Y' );

   _putch( ch );
   _putch( '\r' );    // Carriage return
   _putch( '\n' );    // Line feed
}
```

```Input
abcdefy
```

```Output
Type 'Y' when finished typing keys: abcdefyY
```

## <a name="see-also"></a>Voir aussi

[E/s de console et de port](../../c-runtime-library/console-and-port-i-o.md)<br/>
[_cgets, _cgetws](../../c-runtime-library/cgets-cgetws.md)<br/>
[getc, getwc](getc-getwc.md)<br/>
[_ungetch, _ungetwch, _ungetch_nolock, _ungetwch_nolock](ungetch-ungetwch-ungetch-nolock-ungetwch-nolock.md)<br/>
