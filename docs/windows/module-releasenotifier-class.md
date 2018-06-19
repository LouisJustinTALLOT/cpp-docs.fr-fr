---
title: Module::releasenotifier, classe | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::ReleaseNotifier
dev_langs:
- C++
helpviewer_keywords:
- ReleaseNotifier class
ms.assetid: 17249cd1-4d88-42e3-8146-da9e942d12bd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 76edb403fae12dd8b6221d8bd6ec82424bc5a4f7
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33878390"
---
# <a name="modulereleasenotifier-class"></a>Module::ReleaseNotifier, classe
Appelle un gestionnaire d’événements lorsque le dernier objet dans un module est lancé.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class ReleaseNotifier;  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[Module::ReleaseNotifier::~ReleaseNotifier, destructeur](../windows/module-releasenotifier-tilde-releasenotifier-destructor.md)|Désinitialise l’instance actuelle de la classe Module::ReleaseNotifier.|  
|[Module::ReleaseNotifier::ReleaseNotifier, constructeur](../windows/module-releasenotifier-releasenotifier-constructor.md)|Initialise une nouvelle instance de la classe Module::ReleaseNotifier.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[Module::ReleaseNotifier::Invoke, méthode](../windows/module-releasenotifier-invoke-method.md)|En cas d’implémentation, appelle un gestionnaire d’événements lorsque le dernier objet dans un module est lancé.|  
|[Module::ReleaseNotifier::Release](../windows/module-releasenotifier-release.md)|Supprime l’objet Module::ReleaseNotifier actuel si l’objet a été construit avec un paramètre de `true`.|  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `ReleaseNotifier`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** module.h  
  
 **Espace de noms :** Microsoft::WRL
 
 ## <a name="see-also"></a>Voir aussi
 [Module, classe](../windows/module-class.md)