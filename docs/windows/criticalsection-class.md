---
title: CriticalSection (classe) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::CriticalSection
dev_langs:
- C++
helpviewer_keywords:
- CriticalSection class
ms.assetid: f2e0a024-71a3-4f6b-99ea-d93a4a608ac4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: cab1beeaa3ce54899d1a052e4972bd7e7f52bb57
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42592447"
---
# <a name="criticalsection-class"></a>CriticalSection (classe)

Représente un objet de section critique.

## <a name="syntax"></a>Syntaxe

```cpp
class CriticalSection;
```

## <a name="members"></a>Membres

### <a name="constructor"></a>Constructeur

|Name|Description|
|----------|-----------------|
|[CriticalSection::CriticalSection, constructeur](../windows/criticalsection-criticalsection-constructor.md)|Initialise un objet de synchronisation qui est similaire à un objet mutex, mais peut être utilisé par uniquement les threads d’un processus unique.|
|[CriticalSection::~CriticalSection, destructeur](../windows/criticalsection-tilde-criticalsection-destructor.md)|Annule l’initialisation et détruit actuel **CriticalSection** objet.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CriticalSection::TryLock, méthode](../windows/criticalsection-trylock-method.md)|Tentatives de saisie d’une section critique sans bloquer. Si l’appel réussit, le thread appelant prend possession de la section critique.|
|[CriticalSection::Lock, méthode](../windows/criticalsection-lock-method.md)|Attend que la propriété de l’objet de section critique spécifié. La fonction retourne quand le thread appelant est accordé à la propriété.|
|[CriticalSection::IsValid, méthode](../windows/criticalsection-isvalid-method.md)|Indique si la section critique en cours est valide.|

### <a name="protected-data-members"></a>Membres de données protégés

|Name|Description|
|----------|-----------------|
|[CriticalSection::cs_, données de membre](../windows/criticalsection-cs-data-member.md)|Déclare un membre de données de section critique.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`CriticalSection`

## <a name="requirements"></a>Configuration requise

**En-tête :** corewrappers.h

**Namespace :** Microsoft::WRL::Wrappers

## <a name="see-also"></a>Voir aussi

[Microsoft::WRL::Wrappers, espace de noms](../windows/microsoft-wrl-wrappers-namespace.md)