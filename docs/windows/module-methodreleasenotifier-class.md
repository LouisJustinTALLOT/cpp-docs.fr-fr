---
title: Module::methodreleasenotifier, classe | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::MethodReleaseNotifier
dev_langs:
- C++
helpviewer_keywords:
- MethodReleaseNotifier class
ms.assetid: 5c2902be-964b-488f-9f1c-adf504995cbc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 217e58f73130922d45f0d303e1e91858e8c2272f
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33880820"
---
# <a name="modulemethodreleasenotifier-class"></a>Module::MethodReleaseNotifier, classe
Appelle un gestionnaire d’événements lorsque le dernier objet du module en cours est libéré. Le Gestionnaire d’événements est spécifié par un objet et son membre de pointeur de méthode.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<typename T>  
class MethodReleaseNotifier : public ReleaseNotifier;  
```  
  
#### <a name="parameters"></a>Paramètres  
 `T`  
 Le type de l’objet dont la fonction membre est le Gestionnaire d’événements.  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[Module::MethodReleaseNotifier::MethodReleaseNotifier, constructeur](../windows/module-methodreleasenotifier-methodreleasenotifier-constructor.md)|Initialise une nouvelle instance de la classe Module::MethodReleaseNotifier.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[Module::MethodReleaseNotifier::Invoke, méthode](../windows/module-methodreleasenotifier-invoke-method.md)|Appelle le Gestionnaire d’événements associé à l’objet Module::MethodReleaseNotifier en cours.|  
  
### <a name="protected-data-members"></a>Membres de données protégés  
  
|Name|Description|  
|----------|-----------------|  
|[Module::MethodReleaseNotifier::method_, données de membre](../windows/module-methodreleasenotifier-method-data-member.md)|Contient un pointeur vers le Gestionnaire d’événements pour l’objet Module::MethodReleaseNotifier actuel.|  
|[Module::MethodReleaseNotifier::object_, données de membre](../windows/module-methodreleasenotifier-object-data-member.md)|Contient un pointeur vers l’objet dont la fonction membre est le Gestionnaire d’événements pour l’objet Module::MethodReleaseNotifier actuel.|  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `ReleaseNotifier`  
  
 `MethodReleaseNotifier`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** module.h  
  
 **Espace de noms :** Microsoft::WRL
 
 ## <a name="see-also"></a>Voir aussi
 [Module, classe](../windows/module-class.md)