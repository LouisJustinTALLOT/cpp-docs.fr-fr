---
title: EventTargetArray, classe
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::Details::EventTargetArray
- event/Microsoft::WRL::Details::EventTargetArray::AddTail
- event/Microsoft::WRL::Details::EventTargetArray::Begin
- event/Microsoft::WRL::Details::EventTargetArray::End
- event/Microsoft::WRL::Details::EventTargetArray::EventTargetArray
- event/Microsoft::WRL::Details::EventTargetArray::Length
- event/Microsoft::WRL::Details::EventTargetArray::~EventTargetArray
helpviewer_keywords:
- Microsoft::WRL::Details::EventTargetArray class
- Microsoft::WRL::Details::EventTargetArray::AddTail method
- Microsoft::WRL::Details::EventTargetArray::Begin method
- Microsoft::WRL::Details::EventTargetArray::End method
- Microsoft::WRL::Details::EventTargetArray::EventTargetArray, constructor
- Microsoft::WRL::Details::EventTargetArray::Length method
- Microsoft::WRL::Details::EventTargetArray::~EventTargetArray, destructor
ms.assetid: e3cadb7c-2160-4cbb-a2f8-c28733d1e96d
ms.openlocfilehash: 1f3f8e299dba1f4b6ae5a5767f11989dc2fe8370
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54336412"
---
# <a name="eventtargetarray-class"></a>EventTargetArray, classe

Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.

## <a name="syntax"></a>Syntaxe

```cpp
class EventTargetArray :
    public Microsoft::WRL::RuntimeClass<
        Microsoft::WRL::RuntimeClassFlags<ClassicCom>,
        IUnknown
    >;
```

## <a name="remarks"></a>Notes

Représente un tableau des gestionnaires d’événements.

Les gestionnaires d’événements qui sont associés un [EventSource](eventsource-class.md) objet sont stockées dans un document protégé `EventTargetArray` membre de données.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

Nom                                                           | Description
-------------------------------------------------------------- | -----------------------------------------------------------
[EventTargetArray::EventTargetArray](#eventtargetarray)        | Initialise une nouvelle instance de la classe `EventTargetArray`.
[EventTargetArray :: ~ EventTargetArray](#tilde-eventtargetarray) | Annule l’initialisation en cours `EventTargetArray` classe.

### <a name="public-methods"></a>M&#233;thodes publiques

Nom                                  | Description
------------------------------------- | ---------------------------------------------------------------------------------------
[EventTargetArray::AddTail](#addtail) | Ajoute le Gestionnaire d’événements spécifié à la fin du tableau interne de gestionnaires d’événements.
[EventTargetArray::Begin](#begin)     | Obtient l’adresse du premier élément dans le tableau interne de gestionnaires d’événements.
[EventTargetArray::End](#end)         | Obtient l’adresse du dernier élément dans le tableau interne de gestionnaires d’événements.
[EventTargetArray::Length](#length)   | Obtient le nombre actuel d’éléments dans le tableau interne des gestionnaires d’événements.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`EventTargetArray`

## <a name="requirements"></a>Spécifications

**En-tête :** event.h

**Espace de noms :** Microsoft::WRL::Details

## <a name="tilde-eventtargetarray"></a>EventTargetArray :: ~ EventTargetArray

Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.

```cpp
~EventTargetArray();
```

### <a name="remarks"></a>Notes

Annule l’initialisation en cours `EventTargetArray` classe.

## <a name="addtail"></a>EventTargetArray::AddTail

Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.

```cpp
void AddTail(
   _In_ IUnknown* element
);
```

### <a name="parameters"></a>Paramètres

*element*<br/>
Pointeur vers le Gestionnaire d’événements à ajouter.

### <a name="remarks"></a>Notes

Ajoute le Gestionnaire d’événements spécifié à la fin du tableau interne de gestionnaires d’événements.

`AddTail()` est destiné à être utilisé en interne par uniquement la `EventSource` classe.

## <a name="begin"></a>EventTargetArray::Begin

Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.

```cpp
ComPtr<IUnknown>* Begin();
```

### <a name="return-value"></a>Valeur de retour

L’adresse du premier élément dans le tableau interne de gestionnaires d’événements.

### <a name="remarks"></a>Notes

Obtient l’adresse du premier élément dans le tableau interne de gestionnaires d’événements.

## <a name="end"></a>EventTargetArray::End

Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.

```cpp
ComPtr<IUnknown>* End();
```

### <a name="return-value"></a>Valeur de retour

L’adresse du dernier élément dans le tableau interne de gestionnaires d’événements.

### <a name="remarks"></a>Notes

Obtient l’adresse du dernier élément dans le tableau interne de gestionnaires d’événements.

## <a name="eventtargetarray"></a>EventTargetArray::EventTargetArray

Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.

```cpp
EventTargetArray(
   _Out_ HRESULT* hr,
   size_t items
);
```

### <a name="parameters"></a>Paramètres

*hr*<br/>
Après les opérations de ce constructeur, paramètre *hr* indique si l’allocation du tableau a réussi ou échoué. La liste suivante montre les valeurs possibles pour *hr*.

+   S_OK<br/>
    L’opération a réussi.

+   E_OUTOFMEMORY<br/>
    N’a pas pu allouer la mémoire pour le tableau.

+   S_FALSE<br/>
    Paramètre *éléments* est inférieure ou égale à zéro.

*items*<br/>
Le nombre d’éléments de tableau à allouer.

### <a name="remarks"></a>Notes

Initialise une nouvelle instance de la classe `EventTargetArray`.

`EventTargetArray` permet de garder un tableau des gestionnaires d’événements dans un `EventSource` objet.

## <a name="length"></a>EventTargetArray::Length

Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.

```cpp
size_t Length();
```

### <a name="return-value"></a>Valeur de retour

Le nombre actuel d’éléments dans le tableau interne de gestionnaires d’événements.

### <a name="remarks"></a>Notes

Obtient le nombre actuel d’éléments dans le tableau interne des gestionnaires d’événements.
