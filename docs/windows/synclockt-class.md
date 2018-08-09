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
ms.openlocfilehash: f6b27f45d3a9b9b308a56e1ac8f945969f8c49e2
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/08/2018
ms.locfileid: "39643424"
---
# <a name="synclockt-class"></a>SyncLockT (classe)
Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
 [Microsoft::wrl::wrappers::Details Namespace](../windows/microsoft-wrl-wrappers-details-namespace.md)   
 [SRWLock, classe](../windows/srwlock-class.md)