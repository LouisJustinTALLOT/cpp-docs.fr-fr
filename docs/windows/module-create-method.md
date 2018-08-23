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
ms.openlocfilehash: 9ae4f50e6d2d614e444766babf8e55f5c9f83932
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42609542"
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