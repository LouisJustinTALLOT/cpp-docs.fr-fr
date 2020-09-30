---
title: __argc, __argv, __wargv
description: Décrit les constantes globales de la bibliothèque Runtime C de Microsoft __argc , __argv et __wargv .
ms.date: 11/04/2016
api_name:
- __wargv
- __argv
- __argc
api_location:
- msvcrt120.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- __argv
- __argc
- __wargv
helpviewer_keywords:
- __argv
- __wargv
- __argc
ms.assetid: 17001b0a-04ad-4762-b3a6-c54847f02d7c
no-loc:
- __argc
- __argv
- __wargv
- main
- wmain
ms.openlocfilehash: 02c130be0d2dcb8e48d2bb5c75438c94003fc9dd
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91507597"
---
# <a name="no-loc__argc-no-loc__argv-no-loc__wargv"></a>__argc, __argv, __wargv

La variable globale `__argc` est un décompte du nombre d'arguments de ligne de commande passés au programme. `__argv` est un pointeur vers un tableau de chaînes de caractères codés sur un ou plusieurs octets qui contiennent les arguments du programme, tandis que `__wargv` est un pointeur vers un tableau de chaînes de caractères larges qui contiennent les arguments du programme. Ces variables globales fournissent les arguments à `main` ou `wmain`.

## <a name="syntax"></a>Syntaxe

```C
extern int __argc;
extern char ** __argv;
extern wchar_t ** __wargv;
```

## <a name="remarks"></a>Notes

Dans un programme qui utilise la fonction `main`, les variables `__argc` et `__argv` sont initialisées au démarrage du programme à partir de la ligne de commande utilisée pour démarrer le programme. La ligne de commande est analysée dans des arguments individuels, et les caractères génériques sont développés. Le nombre d'arguments est assigné à `__argc` et les chaînes d'arguments sont allouées sur le tas ; par ailleurs, un pointeur vers le tableau d'arguments est assigné à `__argv`. Dans un programme compilé pour utiliser des caractères larges et une fonction `wmain`, les arguments sont analysés et les caractères génériques développés sous forme de chaînes de caractères larges, tandis qu'un pointeur vers le tableau de chaînes d'arguments est assigné à `__wargv`.

Pour un code portable, nous vous recommandons d'utiliser les arguments passés à `main` pour obtenir les arguments de ligne de commande dans votre programme.

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine Tchar.h|_UNICODE non défini|_UNICODE défini|
|---------------------|---------------------------|-----------------------|
|`__targv`|`__argv`|`__wargv`|

## <a name="requirements"></a>Configuration requise

|Variable globale|En-tête requis|
|---------------------|---------------------|
|`__argc`, `__argv`, `__wargv`|\<stdlib.h>, \<cstdlib> (C++)|

`__argc`, `__argv` et `__wargv` sont des extensions Microsoft. Pour plus d’informations sur la compatibilité, consultez [Compatibilité](../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Variables globales](../c-runtime-library/global-variables.md)\
[main fonction et arguments de ligne de commande (C++)](../cpp/main-function-command-line-args.md)\
[Utilisation à la wmain place de main](../cpp/main-function-command-line-args.md)
