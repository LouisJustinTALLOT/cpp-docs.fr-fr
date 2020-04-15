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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 61086471c6194aaa8434d291647978bf891a8aea
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81337604"
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

*Codepage*<br/>
Nouveau paramètre de page de codes pour les routines multioctets indépendantes des paramètres régionaux.

## <a name="return-value"></a>Valeur de retour

Retourne 0 si la page de codes est correctement définie. Si une valeur de page de code invalide est fournie pour *la page de code,* les retours -1 et le paramètre de page de code sont inchangés. Définit **errno** à **EINVAL** en cas d’échec d’allocation de mémoire.

## <a name="remarks"></a>Notes

La fonction **_setmbcp** spécifie une nouvelle page de code multioctet. Par défaut, le système de runtime définit automatiquement la page de codes multioctets comme étant la page de codes ANSI par défaut du système. Le paramètre de page de codes multioctets influe sur toutes les routines multioctets qui ne sont pas dépendantes des paramètres régionaux. Cependant, il est possible d’instruire **_setmbcp** d’utiliser la page de code définie pour le lieu actuel (voir la liste suivante des constantes manifestes et des résultats de comportement associés). Pour obtenir la liste des routines multioctets qui dépendent de la page de codes des paramètres régionaux et non de la page de codes multioctets, consultez [Interprétation des séquences de caractères multioctets](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md).

La page de codes multioctets a aussi un impact sur le traitement des caractères multioctets assuré par les routines de bibliothèque Runtime suivantes :

||||
|-|-|-|
|[_exec, fonctions](../../c-runtime-library/exec-wexec-functions.md)|[_mktemp](mktemp-wmktemp.md)|[_stat](stat-functions.md)|
|[_fullpath](fullpath-wfullpath.md)|[fonctions _spawn](../../c-runtime-library/spawn-wspawn-functions.md)|[_tempnam](tempnam-wtempnam-tmpnam-wtmpnam.md)|
|[_makepath](makepath-wmakepath.md)|[_splitpath](splitpath-wsplitpath.md)|[tmpnam](tempnam-wtempnam-tmpnam-wtmpnam.md)|

En outre, toutes les routines de bibliothèque en temps d’exécution qui reçoivent des arguments de programme *de caractère* multioctet ou *envp* comme paramètres (tels que les **familles _exec** et **_spawn)** traitent ces chaînes selon la page de code multioctet. Par conséquent, ces routines sont également affectées par un appel à **_setmbcp** qui modifie la page de code multioctets.

*L’argument de la page de code* peut être réglé sur l’une ou l’autre des valeurs suivantes :

- **_MB_CP_ANSI** Utilisez la page de code ANSI obtenue à partir du système d’exploitation lors du démarrage du programme.

- **_MB_CP_LOCALE** Utilisez la page de code de l’endroit actuel obtenue à partir d’un appel précédent à [setlocale](setlocale-wsetlocale.md).

- **_MB_CP_OEM** Utilisez la page de code OEM obtenue à partir du système d’exploitation au démarrage du programme.

- **_MB_CP_SBCS** Utilisez la page de code unique. Lorsque la page de code est réglée sur **_MB_CP_SBCS,** une routine telle que [_ismbblead](ismbblead-ismbblead-l.md) retourne toujours fausse.

- **_MB_CP_UTF8** Utilisez UTF-8.  Lorsque la page de code est définie pour **_MB_CP_UTF8**, une routine telle que [_ismbblead](ismbblead-ismbblead-l.md) retourne toujours faux.

- Toute autre valeur valide de page de code, indépendamment du fait que la valeur soit une page de code ANSI, OEM ou autre page de code supportée par le système d’exploitation (à l’exception de l’UTF-7, qui n’est pas pris en charge).

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_setmbcp**|\<mbctype.h>|

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[_getmbcp](getmbcp.md)<br/>
[setlocale, _wsetlocale](setlocale-wsetlocale.md)<br/>
