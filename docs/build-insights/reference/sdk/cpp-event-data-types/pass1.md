---
title: Pass1, classe
description: Référence de la classe PASS1 du kit de développement logiciel (SDK) C++ Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Pass1
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 99ada8a2db5ac464113d9805797d4b4555367e77
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92923042"
---
# <a name="pass1-class"></a>Pass1, classe

::: moniker range="<=msvc-140"

Le kit de développement logiciel (SDK) C++ Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de **version** de Visual Studio pour cet article sur visual studio 2017 ou visual studio 2019. Elle se trouve en haut de la table des matières sur cette page.

::: moniker-end
::: moniker range=">=msvc-150"

La `Pass1` classe est utilisée avec les fonctions [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)et [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) . Utilisez-le pour faire correspondre un événement [PASS1](../event-table.md#pass1) .

## <a name="syntax"></a>Syntaxe

```cpp
class Pass1 : public LinkerPass
{
public:
    Pass1(const RawEvent& event);
};
```

## <a name="members"></a>Membres

Avec les membres hérités de sa classe de base [LinkerPass](linker-pass.md) , la `Pass1` classe contient les membres suivants :

### <a name="constructors"></a>Constructeurs

[Pass1](#pass1)

## <a name="pass1"></a><a name="pass1"></a> Pass1

```cpp
Pass1(const RawEvent& event);
```

### <a name="parameters"></a>Paramètres

*événement*\
Événement [PASS1](../event-table.md#pass1) .

::: moniker-end
