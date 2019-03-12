---
title: _fmode
ms.date: 11/04/2016
f1_keywords:
- fmode
- _fmode
helpviewer_keywords:
- file translation [C++], default mode
- fmode function
- _fmode function
ms.assetid: ac6df9eb-e5cc-4c54-aff3-373c21983118
ms.openlocfilehash: a41d665eab50203fc3bb176f8bb1bbc30737e844
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/11/2019
ms.locfileid: "57741922"
---
# <a name="fmode"></a>_fmode

La variable `_fmode` définit le mode de traduction de fichiers par défaut pour la traduction de texte ou binaire. Cette variable globale a été dépréciée au profit des versions fonctionnelles plus sécurisées [_get_fmode](../c-runtime-library/reference/get-fmode.md) et [_set_fmode](../c-runtime-library/reference/set-fmode.md), à utiliser à la place. Elle est déclarée comme suit dans Stdlib.h.

## <a name="syntax"></a>Syntaxe

```
extern int _fmode;
```

## <a name="remarks"></a>Remarques

Le paramètre par défaut de `_fmode` est `_O_TEXT` pour la traduction en mode texte. `_O_BINARY` est le paramètre pour le mode binaire.

Vous pouvez modifier la valeur de `_fmode` de trois façons :

- Établir un lien avec Binmode.obj. Le paramètre initial de `_fmode` passe alors à `_O_BINARY`, ce qui entraîne l’ouverture en mode binaire de tous les fichiers sauf `stdin`, `stdout` et `stderr`.

- Effectuer un appel à `_get_fmode` ou `_set_fmode` pour obtenir ou définir la variable globale `_fmode`, respectivement.

- Modifier la valeur de `_fmode` directement en la définissant dans votre programme.

## <a name="see-also"></a>Voir aussi

[Variables globales](../c-runtime-library/global-variables.md)<br/>
[_get_fmode](../c-runtime-library/reference/get-fmode.md)<br/>
[_set_fmode](../c-runtime-library/reference/set-fmode.md)
