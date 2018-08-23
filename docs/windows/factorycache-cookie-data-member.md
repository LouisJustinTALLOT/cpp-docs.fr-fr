---
title: Factorycache::cookie, données de membre | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::FactoryCache::cookie
dev_langs:
- C++
helpviewer_keywords:
- cookie data member
ms.assetid: b1bc79af-a896-4e3b-8afa-64733022eddf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6dba6e5d7fd478d198e48e9d8517d34e13b43484
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42613664"
---
# <a name="factorycachecookie-data-member"></a>FactoryCache::cookie, données de membre

Prend en charge l’infrastructure de la bibliothèque de modèles Windows Runtime C++ et n’est pas destinée à être utilisée directement depuis votre code.

## <a name="syntax"></a>Syntaxe

```cpp
union {
   WINRT_REGISTRATION_COOKIE winrt;
   DWORD com;
} cookie;
```

## <a name="remarks"></a>Notes

Contient une valeur qui identifie un objet de classe Windows Runtime ou COM inscrit et est utilisée ultérieurement pour annuler l’inscription de l’objet.

## <a name="requirements"></a>Configuration requise

**En-tête :** module.h

**Namespace :** Microsoft::WRL::Details

## <a name="see-also"></a>Voir aussi

[FactoryCache, structure](../windows/factorycache-structure.md)  
[Microsoft::WRL::Details, espace de noms](../windows/microsoft-wrl-details-namespace.md)