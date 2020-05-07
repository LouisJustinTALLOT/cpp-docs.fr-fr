---
title: _setmbcp
ms.date: 4/2/2020
api_name:
- _setmbcp
- _o__setmbcp
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
- api-ms-win-crt-locale-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _setmbcp
- setmbcp
helpviewer_keywords:
- setmbcp function
- _setmbcp function
- multibyte code pages
ms.assetid: cfde53b5-0b73-4684-81b1-a8d3aafc85de
ms.openlocfilehash: 18712661b2bda1eaaf0c583b922ad73a781b4abc
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82918825"
---
# <a name="_setmbcp"></a>_setmbcp

Définit une nouvelle page de codes multioctets.

## <a name="syntax"></a>Syntaxe

```C
int _setmbcp(
   int codepage
);
```

### <a name="parameters"></a>Paramètres

*courante*<br/>
Nouveau paramètre de page de codes pour les routines multioctets indépendantes des paramètres régionaux.

## <a name="return-value"></a>Valeur de retour

Retourne 0 si la page de codes est correctement définie. Si une valeur de page de codes non valide est fournie pour *codepage*, retourne-1 et le paramètre de la page de codes est inchangé. Définit **errno** sur **EINVAL** si un échec d’allocation de mémoire se produit.

## <a name="remarks"></a>Notes 

La fonction **_setmbcp** spécifie une nouvelle page de codes multioctets. Par défaut, le système de runtime définit automatiquement la page de codes multioctets comme étant la page de codes ANSI par défaut du système. Le paramètre de page de codes multioctets influe sur toutes les routines multioctets qui ne sont pas dépendantes des paramètres régionaux. Toutefois, il est possible de demander à **_setmbcp** d’utiliser la page de codes définie pour les paramètres régionaux actuels (consultez la liste suivante des constantes de manifeste et les résultats de comportement associés). Pour obtenir la liste des routines multioctets qui dépendent de la page de codes des paramètres régionaux et non de la page de codes multioctets, consultez [Interprétation des séquences de caractères multioctets](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md).

La page de codes multioctets a aussi un impact sur le traitement des caractères multioctets assuré par les routines de bibliothèque Runtime suivantes :

||||
|-|-|-|
|[_exec, fonctions](../../c-runtime-library/exec-wexec-functions.md)|[_mktemp](mktemp-wmktemp.md)|[_stat](stat-functions.md)|
|[_fullpath](fullpath-wfullpath.md)|[fonctions _spawn](../../c-runtime-library/spawn-wspawn-functions.md)|[_tempnam](tempnam-wtempnam-tmpnam-wtmpnam.md)|
|[_makepath](makepath-wmakepath.md)|[_splitpath](splitpath-wsplitpath.md)|[tmpnam](tempnam-wtempnam-tmpnam-wtmpnam.md)|

En outre, toutes les routines de la bibliothèque Runtime qui reçoivent des arguments de programme *argv* ou *envp* à caractères multioctets comme paramètres (tels que les familles **_exec** et **_spawn** ) traitent ces chaînes en fonction de la page de codes multioctets. Par conséquent, ces routines sont également affectées par un appel à **_setmbcp** qui modifie la page de codes multioctets.

L’argument *codepage* peut être défini sur l’une des valeurs suivantes :

- **_MB_CP_ANSI** Utilisez la page de codes ANSI obtenue à partir du système d’exploitation au démarrage du programme.

- **_MB_CP_LOCALE** Utilisez la page de codes des paramètres régionaux actuels obtenue à partir d’un appel précédent à [setlocale](setlocale-wsetlocale.md).

- **_MB_CP_OEM** Utilisez la page de codes OEM obtenue à partir du système d’exploitation au démarrage du programme.

- **_MB_CP_SBCS** Utilisez la page de codes sur un octet. Lorsque la page de codes est définie sur **_MB_CP_SBCS**, une routine comme [_ismbblead](ismbblead-ismbblead-l.md) retourne toujours false.

- **_MB_CP_UTF8** Utilisez UTF-8.  Lorsque la page de codes est définie sur **_MB_CP_UTF8**, une routine comme [_ismbblead](ismbblead-ismbblead-l.md) retourne toujours false.

- Toute autre valeur de page de codes valide, que la valeur soit une page de codes ANSI, OEM ou autre prise en charge par le système d’exploitation (à l’exception de UTF-7, qui n’est pas prise en charge).

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_setmbcp**|\<mbctype.h>|

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[_getmbcp](getmbcp.md)<br/>
[setlocale, _wsetlocale](setlocale-wsetlocale.md)<br/>
