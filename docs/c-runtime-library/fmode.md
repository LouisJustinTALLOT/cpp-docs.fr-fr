---
description: 'En savoir plus sur : _fmode'
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
ms.openlocfilehash: c4e7932369a2ad63b5498078e46cd5610b679ee0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97303878"
---
# <a name="_fmode"></a>_fmode

La variable `_fmode` définit le mode de traduction de fichiers par défaut pour la traduction de texte ou binaire. Cette variable globale a été dépréciée au profit des versions fonctionnelles plus sécurisées [_get_fmode](../c-runtime-library/reference/get-fmode.md) et [_set_fmode](../c-runtime-library/reference/set-fmode.md), à utiliser à la place. Elle est déclarée comme suit dans Stdlib.h.

## <a name="syntax"></a>Syntaxe

```
extern int _fmode;
```

## <a name="remarks"></a>Notes

Le paramètre par défaut de `_fmode` est `_O_TEXT` pour la traduction en mode texte. `_O_BINARY` est le paramètre pour le mode binaire.

Vous pouvez modifier la valeur de `_fmode` de trois façons :

- Lien avec Binmode. obj. Cela modifie la valeur initiale de `_fmode` en `_O_BINARY` , provoquant l’ouverture de tous les fichiers, à l’exception de `stdin` , `stdout` et, `stderr` en mode binaire.

- Effectuer un appel à `_get_fmode` ou `_set_fmode` pour obtenir ou définir la variable globale `_fmode`, respectivement.

- Modifier la valeur de `_fmode` directement en la définissant dans votre programme.

## <a name="see-also"></a>Voir aussi

[Variables globales](../c-runtime-library/global-variables.md)<br/>
[_get_fmode](../c-runtime-library/reference/get-fmode.md)<br/>
[_set_fmode](../c-runtime-library/reference/set-fmode.md)
