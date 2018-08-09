---
title: Constructeur de module::GenericReleaseNotifier::GenericReleaseNotifier | Microsoft Docs
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
ms.openlocfilehash: 5aa78562c934c41b2ff2ab7b381f6b2612426651
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2018
ms.locfileid: "40014586"
---
# <a name="modulegenericreleasenotifiergenericreleasenotifier-constructor"></a>Module::GenericReleaseNotifier::GenericReleaseNotifier, constructeur
Initialise une nouvelle instance de la **Module::GenericReleaseNotifier** classe.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
GenericReleaseNotifier(  
   T callback,   
   bool release  
) throw() : ReleaseNotifier(release), callback_(callback);  
```  
  
### <a name="parameters"></a>Paramètres  
 *rappel*  
 Une expression lambda, functor ou gestionnaire d’événements de pointeur de fonction qui peut être appelé avec l’opérateur de fonction entre parenthèses (`()`).  
  
 *release*  
 Spécifiez **true** pour activer l’appel sous-jacent [Module :: ReleaseNotifier::Release()](../windows/module-releasenotifier-release.md) méthode ; sinon, spécifiez **false**.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** module.h  
  
 **Espace de noms :** Microsoft::WRL  
  
## <a name="see-also"></a>Voir aussi  
 [Module::GenericReleaseNotifier, classe](../windows/module-genericreleasenotifier-class.md)