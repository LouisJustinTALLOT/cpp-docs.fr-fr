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
ms.openlocfilehash: 9ea8800aa22a6b5cae0b3342cf337786fb53fc76
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371504"
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

Représente un éventail de gestionnaires d’événements.

Les gestionnaires d’événements associés à un objet [EventSource](eventsource-class.md) sont stockés dans un membre protégé `EventTargetArray` des données.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

Nom                                                           | Description
-------------------------------------------------------------- | -----------------------------------------------------------
[ÉvénementTargetArray::EventTargetArray](#eventtargetarray)        | Initialise une nouvelle instance de la classe `EventTargetArray`.
[ÉvénementTargetArray: :-EventTargetArray](#tilde-eventtargetarray) | Désinitialise la `EventTargetArray` classe actuelle.

### <a name="public-methods"></a>M&#233;thodes publiques

Nom                                  | Description
------------------------------------- | ---------------------------------------------------------------------------------------
[ÉvénementTargetArray::AddTail](#addtail) | Annexe le gestionnaire d’événements spécifié à la fin de la gamme interne de gestionnaires d’événements.
[ÉvénementTargetArray::Début](#begin)     | Obtient l’adresse du premier élément dans le tableau interne des gestionnaires d’événements.
[ÉvénementTargetArray::Fin](#end)         | Obtient l’adresse du dernier élément dans le tableau interne des gestionnaires d’événements.
[ÉvénementTargetArray::Longueur](#length)   | Obtient le nombre actuel d’éléments dans le tableau interne des gestionnaires d’événements.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`EventTargetArray`

## <a name="requirements"></a>Spécifications

**En-tête:** event.h

**Espace nom:** Microsoft::WRL::Details

## <a name="eventtargetarrayeventtargetarray"></a><a name="tilde-eventtargetarray"></a>ÉvénementTargetArray: :-EventTargetArray

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

```cpp
~EventTargetArray();
```

### <a name="remarks"></a>Notes

Désinitialise la `EventTargetArray` classe actuelle.

## <a name="eventtargetarrayaddtail"></a><a name="addtail"></a>ÉvénementTargetArray::AddTail

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

```cpp
void AddTail(
   _In_ IUnknown* element
);
```

### <a name="parameters"></a>Paramètres

*Élément*<br/>
Pointeur vers le gestionnaire d’événements à l’annexe.

### <a name="remarks"></a>Notes

Annexe le gestionnaire d’événements spécifié à la fin de la gamme interne de gestionnaires d’événements.

`AddTail()`est destiné à être utilisé `EventSource` en interne par seulement la classe.

## <a name="eventtargetarraybegin"></a><a name="begin"></a>ÉvénementTargetArray::Début

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

```cpp
ComPtr<IUnknown>* Begin();
```

### <a name="return-value"></a>Valeur de retour

L’adresse du premier élément dans le tableau interne des gestionnaires d’événements.

### <a name="remarks"></a>Notes

Obtient l’adresse du premier élément dans le tableau interne des gestionnaires d’événements.

## <a name="eventtargetarrayend"></a><a name="end"></a>ÉvénementTargetArray::Fin

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

```cpp
ComPtr<IUnknown>* End();
```

### <a name="return-value"></a>Valeur de retour

L’adresse du dernier élément dans le tableau interne des gestionnaires d’événements.

### <a name="remarks"></a>Notes

Obtient l’adresse du dernier élément dans le tableau interne des gestionnaires d’événements.

## <a name="eventtargetarrayeventtargetarray"></a><a name="eventtargetarray"></a>ÉvénementTargetArray::EventTargetArray

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

```cpp
EventTargetArray(
   _Out_ HRESULT* hr,
   size_t items
);
```

### <a name="parameters"></a>Paramètres

*Hr*<br/>
Après ces opérations de constructeur, *le paramètre hr* indique si l’attribution du tableau a réussi ou échoué. La liste suivante montre les valeurs possibles pour *hr*.

- S_OK<br/>
  L’opération a réussi.

- E_OUTOFMEMORY<br/>
  La mémoire ne pouvait pas être allouée pour le tableau.

- S_FALSE<br/>
  Les *éléments paramètres* sont inférieurs ou égaux à zéro.

*Articles*<br/>
Le nombre d’éléments de tableau à allouer.

### <a name="remarks"></a>Notes

Initialise une nouvelle instance de la classe `EventTargetArray`.

`EventTargetArray`est utilisé pour garder un tableau `EventSource` de gestionnaires d’événements dans un objet.

## <a name="eventtargetarraylength"></a><a name="length"></a>ÉvénementTargetArray::Longueur

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

```cpp
size_t Length();
```

### <a name="return-value"></a>Valeur de retour

Le nombre actuel d’éléments dans la gamme interne de gestionnaires d’événements.

### <a name="remarks"></a>Notes

Obtient le nombre actuel d’éléments dans le tableau interne des gestionnaires d’événements.
