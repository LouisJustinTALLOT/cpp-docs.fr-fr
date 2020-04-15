---
title: Classe EnvironnementVariable
description: La référence de classe 1000 Build Insights SDK EnvironmentVariable.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- EnvironmentVariable
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 963c52e0ea9e048448c6f2b3ac62d9938817467e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325019"
---
# <a name="environmentvariable-class"></a>Classe EnvironnementVariable

::: moniker range="<=vs-2015"

Le SDK Build Insights est compatible avec Visual Studio 2017 et plus. Pour voir la documentation de ces versions, définissez le contrôle du sélecteur Visual Studio **Version** pour cet article à Visual Studio 2017 ou Visual Studio 2019. On le trouve en haut de la table des contenus sur cette page.

::: moniker-end
::: moniker range=">=vs-2017"

La `EnvironmentVariable` classe est utilisée avec les fonctions [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)et [MatchEventStackInMemberFunction.](../functions/match-event-stack-in-member-function.md) Utilisez-le pour correspondre à un [événement ENVIRONMENT_VARIABLE.](../event-table.md#environment-variable)

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

Avec les membres hérités de sa classe `EnvironmentVariable` de base [SimpleEvent,](simple-event.md) la classe contient les membres suivants :

### <a name="constructors"></a>Constructeurs

[EnvironmentVariable](#environment-variable)

### <a name="functions"></a>Fonctions

[Name](#name)
[Valeur](#value) du nom

## <a name="environmentvariable"></a><a name="environment-variable"></a>EnvironnementVariable

```cpp
EnvironmentVariable(const RawEvent& event);
```

### <a name="parameters"></a>Paramètres

*Événement*\
Un [événement ENVIRONMENT_VARIABLE.](../event-table.md#environment-variable)

## <a name="name"></a><a name="name"></a>Nom

```cpp
const wchar_t Name() const;
```

### <a name="return-value"></a>Valeur de retour

Nom de la variable de l’environnement.

## <a name="value"></a><a name="value"></a> Valeur

```cpp
const wchar_t Value() const;
```

### <a name="return-value"></a>Valeur de retour

La valeur de la variable de l’environnement.

::: moniker-end
