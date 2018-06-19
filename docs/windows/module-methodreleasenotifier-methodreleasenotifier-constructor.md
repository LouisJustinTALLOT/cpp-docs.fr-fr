---
title: Constructeur de module::MethodReleaseNotifier::MethodReleaseNotifier | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::MethodReleaseNotifier::MethodReleaseNotifier
dev_langs:
- C++
helpviewer_keywords:
- MethodReleaseNotifier, constructor
ms.assetid: 762e2ca4-0a92-49de-9ff5-d3efa0f067c0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 91540ca3fff03f1f0a449413c2d1ca72781c70f1
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33875225"
---
# <a name="modulemethodreleasenotifiermethodreleasenotifier-constructor"></a>Module::MethodReleaseNotifier::MethodReleaseNotifier, constructeur
Initialise une nouvelle instance de la classe Module::MethodReleaseNotifier.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
MethodReleaseNotifier(  
   _In_ T* object,   
   _In_ void (T::* method)(),   
   bool release) throw() :  
            ReleaseNotifier(release), object_(object),   
            method_(method);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `object`  
 Objet dont la fonction membre est un gestionnaire d’événements.  
  
 `method`  
 La fonction membre de paramètre `object` qui est le Gestionnaire d’événements.  
  
 `release`  
 Spécifiez `true` pour activer l’appel sous-jacent [Module :: ReleaseNotifier::Release()](../windows/module-releasenotifier-release.md) méthode ; sinon, spécifiez `false`.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** module.h  
  
 **Espace de noms :** Microsoft::WRL  
  
## <a name="see-also"></a>Voir aussi  
 [Module::MethodReleaseNotifier, classe](../windows/module-methodreleasenotifier-class.md)