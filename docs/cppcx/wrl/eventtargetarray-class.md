---
description: 'En savoir plus sur : classe EventTargetArray'
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
ms.openlocfilehash: ac3199d2374a47e94705f8f51672bfedd0b7bf20
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97198581"
---
# <a name="eventtargetarray-class"></a>EventTargetArray, classe

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

## <a name="syntax"></a>Syntaxe

```cpp
class EventTargetArray :
    public Microsoft::WRL::RuntimeClass<
        Microsoft::WRL::RuntimeClassFlags<ClassicCom>,
        IUnknown
    >;
```

## <a name="remarks"></a>Notes

Représente un tableau de gestionnaires d’événements.

Les gestionnaires d’événements associés à un objet [EventSource](eventsource-class.md) sont stockés dans des `EventTargetArray` données membres protégées.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

Nom                                                           | Description
-------------------------------------------------------------- | -----------------------------------------------------------
[EventTargetArray :: EventTargetArray](#eventtargetarray)        | Initialise une nouvelle instance de la classe `EventTargetArray`.
[EventTargetArray :: ~ EventTargetArray](#tilde-eventtargetarray) | Réinitialise la `EventTargetArray` classe actuelle.

### <a name="public-methods"></a>M&#233;thodes publiques

Nom                                  | Description
------------------------------------- | ---------------------------------------------------------------------------------------
[EventTargetArray :: AddTail](#addtail) | Ajoute le gestionnaire d’événements spécifié à la fin du tableau interne de gestionnaires d’événements.
[EventTargetArray :: Begin](#begin)     | Obtient l’adresse du premier élément dans le tableau interne de gestionnaires d’événements.
[EventTargetArray :: fin](#end)         | Obtient l’adresse du dernier élément du tableau interne de gestionnaires d’événements.
[EventTargetArray :: length](#length)   | Obtient le nombre actuel d’éléments dans le tableau interne de gestionnaires d’événements.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`EventTargetArray`

## <a name="requirements"></a>Spécifications

**En-tête :** Event. h

**Espace de noms :** Microsoft :: WRL ::D étails

## <a name="eventtargetarrayeventtargetarray"></a><a name="tilde-eventtargetarray"></a> EventTargetArray :: ~ EventTargetArray

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

```cpp
~EventTargetArray();
```

### <a name="remarks"></a>Notes

Réinitialise la `EventTargetArray` classe actuelle.

## <a name="eventtargetarrayaddtail"></a><a name="addtail"></a> EventTargetArray :: AddTail

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

```cpp
void AddTail(
   _In_ IUnknown* element
);
```

### <a name="parameters"></a>Paramètres

*appartient*<br/>
Pointeur vers le gestionnaire d’événements à ajouter.

### <a name="remarks"></a>Notes

Ajoute le gestionnaire d’événements spécifié à la fin du tableau interne de gestionnaires d’événements.

`AddTail()` est destiné à être utilisé en interne par la `EventSource` classe uniquement.

## <a name="eventtargetarraybegin"></a><a name="begin"></a> EventTargetArray :: Begin

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

```cpp
ComPtr<IUnknown>* Begin();
```

### <a name="return-value"></a>Valeur renvoyée

Adresse du premier élément dans le tableau interne de gestionnaires d’événements.

### <a name="remarks"></a>Notes

Obtient l’adresse du premier élément dans le tableau interne de gestionnaires d’événements.

## <a name="eventtargetarrayend"></a><a name="end"></a> EventTargetArray :: fin

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

```cpp
ComPtr<IUnknown>* End();
```

### <a name="return-value"></a>Valeur renvoyée

Adresse du dernier élément du tableau interne de gestionnaires d’événements.

### <a name="remarks"></a>Notes

Obtient l’adresse du dernier élément du tableau interne de gestionnaires d’événements.

## <a name="eventtargetarrayeventtargetarray"></a><a name="eventtargetarray"></a> EventTargetArray :: EventTargetArray

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

```cpp
EventTargetArray(
   _Out_ HRESULT* hr,
   size_t items
);
```

### <a name="parameters"></a>Paramètres

*heure(s)*<br/>
Après les opérations de ce constructeur, le paramètre *HR* indique si l’allocation du tableau a réussi ou échoué. La liste suivante affiche les valeurs possibles pour *HR*.

- S_OK<br/>
  L’opération a réussi.

- E_OUTOFMEMORY<br/>
  Impossible d’allouer de la mémoire pour le tableau.

- S_FALSE<br/>
  Les *éléments* de paramètre sont inférieurs ou égaux à zéro.

*items*<br/>
Nombre d’éléments de tableau à allouer.

### <a name="remarks"></a>Notes

Initialise une nouvelle instance de la classe `EventTargetArray`.

`EventTargetArray` est utilisé pour conserver un tableau de gestionnaires d’événements dans un `EventSource` objet.

## <a name="eventtargetarraylength"></a><a name="length"></a> EventTargetArray :: length

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

```cpp
size_t Length();
```

### <a name="return-value"></a>Valeur renvoyée

Nombre actuel d’éléments dans le tableau interne de gestionnaires d’événements.

### <a name="remarks"></a>Notes

Obtient le nombre actuel d’éléments dans le tableau interne de gestionnaires d’événements.
