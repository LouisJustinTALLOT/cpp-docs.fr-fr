---
title: EnvironmentVariable, classe
description: Référence C++ de la classe EnvironmentVariable du kit de développement logiciel (SDK) Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- EnvironmentVariable
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 19e9278e76fb2116dac30a0e790fba86c6c56484
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333439"
---
# <a name="environmentvariable-class"></a>EnvironmentVariable, classe

::: moniker range="<=vs-2015"

Le C++ Kit de développement logiciel (SDK) Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de version de Visual Studio pour cet article sur Visual Studio 2017 ou Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

La classe `EnvironmentVariable` est utilisée avec les fonctions [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)et [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) . Utilisez-le pour faire correspondre un événement [ENVIRONMENT_VARIABLE](../event-table.md#environment-variable) .

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

Avec les membres hérités de sa classe de base [SimpleEvent](simple-event.md) , la classe `EnvironmentVariable` contient les membres suivants :

### <a name="constructors"></a>Constructeurs

[EnvironmentVariable](#environment-variable)

### <a name="functions"></a>Fonctions

[Nom](#name)
[Valeur](#value)

## <a name="environment-variable"></a>EnvironmentVariable

```cpp
EnvironmentVariable(const RawEvent& event);
```

### <a name="parameters"></a>Paramètres

*event*\
Événement [ENVIRONMENT_VARIABLE](../event-table.md#environment-variable) .

## <a name="name"></a> Name

```cpp
const wchar_t Name() const;
```

### <a name="return-value"></a>Valeur de retour

Nom de la variable d’environnement.

## <a name="value"></a>Ajoutée

```cpp
const wchar_t Value() const;
```

### <a name="return-value"></a>Valeur de retour

Valeur de la variable d’environnement.

::: moniker-end
