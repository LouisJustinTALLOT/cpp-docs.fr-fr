---
title: high_method_prefix
ms.date: 10/18/2018
f1_keywords:
- high_method_prefix
helpviewer_keywords:
- high_method_prefix attribute
ms.assetid: cacebf09-12f5-4919-ad40-939e206e340c
ms.openlocfilehash: 69e96a8a8f92316e32074a861456fffb83c79434
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50616446"
---
# <a name="highmethodprefix"></a>high_method_prefix

**Spécifique à C++**

Spécifie un préfixe à utiliser pour nommer les propriétés et les méthodes de haut niveau.

## <a name="syntax"></a>Syntaxe

```
high_method_prefix("Prefix")
```

### <a name="parameters"></a>Paramètres

*Prefix*<br/>
Préfixe à utiliser.

## <a name="remarks"></a>Notes

Par défaut, les propriétés de gestion des erreurs et les méthodes de niveau supérieur sont exposées par des fonctions membres nommées sans préfixe. Les noms sont issus de la bibliothèque de types.

**FIN spécifique à C++**

## <a name="see-also"></a>Voir aussi

[attributs #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[directive #import](../preprocessor/hash-import-directive-cpp.md)