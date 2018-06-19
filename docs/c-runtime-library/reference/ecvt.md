---
title: _ecvt | Microsoft Docs
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _ecvt
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
- _ecvt
dev_langs:
- C++
helpviewer_keywords:
- _ecvt function
- numbers, converting
- converting double numbers
- ecvt function
ms.assetid: a916eb05-92d1-4b5c-8563-093acdb49dc8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 63514db5abe0a7cd531590dd419aa4b5931e7729
ms.sourcegitcommit: 6e3cf8df676d59119ce88bf5321d063cf479108c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/22/2018
ms.locfileid: "34450961"
---
# <a name="ecvt"></a>_ecvt

Convertit un **double** nombre en une chaîne. Une version plus sécurisée de cette fonction est disponible. Consultez [_ecvt_s](ecvt-s.md).

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

*valeur*<br/>
Nombre à convertir.

*count*<br/>
Nombre de chiffres stockés.

*dec*<br/>
Position de la virgule décimale stockée.

*sign*<br/>
Signe du nombre converti.

## <a name="return-value"></a>Valeur de retour

**_ecvt** retourne un pointeur vers la chaîne de chiffres ; **NULL** si une erreur s’est produite.

## <a name="remarks"></a>Notes

Le **_ecvt** fonction convertit un nombre à virgule flottante en une chaîne de caractères. Le *valeur* paramètre est le nombre à virgule flottante à convertir. Cette fonction stocke jusqu'à *nombre* chiffres de *valeur* sous forme de chaîne et ajoute un caractère null ('\0'). Si le nombre de chiffres dans *valeur* dépasse *nombre*, les chiffres de poids faible est arrondi. S’il y a moins de *nombre* chiffres, la chaîne est rempli de zéros.

Le nombre total de chiffres retourné par **_ecvt** n’excédera pas **_CVTBUFSIZE**.

Seuls des chiffres sont stockés dans la chaîne. La position de la virgule décimale et le signe de *valeur* peut être obtenu à partir de *dec* et *signe* après l’appel. Le *dec* paramètre pointe vers une valeur entière en donnant la position de la virgule décimale en ce qui concerne le début de la chaîne. Une valeur entière ou 0 indique que la virgule décimale est située à gauche du premier chiffre. Le *signe* paramètre pointe vers un entier qui indique le signe du nombre converti. Si la valeur entière est 0, le nombre est positif. Sinon, le nombre est négatif.

La différence entre **_ecvt** et **_fcvt** est dans l’interprétation de la *nombre* paramètre. **_ecvt** interprète *nombre* comme le nombre total de chiffres dans la chaîne de sortie, tandis que **_fcvt** interprète *nombre* en tant que le nombre de chiffres après le virgule décimale.

**_ecvt** et **_fcvt** utilisent un seul tampon alloué de manière statique pour la conversion. Chaque appel à une de ces routines détruit le résultat de l’appel précédent.

Cette fonction valide ses paramètres. Si *dec* ou *signe* est **NULL**, ou *nombre* est 0, le Gestionnaire de paramètre non valide est appelé, comme décrit dans [paramètre Validation](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, **errno** a la valeur **EINVAL** et **NULL** est retourné.

## <a name="requirements"></a>Spécifications

|Fonction|En-tête requis|
|--------------|---------------------|
|**_ecvt**|\<stdlib.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

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
