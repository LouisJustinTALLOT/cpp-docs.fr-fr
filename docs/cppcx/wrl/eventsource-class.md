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
ms.openlocfilehash: bb9151e55d133e3e5d8bf10baeb8448101ad6ce0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371538"
---
# <a name="eventsource-class"></a>EventSource (classe)

Représente un événement non-agile. Les fonctions membres d'`EventSource` ajoutent, suppriment et appellent des gestionnaires d'événements. Pour les événements agiles, utilisez [AgileEventSource](agileeventsource-class.md).

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
| [EventSource::Ajouter](#add)             | Annexe le gestionnaire d’événements représenté par l’interface délégué spécifiée `EventSource` à l’ensemble des gestionnaires d’événements pour l’objet actuel.                     |
| [EventSource::GetSize](#getsize)     | Récupère le nombre de gestionnaires d’événements associés à l’objet actuel. `EventSource`                                                                         |
| [EventSource::InvokeAll](#invokeall) | Appelle chaque gestionnaire d’événements associé à l’objet actuel `EventSource` en utilisant les types d’arguments spécifiés et les arguments.                                      |
| [EventSource::Supprimer](#remove)       | Supprime le gestionnaire d’événements représenté par le jeton d’inscription à `EventSource` l’événement spécifié de l’ensemble de gestionnaires d’événements associés à l’objet actuel. |

### <a name="protected-data-members"></a>Membres de données protégés

| Nom                                                    | Description                                                                                                                       |
| ------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------- |
| [EventSource::addRemoveLock_](#addremovelock)           | Synchronise l’accès au tableau [de targets_](#targets) lors de l’ajout, de l’élimination ou de l’invocation des gestionnaires d’événements.                          |
| [EventSource::targets_](#targets)                       | Un éventail d’un ou plusieurs gestionnaires d’événements.                                                                                           |
| [EventSource::targetsPointerLock_](#targetspointerlock) | Synchronise l’accès aux membres des données internes, même pendant que les gestionnaires d’événements pour cet EventSource sont ajoutés, supprimés ou invoqués. |

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`EventSource`

## <a name="requirements"></a>Spécifications

**En-tête:** event.h

**Espace de noms :** Microsoft::WRL

## <a name="eventsourceadd"></a><a name="add"></a>EventSource::Ajouter

Annexe le gestionnaire d’événements représenté par l’interface délégué spécifiée `EventSource` à l’ensemble des gestionnaires d’événements pour l’objet actuel.

```cpp
HRESULT Add(
   _In_ TDelegateInterface* delegateInterface,
   _Out_ EventRegistrationToken* token
);
```

### <a name="parameters"></a>Paramètres

*déléguéInterface*<br/>
L’interface d’un objet délégué, qui représente un gestionnaire d’événements.

*Jeton*<br/>
Lorsque cette opération se termine, une poignée qui représente l’événement. Utilisez ce jeton comme paramètre de la méthode [Supprimer()](#remove) pour jeter le gestionnaire d’événements.

### <a name="return-value"></a>Valeur de retour

S_OK si l'opération réussit. Sinon, une valeur HRESULT indique l'erreur.

## <a name="eventsourceaddremovelock_"></a><a name="addremovelock"></a>EventSource::addRemoveLock_

Synchronise l’accès au tableau [de targets_](#targets) lors de l’ajout, de l’élimination ou de l’invocation des gestionnaires d’événements.

```cpp
Wrappers::SRWLock addRemoveLock_;
```

## <a name="eventsourceeventsource"></a><a name="eventsource"></a>EventSource::EventSource

Initialise une nouvelle instance de la classe `EventSource`.

```cpp
EventSource();
```

## <a name="eventsourcegetsize"></a><a name="getsize"></a>EventSource::GetSize

Récupère le nombre de gestionnaires d’événements associés à l’objet actuel. `EventSource`

```cpp
size_t GetSize() const;
```

### <a name="return-value"></a>Valeur de retour

Le nombre de gestionnaires d’événements dans [targets_](#targets).

## <a name="eventsourceinvokeall"></a><a name="invokeall"></a>EventSource::InvokeAll

Appelle chaque gestionnaire d’événements associé à l’objet actuel `EventSource` en utilisant les types d’arguments spécifiés et les arguments.

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
Le type de l’argument zéro gestionnaire d’événement.

*T1*<br/>
Le type de l’argument du premier gestionnaire d’événement.

*T2 T2*<br/>
Le type de l’argument du gestionnaire de deuxième événement.

*T3*<br/>
Le type de l’argument du troisième gestionnaire d’événement.

*T4*<br/>
Le type de l’argument du gestionnaire d’événement quatrième.

*T5*<br/>
Le type de l’argument du gestionnaire de cinquième événement.

*T6*<br/>
Le type de l’argument du gestionnaire de sixième événement.

*T7 (T7)*<br/>
Le type de l’argument du gestionnaire de septième événement.

*T8 (T8)*<br/>
Le type de l’argument du gestionnaire de l’événement huitième.

*T9 T9*<br/>
Le type de la neuvième argument de gestionnaire d’événement.

*arg0*<br/>
L’argument zéro gestionnaire d’événement.

*arg1*<br/>
Le premier argument de gestionnaire d’événement.

*arg2*<br/>
Le deuxième argument de gestionnaire d’événement.

*arg3*<br/>
Le troisième argument de gestionnaire d’événement.

*arg4*<br/>
Le quatrième argument de gestionnaire d’événement.

*arg5*<br/>
Le cinquième argument de gestionnaire d’événement.

*arg6*<br/>
Le sixième argument de gestionnaire d’événement.

*arg7*<br/>
Le septième argument de gestionnaire d’événement.

*arg8*<br/>
La huitième dispute de gestionnaire d’événements.

*arg9*<br/>
La neuvième dispute de gestionnaire d’événement.

## <a name="eventsourceremove"></a><a name="remove"></a>EventSource::Supprimer

Supprime le gestionnaire d’événements représenté par le jeton d’inscription à `EventSource` l’événement spécifié de l’ensemble de gestionnaires d’événements associés à l’objet actuel.

```cpp
HRESULT Remove(
   EventRegistrationToken token
);
```

### <a name="parameters"></a>Paramètres

*Jeton*<br/>
Une poignée qui représente un gestionnaire d’événements. Ce jeton a été retourné lorsque le gestionnaire de l’événement a été enregistré par la méthode [Add().](#add)

### <a name="return-value"></a>Valeur de retour

S_OK si l'opération réussit. Sinon, une valeur HRESULT indique l'erreur.

### <a name="remarks"></a>Notes

Pour plus d’informations sur la `EventRegistrationToken` structure, voir le sujet **Windows::Foundation:EventRegistrationToken Structure** dans la documentation de référence Windows **Runtime.**

## <a name="eventsourcetargets_"></a><a name="targets"></a>EventSource::targets_

Un éventail d’un ou plusieurs gestionnaires d’événements.

```cpp
ComPtr<Details::EventTargetArray> targets_;
```

### <a name="remarks"></a>Notes

Lorsque l’événement qui est `EventSource` représenté par l’objet actuel se produit, les gestionnaires d’événements sont appelés.

## <a name="eventsourcetargetspointerlock_"></a><a name="targetspointerlock"></a>EventSource::targetsPointerLock_

Synchronise l’accès aux membres des données `EventSource` internes, même pendant que les gestionnaires d’événements pour cela sont ajoutés, supprimés ou invoqués.

```cpp
Wrappers::SRWLock targetsPointerLock_;
```
