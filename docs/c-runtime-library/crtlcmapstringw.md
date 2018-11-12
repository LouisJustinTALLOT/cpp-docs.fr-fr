---
title: __crtLCMapStringW
ms.date: 11/04/2016
apiname:
- __crtLCMapStringW
apilocation:
- msvcr90.dll
- msvcr110_clr0400.dll
- msvcr100.dll
- msvcrt.dll
- msvcr120.dll
- msvcr110.dll
- msvcr80.dll
apitype: DLLExport
f1_keywords:
- __crtLCMapStringW
helpviewer_keywords:
- __crtLCMapStringW
ms.assetid: 45b4ac0e-438c-4fa3-b4d1-34195f4467d9
ms.openlocfilehash: 0c3752baba05e18903c32919505d702081d09dca
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50468417"
---
# <a name="crtlcmapstringw"></a>__crtLCMapStringW

Mappe une chaîne de caractères à une autre en effectuant une transformation dépendante des paramètres régionaux spécifiés. Cette fonction peut aussi être utilisée pour générer une clé de tri pour la chaîne d’entrée.

## <a name="syntax"></a>Syntaxe

```cpp
int __crtLCMapStringW(
   LCID    Locale,
   DWORD   dwMapFlags,
   LPCWSTR lpSrcStr,
   int     cchSrc,
   LPWSTR  lpDestStr,
   int     cchDest)
```

#### <a name="parameters"></a>Paramètres

*Paramètres régionaux*<br/>
Identificateur de paramètres régionaux. Les paramètres régionaux fournissent un contexte pour le mappage de chaînes ou la génération de clés de tri. Une application peut utiliser la macro `MAKELCID` pour créer un identificateur de paramètres régionaux.

*dwMapFlags*<br/>
Type de transformation à utiliser pendant le mappage de chaînes ou la génération de clés de tri.

*lpSrcStr*<br/>
Pointeur vers une chaîne source que la fonction mappe ou utilise pour la génération de clés de tri. Ce paramètre est censé être une chaîne de type Unicode.

*cchSrc*<br/>
Taille en caractères de la chaîne pointée par le paramètre `lpSrcStr` . Ce nombre peut ou non inclure le terminateur null.

La valeur -1 de `cchSrc` indique que la chaîne pointée par `lpSrcStr` se termine par un caractère Null. Si c’est le cas et si cette fonction est utilisée dans son mode mappage de chaîne, la fonction calcule la longueur proprement dite de la chaîne et termine la chaîne mappée stockée dans `*lpDestStr`par un caractère null.

*lpDestStr*<br/>
Pointeur long désignant une mémoire tampon dans laquelle la fonction stocke la chaîne mappée ou la clé de tri.

*cchDest*<br/>
Taille en caractères de la mémoire tampon pointée par `lpDestStr`.

## <a name="return-value"></a>Valeur de retour

Si la valeur de `cchDest` est différente de zéro, le nombre de caractères (ou d’octets si `LCMAP_SORTKEY` est spécifié) écrits dans la mémoire tampon indique que l’opération a réussi. Ce nombre inclut l’espace destiné à accueillir un terminateur null.

Si la valeur de `cchDest` est égale à zéro, la taille de la mémoire tampon en caractères (ou en octets si `LCMAP_SORTKEY` est spécifié) nécessaire pour recevoir la chaîne traduite ou la clé de tri indique que l’opération a réussi. Cette taille inclut de l’espace destiné à accueillir un terminateur null.

La valeur zéro indique l’échec de l’opération. Pour obtenir des informations plus complètes sur les erreurs, appelez la fonction `GetLastError` .

## <a name="remarks"></a>Notes

Si `cchSrc` est supérieure à zéro et que `lpSrcStr` est une chaîne qui se termine par un caractère null, `__crtLCMapStringW` affecte à `cchSrc` la longueur de la chaîne. `__crtLCMapStringW` appelle ensuite la version de chaîne étendue (Unicode) de la fonction `LCMapString` avec les paramètres spécifiés. Pour plus d’informations sur les paramètres et la valeur de retour de cette fonction, consultez [LCMapString](/windows/desktop/api/winnls/nf-winnls-lcmapstringa).

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|__crtLCMapStringW|awint.h|