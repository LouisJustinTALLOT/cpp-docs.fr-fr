---
title: _fcvt
ms.date: 04/05/2018
api_name:
- _fcvt
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
ms.openlocfilehash: a90f8510e734c8459867d323eccccc75e94983d1
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70941319"
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

**_fcvt** retourne un pointeur vers la chaîne de chiffres, **null** en cas d’erreur.

## <a name="remarks"></a>Notes

La fonction **_fcvt** convertit un nombre à virgule flottante en une chaîne de caractères terminée par le caractère null. Le paramètre de *valeur* est le nombre à virgule flottante à convertir. **_fcvt** stocke les chiffres de *valeur* sous forme de chaîne et ajoute un caractère null (' \ 0 '). Le paramètre *Count* spécifie le nombre de chiffres à stocker après la virgule décimale. Les chiffres excédentaires sont arrondis à la *valeur nombre* d’emplacements. Si le *nombre* de chiffres de précision est inférieur à, la chaîne est remplie de zéros.

Le nombre total de chiffres renvoyés par **_fcvt** ne dépasse pas **_CVTBUFSIZE**.

Seuls des chiffres sont stockés dans la chaîne. La position de la virgule décimale et le signe de la *valeur* peuvent être obtenus à partir de *Dec* et du signe après l’appel. Le paramètre *Dec* pointe sur une valeur entière ; Cette valeur entière indique la position de la virgule décimale par rapport au début de la chaîne. Une valeur entière ou zéro indique que la virgule décimale est située à gauche du premier chiffre. Le paramètre *signe* pointe sur un entier indiquant le signe de la *valeur*. L’entier est défini sur 0 si la *valeur* est positive et est définie sur un nombre différent de zéro si la *valeur* est négative.

La différence entre **_ecvt** et **_fcvt** est l’interprétation du paramètre *Count* . **_ecvt** interprète le *nombre comme le* nombre total de chiffres dans la chaîne de sortie, tandis que **_fcvt** interprète le nombre comme le nombre de chiffres après la virgule décimale.

**_ecvt** et **_fcvt** utilisent une seule mémoire tampon allouée de manière statique pour la conversion. Chaque appel à une de ces routines détruit les résultats de l’appel précédent.

Cette fonction valide ses paramètres. Si *Dec* ou *Sign* est **null**ou si *Count* a la valeur 0, le gestionnaire de paramètre non valide est appelé, comme décrit dans [validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, **errno** a la valeur **EINVAL** et la **valeur null** est retournée.

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
