---
title: AsyncResultType, énumération
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncResultType
helpviewer_keywords:
- AsyncResultType enumeration
ms.assetid: 4195d234-3f3f-4363-9118-6ad2a7551cf2
ms.openlocfilehash: b8a2a9ec803fba1be0012fcb58bf3b42e78f9071
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214160"
---
# <a name="asyncresulttype-enumeration"></a>AsyncResultType, énumération

Spécifie le type de résultat retourné par la méthode `GetResults()`.

## <a name="syntax"></a>Syntaxe

```cpp
enum AsyncResultType;
```

## <a name="members"></a>Membres

### <a name="values"></a>Valeurs

|Name|Description|
|----------|-----------------|
|`MultipleResults`|Ensemble de plusieurs résultats, qui sont présentés progressivement entre l’état de `Start` et avant l’appel de `Close()`.|
|`SingleResult`|Un résultat unique, qui est présenté après l’événement `Complete` se produit.|

## <a name="requirements"></a>Spécifications

**En-tête :** Async. h

**Espace de noms :** Microsoft::WRL

## <a name="see-also"></a>Voir aussi

[Microsoft::WRL, espace de noms](microsoft-wrl-namespace.md)
