---
title: _fcvt
ms.date: 04/05/2018
apiname:
- _fcvt
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
- api-ms-win-crt-convert-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _fcvt
helpviewer_keywords:
- converting floating point, to strings
- _fcvt function
- floating-point functions, converting number to string
- fcvt function
- floating-point functions
ms.assetid: 74584c88-f0dd-4907-8fca-52da5df583f5
ms.openlocfilehash: ae9323e3bb629fd61b35a8c844b00bfcc73235bb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62334838"
---
# <a name="fcvt"></a>_fcvt

Convertir un nombre à virgule flottante en chaîne. Une version plus sécurisée de cette fonction est disponible. Consultez [_fcvt_s](fcvt-s.md).

## <a name="syntax"></a>Syntaxe

```C
char *_fcvt(
   double value,
   int count,
   int *dec,
   int *sign
);
```

### <a name="parameters"></a>Paramètres

*value*<br/>
Nombre à convertir.

*count*<br/>
Nombre de chiffres après la virgule décimale.

*dec*<br/>
Pointeur désignant la position de la virgule décimale stockée.

*sign*<br/>
Pointeur désignant l’indicateur de signe stocké.

## <a name="return-value"></a>Valeur de retour

**_fcvt** retourne un pointeur vers la chaîne de chiffres, **NULL** en cas d’erreur.

## <a name="remarks"></a>Notes

Le **_fcvt** fonction convertit un nombre à virgule flottante en une chaîne de caractères se terminant par null. Le *valeur* paramètre correspond au nombre à virgule flottante à convertir. **_fcvt** stocke les chiffres de *valeur* sous forme de chaîne et ajoute un caractère null ('\0'). Le *nombre* paramètre spécifie le nombre de chiffres à stocker après la virgule décimale. Chiffres en trop sont arrondis à *nombre* place. S’il existe moins de *nombre* chiffres de précision, la chaîne est remplie de zéros.

Le nombre total de chiffres retournés par **_fcvt** n’excédera pas **_CVTBUFSIZE**.

Seuls des chiffres sont stockés dans la chaîne. La position de la virgule décimale et le signe de *valeur* peut être obtenu à partir de *dec* et sign après l’appel. Le *dec* paramètre pointe vers une valeur entière ; celle-ci indique la position de la virgule décimale par rapport au début de la chaîne. Une valeur entière ou zéro indique que la virgule décimale est située à gauche du premier chiffre. Le paramètre *connexion* pointe vers un entier indiquant le signe de *valeur*. L’entier est défini sur 0 si *valeur* est un nombre positif et est défini sur un nombre différent de zéro si *valeur* est un nombre négatif.

La différence entre **_ecvt** et **_fcvt** est dans l’interprétation de la *nombre* paramètre. **_ecvt** interprète *nombre* comme le nombre total de chiffres dans la chaîne de sortie, tandis que **_fcvt** interprète *nombre* en tant que le nombre de chiffres après le virgule décimale.

**_ecvt** et **_fcvt** utilisent un seul tampon alloué de manière statique pour la conversion. Chaque appel à une de ces routines détruit les résultats de l’appel précédent.

Cette fonction valide ses paramètres. Si *dec* ou *connexion* est **NULL**, ou *nombre* est 0, le Gestionnaire de paramètre non valide est appelé, comme décrit dans [paramètre Validation](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, **errno** a la valeur **EINVAL** et **NULL** est retourné.

## <a name="requirements"></a>Configuration requise

|Fonction|En-tête requis|
|--------------|---------------------|
|**_fcvt**|\<stdlib.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// crt_fcvt.c
// compile with: /W3
// This program converts the constant
// 3.1415926535 to a string and sets the pointer
// buffer to point to that string.

#include <stdlib.h>
#include <stdio.h>

int main( void )
{
   int  decimal, sign;
   char *buffer;
   double source = 3.1415926535;

   buffer = _fcvt( source, 7, &decimal, &sign ); // C4996
   // Note: _fcvt is deprecated; consider using _fcvt_s instead
   printf( "source: %2.10f   buffer: '%s'   decimal: %d   sign: %d\n",
            source, buffer, decimal, sign );
}
```

```Output
source: 3.1415926535   buffer: '31415927'   decimal: 1   sign: 0
```

## <a name="see-also"></a>Voir aussi

[Conversion de données](../../c-runtime-library/data-conversion.md)<br/>
[Prise en charge de la virgule flottante](../../c-runtime-library/floating-point-support.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
[_ecvt](ecvt.md)<br/>
[_gcvt](gcvt.md)<br/>
