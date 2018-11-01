---
title: _fcvt_s
ms.date: 04/05/2018
apiname:
- _fcvt_s
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
- fcvt_s
- _fcvt_s
helpviewer_keywords:
- fcvt_s function
- converting floating point, to strings
- floating-point functions, converting number to string
- _fcvt_s function
ms.assetid: 48671197-1d29-4c2b-a5d8-d2368f5f68a1
ms.openlocfilehash: 51ff3c675f1f53aee9beab629b17193164a2e7eb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50536848"
---
# <a name="fcvts"></a>_fcvt_s

Convertir un nombre à virgule flottante en chaîne. Il s’agit d’une version de [_fcvt](fcvt.md) assortie des améliorations de sécurité décrites dans [Fonctionnalités de sécurité dans le CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Syntaxe

```C
errno_t _fcvt_s(
   char* buffer,
   size_t sizeInBytes,
   double value,
   int count,
   int *dec,
   int *sign
);
template <size_t size>
errno_t _fcvt_s(
   char (&buffer)[size],
   double value,
   int count,
   int *dec,
   int *sign
); // C++ only
```

### <a name="parameters"></a>Paramètres

*buffer*<br/>
La mémoire tampon fournie destinée à contenir le résultat de la conversion.

*sizeInBytes*<br/>
Taille de la mémoire tampon en octets.

*valeur*<br/>
Nombre à convertir.

*count*<br/>
Nombre de chiffres après la virgule décimale.

*dec*<br/>
Pointeur désignant la position de la virgule décimale stockée.

*sign*<br/>
Pointeur désignant l’indicateur de signe stocké.

## <a name="return-value"></a>Valeur de retour

Zéro si l’opération réussit. En cas d’échec, la valeur de retour est un code d’erreur. Les codes d’erreur sont définis dans Errno.h. Pour obtenir la liste de ces erreurs, consultez [errno, _doserrno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

En cas de paramètre non valide, comme indiqué dans le tableau suivant, cette fonction appelle le gestionnaire de paramètres non valides, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, cette fonction affecte **errno** à **EINVAL** et retourne **EINVAL**.

### <a name="error-conditions"></a>Conditions d’erreur

|*buffer*|*sizeInBytes*|par défaut|count|dec|sign|Retourner|Valeur dans *mémoire tampon*|
|--------------|-------------------|-----------|-----------|---------|----------|------------|-----------------------|
|**NULL**|any|any|any|any|any|**EINVAL**|Non modifiée.|
|Pas **NULL** (pointe vers une mémoire valide)|<=0|any|any|any|any|**EINVAL**|Non modifiée.|
|any|any|any|any|**NULL**|any|**EINVAL**|Non modifiée.|
|any|any|any|any|any|**NULL**|**EINVAL**|Non modifiée.|

## <a name="security-issues"></a>Problèmes de sécurité

**_fcvt_s** peut générer une violation d’accès si *tampon* ne pointe pas vers une mémoire valide et n’est pas **NULL**.

## <a name="remarks"></a>Notes

Le **_fcvt_s** fonction convertit un nombre à virgule flottante en une chaîne de caractères se terminant par null. Le *valeur* paramètre correspond au nombre à virgule flottante à convertir. **_fcvt_s** stocke les chiffres de *valeur* sous forme de chaîne et ajoute un caractère null ('\0'). Le *nombre* paramètre spécifie le nombre de chiffres à stocker après la virgule décimale. Chiffres en trop sont arrondis à *nombre* place. S’il existe moins de *nombre* chiffres de précision, la chaîne est remplie de zéros.

Seuls des chiffres sont stockés dans la chaîne. La position de la virgule décimale et le signe de *valeur* peut être obtenu à partir de *dec* et *connexion* après l’appel. Le *dec* paramètre pointe vers une valeur entière ; celle-ci indique la position de la virgule décimale par rapport au début de la chaîne. Une valeur entière ou zéro indique que la virgule décimale est située à gauche du premier chiffre. Le paramètre *connexion* pointe vers un entier indiquant le signe de *valeur*. L’entier est défini sur 0 si *valeur* est un nombre positif et est défini sur un nombre différent de zéro si *valeur* est un nombre négatif.

Une mémoire tampon de longueur **_CVTBUFSIZE** est suffisante pour n’importe quel flottante valeur de point.

La différence entre **_ecvt_s** et **_fcvt_s** est dans l’interprétation de la *nombre* paramètre. **_ecvt_s** interprète *nombre* comme le nombre total de chiffres dans la chaîne de sortie, et **_fcvt_s** interprète *nombre* en tant que le nombre de chiffres après le virgule décimale.

En C++, l’utilisation de cette fonction est simplifiée par une surcharge de modèle ; la surcharge peut déduire automatiquement la longueur de la mémoire tampon, ce qui évite d’avoir à spécifier un argument de taille. Pour plus d'informations, consultez [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md).

La version de débogage de cette fonction remplit d’abord la mémoire tampon avec 0xFD. Pour désactiver ce comportement, utilisez [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md).

## <a name="requirements"></a>Configuration requise

|Fonction|En-tête requis|En-tête facultatif|
|--------------|---------------------|---------------------|
|**_fcvt_s**|\<stdlib.h>|\<errno.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

**Bibliothèques :** toutes les versions des [fonctionnalités de bibliothèque CRT](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Exemple

```C
// fcvt_s.c
#include <stdio.h>
#include <stdlib.h>
#include <errno.h>

int main()
{
    char * buf = 0;
    int decimal;
    int sign;
    int err;

    buf = (char*) malloc(_CVTBUFSIZE);
    err = _fcvt_s(buf, _CVTBUFSIZE, 1.2, 5, &decimal, &sign);

    if (err != 0)
    {
        printf("_fcvt_s failed with error code %d\n", err);
        exit(1);
    }

    printf("Converted value: %s\n", buf);
}
```

```Output
Converted value: 120000
```

## <a name="see-also"></a>Voir aussi

[Conversion de données](../../c-runtime-library/data-conversion.md)<br/>
[Prise en charge de la virgule flottante](../../c-runtime-library/floating-point-support.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
[_ecvt_s](ecvt-s.md)<br/>
[_gcvt_s](gcvt-s.md)<br/>
[_fcvt](fcvt.md)<br/>
