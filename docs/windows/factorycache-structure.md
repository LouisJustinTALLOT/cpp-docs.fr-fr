---
title: FactoryCache (Structure) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::FactoryCache
dev_langs:
- C++
helpviewer_keywords:
- FactoryCache structure
ms.assetid: 624544e6-0989-47f6-a3e9-edb60e1ee6d4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: df2335a49d2d5daf862db7cea7eb413c01164bee
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42609026"
---
# <a name="factorycache-structure"></a>FactoryCache (structure)

Prend en charge l’infrastructure de la bibliothèque de modèles Windows Runtime C++ et n’est pas destinée à être utilisée directement depuis votre code.

## <a name="syntax"></a>Syntaxe

```cpp
struct FactoryCache;
```

## <a name="remarks"></a>Notes

Contient l’emplacement d’une fabrique de classe et une valeur qui identifie un inscrits wrt ou l’objet de classe COM.

## <a name="members"></a>Membres

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[FactoryCache::cookie, données de membre](../windows/factorycache-cookie-data-member.md)|Contient une valeur qui identifie un objet de classe Windows Runtime ou COM inscrit et est utilisée ultérieurement pour annuler l’inscription de l’objet.|
|[FactoryCache::factory, données de membre](../windows/factorycache-factory-data-member.md)|Pointe vers une fabrique de classe Windows Runtime ou COM.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`FactoryCache`

## <a name="requirements"></a>Configuration requise

**En-tête :** module.h

**Namespace :** Microsoft::WRL::Details

## <a name="see-also"></a>Voir aussi

[Microsoft::WRL::Details, espace de noms](../windows/microsoft-wrl-details-namespace.md)