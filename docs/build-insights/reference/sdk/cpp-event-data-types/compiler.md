---
title: Classe du compilateur
description: Référence de classe du compilateur SDK C++ Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Compiler
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 52f8bb2ffc474cbf8e58552c77a4bb9fabc13c7e
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92923326"
---
# <a name="compiler-class"></a>Classe du compilateur

::: moniker range="<=msvc-140"

Le kit de développement logiciel (SDK) C++ Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de **version** de Visual Studio pour cet article sur visual studio 2017 ou visual studio 2019. Elle se trouve en haut de la table des matières sur cette page.

::: moniker-end
::: moniker range=">=msvc-150"

La `Compiler` classe est utilisée avec les fonctions [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)et [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) . Utilisez-le pour faire correspondre un événement [du compilateur](../event-table.md#compiler) .

## <a name="syntax"></a>Syntaxe

```cpp
class Compiler : public Invocation
{
public:
    Compiler(const RawEvent& event);
};
```

## <a name="members"></a>Membres

Avec les membres hérités de sa classe de base d' [appel](invocation.md) , la `Compiler` classe contient les membres suivants :

### <a name="constructors"></a>Constructeurs

[Compiler](#compiler)

## <a name="compiler"></a><a name="compiler"></a> Compiler

```cpp
Compiler(const RawEvent& event);
```

### <a name="parameters"></a>Paramètres

*événement*\
Événement [du compilateur](../event-table.md#compiler) .

::: moniker-end
