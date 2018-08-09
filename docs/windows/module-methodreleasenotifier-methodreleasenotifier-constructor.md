---
title: Constructeur de module::MethodReleaseNotifier::MethodReleaseNotifier | Microsoft Docs
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
ms.openlocfilehash: 01c000ee928e9394827a69acb48ef0f41478a699
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2018
ms.locfileid: "40018505"
---
# <a name="modulemethodreleasenotifiermethodreleasenotifier-constructor"></a>Module::MethodReleaseNotifier::MethodReleaseNotifier, constructeur
Initialise une nouvelle instance de la **Module::MethodReleaseNotifier** classe.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
MethodReleaseNotifier(  
   _In_ T* object,   
   _In_ void (T::* method)(),   
   bool release) throw() :  
            ReleaseNotifier(release), object_(object),   
            method_(method);  
```  
  
### <a name="parameters"></a>Paramètres  
 *object*  
 Objet dont la fonction membre est un gestionnaire d’événements.  
  
 *(Méthode)*  
 La fonction membre de paramètre *objet* qui est le Gestionnaire d’événements.  
  
 *release*  
 Spécifiez **true** pour activer l’appel sous-jacent [Module :: ReleaseNotifier::Release()](../windows/module-releasenotifier-release.md) méthode ; sinon, spécifiez **false**.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** module.h  
  
 **Espace de noms :** Microsoft::WRL  
  
## <a name="see-also"></a>Voir aussi  
 [Module::MethodReleaseNotifier, classe](../windows/module-methodreleasenotifier-class.md)