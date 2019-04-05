---
title: no_namespace
ms.date: 11/04/2016
f1_keywords:
- no_namespace
helpviewer_keywords:
- no_namespace attribute
ms.assetid: 5d81b741-a558-451b-b493-1f3b18967337
ms.openlocfilehash: f6bd60de02bf0166d5cf0b0cd1bc1de56ceda5bf
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/05/2019
ms.locfileid: "59028715"
---
# <a name="nonamespace"></a>no_namespace
**Section spécifique à C++**

Indique que le nom de l'espace de noms n'est pas généré par le compilateur.

## <a name="syntax"></a>Syntaxe

```
no_namespace
```

## <a name="remarks"></a>Notes

Le contenu de la bibliothèque de types dans le fichier d'en-tête `#import` est normalement défini dans un espace de noms. Le nom de l’espace de noms est spécifié dans le `library` instruction du fichier IDL d’origine. Si le **no_namespace** attribut est spécifié, alors que cet espace de noms n’est pas généré par le compilateur.

Si vous souhaitez utiliser un nom d’espace de noms différent, puis utiliser le [rename_namespace](../preprocessor/rename-namespace.md) d’attribut à la place.

**FIN de la section spécifique à C++**

## <a name="see-also"></a>Voir aussi

[Attributs #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import, directive](../preprocessor/hash-import-directive-cpp.md)