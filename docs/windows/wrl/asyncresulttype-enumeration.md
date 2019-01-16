---
title: AsyncResultType (énumération)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncResultType
helpviewer_keywords:
- AsyncResultType enumeration
ms.assetid: 4195d234-3f3f-4363-9118-6ad2a7551cf2
ms.openlocfilehash: 309ed876c71f453336ecc2ed10eedc07f2a80be8
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54335956"
---
# <a name="asyncresulttype-enumeration"></a>AsyncResultType (énumération)

Spécifie le type de résultat retourné par la `GetResults()` (méthode).

## <a name="syntax"></a>Syntaxe

```cpp
enum AsyncResultType;
```

## <a name="members"></a>Membres

### <a name="values"></a>Valeurs

|Nom|Description|
|----------|-----------------|
|`MultipleResults`|Un ensemble de résultats multiples, qui sont présentées progressivement entre `Start` état et avant `Close()` est appelée.|
|`SingleResult`|Un résultat unique, qui est présenté après la `Complete` événement se produit.|

## <a name="requirements"></a>Spécifications

**En-tête :** async.h

**Espace de noms :** Microsoft::wrl

## <a name="see-also"></a>Voir aussi

[Microsoft::WRL, espace de noms](microsoft-wrl-namespace.md)