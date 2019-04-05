---
title: raw_method_prefix
ms.date: 03/27/2019
f1_keywords:
- raw_method_prefix
helpviewer_keywords:
- raw_method_prefix attribute
ms.assetid: 71490313-af78-4bb2-b28a-eee67950d30b
ms.openlocfilehash: 963e04752dcb797343550d9b89f778bfe0e8a593
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/05/2019
ms.locfileid: "59021409"
---
# <a name="rawmethodprefix"></a>raw_method_prefix

**Section spécifique à C++**

Spécifie un préfixe différent pour éviter les collisions de noms.

## <a name="syntax"></a>Syntaxe

```
raw_method_prefix("Prefix")
```

### <a name="parameters"></a>Paramètres

*Préfixe*<br/>
Le préfixe à utiliser.

## <a name="remarks"></a>Notes

Propriétés de bas niveau et les méthodes sont exposées par les fonctions membres nommées avec un préfixe par défaut de **raw_** afin d’éviter les collisions de noms avec les fonctions membres de la gestion des erreurs générales.

> [!NOTE]
> Les effets de la **raw_method_prefix** attribut ne sera pas modifié par la présence de la [raw_interfaces_only](raw-interfaces-only.md) attribut. Le **raw_method_prefix** est toujours prioritaire sur `raw_interfaces_only` pour spécifier un préfixe. Si les deux attributs sont utilisés dans le même `#import` instruction, puis le préfixe spécifié par le **raw_method_prefix** attribut est utilisé.

**FIN de la section spécifique à C++**

## <a name="see-also"></a>Voir aussi

[Attributs #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import, directive](../preprocessor/hash-import-directive-cpp.md)