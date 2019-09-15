---
title: __crtLCMapStringW
ms.date: 11/04/2016
api_name:
- __crtLCMapStringW
api_location:
- msvcr90.dll
- msvcr110_clr0400.dll
- msvcr100.dll
- msvcrt.dll
- msvcr120.dll
- msvcr110.dll
- msvcr80.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- __crtLCMapStringW
helpviewer_keywords:
- __crtLCMapStringW
ms.assetid: 45b4ac0e-438c-4fa3-b4d1-34195f4467d9
ms.openlocfilehash: 8d9458529e5772f31e3ae5463d3a6ff5a7b726e9
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70940447"
---
# <a name="__crtlcmapstringw"></a>__crtLCMapStringW

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

Si `cchSrc` est supérieure à zéro et que `lpSrcStr` est une chaîne qui se termine par un caractère null, `__crtLCMapStringW` affecte à `cchSrc` la longueur de la chaîne. `__crtLCMapStringW` appelle ensuite la version de chaîne étendue (Unicode) de la fonction `LCMapString` avec les paramètres spécifiés. Pour plus d’informations sur les paramètres et la valeur de retour de cette fonction, consultez [LCMapString](/windows/win32/api/winnls/nf-winnls-lcmapstringw).

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|__crtLCMapStringW|awint.h|