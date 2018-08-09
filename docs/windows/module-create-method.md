---
title: Module::Create, méthode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::Create
dev_langs:
- C++
helpviewer_keywords:
- Create method
ms.assetid: bfa97fd7-5226-4604-92a5-3b9697053e64
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 1b3f865addd83bec64250807285947ea1c92e59f
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2018
ms.locfileid: "40016611"
---
# <a name="modulecreate-method"></a>Module::Create, méthode
Crée une instance d’un module.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
WRL_NOTHROW static Module& Create();  
template<typename T>  
WRL_NOTHROW static Module& Create(  
   T callback  
);  
template<typename T>  
WRL_NOTHROW static Module& Create(  
   _In_ T* object,  
   _In_ void (T::* method)()  
);  
```  
  
### <a name="parameters"></a>Paramètres  
 *T*  
 Type de module.  
  
 *rappel*  
 Appelé lorsque le dernier objet d’instance du module est relâché.  
  
 *object*  
 Le *objet* et *méthode* paramètres sont utilisés conjointement. Pointe vers le dernier objet d’instance lorsque le dernier objet d’instance dans le module est lancé.  
  
 *(Méthode)*  
 Le *objet* et *méthode* paramètres sont utilisés conjointement. Points à la méthode du dernier objet d’instance lorsque le dernier objet d’instance dans le module est lancé.  
  
## <a name="return-value"></a>Valeur de retour  
 Référence au module.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** module.h  
  
 **Espace de noms :** Microsoft::WRL  
  
## <a name="see-also"></a>Voir aussi  
[Module, classe](../windows/module-class.md)