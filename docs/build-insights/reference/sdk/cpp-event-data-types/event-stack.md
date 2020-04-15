---
title: Cours EventStack
description: La référence de classe CMD Build Insights SDK EventStack.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- EventStack
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: eaaaedcbf57fdaf8e437a80a7823488febac3e1d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324981"
---
# <a name="eventstack-class"></a>Cours EventStack

::: moniker range="<=vs-2015"

Le SDK Build Insights est compatible avec Visual Studio 2017 et plus. Pour voir la documentation de ces versions, définissez le contrôle du sélecteur Visual Studio **Version** pour cet article à Visual Studio 2017 ou Visual Studio 2019. On le trouve en haut de la table des contenus sur cette page.

::: moniker-end
::: moniker range=">=vs-2017"

La `EventStack` classe est une collection d’objets [Event.](event.md) Tous les événements reçus de la SDK Build Insights de CMD se présentent sous la forme d’un `EventStack` objet. La dernière entrée dans cette pile est l’événement en cours de traitement. Les entrées qui précèdent la dernière entrée sont la hiérarchie parente de l’événement actuel. Pour plus d’informations sur le modèle d’événement utilisé dans les aperçus build de C, voir [tableau d’événements](../event-table.md).

## <a name="syntax"></a>Syntaxe

```cpp
class EventStack
{
public:
    EventStack(const EVENT_COLLECTION_DATA& data);

    size_t      Size() const;
    RawEvent    Back() const;
    RawEvent    operator[] (size_t index) const;
};
```

## <a name="members"></a>Membres

### <a name="constructors"></a>Constructeurs

[EventStack](#event-stack)

### <a name="functions"></a>Fonctions

[Back](#back)
[operator[]](#subscript-operator)
[Taille](#size)

## <a name="back"></a><a name="back"></a>Précédent

```cpp
RawEvent Back() const;
```

### <a name="return-value"></a>Valeur de retour

Un objet [RawEvent](raw-event.md) qui représente la dernière entrée dans la pile. La dernière entrée dans une pile d’événements est l’événement qui a été déclenché.

## <a name="eventstack"></a><a name="event-stack"></a>EventStack

```cpp
EventStack(const EVENT_COLLECTION_DATA& data);
```

### <a name="parameters"></a>Paramètres

*Données*\
Les données brutes `EventStack` à partir desquelles le est construit.

### <a name="remarks"></a>Notes

Vous n’avez généralement `EventStack` pas besoin de construire des objets vous-même. Ils vous sont fournis par le SDK Build Insights lorsque des événements sont traités au cours d’une séance d’analyse ou de relogging.

## <a name="operator"></a><a name="subscript-operator"></a>opérateur[]

```cpp
RawEvent operator[] (size_t index) const;
```

### <a name="parameters"></a>Paramètres

*Index*\
L’index de l’élément d’accès dans la pile d’événements.

### <a name="return-value"></a>Valeur de retour

Un objet [RawEvent](raw-event.md) qui représente l’événement stocké à la position indiquée par *index* dans la pile d’événements.

## <a name="size"></a><a name="size"></a>Taille

```cpp
size_t Size() const;
```

### <a name="return-value"></a>Valeur de retour

La taille de la pile d’événements.

::: moniker-end
