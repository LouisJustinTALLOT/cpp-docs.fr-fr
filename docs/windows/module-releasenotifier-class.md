---
title: Module::releasenotifier, classe | Microsoft Docs
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
ms.openlocfilehash: 97c998f7e0814c5acae55dd3e9b747faed0242e1
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2018
ms.locfileid: "40016221"
---
# <a name="modulereleasenotifier-class"></a>Module::ReleaseNotifier, classe
Appelle un gestionnaire d’événements lorsque le dernier objet dans un module est lancé.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
class ReleaseNotifier;  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[Module::ReleaseNotifier::~ReleaseNotifier, destructeur](../windows/module-releasenotifier-tilde-releasenotifier-destructor.md)|Annule l’initialisation de l’instance actuelle de la **Module::ReleaseNotifier** classe.|  
|[Module::ReleaseNotifier::ReleaseNotifier, constructeur](../windows/module-releasenotifier-releasenotifier-constructor.md)|Initialise une nouvelle instance de la **Module::ReleaseNotifier** classe.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[Module::ReleaseNotifier::Invoke, méthode](../windows/module-releasenotifier-invoke-method.md)|En cas d’implémentation, appelle un gestionnaire d’événements lorsque le dernier objet dans un module est lancé.|  
|[Module::ReleaseNotifier::Release](../windows/module-releasenotifier-release.md)|Supprime l’actuel **Module::ReleaseNotifier** si l’objet a été construit avec un paramètre de l’objet **true**.|  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `ReleaseNotifier`  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** module.h  
  
 **Espace de noms :** Microsoft::WRL
 
 ## <a name="see-also"></a>Voir aussi
 [Module, classe](../windows/module-class.md)