---
title: EnvironmentVariable, classe
description: Référence de la classe EnvironmentVariable du kit de développement logiciel (SDK) C++ Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- EnvironmentVariable
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: f707ab744aaf6097975ba9e189815df3c9f32266
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92920761"
---
# <a name="environmentvariable-class"></a>EnvironmentVariable, classe

::: moniker range="<=msvc-140"

Le kit de développement logiciel (SDK) C++ Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de **version** de Visual Studio pour cet article sur visual studio 2017 ou visual studio 2019. Elle se trouve en haut de la table des matières sur cette page.

::: moniker-end
::: moniker range=">=msvc-150"

La `EnvironmentVariable` classe est utilisée avec les fonctions [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)et [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) . Utilisez-le pour faire correspondre un événement [ENVIRONMENT_VARIABLE](../event-table.md#environment-variable) .

## <a name="syntax"></a>Syntaxe

```cpp
class EnvironmentVariable : public SimpleEvent
{
public:
    EnvironmentVariable(const RawEvent& event);

    const wchar_t* Name() const;
    const wchar_t* Value() const;
};
```

## <a name="members"></a>Membres

Avec les membres hérités de sa classe de base [SimpleEvent](simple-event.md) , la `EnvironmentVariable` classe contient les membres suivants :

### <a name="constructors"></a>Constructeurs

[EnvironmentVariable](#environment-variable)

### <a name="functions"></a>Fonctions

[Nom](#name) 
 [Valeur](#value)

## <a name="environmentvariable"></a><a name="environment-variable"></a> EnvironmentVariable

```cpp
EnvironmentVariable(const RawEvent& event);
```

### <a name="parameters"></a>Paramètres

*événement*\
Événement [ENVIRONMENT_VARIABLE](../event-table.md#environment-variable) .

## <a name="name"></a><a name="name"></a> Nomme

```cpp
const wchar_t Name() const;
```

### <a name="return-value"></a>Valeur de retour

Nom de la variable d’environnement.

## <a name="value"></a><a name="value"></a> Valeur

```cpp
const wchar_t Value() const;
```

### <a name="return-value"></a>Valeur de retour

Valeur de la variable d’environnement.

::: moniker-end
