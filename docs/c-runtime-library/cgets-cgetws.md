---
description: 'En savoir plus sur : _cgets, _cgetws'
title: _cgets, _cgetws
ms.date: 4/2/2020
api_name:
- _cgetws
- _cgets
- _o__cgets
- _o__cgetws
api_location:
- msvcr100.dll
- msvcr110.dll
- msvcr80.dll
- msvcr120.dll
- msvcr90.dll
- msvcrt.dll
- msvcr110_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-conio-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- cgetws
- _cgetws
- _cgets
helpviewer_keywords:
- _cgetws function
- strings [C++], getting from console
- console, getting strings from
- _cgets function
- cgetws function
- cgets function
ms.assetid: 4d5e134a-58c3-4f62-befd-5d235b0212f4
ms.openlocfilehash: ac712c7ee51c3f06dfe1dd4e881630768a7e6b20
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97221681"
---
# <a name="_cgets-_cgetws"></a>_cgets, _cgetws

Obtient une chaîne de caractères à partir de la console. Des versions plus sécurisées de ces fonctions sont disponibles. Consultez [_cgets_s, _cgetws_s](../c-runtime-library/reference/cgets-s-cgetws-s.md).

> [!IMPORTANT]
> Ces fonctions sont obsolètes. Depuis Visual Studio 2015, elles ne sont pas disponibles dans la bibliothèque CRT. Les versions sécurisées de ces fonctions, _cgets_s et _cgetws_s, sont toujours disponibles. Pour plus d’informations sur ces fonctions alternatives, consultez [_cgets_s, _cgetws_s](../c-runtime-library/reference/cgets-s-cgetws-s.md).

> [!IMPORTANT]
> Cette API ne peut pas être utilisée dans les applications qui s'exécutent dans le Windows Runtime. Pour plus d’informations, consultez [Fonctions CRT non prises en charge dans les applications de la plateforme Windows universelle](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```
char *_cgets(
   char *buffer
);
wchar_t *_cgetws(
   wchar_t *buffer
);
template <size_t size>
char *_cgets(
   char (&buffer)[size]
); // C++ only
template <size_t size>
wchar_t *_cgetws(
   wchar_t (&buffer)[size]
); // C++ only
```

#### <a name="parameters"></a>Paramètres

*mémoire tampon*<br/>
Emplacement de stockage des données.

## <a name="return-value"></a>Valeur renvoyée

`_cgets` et `_cgetws` retournent un pointeur vers le début de la chaîne, à l’emplacement `buffer[2]`. Si `buffer` a la valeur **NULL** ou est une chaîne vide, ces fonctions appellent le gestionnaire de paramètres non valides, comme décrit dans [Validation de paramètre](../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à continuer, elles retournent **NULL** et définissent `errno` avec la valeur `EINVAL`.

## <a name="remarks"></a>Notes

Ces fonctions lisent une chaîne de caractères à partir de la console, et stockent la chaîne et sa longueur à l’emplacement désigné par `buffer`. Le paramètre `buffer` doit être un pointeur vers un tableau de caractères. Le premier élément du tableau, `buffer[0]`, doit contenir la longueur maximale (en caractères) de la chaîne à lire. Le tableau doit contenir suffisamment d’éléments pour stocker la chaîne, un caractère null de fin (« \0 ») et 2 octets supplémentaires. La fonction lit les caractères jusqu’à une combinaison CRLF (retour chariot - saut de ligne) ou jusqu’à ce que le nombre de caractères spécifiés soit lu. La chaîne est stockée à partir de `buffer[2]`. Si la fonction lit un CRLF, elle stocke le caractère null (« \0 »). La fonction stocke ensuite la longueur réelle de la chaîne dans le deuxième élément du tableau, `buffer[1]`.

Comme toutes les touches d’édition sont actives quand `_cgets` ou `_cgetws` est appelée alors que c’est une fenêtre de console qui est active, le fait d’appuyer sur la touche F3 répète la dernière entrée saisie.

En C++, ces fonctions ont des surcharges de modèle qui appellent les équivalents plus récents et sécurisés de ces fonctions. Pour plus d’informations, consultez [Sécuriser les surcharges de modèle](../c-runtime-library/secure-template-overloads.md).

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](global-state.md).

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine Tchar.h|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|--------------------------------------|--------------------|-----------------------|
|`_cgetts`|`_cgets`|`_cgets`|`_cgetws`|

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|`_cgets`|\<conio.h>|
|`_cgetws`|\<conio.h> ou \<wchar.h>|

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```c
// crt_cgets.c
// compile with: /c /W3
// This program creates a buffer and initializes
// the first byte to the size of the buffer. Next, the
// program accepts an input string using _cgets and displays
// the size and text of that string.

#include <conio.h>
#include <stdio.h>
#include <errno.h>

int main( void )
{
   char buffer[83] = { 80 };  // Maximum characters in 1st byte
   char *result;

   printf( "Input line of text, followed by carriage return:\n");

   // Input a line of text:
   result = _cgets( buffer ); // C4996
   // Note: _cgets is deprecated; consider using _cgets_s
   if (!result)
   {
      printf( "An error occurred reading from the console:"
              " error code %d\n", errno);
   }
   else
   {
      printf( "\nLine length = %d\nText = %s\n",
              buffer[1], result );
   }
}
```

```Output

      A line of input.Input line of text, followed by carriage return:
Line Length = 16
Text = A line of input.
```

## <a name="see-also"></a>Voir aussi

[E/s de console et de port](../c-runtime-library/console-and-port-i-o.md)<br/>
[_getch, _getwch](../c-runtime-library/reference/getch-getwch.md)
