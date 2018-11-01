---
title: _setmbcp
ms.date: 11/04/2016
apiname:
- _setmbcp
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
- api-ms-win-crt-locale-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _setmbcp
- setmbcp
helpviewer_keywords:
- setmbcp function
- _setmbcp function
- multibyte code pages
ms.assetid: cfde53b5-0b73-4684-81b1-a8d3aafc85de
ms.openlocfilehash: c1f4967baa5fda68a7df33bcd08935dca23fab16
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50532208"
---
# <a name="setmbcp"></a>_setmbcp

Définit une nouvelle page de codes multioctets.

## <a name="syntax"></a>Syntaxe

```C
int _setmbcp(
   int codepage
);
```

### <a name="parameters"></a>Paramètres

*page de codes*<br/>
Nouveau paramètre de page de codes pour les routines multioctets indépendantes des paramètres régionaux.

## <a name="return-value"></a>Valeur de retour

Retourne 0 si la page de codes est correctement définie. Si une valeur de page de code non valide est fournie pour *page de codes*, retourne -1 et le paramètre de page de code est inchangé. Jeux **errno** à **EINVAL** si un échec d’allocation de mémoire se produit.

## <a name="remarks"></a>Notes

Le **_setmbcp** fonction spécifie une nouvelle page de codes multioctets. Par défaut, le système de runtime définit automatiquement la page de codes multioctets comme étant la page de codes ANSI par défaut du système. Le paramètre de page de codes multioctets influe sur toutes les routines multioctets qui ne sont pas dépendantes des paramètres régionaux. Toutefois, il est possible d’indiquer à **_setmbcp** à utiliser la page de codes définie pour les paramètres régionaux (consultez la liste suivante des constantes manifestes et associés les résultats de comportement). Pour obtenir la liste des routines multioctets qui dépendent de la page de codes des paramètres régionaux et non de la page de codes multioctets, consultez [Interprétation des séquences de caractères multioctets](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md).

La page de codes multioctets a aussi un impact sur le traitement des caractères multioctets assuré par les routines de bibliothèque Runtime suivantes :

||||
|-|-|-|
|[fonctions _exec](../../c-runtime-library/exec-wexec-functions.md)|[_mktemp](mktemp-wmktemp.md)|[_stat](stat-functions.md)|
|[_fullpath](fullpath-wfullpath.md)|[fonctions _spawn](../../c-runtime-library/spawn-wspawn-functions.md)|[_tempnam](tempnam-wtempnam-tmpnam-wtmpnam.md)|
|[_makepath](makepath-wmakepath.md)|[_splitpath](splitpath-wsplitpath.md)|[tmpnam](tempnam-wtempnam-tmpnam-wtmpnam.md)|

En outre, toutes les routines de bibliothèque Runtime qui reçoivent des caractères multioctets *argv* ou *envp* arguments en tant que paramètres de programme (tel que le **_exec** et **_spawn** familles) traitent ces chaînes en fonction de la page de codes multioctets. Par conséquent, ces routines sont également affectés par un appel à **_setmbcp** qui modifie la page de codes multioctets.

Le *page de codes* argument peut être défini à une des valeurs suivantes :

- **_MB_CP_ANSI** page de codes ANSI de l’utilisation est obtenu à partir du système d’exploitation au démarrage du programme.

- **_MB_CP_LOCALE** utilisez page de codes de paramètres régionaux actuels obtenu à partir d’un appel précédent à [setlocale](setlocale-wsetlocale.md).

- **_MB_CP_OEM** page de codes OEM de l’utilisation est obtenu à partir du système d’exploitation au démarrage du programme.

- **_MB_CP_SBCS** utilise la page de codes à octet unique. Quand la page de codes est définie sur **_MB_CP_SBCS**, une routine telle que [_ismbblead](ismbblead-ismbblead-l.md) retourne toujours false.

- N’importe quelle autre valeur de page de codes valide, que ce soit ANSI, OEM ou toute autre page de codes prise en charge par le système d’exploitation (à l’exception de UTF-7 et UTF-8, qui ne sont pas pris en charge).

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**_setmbcp**|\<mbctype.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[_getmbcp](getmbcp.md)<br/>
[setlocale, _wsetlocale](setlocale-wsetlocale.md)<br/>
