---
title: Synclockwithstatust, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT
dev_langs:
- C++
helpviewer_keywords:
- SyncLockWithStatusT class
ms.assetid: 4832fd93-0ac8-4168-9404-b43fefea7476
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a0c53832acdd7a785ccc36941cd317a9d0705173
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42583624"
---
# <a name="synclockwithstatust-class"></a>SyncLockWithStatusT, classe

Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.

## <a name="syntax"></a>Syntaxe

```cpp
template <
   typename SyncTraits
>
class SyncLockWithStatusT : public SyncLockT<SyncTraits>;
```

### <a name="parameters"></a>Paramètres

*SyncTraits*  
Un type qui peut prendre exclusif ou la propriété d’une ressource partagée.

## <a name="remarks"></a>Notes

Représente un type qui peut prendre exclusif ou la propriété d’une ressource partagée.

Le **SyncLockWithStatusT** classe est utilisée pour implémenter le [Mutex](../windows/mutex-class1.md) et [sémaphore](../windows/semaphore-class.md) classes.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[SyncLockWithStatusT::SyncLockWithStatusT, constructeur](../windows/synclockwithstatust-synclockwithstatust-constructor.md)|Initialise une nouvelle instance de la **SyncLockWithStatusT** classe.|

### <a name="protected-constructors"></a>Constructeurs protégés

|Nom|Description|
|----------|-----------------|
|[SyncLockWithStatusT::SyncLockWithStatusT, constructeur](../windows/synclockwithstatust-synclockwithstatust-constructor.md)|Initialise une nouvelle instance de la **SyncLockWithStatusT** classe.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[SyncLockWithStatusT::GetStatus, méthode](../windows/synclockwithstatust-getstatus-method.md)|Récupère l’état d’attente de l’actuel **SyncLockWithStatusT** objet.|
|[SyncLockWithStatusT::IsLocked, méthode](../windows/synclockwithstatust-islocked-method.md)|Indique si l’actuel **SyncLockWithStatusT** objet possède une ressource, c'est-à-dire, le **SyncLockWithStatusT** objet est *verrouillé*.|

### <a name="protected-data-members"></a>Membres de données protégés

|Name|Description|
|----------|-----------------|
|[SyncLockWithStatusT::status_, données de membre](../windows/synclockwithstatust-status-data-member.md)|Contient le résultat de l’opération d’attente sous-jacente après une opération de verrouillage sur un objet selon actuel **SyncLockWithStatusT** objet.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`SyncLockT`

`SyncLockWithStatusT`

## <a name="requirements"></a>Configuration requise

**En-tête :** corewrappers.h

**Namespace :** Microsoft::WRL::Wrappers::Details

## <a name="see-also"></a>Voir aussi

[Microsoft::WRL::Wrappers::Details, espace de noms](../windows/microsoft-wrl-wrappers-details-namespace.md)