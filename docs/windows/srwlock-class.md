---
title: SRWLock (classe) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::SRWLock
dev_langs:
- C++
helpviewer_keywords:
- SRWLock class
ms.assetid: 4fa250e3-5f29-4b06-ac24-61b6c04ade93
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 23881f2065276aa7ae7b6ee95b5449abb07dd2de
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/08/2018
ms.locfileid: "39641951"
---
# <a name="srwlock-class"></a>SRWLock (classe)
Représente un verrou SRW.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class SRWLock;  
```  
  
## <a name="remarks"></a>Notes  
 Un verrou SRW est utilisé pour synchroniser l’accès entre plusieurs threads à un objet ou une ressource. Pour plus d’informations, consultez [des fonctions de synchronisation](http://msdn.microsoft.com/9b6359c2-0113-49b6-83d0-316ad95aba1b).  
  
## <a name="members"></a>Membres  
  
### <a name="public-typedefs"></a>Typedefs publics  
  
|||  
|-|-|  
|`SyncLockExclusive`|Synonyme pour un **SRWLock** objet est acquis en mode exclusif.|  
|`SyncLockShared`|Synonyme pour un **SRWLock** objet est acquis en mode partagé.|  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[SRWLock::SRWLock, constructeur](../windows/srwlock-srwlock-constructor.md)|Initialise une nouvelle instance de la **SRWLock** classe.|  
|[SRWLock::~SRWLock, destructeur](../windows/srwlock-tilde-srwlock-destructor.md)|Annule l’initialisation d’une instance de la **SRWLock** classe.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[SRWLock::LockExclusive, méthode](../windows/srwlock-lockexclusive-method.md)|Acquiert un **SRWLock** objet en mode exclusif.|  
|[SRWLock::LockShared, méthode](../windows/srwlock-lockshared-method.md)|Acquiert un **SRWLock** objet en mode partagé.|  
|[SRWLock::TryLockExclusive, méthode](../windows/srwlock-trylockexclusive-method.md)|Tente d’acquérir un **SRWLock** objet en mode exclusif pour la valeur actuelle ou spécifiée **SRWLock** objet.|  
|[SRWLock::TryLockShared, méthode](../windows/srwlock-trylockshared-method.md)|Tente d’acquérir un **SRWLock** objet en mode partagé pour la valeur actuelle ou spécifiée **SRWLock** objet.|  
  
### <a name="protected-data-member"></a>Membre de données protégées  
  
|Name|Description|  
|----------|-----------------|  
|[SRWLock::SRWLock_, données de membre](../windows/srwlock-srwlock-data-member.md)|Contient la variable sous-jacente de verrou actif **SRWLock** objet.|  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `SRWLock`  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** corewrappers.h  
  
 **Namespace :** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>Voir aussi  
 [Microsoft::WRL::Wrappers, espace de noms](../windows/microsoft-wrl-wrappers-namespace.md)