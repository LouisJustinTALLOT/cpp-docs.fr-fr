---
title: Module::genericreleasenotifier, classe | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::GenericReleaseNotifier
dev_langs:
- C++
helpviewer_keywords:
- GenericReleaseNotifier class
ms.assetid: 244a8fbe-f89b-409b-aa65-db3e37f9b125
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c3ba58e08bac36d905fbf874546d7791f2aa3fcb
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33882006"
---
# <a name="modulegenericreleasenotifier-class"></a>Module::GenericReleaseNotifier, classe
Appelle un gestionnaire d’événements lorsque le dernier objet du module en cours est libéré. Le Gestionnaire d’événements est spécifié par sur une expression lambda, functor ou pointeur de fonction.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<typename T>  
class GenericReleaseNotifier : public ReleaseNotifier;  
```  
  
#### <a name="parameters"></a>Paramètres  
 `T`  
 Le type du membre de données qui contient l’emplacement du Gestionnaire d’événements.  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[Module::GenericReleaseNotifier::GenericReleaseNotifier, constructeur](../windows/module-genericreleasenotifier-genericreleasenotifier-constructor.md)|Initialise une nouvelle instance de la classe Module::GenericReleaseNotifier.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[Module::GenericReleaseNotifier::Invoke, méthode](../windows/module-genericreleasenotifier-invoke-method.md)|Appelle le Gestionnaire d’événements associé à l’objet Module::GenericReleaseNotifier en cours.|  
  
### <a name="protected-data-members"></a>Membres de données protégés  
  
|Name|Description|  
|----------|-----------------|  
|[Module::GenericReleaseNotifier::callback_, données de membre](../windows/module-genericreleasenotifier-callback-data-member.md)|Contient l’expression lambda, un functor ou un pointeur de fonction gestionnaire associé à l’objet Module::GenericReleaseNotifier en cours.|  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `ReleaseNotifier`  
  
 `GenericReleaseNotifier`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** module.h  
  
 **Espace de noms :** Microsoft::WRL
 
 ## <a name="see-also"></a>Voir aussi
 [Module, classe](../windows/module-class.md)