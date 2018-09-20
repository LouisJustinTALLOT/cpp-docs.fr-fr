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
ms.openlocfilehash: a8b84bcaec7dbadfb7b735264df12f7e958dcd20
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46444695"
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

*T*<br/>
Type de module.

*rappel*<br/>
Appelé lorsque le dernier objet d’instance du module est relâché.

*object*<br/>
Le *objet* et *méthode* paramètres sont utilisés conjointement. Pointe vers le dernier objet d’instance lorsque le dernier objet d’instance dans le module est lancé.

*(Méthode)*<br/>
Le *objet* et *méthode* paramètres sont utilisés conjointement. Points à la méthode du dernier objet d’instance lorsque le dernier objet d’instance dans le module est lancé.

## <a name="return-value"></a>Valeur de retour

Référence au module.

## <a name="requirements"></a>Configuration requise

**En-tête :** module.h

**Espace de noms :** Microsoft::WRL

## <a name="see-also"></a>Voir aussi

[Module, classe](../windows/module-class.md)