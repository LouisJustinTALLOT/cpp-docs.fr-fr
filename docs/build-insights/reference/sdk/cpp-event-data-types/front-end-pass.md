---
title: FrontEndPass, classe
description: Référence de la classe FrontEndPass du kit de développement logiciel (SDK) C++ Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- FrontEndPass
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: c2959b1b80163819287b1907c9d25ca75aa5bbc2
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92923206"
---
# <a name="frontendpass-class"></a>FrontEndPass, classe

::: moniker range="<=msvc-140"

Le kit de développement logiciel (SDK) C++ Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de **version** de Visual Studio pour cet article sur visual studio 2017 ou visual studio 2019. Elle se trouve en haut de la table des matières sur cette page.

::: moniker-end
::: moniker range=">=msvc-150"

La `FrontEndPass` classe est utilisée avec les fonctions [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)et [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) . Utilisez-le pour faire correspondre un événement [FRONT_END_PASS](../event-table.md#front-end-pass) .

## <a name="syntax"></a>Syntaxe

```cpp
class FrontEndPass : public CompilerPass
{
public:
    FrontEndPass(const RawEvent& event);
};
```

## <a name="members"></a>Membres

Avec les membres hérités de sa classe de base [CompilerPass](compiler-pass.md) , la `FrontEndPass` classe contient les membres suivants :

### <a name="constructors"></a>Constructeurs

[FrontEndPass](#front-end-pass)

## <a name="frontendpass"></a><a name="front-end-pass"></a> FrontEndPass

```cpp
FrontEndPass(const RawEvent& event);
```

### <a name="parameters"></a>Paramètres

*événement*\
Événement [FRONT_END_PASS](../event-table.md#front-end-pass) .

::: moniker-end
