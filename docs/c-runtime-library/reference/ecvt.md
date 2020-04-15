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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 5e1760d5c68e650f6fbf44866d4e368b9d6233b6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81348023"
---
# <a name="_ecvt"></a>_ecvt

Convertit un **double** numéro en une chaîne. Une version plus sécurisée de cette fonction est disponible. Consultez [_ecvt_s](ecvt-s.md).

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

*dec*<br/>
Position de la virgule décimale stockée.

*sign*<br/>
Signe du nombre converti.

## <a name="return-value"></a>Valeur de retour

**_ecvt** renvoie un pointeur à la chaîne de chiffres; **NULL** en cas d’erreur.

## <a name="remarks"></a>Notes

La fonction **_ecvt** convertit un numéro de point flottant en une chaîne de caractères. Le paramètre de *valeur* est le nombre de points flottants à convertir. Cette fonction stocke jusqu’à *compter* les chiffres de *valeur* comme une chaîne et annexe un caractère nul ('0'). Si le nombre de chiffres en *valeur* dépasse le *nombre,* le chiffre de faible commande est arrondi. S’il y a moins de chiffres de *comptage,* la chaîne est rembourrée avec des zéros.

Le nombre total de chiffres retournés par **_ecvt** ne dépassera pas **_CVTBUFSIZE**.

Seuls des chiffres sont stockés dans la chaîne. La position du point décimal et le signe de *valeur* peuvent être obtenus à partir de *déc* et *signe après* l’appel. Le paramètre *déc* indique une valeur integer donnant la position du point décimal par rapport au début de la chaîne. Une valeur entière ou 0 indique que la virgule décimale est située à gauche du premier chiffre. Le paramètre de *signe* indique un intégrant qui indique le signe du nombre converti. Si la valeur entière est 0, le nombre est positif. Sinon, le nombre est négatif.

La différence entre **_ecvt** et **_fcvt** réside dans l’interprétation du paramètre de *comptage.* **_ecvt** interprète *le* nombre total de chiffres dans la chaîne de sortie, tandis que **_fcvt** interprète le *nombre* de chiffres après le point décimal.

**_ecvt** et **_fcvt** utiliser un seul tampon statiquement alloué pour la conversion. Chaque appel à une de ces routines détruit le résultat de l’appel précédent.

Cette fonction valide ses paramètres. Si *déc* ou *signe* est **NULL**, ou *compte* est de 0, le gestionnaire de paramètre invalide est invoqué, tel que décrit dans la validation [de paramètres](../../c-runtime-library/parameter-validation.md). Si l’exécution se poursuit, **errno** est réglé sur **EINVAL** et **NULL** est retourné.

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

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
[Soutien à la pointe flottante](../../c-runtime-library/floating-point-support.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
[_fcvt](fcvt.md)<br/>
[_gcvt](gcvt.md)<br/>
