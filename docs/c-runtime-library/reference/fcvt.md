---
title: _fcvt
ms.date: 4/2/2020
api_name:
- _fcvt
- _o__fcvt
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
- _fcvt
helpviewer_keywords:
- converting floating point, to strings
- _fcvt function
- floating-point functions, converting number to string
- fcvt function
- floating-point functions
ms.assetid: 74584c88-f0dd-4907-8fca-52da5df583f5
ms.openlocfilehash: a017ed58b962520793d5b10b088793dbc9b8a83d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81347431"
---
# <a name="_fcvt"></a>_fcvt

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

**_fcvt** renvoie un pointeur à la chaîne de chiffres, **NULL** sur erreur.

## <a name="remarks"></a>Notes

La fonction **_fcvt** convertit un numéro de point flottant en une chaîne de caractères à bout de terminaisons nulles. Le paramètre de *valeur* est le nombre de points flottants à convertir. **_fcvt** stocke les chiffres de la *valeur* comme une chaîne et appende un caractère nul ('0'). Le *paramètre de comptage* spécifie le nombre de chiffres à stocker après le point décimal. Les chiffres excédentaires sont arrondis pour *compter* les endroits. S’il y a moins de chiffres de *précision,* la corde est rembourrée avec des zéros.

Le nombre total de chiffres retournés par **_fcvt** ne dépassera pas **_CVTBUFSIZE**.

Seuls des chiffres sont stockés dans la chaîne. La position du point décimal et le signe de *valeur* peuvent être obtenus à partir de *déc* et signe après l’appel. Le paramètre *déc* indique une valeur integer; cette valeur integer donne la position du point décimal par rapport au début de la chaîne. Une valeur entière ou zéro indique que la virgule décimale est située à gauche du premier chiffre. Le *signe de* paramètre indique un intégrant indiquant le signe de *valeur*. L’intégrateur est réglé à 0 si *la valeur* est positive et est réglé à un nombre non zéro si *la valeur* est négative.

La différence entre **_ecvt** et **_fcvt** réside dans l’interprétation du paramètre de *comptage.* **_ecvt** interprète *le* nombre total de chiffres dans la chaîne de sortie, tandis que **_fcvt** interprète le *nombre* de chiffres après le point décimal.

**_ecvt** et **_fcvt** utiliser un seul tampon statiquement alloué pour la conversion. Chaque appel à une de ces routines détruit les résultats de l’appel précédent.

Cette fonction valide ses paramètres. Si *déc* ou *signe* est **NULL**, ou *compte* est de 0, le gestionnaire de paramètre invalide est invoqué, tel que décrit dans la validation [de paramètres](../../c-runtime-library/parameter-validation.md). Si l’exécution se poursuit, **errno** est réglé sur **EINVAL** et **NULL** est retourné.

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Fonction|En-tête requis|
|--------------|---------------------|
|**_fcvt**|\<stdlib.h>|

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

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
[Soutien à la pointe flottante](../../c-runtime-library/floating-point-support.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
[_ecvt](ecvt.md)<br/>
[_gcvt](gcvt.md)<br/>
