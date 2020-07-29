---
title: _ecvt
ms.date: 4/2/2020
api_name:
- _ecvt
- _o__ecvt
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
- api-ms-win-crt-convert-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _ecvt
helpviewer_keywords:
- _ecvt function
- numbers, converting
- converting double numbers
- ecvt function
ms.assetid: a916eb05-92d1-4b5c-8563-093acdb49dc8
ms.openlocfilehash: 227010fde5dc5ec82fc13c724c8d5a2f43788a8f
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87234196"
---
# <a name="_ecvt"></a>_ecvt

Convertit un **`double`** nombre en une chaîne. Une version plus sécurisée de cette fonction est disponible. Consultez [_ecvt_s](ecvt-s.md).

## <a name="syntax"></a>Syntaxe

```C
char *_ecvt(
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
Nombre de chiffres stockés.

*decembre*<br/>
Position de la virgule décimale stockée.

*sign*<br/>
Signe du nombre converti.

## <a name="return-value"></a>Valeur de retour

**_ecvt** retourne un pointeur vers la chaîne de chiffres ; **Null** si une erreur s’est produite.

## <a name="remarks"></a>Notes

La fonction **_ecvt** convertit un nombre à virgule flottante en une chaîne de caractères. Le paramètre de *valeur* est le nombre à virgule flottante à convertir. Cette fonction stocke jusqu’à *Count* chiffres de *valeur* sous forme de chaîne et ajoute un caractère null (' \ 0 '). Si le nombre de chiffres dans la *valeur* dépasse le *nombre*, le chiffre de poids faible est arrondi. Si le *nombre* de chiffres est inférieur à, la chaîne est complétée par des zéros.

Le nombre total de chiffres renvoyés par **_ecvt** ne doit pas dépasser **_CVTBUFSIZE**.

Seuls des chiffres sont stockés dans la chaîne. La position de la virgule décimale et le signe de la *valeur* peuvent être obtenus à partir de *Dec* et du *signe* après l’appel. Le paramètre *Dec* pointe vers une valeur entière indiquant la position de la virgule décimale par rapport au début de la chaîne. Une valeur entière ou 0 indique que la virgule décimale est située à gauche du premier chiffre. Le paramètre *Sign* pointe sur un entier qui indique le signe du nombre converti. Si la valeur entière est 0, le nombre est positif. Sinon, le nombre est négatif.

La différence entre **_ecvt** et **_fcvt** est l’interprétation du paramètre *Count* . **_ecvt** interprète le *nombre comme le* nombre total de chiffres dans la chaîne de sortie, tandis que *count* **_fcvt** interprète le nombre comme le nombre de chiffres après la virgule décimale.

**_ecvt** et **_fcvt** utilisent une seule mémoire tampon allouée de manière statique pour la conversion. Chaque appel à une de ces routines détruit le résultat de l’appel précédent.

Cette fonction valide ses paramètres. Si *Dec* ou *Sign* est **null**ou si *Count* a la valeur 0, le gestionnaire de paramètre non valide est appelé, comme décrit dans [validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, **errno** a la valeur **EINVAL** et la **valeur null** est retournée.

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Fonction|En-tête requis|
|--------------|---------------------|
|**_ecvt**|\<stdlib.h>|

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// crt_ecvt.c
// compile with: /W3
// This program uses _ecvt to convert a
// floating-point number to a character string.

#include <stdlib.h>
#include <stdio.h>

int main( void )
{
   int     decimal,   sign;
   char    *buffer;
   int     precision = 10;
   double  source = 3.1415926535;

   buffer = _ecvt( source, precision, &decimal, &sign ); // C4996
   // Note: _ecvt is deprecated; consider using _ecvt_s instead
   printf( "source: %2.10f   buffer: '%s'  decimal: %d  sign: %d\n",
           source, buffer, decimal, sign );
}
```

```Output
source: 3.1415926535   buffer: '3141592654'  decimal: 1  sign: 0
```

## <a name="see-also"></a>Voir aussi

[Conversion de données](../../c-runtime-library/data-conversion.md)<br/>
[Prise en charge de la virgule flottante](../../c-runtime-library/floating-point-support.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
[_fcvt](fcvt.md)<br/>
[_gcvt](gcvt.md)<br/>
