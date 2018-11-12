---
title: rename_namespace
ms.date: 10/18/2018
f1_keywords:
- rename_namespace
helpviewer_keywords:
- rename_namespace attribute
ms.assetid: 45006d2b-36cd-4bec-98b9-3b8ec45299e3
ms.openlocfilehash: 6521fe0a5bfbe482bf2aed8f5a32221abdc6d6d3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50531593"
---
# <a name="renamenamespace"></a>rename_namespace

**Spécifique à C++**

Renomme l'espace de noms qui contient le contenu de la bibliothèque de types.

## <a name="syntax"></a>Syntaxe

```
rename_namespace("NewName")
```

### <a name="parameters"></a>Paramètres

*NewName*<br/>
Nom du nouvel espace de noms.

## <a name="remarks"></a>Notes

Il accepte un seul argument, *NewName*, qui spécifie le nouveau nom de l’espace de noms.

Pour supprimer l’espace de noms, utilisez le [no_namespace](../preprocessor/no-namespace.md) attribut à la place.

**FIN spécifique à C++**

## <a name="see-also"></a>Voir aussi

[attributs #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[directive #import](../preprocessor/hash-import-directive-cpp.md)