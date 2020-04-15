---
title: Cours EventGroup
description: La référence de classe CMD Build Insights SDK EventGroup.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- EventGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 596c18ca0e9b4d7b26c4ed5209b16871952c4af2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324985"
---
# <a name="eventgroup-class"></a>Cours EventGroup

::: moniker range="<=vs-2015"

Le SDK Build Insights est compatible avec Visual Studio 2017 et plus. Pour voir la documentation de ces versions, définissez le contrôle du sélecteur Visual Studio **Version** pour cet article à Visual Studio 2017 ou Visual Studio 2019. On le trouve en haut de la table des contenus sur cette page.

::: moniker-end
::: moniker range=">=vs-2017"

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

*TActivité* Le type d’activité contenu dans le groupe.

## <a name="members"></a>Membres

### <a name="functions"></a>Fonctions

[Back](#back)
[begin front](#begin)
[end](#end)
[Front](#front)
[Size](#size) [operator[]](#subscript-operator)operator[] Taille


## <a name="back"></a><a name="back"></a>Précédent

```cpp
const TActivity& Back() const;
```

### <a name="return-value"></a>Valeur de retour

Une référence au dernier événement d’activité dans le groupe.

## <a name="begin"></a><a name="begin"></a>Commencer

```cpp
std::deque<TActivity>::const_iterator begin() const;
```

### <a name="return-value"></a>Valeur de retour

Un itérateur pointant au début du groupe d’événements d’activité.

## <a name="end"></a><a name="end"></a>Fin

```cpp
std::deque<TActivity>::const_iterator end() const;
```

### <a name="return-value"></a>Valeur de retour

Un itérateur pointant une position au-delà de la fin du groupe d’événements d’activité.

## <a name="front"></a><a name="front"></a>Avant

```cpp
const TActivity& Front() const;
```

### <a name="return-value"></a>Valeur de retour

Une référence au premier événement d’activité dans le groupe.

## <a name="operator"></a><a name="subscript-operator"></a>opérateur[]

```cpp
const TActivity& operator[](size_t index) const;
```

### <a name="parameters"></a>Paramètres

*Index*\
L’index de l’élément d’accès dans le groupe d’événements d’activité.

### <a name="return-value"></a>Valeur de retour

L’événement de la pile d’événements stocké à la position indiquée par *index*.

## <a name="size"></a><a name="size"></a>Taille

```cpp
size_t Size() const;
```

### <a name="return-value"></a>Valeur de retour

La taille du groupe d’événements.

::: moniker-end
