---
title: SRWLOCK, classe | Documents Microsoft
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
ms.openlocfilehash: ec31b1469f437ff2776ed9da52fbcd7557fca8e2
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33891751"
---
# <a name="srwlock-class"></a>SRWLock (classe)
Représente un verrou de lecteur/writer compacte.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class SRWLock;  
```  
  
## <a name="remarks"></a>Notes  
 Un verrou de lecteur/writer compacte est utilisé pour synchroniser l’accès entre plusieurs threads à un objet ou une ressource. Pour plus d’informations, consultez [des fonctions de synchronisation](http://msdn.microsoft.com/en-us/9b6359c2-0113-49b6-83d0-316ad95aba1b).  
  
## <a name="members"></a>Membres  
  
### <a name="public-typedefs"></a>Typedefs publics  
  
|||  
|-|-|  
|**SyncLockExclusive**|Synonyme pour un objet SRWLock acquis en mode exclusif.|  
|**SyncLockShared**|Synonyme pour un objet SRWLock acquis en mode partagé.|  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[SRWLock::SRWLock, constructeur](../windows/srwlock-srwlock-constructor.md)|Initialise une nouvelle instance de la classe SRWLock.|  
|[SRWLock::~SRWLock, destructeur](../windows/srwlock-tilde-srwlock-destructor.md)|Annule l’initialisation d’une instance de la classe SRWLock.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[SRWLock::LockExclusive, méthode](../windows/srwlock-lockexclusive-method.md)|Acquiert un objet SRWLock en mode exclusif.|  
|[SRWLock::LockShared, méthode](../windows/srwlock-lockshared-method.md)|Acquiert un objet SRWLock en mode partagé.|  
|[SRWLock::TryLockExclusive, méthode](../windows/srwlock-trylockexclusive-method.md)|Tente d’acquérir un objet SRWLock en mode exclusif pour l’objet SRWLock actuelle ou spécifiée.|  
|[SRWLock::TryLockShared, méthode](../windows/srwlock-trylockshared-method.md)|Tente d’acquérir un objet SRWLock en mode partagé pour l’objet SRWLock actuelle ou spécifiée.|  
  
### <a name="protected-data-member"></a>Membre de données protégées  
  
|Name|Description|  
|----------|-----------------|  
|[SRWLock::SRWLock_, données de membre](../windows/srwlock-srwlock-data-member.md)|Contient la variable sous-jacente de verrou pour l’objet SRWLock actuel.|  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `SRWLock`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** corewrappers.h  
  
 **Namespace :** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>Voir aussi  
 [Microsoft::WRL::Wrappers, espace de noms](../windows/microsoft-wrl-wrappers-namespace.md)