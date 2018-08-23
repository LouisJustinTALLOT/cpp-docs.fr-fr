---
title: SyncLockT (classe) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockT
dev_langs:
- C++
helpviewer_keywords:
- SyncLockT class
ms.assetid: a967f6f7-3555-43d1-b210-2bb65d63d15e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e8589c43d49709842a745464d2727860ccd2c1e2
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42609675"
---
# <a name="synclockt-class"></a>SyncLockT (classe)

Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.

## <a name="syntax"></a>Syntaxe

```cpp
template <
   typename SyncTraits
>
class SyncLockT;
```

### <a name="parameters"></a>Paramètres

*SyncTraits*  
Type qui peut prendre possession d’une ressource.

## <a name="remarks"></a>Notes

Représente un type qui peut prendre exclusif ou la propriété d’une ressource partagée.

Le **SyncLockT** classe est utilisée, par exemple, pour aider à implémenter la [SRWLock](../windows/srwlock-class.md) classe.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[SyncLockT::SyncLockT, constructeur](../windows/synclockt-synclockt-constructor.md)|Initialise une nouvelle instance de la **SyncLockT** classe.|
|[SyncLockT::~SyncLockT, destructeur](../windows/synclockt-tilde-synclockt-destructor.md)|Annule l’initialisation d’une instance de la **SyncLockT** classe.|

### <a name="protected-constructors"></a>Constructeurs protégés

|Nom|Description|
|----------|-----------------|
|[SyncLockT::SyncLockT, constructeur](../windows/synclockt-synclockt-constructor.md)|Initialise une nouvelle instance de la **SyncLockT** classe.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[SyncLockT::IsLocked, méthode](../windows/synclockt-islocked-method.md)|Indique si l’actuel **SyncLockT** objet possède une ressource, c'est-à-dire, le **SyncLockT** objet est *verrouillé*.|
|[SyncLockT::Unlock, méthode](../windows/synclockt-unlock-method.md)|Contrôle de la ressource détenue par l’actuel **SyncLockT** de l’objet, le cas échéant.|

### <a name="protected-data-members"></a>Membres de données protégés

|Name|Description|
|----------|-----------------|
|[SyncLockT::sync_, données de membre](../windows/synclockt-sync-data-member.md)|Contient la ressource sous-jacente représentée par la **SyncLockT** classe.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`SyncLockT`

## <a name="requirements"></a>Configuration requise

**En-tête :** corewrappers.h

**Namespace :** Microsoft::WRL::Wrappers::Details

## <a name="see-also"></a>Voir aussi

[Microsoft::WRL::Wrappers::Details, espace de noms](../windows/microsoft-wrl-wrappers-details-namespace.md)  
[SRWLock, classe](../windows/srwlock-class.md)