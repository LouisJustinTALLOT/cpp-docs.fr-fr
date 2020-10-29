---
title: EventGroup, classe
description: Référence de la classe EventGroup du kit de développement logiciel (SDK) C++ Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- EventGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 57cbc7a053132909149aee182b9560e2ee33c161
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92923313"
---
# <a name="eventgroup-class"></a>EventGroup, classe

::: moniker range="<=msvc-140"

Le kit de développement logiciel (SDK) C++ Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de **version** de Visual Studio pour cet article sur visual studio 2017 ou visual studio 2019. Elle se trouve en haut de la table des matières sur cette page.

::: moniker-end
::: moniker range=">=msvc-150"

Le `EventGroup` modèle de classe est la classe de base pour toutes les classes de capture de groupe.

## <a name="syntax"></a>Syntaxe

```cpp
template <typename TActivity>
class EventGroup;
{
public:
    size_t Size() const;

    const TActivity& operator[](size_t index) const;
    const TActivity& Front() const;
    const TActivity& Back() const;

    std::deque<TActivity>::const_iterator begin() const;
    std::deque<TActivity>::const_iterator end() const;
};
```

### <a name="parameters"></a>Paramètres

*Tactabilité* Type d’activité contenu dans le groupe.

## <a name="members"></a>Membres

### <a name="functions"></a>Fonctions

En [retour](#back) 
 [commencer](#begin) 
 [fin](#end) 
 [Avant](#front) 
 [[]](#subscript-operator) 
 , opérateur [Taille](#size)

## <a name="back"></a><a name="back"></a> Précédent

```cpp
const TActivity& Back() const;
```

### <a name="return-value"></a>Valeur de retour

Référence au dernier événement d’activité dans le groupe.

## <a name="begin"></a><a name="begin"></a> commencer

```cpp
std::deque<TActivity>::const_iterator begin() const;
```

### <a name="return-value"></a>Valeur de retour

Itérateur pointant au début du groupe d’événements d’activité.

## <a name="end"></a><a name="end"></a> effet

```cpp
std::deque<TActivity>::const_iterator end() const;
```

### <a name="return-value"></a>Valeur de retour

Itérateur pointant vers une position au-delà de la fin du groupe d’événements d’activité.

## <a name="front"></a><a name="front"></a> Frontal

```cpp
const TActivity& Front() const;
```

### <a name="return-value"></a>Valeur de retour

Référence au premier événement d’activité dans le groupe.

## <a name="operator"></a><a name="subscript-operator"></a> [], opérateur

```cpp
const TActivity& operator[](size_t index) const;
```

### <a name="parameters"></a>Paramètres

*évaluer*\
Index de l’élément auquel accéder dans le groupe d’événements d’activité.

### <a name="return-value"></a>Valeur de retour

Événement de la pile d’événements stocké à la position indiquée par l' *index* .

## <a name="size"></a><a name="size"></a> Corps

```cpp
size_t Size() const;
```

### <a name="return-value"></a>Valeur de retour

Taille du groupe d’événements.

::: moniker-end
