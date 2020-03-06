---
title: EventGroup, classe
description: Référence C++ de la classe EventGroup du kit de développement logiciel (SDK) Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- EventGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: ac8ac70f3fc160714b86dd0c483808a4d06e7699
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333432"
---
# <a name="eventgroup-class"></a>EventGroup, classe

::: moniker range="<=vs-2015"

Le C++ Kit de développement logiciel (SDK) Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de version de Visual Studio pour cet article sur Visual Studio 2017 ou Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

Le modèle de classe `EventGroup` est la classe de base pour toutes les classes de capture de groupe.

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

[Retour](#back)
[début](#begin)
[fin](#end)
[
](#front) [opérateur]](#subscript-operator) [taille](#size) de


## <a name="back"></a>Précédent

```cpp
const TActivity& Back() const;
```

### <a name="return-value"></a>Valeur de retour

Référence au dernier événement d’activité dans le groupe.

## <a name="begin"></a>commencer

```cpp
std::deque<TActivity>::const_iterator begin() const;
```

### <a name="return-value"></a>Valeur de retour

Itérateur pointant au début du groupe d’événements d’activité.

## <a name="end"></a>effet

```cpp
std::deque<TActivity>::const_iterator end() const;
```

### <a name="return-value"></a>Valeur de retour

Itérateur pointant vers une position au-delà de la fin du groupe d’événements d’activité.

## <a name="front"></a>Frontal

```cpp
const TActivity& Front() const;
```

### <a name="return-value"></a>Valeur de retour

Référence au premier événement d’activité dans le groupe.

## <a name="subscript-operator"></a>[], opérateur

```cpp
const TActivity& operator[](size_t index) const;
```

### <a name="parameters"></a>Paramètres

\ d' *index*
Index de l’élément auquel accéder dans le groupe d’événements d’activité.

### <a name="return-value"></a>Valeur de retour

Événement de la pile d’événements stocké à la position indiquée par l' *index*.

## <a name="size"></a>Corps

```cpp
size_t Size() const;
```

### <a name="return-value"></a>Valeur de retour

Taille du groupe d’événements.

::: moniker-end
