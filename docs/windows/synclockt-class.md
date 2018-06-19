---
title: Synclockt, classe | Documents Microsoft
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
ms.openlocfilehash: e05a1be5d84db52573d3c3235936ecf82dde5894
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33892850"
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
  
#### <a name="parameters"></a>Paramètres  
 `SyncTraits`  
 Type qui peut prendre possession d’une ressource.  
  
## <a name="remarks"></a>Notes  
 Représente un type qui peut prendre exclusif ou partagé possession d’une ressource.  
  
 La classe SyncLockT est utilisée, par exemple, pour aider à implémenter la [SRWLock](../windows/srwlock-class.md) classe.  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[SyncLockT::SyncLockT, constructeur](../windows/synclockt-synclockt-constructor.md)|Initialise une nouvelle instance de la classe SyncLockT.|  
|[SyncLockT::~SyncLockT, destructeur](../windows/synclockt-tilde-synclockt-destructor.md)|Annule l’initialisation d’une instance de la classe SyncLockT.|  
  
### <a name="protected-constructors"></a>Constructeurs protégés  
  
|Nom|Description|  
|----------|-----------------|  
|[SyncLockT::SyncLockT, constructeur](../windows/synclockt-synclockt-constructor.md)|Initialise une nouvelle instance de la classe SyncLockT.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[SyncLockT::IsLocked, méthode](../windows/synclockt-islocked-method.md)|Indique si l’objet SyncLockT actuel possède une ressource ; l’objet SyncLockT est *verrouillé*.|  
|[SyncLockT::Unlock, méthode](../windows/synclockt-unlock-method.md)|Libère le contrôle de la ressource détenue par l’objet SyncLockT actuel, le cas échéant.|  
  
### <a name="protected-data-members"></a>Membres de données protégés  
  
|Name|Description|  
|----------|-----------------|  
|[SyncLockT::sync_, données de membre](../windows/synclockt-sync-data-member.md)|Contient la ressource sous-jacente représentée par la classe SyncLockT.|  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `SyncLockT`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** corewrappers.h  
  
 **Namespace :** Microsoft::WRL::Wrappers::Details  
  
## <a name="see-also"></a>Voir aussi  
 [Microsoft::wrl::wrappers::Details Namespace](../windows/microsoft-wrl-wrappers-details-namespace.md)   
 [SRWLock, classe](../windows/srwlock-class.md)