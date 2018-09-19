---
title: _fmode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- fmode
- _fmode
dev_langs:
- C++
helpviewer_keywords:
- file translation [C++], default mode
- fmode function
- _fmode function
ms.assetid: ac6df9eb-e5cc-4c54-aff3-373c21983118
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cfc89eeda690632979521fa8a4e91c48c8b3c866
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46080829"
---
# <a name="fmode"></a>_fmode

La variable `_fmode` définit le mode de traduction de fichiers par défaut pour la traduction de texte ou binaire. Cette variable globale a été dépréciée au profit des versions fonctionnelles plus sécurisées [_get_fmode](../c-runtime-library/reference/get-fmode.md) et [_set_fmode](../c-runtime-library/reference/set-fmode.md), à utiliser à la place. Elle est déclarée comme suit dans Stdlib.h.

## <a name="syntax"></a>Syntaxe

```
extern int _fmode;
```

## <a name="remarks"></a>Notes

Le paramètre par défaut de `_fmode` est `_O_TEXT` pour la traduction en mode texte. `_O_BINARY` est le paramètre pour le mode binaire.

Vous pouvez modifier la valeur de `_fmode` de trois façons :

- Établir un lien avec Binmode.obj. Le paramètre initial de `_fmode` passe alors à `_O_BINARY`, ce qui entraîne l’ouverture en mode binaire de tous les fichiers sauf `stdin`, `stdout` et `stderr`.

- Effectuer un appel à `_get_fmode` ou `_set_fmode` pour obtenir ou définir la variable globale `_fmode`, respectivement.

- Modifier la valeur de `_fmode` directement en la définissant dans votre programme.

## <a name="see-also"></a>Voir aussi

[Variables globales](../c-runtime-library/global-variables.md)<br/>
[_get_fmode](../c-runtime-library/reference/get-fmode.md)<br/>
[_set_fmode](../c-runtime-library/reference/set-fmode.md)