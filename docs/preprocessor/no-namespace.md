---
title: no_namespace
ms.date: 11/04/2016
f1_keywords:
- no_namespace
helpviewer_keywords:
- no_namespace attribute
ms.assetid: 5d81b741-a558-451b-b493-1f3b18967337
ms.openlocfilehash: b17bf5fb5f44d5453de29febe001f9e8737102b5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50540437"
---
# <a name="nonamespace"></a>no_namespace
**Spécifique à C++**

Indique que le nom de l'espace de noms n'est pas généré par le compilateur.

## <a name="syntax"></a>Syntaxe

```
no_namespace
```

## <a name="remarks"></a>Notes

Le contenu de la bibliothèque de types dans le fichier d'en-tête `#import` est normalement défini dans un espace de noms. Le nom de l’espace de noms est spécifié dans le `library` instruction du fichier IDL d’origine. Si le **no_namespace** attribut est spécifié, alors que cet espace de noms n’est pas généré par le compilateur.

Si vous souhaitez utiliser un nom d’espace de noms différent, puis utiliser le [rename_namespace](../preprocessor/rename-namespace.md) d’attribut à la place.

**FIN spécifique à C++**

## <a name="see-also"></a>Voir aussi

[attributs #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[directive #import](../preprocessor/hash-import-directive-cpp.md)