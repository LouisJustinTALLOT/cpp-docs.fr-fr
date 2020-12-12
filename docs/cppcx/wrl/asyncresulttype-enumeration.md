---
description: 'En savoir plus sur : énumération Asyncresulttype,'
title: AsyncResultType (énumération)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncResultType
helpviewer_keywords:
- AsyncResultType enumeration
ms.assetid: 4195d234-3f3f-4363-9118-6ad2a7551cf2
ms.openlocfilehash: 431c0cabf98b3636bbae02b2f05a14d11d122740
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97175818"
---
# <a name="asyncresulttype-enumeration"></a>AsyncResultType (énumération)

Spécifie le type de résultat retourné par la `GetResults()` méthode.

## <a name="syntax"></a>Syntaxe

```cpp
enum AsyncResultType;
```

## <a name="members"></a>Membres

### <a name="values"></a>Valeurs

|Nom|Description|
|----------|-----------------|
|`MultipleResults`|Ensemble de plusieurs résultats, qui sont présentés progressivement entre les `Start` États et avant l' `Close()` appel à.|
|`SingleResult`|Résultat unique, présenté après l' `Complete` événement.|

## <a name="requirements"></a>Spécifications

**En-tête :** Async. h

**Espace de noms :** Microsoft::WRL

## <a name="see-also"></a>Voir aussi

[Microsoft :: WRL, espace de noms](microsoft-wrl-namespace.md)
