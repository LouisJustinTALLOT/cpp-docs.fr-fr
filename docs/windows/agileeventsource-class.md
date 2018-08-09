---
title: Agileeventsource, classe | Microsoft Docs
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
ms.openlocfilehash: 90a2c582c2740846f90270fe9f45b96871329252
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/08/2018
ms.locfileid: "39642836"
---
# <a name="agileeventsource-class"></a>Agileeventsource, classe

Représente un événement est déclenché par un composant agile, qui est un composant qui est accessible à partir de n’importe quel thread. Hérite de [EventSource](eventsource-class.md) et remplace le `Add` fonction membre avec un paramètre de type supplémentaires pour spécifier des options pour l’appel de l’événement agile.

## <a name="syntax"></a>Syntaxe

```cpp
template<typename TDelegateInterface, typename TEventSourceOptions = Microsoft::WRL::InvokeModeOptions<FireAll>>
class AgileEventSource
    : public Microsoft::WRL::EventSource<TDelegateInterface, TEventSourceOptions>;
```

## <a name="parameters"></a>Paramètres  
 *TDelegateInterface*  
 L’interface à un délégué qui représente un gestionnaire d’événements.

 *TEventSourceOptions*  
 Un [InvokeModeOptions](invokemodeoptions-structure.md) structure dont le champ invokeMode a la valeur `InvokeMode::StopOnFirstError` ou `InvokeMode::FireAll`.

## <a name="remarks"></a>Notes

La grande majorité des composants dans le Runtime Windows sont des composants agiles. Pour plus d’informations, consultez [thread et Marshaling (C++ / c++ / CX)](../cppcx/threading-and-marshaling-c-cx.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

 `EventSource` `AgileEventSource`

## <a name="requirements"></a>Configuration requise

 **En-tête :** event.h

 **Espace de noms :** Microsoft::WRL

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[AgileEventSource::Add (méthode)](#add)|Ajoute le Gestionnaire d’événements agile représenté par l’interface de délégué spécifié à l’ensemble des gestionnaires d’événements pour actuel **AgileEventSource** objet.|

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
L’interface à un objet délégué, qui représente un gestionnaire d’événements.

*Jeton*  
Lorsque cette opération se termine, un handle qui représente l’événement. Utiliser ce jeton en tant que paramètre à la `Remove()` méthode pour ignorer le Gestionnaire d’événements.

### <a name="return-value"></a>Valeur de retour

S_OK si l'opération réussit. Sinon, une valeur HRESULT indique l'erreur.


## <a name="see-also"></a>Voir aussi
 [Microsoft::WRL, espace de noms](../windows/microsoft-wrl-namespace.md)