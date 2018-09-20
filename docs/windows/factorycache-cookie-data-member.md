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
ms.openlocfilehash: 97af2db56cab99412faf35efa8cd351946ab4828
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46410297"
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

[FactoryCache, structure](../windows/factorycache-structure.md)<br/>
[Microsoft::WRL::Details, espace de noms](../windows/microsoft-wrl-details-namespace.md)