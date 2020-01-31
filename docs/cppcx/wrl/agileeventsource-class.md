---
title: AgileEventSource, classe
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::AgileEventSource
- event/Microsoft::WRL::InvokeModeOptions
helpviewer_keywords:
- AgileEventSource class
ms.openlocfilehash: fa1e0a72d865b2993e149f6e4d2b57fe13463a61
ms.sourcegitcommit: b8c22e6d555cf833510753cba7a368d57e5886db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76821738"
---
# <a name="agileeventsource-class"></a>AgileEventSource, classe

Représente un événement déclenché par un composant agile, qui est un composant accessible à partir de n’importe quel thread. Hérite de [EventSource](eventsource-class.md) et substitue la fonction membre `Add` par un paramètre de type supplémentaire pour spécifier les options d’appel de l’événement agile.

## <a name="syntax"></a>Syntaxe

```cpp
template<
    typename TDelegateInterface,
    typename TEventSourceOptions = Microsoft::WRL::InvokeModeOptions<FireAll>
>
class AgileEventSource :
    public Microsoft::WRL::EventSource<
        TDelegateInterface, TEventSourceOptions>;
```

## <a name="parameters"></a>Parameters

*TDelegateInterface*<br/>
Interface à un délégué qui représente un gestionnaire d’événements.

*TEventSourceOptions*<br/>
Structure [InvokeModeOptions](invokemodeoptions-structure.md) dont le champ invokeMode a la valeur `InvokeMode::StopOnFirstError` ou `InvokeMode::FireAll`.

## <a name="remarks"></a>Notes

La grande majorité des composants de la Windows Runtime sont des composants agiles. Pour plus d’informations, consultez [Threading et marshalingC++(/CX)](../../cppcx/threading-and-marshaling-c-cx.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`EventSource`

`AgileEventSource`

## <a name="requirements"></a>Configuration requise pour

**En-tête :** Event. h

**Espace de noms :** Microsoft::WRL

## <a name="members"></a>Members

### <a name="public-methods"></a>Méthodes publiques

|Name|Description|
|----------|-----------------|
|[AgileEventSource :: Add, méthode](#add)|Ajoute le gestionnaire d’événements agile représenté par l’interface de délégué spécifiée au jeu de gestionnaires d’événements pour l’objet **AgileEventSource** actuel.|

## <a name="add"></a>AgileEventSource :: Add, méthode

Ajoute le gestionnaire d’événements représenté par l’interface de délégué spécifiée au jeu de gestionnaires d’événements pour l’objet [EventSource](eventsource-class.md) en cours.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT Add(
   _In_ TDelegateInterface* delegateInterface,
   _Out_ EventRegistrationToken* token
);
```

### <a name="parameters"></a>Parameters

*delegateInterface*<br/>
Interface à un objet délégué, qui représente un gestionnaire d’événements.

*token*<br/>
Lorsque cette opération est terminée, il s’agit d’un handle qui représente l’événement. Utilisez ce jeton comme paramètre de la méthode `Remove()` pour ignorer le gestionnaire d’événements.

### <a name="return-value"></a>Valeur de retour

S_OK si l'opération réussit. Sinon, une valeur HRESULT indique l'erreur.

## <a name="see-also"></a>Voir aussi

[Microsoft::WRL, espace de noms](microsoft-wrl-namespace.md)