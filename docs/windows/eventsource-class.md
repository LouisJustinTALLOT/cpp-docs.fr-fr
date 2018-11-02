---
title: EventSource (classe)
ms.date: 09/12/2018
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::EventSource
- event/Microsoft::WRL::EventSource::Add
- event/Microsoft::WRL::EventSource::addRemoveLock_
- event/Microsoft::WRL::EventSource::EventSource
- event/Microsoft::WRL::EventSource::GetSize
- event/Microsoft::WRL::EventSource::InvokeAll
- event/Microsoft::WRL::EventSource::Remove
- event/Microsoft::WRL::EventSource::targets_
- event/Microsoft::WRL::EventSource::targetsPointerLock_
helpviewer_keywords:
- Microsoft::WRL::EventSource class
- Microsoft::WRL::EventSource::Add method
- Microsoft::WRL::EventSource::addRemoveLock_ data member
- Microsoft::WRL::EventSource::EventSource, constructor
- Microsoft::WRL::EventSource::GetSize method
- Microsoft::WRL::EventSource::InvokeAll method
- Microsoft::WRL::EventSource::Remove method
- Microsoft::WRL::EventSource::targets_ data member
- Microsoft::WRL::EventSource::targetsPointerLock_ data member
ms.assetid: 91f1c072-6af4-44e6-b6d8-ac6d0c688dde
ms.openlocfilehash: e9070fe756410e3e1bb1e5840eb3f06e29c2f46b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50561276"
---
# <a name="eventsource-class"></a>EventSource (classe)

Représente un événement non agile. Les fonctions membres d'`EventSource` ajoutent, suppriment et appellent des gestionnaires d'événements. Pour les événements agiles, utiliser [AgileEventSource](agileeventsource-class.md).

## <a name="syntax"></a>Syntaxe

```cpp
template<typename TDelegateInterface>
class EventSource;
```

### <a name="parameters"></a>Paramètres

*TDelegateInterface*<br/>
L’interface à un délégué qui représente un gestionnaire d’événements.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

| Nom                                     | Description                                            |
| ---------------------------------------- | ------------------------------------------------------ |
| [EventSource::EventSource](#eventsource) | Initialise une nouvelle instance de la classe `EventSource`. |

### <a name="public-methods"></a>M&#233;thodes publiques

| Nom                                 | Description                                                                                                                                                      |
| ------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [EventSource::Add](#add)             | Ajoute le Gestionnaire d’événements représenté par l’interface de délégué spécifié à l’ensemble des gestionnaires d’événements pour actuel `EventSource` objet.                     |
| [EventSource::GetSize](#getsize)     | Récupère le nombre de gestionnaires d’événements associés à l’actuel `EventSource` objet.                                                                         |
| [EventSource::InvokeAll](#invokeall) | Appelle chaque gestionnaire d’événements associé actuel `EventSource` avec les types d’arguments spécifiés et les arguments de l’objet.                                      |
| [EventSource::Remove](#remove)       | Supprime le Gestionnaire d’événements représenté par le jeton d’inscription d’événement spécifié à partir de l’ensemble des gestionnaires d’événements associés à l’actuel `EventSource` objet. |

### <a name="protected-data-members"></a>Membres de données protégés

| Name                                                    | Description                                                                                                                       |
| ------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------- |
| [EventSource::addRemoveLock_](#addremovelock)           | Synchronise l’accès à la [targets_](#targets) tableau lors de l’ajout, suppression ou appeler des gestionnaires d’événements.                          |
| [EventSource::targets_](#targets)                       | Tableau d’un ou plusieurs gestionnaires d’événements.                                                                                           |
| [EventSource::targetsPointerLock_](#targetspointerlock) | Synchronise l’accès aux membres de données internes, même lorsque des gestionnaires d’événements pour cette source d’événement sont ajoutés, supprimés ou appelé. |

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`EventSource`

## <a name="requirements"></a>Configuration requise

**En-tête :** event.h

**Espace de noms :** Microsoft::WRL

## <a name="add"></a>EventSource::Add

Ajoute le Gestionnaire d’événements représenté par l’interface de délégué spécifié à l’ensemble des gestionnaires d’événements pour actuel `EventSource` objet.

```cpp
HRESULT Add(
   _In_ TDelegateInterface* delegateInterface,
   _Out_ EventRegistrationToken* token
);
```

### <a name="parameters"></a>Paramètres

*delegateInterface*<br/>
L’interface à un objet délégué, qui représente un gestionnaire d’événements.

*Jeton*<br/>
Lorsque cette opération se termine, un handle qui représente l’événement. Utiliser ce jeton en tant que paramètre à la [Remove()](#remove) méthode pour ignorer le Gestionnaire d’événements.

### <a name="return-value"></a>Valeur de retour

S_OK si l'opération réussit. Sinon, une valeur HRESULT indique l'erreur.

## <a name="addremovelock"></a>EventSource::addRemoveLock_

Synchronise l’accès à la [targets_](#targets) tableau lors de l’ajout, suppression ou appeler des gestionnaires d’événements.

```cpp
Wrappers::SRWLock addRemoveLock_;
```

## <a name="eventsource"></a>EventSource::EventSource

Initialise une nouvelle instance de la classe `EventSource`.

```cpp
EventSource();
```

## <a name="getsize"></a>EventSource::GetSize

Récupère le nombre de gestionnaires d’événements associés à l’actuel `EventSource` objet.

```cpp
size_t GetSize() const;
```

### <a name="return-value"></a>Valeur de retour

Le nombre de gestionnaires d’événements dans [targets_](#targets).

## <a name="invokeall"></a>EventSource::InvokeAll

Appelle chaque gestionnaire d’événements associé actuel `EventSource` avec les types d’arguments spécifiés et les arguments de l’objet.

```cpp
void InvokeAll();
template <
   typename T0
>
void InvokeAll(
   T0arg0
);
template <
   typename T0,
   typename T1
>
void InvokeAll(
   T0arg0,
   T1arg1
);
template <
   typename T0,
   typename T1,
   typename T2
>
void InvokeAll(
   T0arg0,
   T1arg1,
   T2arg2
);
template <
   typename T0,
   typename T1,
   typename T2,
   typename T3
>
void InvokeAll(
   T0arg0,
   T1arg1,
   T2arg2,
   T3arg3
);
template <
   typename T0,
   typename T1,
   typename T2,
   typename T3,
   typename T4
>
void InvokeAll(
   T0arg0,
   T1arg1,
   T2arg2,
   T3arg3,
   T4arg4
);
template <
   typename T0,
   typename T1,
   typename T2,
   typename T3,
   typename T4,
   typename T5
>
void InvokeAll(
   T0arg0,
   T1arg1,
   T2arg2,
   T3arg3,
   T4arg4,
   T5arg5
);
template <
   typename T0,
   typename T1,
   typename T2,
   typename T3,
   typename T4,
   typename T5,
   typename T6
>
void InvokeAll(
   T0arg0,
   T1arg1,
   T2arg2,
   T3arg3,
   T4arg4,
   T5arg5,
   T6arg6
);
template <
   typename T0,
   typename T1,
   typename T2,
   typename T3,
   typename T4,
   typename T5,
   typename T6,
   typename T7
>
void InvokeAll(
   T0arg0,
   T1arg1,
   T2arg2,
   T3arg3,
   T4arg4,
   T5arg5,
   T6arg6,
   T7arg7
);
template <
   typename T0,
   typename T1,
   typename T2,
   typename T3,
   typename T4,
   typename T5,
   typename T6,
   typename T7,
   typename T8
>
void InvokeAll(
   T0arg0,
   T1arg1,
   T2arg2,
   T3arg3,
   T4arg4,
   T5arg5,
   T6arg6,
   T7arg7,
   T8arg8
);
template <
   typename T0,
   typename T1,
   typename T2,
   typename T3,
   typename T4,
   typename T5,
   typename T6,
   typename T7,
   typename T8,
   typename T9
>
void InvokeAll(
   T0arg0,
   T1arg1,
   T2arg2,
   T3arg3,
   T4arg4,
   T5arg5,
   T6arg6,
   T7arg7,
   T8arg8,
   T9arg9
);
```

### <a name="parameters"></a>Paramètres

*T0*<br/>
Le type de l’argument de gestionnaire d’événements zeroth.

*T1*<br/>
Le type du premier argument de gestionnaire d’événements.

*T2*<br/>
Le type du deuxième argument de gestionnaire d’événements.

*T3*<br/>
Le type du troisième argument de gestionnaire d’événements.

*T4*<br/>
Le type du quatrième argument de gestionnaire d’événements.

*T5*<br/>
Le type du cinquième argument de gestionnaire d’événements.

*T6*<br/>
Le type du sixième argument de gestionnaire d’événements.

*T7*<br/>
Le type du septième argument de gestionnaire d’événements.

*T8*<br/>
Le type de l’argument de gestionnaire d’événements huitième.

*T9*<br/>
Le type du neuvième argument de gestionnaire d’événements.

*arg0*<br/>
L’argument Gestionnaire d’événement zeroth.

*arg1*<br/>
Le premier argument de gestionnaire de l’événement.

*Arg2*<br/>
Le deuxième argument de gestionnaire de l’événement.

*Arg3*<br/>
Le troisième argument de gestionnaire de l’événement.

*Arg4*<br/>
Le quatrième argument de gestionnaire de l’événement.

*Arg5*<br/>
Le cinquième argument de gestionnaire de l’événement.

*Arg6*<br/>
Sixième argument de gestionnaire d’événements.

*Arg7*<br/>
Septième argument de gestionnaire d’événements.

*Arg8*<br/>
Argument d’événement huitième gestionnaire.

*Arg9*<br/>
Neuvième argument de gestionnaire d’événements.

## <a name="remove"></a>EventSource::Remove

Supprime le Gestionnaire d’événements représenté par le jeton d’inscription d’événement spécifié à partir de l’ensemble des gestionnaires d’événements associés à l’actuel `EventSource` objet.

```cpp
HRESULT Remove(
   EventRegistrationToken token
);
```

### <a name="parameters"></a>Paramètres

*Jeton*<br/>
Handle qui représente un gestionnaire d’événements. Ce jeton a été retourné lorsque le Gestionnaire d’événements a été inscrit par le [Add()](#add) (méthode).

### <a name="return-value"></a>Valeur de retour

S_OK si l'opération réussit. Sinon, une valeur HRESULT indique l'erreur.

### <a name="remarks"></a>Notes

Pour plus d’informations sur la `EventRegistrationToken` structure, consultez la **Windows::Foundation :: eventregistrationtoken Structure** rubrique dans le **Windows Runtime** documentation de référence.

## <a name="targets"></a>EventSource::targets_

Tableau d’un ou plusieurs gestionnaires d’événements.

```cpp
ComPtr<Details::EventTargetArray> targets_;
```

### <a name="remarks"></a>Notes

Lorsque l’événement qui est représenté par l’actuel `EventSource` objet se produit, les gestionnaires d’événements sont appelées.

## <a name="targetspointerlock"></a>EventSource::targetsPointerLock_

Synchronise l’accès aux membres de données internes même lorsque les gestionnaires d’événements pour ce `EventSource` sont ajoutés, supprimés ou appelée.

```cpp
Wrappers::SRWLock targetsPointerLock_;
```
