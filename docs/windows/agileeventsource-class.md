---
title: Classe de AgileEventSource | Documents Microsoft
ms.custom: ''
ms.date: 03/22/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::AgileEventSource
- event/Microsoft::WRL::InvokeModeOptions
dev_langs:
- C++
helpviewer_keywords:
- AgileEventSource class
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 58eb96e3a0268d3ba70b60d9c315e935e19485f3
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33858118"
---
# <a name="agileeventsource-class"></a>Classe de AgileEventSource

Représente un événement déclenché par un composant agile, qui est un composant qui est accessible à partir de n’importe quel thread. Hérite de [EventSource](eventsource-class.md) et remplace le `Add` fonction membre avec un paramètre de type supplémentaires pour spécifier des options pour l’appel de l’événement agile.

## <a name="syntax"></a>Syntaxe

```
template<typename TDelegateInterface, typename TEventSourceOptions = Microsoft::WRL::InvokeModeOptions<FireAll>>
class AgileEventSource
    : public Microsoft::WRL::EventSource<TDelegateInterface, TEventSourceOptions>;
```

## <a name="parameters"></a>Paramètres  
 `TDelegateInterface`  

 L’interface d’un délégué qui représente un gestionnaire d’événements.

 `TEventSourceOptions`  
 Un [InvokeModeOptions](invokemodeoptions-structure.md) structure dont le champ invokeMode a la valeur `InvokeMode::StopOnFirstError` ou `InvokeMode::FireAll`.

## <a name="remarks"></a>Notes

La grande majorité des composants dans le Windows Runtime sont des composants agiles. Pour plus d’informations, consultez [thread et Marshaling (C + c++ / CX)](../cppcx/threading-and-marshaling-c-cx.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

 `EventSource` `AgileEventSource`

## <a name="requirements"></a>Spécifications

 **En-tête :** event.h

 **Espace de noms :** Microsoft::WRL

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[AgileEventSource::Add (méthode)](#add)|Ajoute le Gestionnaire d’événements agile représenté par l’interface de délégué spécifié à l’ensemble des gestionnaires d’événements pour l’objet AgileEventSource en cours.|

## <a name="add"></a> AgileEventSource::Add (méthode)

Ajoute le Gestionnaire d’événements représenté par l’interface de délégué spécifié à l’ensemble des gestionnaires d’événements pour actuel [EventSource](eventsource-class.md) objet.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT Add(
   _In_ TDelegateInterface* delegateInterface,
   _Out_ EventRegistrationToken* token
);
```

### <a name="parameters"></a>Paramètres

*delegateInterface*

Interface à un seul objet délégué, qui représente un gestionnaire d’événements.

*jeton* quand cette opération est terminée, un handle qui représente l’événement. Utiliser ce jeton en tant que paramètre à la méthode Remove() pour ignorer le Gestionnaire d’événements.

### <a name="return-value"></a>Valeur de retour

S_OK si l'opération réussit. Sinon, une valeur HRESULT indique l'erreur.


## <a name="see-also"></a>Voir aussi

 [Microsoft::WRL, espace de noms](../windows/microsoft-wrl-namespace.md)
