---
title: Constructeur de module::GenericReleaseNotifier::GenericReleaseNotifier | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::GenericReleaseNotifier::GenericReleaseNotifier
dev_langs:
- C++
helpviewer_keywords:
- GenericReleaseNotifier, constructor
ms.assetid: feb5b687-a4b0-4809-9022-8f292181b7a1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: bb07c7f53e27e380ba5775369611299cad0f60d4
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33875056"
---
# <a name="modulegenericreleasenotifiergenericreleasenotifier-constructor"></a>Module::GenericReleaseNotifier::GenericReleaseNotifier, constructeur
Initialise une nouvelle instance de la classe Module::GenericReleaseNotifier.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      GenericReleaseNotifier(  
   T callback,   
   bool release  
) throw() : ReleaseNotifier(release), callback_(callback);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `callback`  
 Une expression lambda, un functor ou un gestionnaire d’événements de pointeur de fonction qui peut être appelé avec l’opérateur de fonction entre parenthèses (`()`).  
  
 `release`  
 Spécifiez `true` pour activer l’appel sous-jacent [Module :: ReleaseNotifier::Release()](../windows/module-releasenotifier-release.md) méthode ; sinon, spécifiez `false`.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** module.h  
  
 **Espace de noms :** Microsoft::WRL  
  
## <a name="see-also"></a>Voir aussi  
 [Module::GenericReleaseNotifier, classe](../windows/module-genericreleasenotifier-class.md)