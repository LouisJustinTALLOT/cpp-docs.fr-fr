---
title: LinkerPass, classe
description: Référence de la classe LinkerPass du kit de développement logiciel (SDK) C++ Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- LinkerPass
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: bee4538ff04ec14effe0223a178ffdb2cca37a75
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92920591"
---
# <a name="linkerpass-class"></a>LinkerPass, classe

::: moniker range="<=msvc-140"

Le kit de développement logiciel (SDK) C++ Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de **version** de Visual Studio pour cet article sur visual studio 2017 ou visual studio 2019. Elle se trouve en haut de la table des matières sur cette page.

::: moniker-end
::: moniker range=">=msvc-150"

La `LinkerPass` classe est utilisée avec les fonctions [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)et [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) . Utilisez-le pour faire correspondre un événement [PASS1](../event-table.md#pass1) ou [pass2](../event-table.md#pass2) .

## <a name="syntax"></a>Syntaxe

```cpp
class LinkerPass : public Activity
{
public:
    LinkerPass(const RawEvent& event);
};
```

## <a name="members"></a>Membres

Avec les membres hérités de sa classe de base [Activity](activity.md) , la `LinkerPass` classe contient les membres suivants :

### <a name="constructors"></a>Constructeurs

[LinkerPass](#linker-pass)

## <a name="linkerpass"></a><a name="linker-pass"></a> LinkerPass

```cpp
LinkerPass(const RawEvent& event);
```

### <a name="parameters"></a>Paramètres

*événement*\
Événement [PASS1](../event-table.md#pass1) ou [pass2](../event-table.md#pass2) .

::: moniker-end
