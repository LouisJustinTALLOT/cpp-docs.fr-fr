---
title: EventStack, classe
description: Référence de la classe EventStack du kit de développement logiciel (SDK) C++ Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- EventStack
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: b4f1e92011acdf8272fe631843c03c2f960a1234
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92920708"
---
# <a name="eventstack-class"></a>EventStack, classe

::: moniker range="<=msvc-140"

Le kit de développement logiciel (SDK) C++ Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de **version** de Visual Studio pour cet article sur visual studio 2017 ou visual studio 2019. Elle se trouve en haut de la table des matières sur cette page.

::: moniker-end
::: moniker range=">=msvc-150"

La `EventStack` classe est une collection d’objets d' [événement](event.md) . Tous les événements reçus à partir du kit de développement logiciel (SDK) Build Insights C++ sont fournis sous la forme d’un `EventStack` objet. La dernière entrée dans cette pile est l’événement en cours de traitement. Les entrées qui précèdent la dernière entrée sont la hiérarchie parente de l’événement actuel. Pour plus d’informations sur le modèle d’événement utilisé dans C++ Build Insights, consultez la rubrique [table des événements](../event-table.md).

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

En [retour](#back) 
 [[]](#subscript-operator) 
 , opérateur [Taille](#size)

## <a name="back"></a><a name="back"></a> Précédent

```cpp
RawEvent Back() const;
```

### <a name="return-value"></a>Valeur de retour

Objet [RawEvent](raw-event.md) qui représente la dernière entrée dans la pile. La dernière entrée dans une pile d’événements est l’événement qui a été déclenché.

## <a name="eventstack"></a><a name="event-stack"></a> EventStack

```cpp
EventStack(const EVENT_COLLECTION_DATA& data);
```

### <a name="parameters"></a>Paramètres

*métadonnée*\
Données brutes à partir desquelles la `EventStack` est générée.

### <a name="remarks"></a>Notes

Vous n’avez généralement pas besoin de construire des `EventStack` objets vous-même. Ils vous sont fournis par le kit de développement logiciel (SDK) Build Insights C++ lorsque les événements sont traités pendant une session d’analyse ou de rejournalisation.

## <a name="operator"></a><a name="subscript-operator"></a> [], opérateur

```cpp
RawEvent operator[] (size_t index) const;
```

### <a name="parameters"></a>Paramètres

*évaluer*\
Index de l’élément auquel accéder dans la pile des événements.

### <a name="return-value"></a>Valeur de retour

Objet [RawEvent](raw-event.md) qui représente l’événement stocké à la position indiquée par l' *index* dans la pile des événements.

## <a name="size"></a><a name="size"></a> Corps

```cpp
size_t Size() const;
```

### <a name="return-value"></a>Valeur de retour

Taille de la pile d’événements.

::: moniker-end
