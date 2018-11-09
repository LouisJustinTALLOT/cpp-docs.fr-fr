---
title: to, fonctions
ms.date: 11/04/2016
apilocation:
- msvcr120.dll
- msvcr90.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr80.dll
- msvcr100.dll
apitype: DLLExport
f1_keywords:
- To
helpviewer_keywords:
- to functions
- string conversion, to different characters
- string conversion, case
- lowercase, converting strings
- uppercase, converting strings
- case, converting
- characters, converting
ms.assetid: f636a4c6-8c9f-4be2-baac-064f9dbae300
ms.openlocfilehash: 8a6a1a69147c135ce539393e535f0e1f2d03ccfa
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50580752"
---
# <a name="to-functions"></a>to, fonctions

Chaque fonction **to** et sa macro associée, le cas échéant, convertissent un caractère unique en un autre caractère.

|||
|-|-|
|[__toascii](../c-runtime-library/reference/toascii-toascii.md)|[toupper, _toupper, towupper](../c-runtime-library/reference/toupper-toupper-towupper-toupper-l-towupper-l.md)|
|[tolower, _tolower, towlower](../c-runtime-library/reference/tolower-tolower-towlower-tolower-l-towlower-l.md)||

## <a name="remarks"></a>Notes

Les fonctions **to** et les conversions de macro sont les suivantes.

|Routine|Macro|Description|
|-------------|-----------|-----------------|
|`__toascii`|`__toascii`|Convertit `c` en caractère ASCII|
|`tolower`|`tolower`|Convertit `c` en minuscules si besoin|
|`_tolower`|`_tolower`|Convertit `c` en minuscules|
|`towlower`|Aucun.|Convertit `c` en lettre minuscule à caractères larges correspondante|
|`toupper`|`toupper`|Convertit `c` en majuscules si besoin|
|`_toupper`|`_toupper`|Convertit `c` en majuscules|
|`towupper`|Aucun.|Convertit c en lettre majuscule à caractères larges correspondante|

Pour utiliser les versions de fonction des routines **to** également définies en tant que macros, supprimez les définitions de macro avec des directives `#undef` ou n’incluez pas CTYPE.H. Si vous utilisez l’option de compilateur /Za, le compilateur utilise la version de fonction `toupper` ou `tolower`. Les déclarations des fonctions `toupper` et `tolower` sont dans STDLIB.H.

La routine `__toascii` définit tous les bits sauf les 7 bits de poids faible de `c` sur 0, afin que la valeur convertie représente un caractère du jeu de caractères ASCII. Si `c` représente déjà un caractère ASCII, `c` est inchangé.

Les routines `tolower` et `toupper` :

- dépendent de la catégorie `LC_CTYPE` des paramètres régionaux actuels (`tolower` appelle `isupper` et `toupper` appelle `islower`) ;

- convertissent `c` si `c` représente une lettre convertible de la casse appropriée dans les paramètres régionaux actuels et que la casse opposée existe pour ces paramètres régionaux. Sinon, `c` est inchangé.

Les routines `_tolower` et `_toupper` :

- sont des versions indépendantes des paramètres régionaux et beaucoup plus rapides de `tolower` et **toupper** ;

- peuvent être utilisées uniquement quand **isascii (**`c`**)** et **isupper (**`c`**)** ou **islower (**`c`**)**, respectivement, sont différents de zéro ;

- produisent des résultats inattendus si `c` n’est pas une lettre ASCII de la casse appropriée à la conversion.

Les fonctions `towlower` et `towupper` retournent une copie convertie de `c` si et seulement si les deux conditions suivantes sont différentes de zéro. Sinon, `c` est inchangé.

- `c` est un caractère large de la casse appropriée (autrement dit, pour lequel `iswupper` ou **iswlower**, respectivement, sont différents de zéro).

- Il existe un caractère large correspondant de la casse cible (autrement dit, pour lequel `iswlower` ou **iswupper**, respectivement, sont différents de zéro).

## <a name="example"></a>Exemple

```
// crt_toupper.c
/* This program uses toupper and tolower to
 * analyze all characters between 0x0 and 0x7F. It also
 * applies _toupper and _tolower to any code in this
 * range for which these functions make sense.
 */

#include <ctype.h>
#include <string.h>

char msg[] = "Some of THESE letters are Capitals.";
char *p;

int main( void )
{
   printf( "%s\n", msg );

   /* Reverse case of message. */
   for( p = msg; p < msg + strlen( msg ); p++ )
   {
      if( islower( *p ) )
         putchar( _toupper( *p ) );
      else if( isupper( *p ) )
         putchar( _tolower( *p ) );
      else
         putchar( *p );
   }
}
```

```Output
Some of THESE letters are Capitals.
sOME OF these LETTERS ARE cAPITALS.
```

## <a name="see-also"></a>Voir aussi

[Conversion de données](../c-runtime-library/data-conversion.md)<br/>
[Paramètres régionaux](../c-runtime-library/locale.md)<br/>
[is, isw, routines](../c-runtime-library/is-isw-routines.md)