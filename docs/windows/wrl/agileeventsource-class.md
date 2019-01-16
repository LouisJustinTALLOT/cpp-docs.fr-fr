---
title: Agileeventsource, classe
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::AgileEventSource
- event/Microsoft::WRL::InvokeModeOptions
helpviewer_keywords:
- AgileEventSource class
ms.openlocfilehash: a18b4fd7873bcc0895354186dc9b0cc7e6b71bd4
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54335992"
---
# <a name="agileeventsource-class"></a>Agileeventsource, classe

Représente un événement est déclenché par un composant agile, qui est un composant qui est accessible à partir de n’importe quel thread. Hérite de [EventSource](eventsource-class.md) et remplace le `Add` fonction membre avec un paramètre de type supplémentaires pour spécifier des options pour l’appel de l’événement agile.

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
L’interface à un délégué qui représente un gestionnaire d’événements.

*TEventSourceOptions*<br/>
Un [InvokeModeOptions](invokemodeoptions-structure.md) structure dont le champ invokeMode a la valeur `InvokeMode::StopOnFirstError` ou `InvokeMode::FireAll`.

## <a name="remarks"></a>Notes

La grande majorité des composants dans le Runtime Windows sont des composants agiles. Pour plus d’informations, consultez [thread et Marshaling (C++ / c++ / CX)](../../cppcx/threading-and-marshaling-c-cx.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`EventSource`

`AgileEventSource`

## <a name="requirements"></a>Spécifications

**En-tête :** event.h

**Espace de noms :** Microsoft::wrl

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

*delegateInterface*<br/>
L’interface à un objet délégué, qui représente un gestionnaire d’événements.

*token*<br/>
Lorsque cette opération se termine, un handle qui représente l’événement. Utiliser ce jeton en tant que paramètre à la `Remove()` méthode pour ignorer le Gestionnaire d’événements.

### <a name="return-value"></a>Valeur de retour

S_OK si l'opération réussit. Sinon, une valeur HRESULT indique l'erreur.

## <a name="see-also"></a>Voir aussi

[Microsoft::WRL, espace de noms](microsoft-wrl-namespace.md)