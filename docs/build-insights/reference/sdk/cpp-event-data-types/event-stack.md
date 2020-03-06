---
title: EventStack, classe
description: Référence C++ de la classe EventStack du kit de développement logiciel (SDK) Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- EventStack
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 6da2fd25082399b82d788c5d119a39e2f7388714
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333404"
---
# <a name="eventstack-class"></a>EventStack, classe

::: moniker range="<=vs-2015"

Le C++ Kit de développement logiciel (SDK) Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de version de Visual Studio pour cet article sur Visual Studio 2017 ou Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

La classe `EventStack` est une collection d’objets [Event](event.md) . Tous les événements reçus à C++ partir du kit de développement logiciel (SDK) Build Insights sont fournis sous la forme d’un objet `EventStack`. La dernière entrée dans cette pile est l’événement en cours de traitement. Les entrées qui précèdent la dernière entrée sont la hiérarchie parente de l’événement actuel. Pour plus d’informations sur le modèle d’événement C++ utilisé dans Build Insights, consultez la rubrique [table des événements](../event-table.md).

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

[Replace](#back)
[operator []](#subscript-operator)
[taille](#size)

## <a name="back"></a>Précédent

```cpp
RawEvent Back() const;
```

### <a name="return-value"></a>Valeur de retour

Objet [RawEvent](raw-event.md) qui représente la dernière entrée dans la pile. La dernière entrée dans une pile d’événements est l’événement qui a été déclenché.

## <a name="event-stack"></a>EventStack

```cpp
EventStack(const EVENT_COLLECTION_DATA& data);
```

### <a name="parameters"></a>Paramètres

\ de *données*
Données brutes à partir desquelles la `EventStack` est générée.

### <a name="remarks"></a>Notes

Vous n’avez généralement pas besoin de construire des objets `EventStack` vous-même. Elles vous sont fournies par le kit C++ de développement logiciel (SDK) Build Insights lorsque les événements sont traités pendant une session d’analyse ou de rejournalisation.

## <a name="subscript-operator"></a>[], opérateur

```cpp
RawEvent operator[] (size_t index) const;
```

### <a name="parameters"></a>Paramètres

\ d' *index*
Index de l’élément auquel accéder dans la pile des événements.

### <a name="return-value"></a>Valeur de retour

Objet [RawEvent](raw-event.md) qui représente l’événement stocké à la position indiquée par l' *index* dans la pile des événements.

## <a name="size"></a>Corps

```cpp
size_t Size() const;
```

### <a name="return-value"></a>Valeur de retour

Taille de la pile d’événements.

::: moniker-end
