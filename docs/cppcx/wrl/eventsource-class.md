---
description: 'En savoir plus sur : EventSource, classe'
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
ms.openlocfilehash: 2553d82a0fc16cd759f43ef2e4ae9527884cab10
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97272810"
---
# <a name="eventsource-class"></a>EventSource (classe)

Représente un événement non agile. Les fonctions membres d'`EventSource` ajoutent, suppriment et appellent des gestionnaires d'événements. Pour les événements agiles, utilisez [AgileEventSource](agileeventsource-class.md).

## <a name="syntax"></a>Syntaxe

```cpp
template<typename TDelegateInterface>
class EventSource;
```

### <a name="parameters"></a>Paramètres

*TDelegateInterface*<br/>
Interface à un délégué qui représente un gestionnaire d’événements.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

| Nom                                     | Description                                            |
| ---------------------------------------- | ------------------------------------------------------ |
| [EventSource :: EventSource](#eventsource) | Initialise une nouvelle instance de la classe `EventSource`. |

### <a name="public-methods"></a>M&#233;thodes publiques

| Nom                                 | Description                                                                                                                                                      |
| ------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [EventSource :: Add](#add)             | Ajoute le gestionnaire d’événements représenté par l’interface de délégué spécifiée au jeu de gestionnaires d’événements pour l' `EventSource` objet actuel.                     |
| [EventSource :: Deis](#getsize)     | Récupère le nombre de gestionnaires d’événements associés à l’objet actuel `EventSource` .                                                                         |
| [EventSource :: InvokeAll](#invokeall) | Appelle chaque gestionnaire d’événements associé à l' `EventSource` objet en cours à l’aide des types d’arguments et des arguments spécifiés.                                      |
| [EventSource :: Remove](#remove)       | Supprime le gestionnaire d’événements représenté par le jeton d’inscription d’événement spécifié de l’ensemble de gestionnaires d’événements associé à l' `EventSource` objet actuel. |

### <a name="protected-data-members"></a>Membres de données protégés

| Nom                                                    | Description                                                                                                                       |
| ------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------- |
| [EventSource :: addRemoveLock_](#addremovelock)           | Synchronise l’accès au tableau [targets_](#targets) lors de l’ajout, de la suppression ou de l’appel de gestionnaires d’événements.                          |
| [EventSource :: targets_](#targets)                       | Tableau d’un ou plusieurs gestionnaires d’événements.                                                                                           |
| [EventSource :: targetsPointerLock_](#targetspointerlock) | Synchronise l’accès aux membres de données internes même si les gestionnaires d’événements pour ce EventSource sont ajoutés, supprimés ou appelés. |

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`EventSource`

## <a name="requirements"></a>Spécifications

**En-tête :** Event. h

**Espace de noms :** Microsoft::WRL

## <a name="eventsourceadd"></a><a name="add"></a> EventSource :: Add

Ajoute le gestionnaire d’événements représenté par l’interface de délégué spécifiée au jeu de gestionnaires d’événements pour l' `EventSource` objet actuel.

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
Lorsque cette opération est terminée, il s’agit d’un handle qui représente l’événement. Utilisez ce jeton en tant que paramètre de la méthode [Remove ()](#remove) pour abandonner le gestionnaire d’événements.

### <a name="return-value"></a>Valeur renvoyée

S_OK si l'opération réussit. Sinon, une valeur HRESULT indique l'erreur.

## <a name="eventsourceaddremovelock_"></a><a name="addremovelock"></a> EventSource :: addRemoveLock_

Synchronise l’accès au tableau [targets_](#targets) lors de l’ajout, de la suppression ou de l’appel de gestionnaires d’événements.

```cpp
Wrappers::SRWLock addRemoveLock_;
```

## <a name="eventsourceeventsource"></a><a name="eventsource"></a> EventSource :: EventSource

Initialise une nouvelle instance de la classe `EventSource`.

```cpp
EventSource();
```

## <a name="eventsourcegetsize"></a><a name="getsize"></a> EventSource :: Deis

Récupère le nombre de gestionnaires d’événements associés à l’objet actuel `EventSource` .

```cpp
size_t GetSize() const;
```

### <a name="return-value"></a>Valeur renvoyée

Nombre de gestionnaires d’événements dans [targets_](#targets).

## <a name="eventsourceinvokeall"></a><a name="invokeall"></a> EventSource :: InvokeAll

Appelle chaque gestionnaire d’événements associé à l' `EventSource` objet en cours à l’aide des types d’arguments et des arguments spécifiés.

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
Type de l’argument du gestionnaire d’événements avant toute chose.

*T1*<br/>
Type du premier argument du gestionnaire d’événements.

*T2*<br/>
Type du deuxième argument du gestionnaire d’événements.

*T3*<br/>
Type du troisième argument du gestionnaire d’événements.

*T4*<br/>
Type du quatrième argument du gestionnaire d’événements.

*T5*<br/>
Type du cinquième argument du gestionnaire d’événements.

*T6*<br/>
Type du sixième argument du gestionnaire d’événements.

*T7*<br/>
Type du septième argument du gestionnaire d’événements.

*T8*<br/>
Type du huitième argument du gestionnaire d’événements.

*T9*<br/>
Type du neuvième argument du gestionnaire d’événements.

*arg0*<br/>
Argument du gestionnaire d’événements avant toute chose.

*arg1*<br/>
Premier argument du gestionnaire d’événements.

*arg2*<br/>
Deuxième argument du gestionnaire d’événements.

*Arg3*<br/>
Troisième argument du gestionnaire d’événements.

*Arg4*<br/>
Quatrième argument du gestionnaire d’événements.

*Arg5*<br/>
Cinquième argument du gestionnaire d’événements.

*arg6*<br/>
Sixième argument du gestionnaire d’événements.

*arg7*<br/>
Septième argument du gestionnaire d’événements.

*arg8*<br/>
Huitième argument du gestionnaire d’événements.

*arg9*<br/>
Neuvième argument du gestionnaire d’événements.

## <a name="eventsourceremove"></a><a name="remove"></a> EventSource :: Remove

Supprime le gestionnaire d’événements représenté par le jeton d’inscription d’événement spécifié de l’ensemble de gestionnaires d’événements associé à l' `EventSource` objet actuel.

```cpp
HRESULT Remove(
   EventRegistrationToken token
);
```

### <a name="parameters"></a>Paramètres

*token*<br/>
Handle qui représente un gestionnaire d’événements. Ce jeton a été retourné lorsque le gestionnaire d’événements a été enregistré par la méthode [Add ()](#add) .

### <a name="return-value"></a>Valeur renvoyée

S_OK si l'opération réussit. Sinon, une valeur HRESULT indique l'erreur.

### <a name="remarks"></a>Notes

Pour plus d’informations sur la `EventRegistrationToken` structure, consultez la rubrique relative à la **structure Windows :: Foundation :: EventRegistrationToken** dans la documentation de référence de **Windows Runtime** .

## <a name="eventsourcetargets_"></a><a name="targets"></a> EventSource :: targets_

Tableau d’un ou plusieurs gestionnaires d’événements.

```cpp
ComPtr<Details::EventTargetArray> targets_;
```

### <a name="remarks"></a>Notes

Lorsque l’événement représenté par l' `EventSource` objet actuel se produit, les gestionnaires d’événements sont appelés.

## <a name="eventsourcetargetspointerlock_"></a><a name="targetspointerlock"></a> EventSource :: targetsPointerLock_

Synchronise l’accès aux membres de données internes même pendant l’ajout, la suppression ou l’appel de gestionnaires d’événements `EventSource` .

```cpp
Wrappers::SRWLock targetsPointerLock_;
```
