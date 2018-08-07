---
title: Module::genericreleasenotifier, classe | Microsoft Docs
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
ms.openlocfilehash: 9e850c90ef873e64352ace64ff680cd93474a4a1
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/07/2018
ms.locfileid: "39606421"
---
# <a name="modulegenericreleasenotifier-class"></a>Module::GenericReleaseNotifier, classe
Appelle un gestionnaire d’événements lorsque le dernier objet du module en cours est relâché. Le Gestionnaire d’événements est spécifié par dans une expression lambda, functor ou pointeur de fonction.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<typename T>  
class GenericReleaseNotifier : public ReleaseNotifier;  
```  
  
### <a name="parameters"></a>Paramètres  
 *T*  
 Le type du membre de données qui contient l’emplacement du Gestionnaire d’événements.  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[Module::GenericReleaseNotifier::GenericReleaseNotifier, constructeur](../windows/module-genericreleasenotifier-genericreleasenotifier-constructor.md)|Initialise une nouvelle instance de la **Module::GenericReleaseNotifier** classe.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[Module::GenericReleaseNotifier::Invoke, méthode](../windows/module-genericreleasenotifier-invoke-method.md)|Appelle le Gestionnaire d’événements associé actuel **Module::GenericReleaseNotifier** objet.|  
  
### <a name="protected-data-members"></a>Membres de données protégés  
  
|Name|Description|  
|----------|-----------------|  
|[Module::GenericReleaseNotifier::callback_, données de membre](../windows/module-genericreleasenotifier-callback-data-member.md)|Contient l’expression lambda, functor ou gestionnaire d’événements de pointeur de fonction associé actuel **Module::GenericReleaseNotifier** objet.|  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `ReleaseNotifier`  
  
 `GenericReleaseNotifier`  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** module.h  
  
 **Espace de noms :** Microsoft::WRL
 
 ## <a name="see-also"></a>Voir aussi
 [Module, classe](../windows/module-class.md)