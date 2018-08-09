---
title: 'Module::ReleaseNotifier :: appeler la méthode | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::ReleaseNotifier::Invoke
dev_langs:
- C++
helpviewer_keywords:
- Invoke method
ms.assetid: f62686fe-74bf-482b-a46b-6a3c09b80e7e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 48e488188ed040d29ef70f273991d1df9cf1d63e
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2018
ms.locfileid: "40014602"
---
# <a name="modulereleasenotifierinvoke-method"></a>Module::ReleaseNotifier::Invoke, méthode
En cas d’implémentation, appelle un gestionnaire d’événements lorsque le dernier objet dans un module est lancé.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
virtual void Invoke() = 0;  
```  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** module.h  
  
 **Espace de noms :** Microsoft::WRL  
  
## <a name="see-also"></a>Voir aussi  
 [Module::ReleaseNotifier, classe](../windows/module-releasenotifier-class.md)