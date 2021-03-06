---
description: 'En savoir plus sur : classe AgileEventSource'
title: AgileEventSource, classe
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::AgileEventSource
helpviewer_keywords:
- AgileEventSource class
ms.openlocfilehash: d2e48d59d8706eb65828bc5b77ffaf9d4158bc1f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97204574"
---
# <a name="agileeventsource-class"></a>AgileEventSource, classe

Représente un événement déclenché par un composant agile, qui est un composant accessible à partir de n’importe quel thread. Hérite de [EventSource](eventsource-class.md) et remplace la `Add` fonction membre par un paramètre de type supplémentaire pour spécifier les options d’appel de l’événement agile.

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

## <a name="parameters"></a>Paramètres

*TDelegateInterface*<br/>
Interface à un délégué qui représente un gestionnaire d’événements.

*TEventSourceOptions*<br/>
Structure [InvokeModeOptions](invokemodeoptions-structure.md) dont le champ invokeMode a la valeur `InvokeMode::StopOnFirstError` ou `InvokeMode::FireAll` .

## <a name="remarks"></a>Notes

La grande majorité des composants de la Windows Runtime sont des composants agiles. Pour plus d’informations, consultez [Threading et marshaling (C++/CX)](../../cppcx/threading-and-marshaling-c-cx.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`EventSource`

`AgileEventSource`

## <a name="requirements"></a>Spécifications

**En-tête :** Event. h

**Espace de noms :** Microsoft::WRL

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[AgileEventSource :: Add, méthode](#add)|Ajoute le gestionnaire d’événements agile représenté par l’interface de délégué spécifiée au jeu de gestionnaires d’événements pour l’objet **AgileEventSource** actuel.|

## <a name="agileeventsourceadd-method"></a><a name="add"></a> AgileEventSource :: Add, méthode

Ajoute le gestionnaire d’événements représenté par l’interface de délégué spécifiée au jeu de gestionnaires d’événements pour l’objet [EventSource](eventsource-class.md) en cours.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT Add(
   _In_ TDelegateInterface* delegateInterface,
   _Out_ EventRegistrationToken* token
);
```

### <a name="parameters"></a>Paramètres

*delegateInterface*<br/>
Interface à un objet délégué, qui représente un gestionnaire d’événements.

*token*<br/>
Lorsque cette opération est terminée, il s’agit d’un handle qui représente l’événement. Utilisez ce jeton comme paramètre de la `Remove()` méthode pour abandonner le gestionnaire d’événements.

### <a name="return-value"></a>Valeur renvoyée

S_OK si l'opération réussit. Sinon, une valeur HRESULT indique l'erreur.

## <a name="see-also"></a>Voir aussi

[Microsoft :: WRL, espace de noms](microsoft-wrl-namespace.md)
