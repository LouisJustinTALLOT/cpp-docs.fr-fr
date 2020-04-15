---
title: Classe LinkerPass
description: La référence de classe CMD Build Insights SDK LinkerPass.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- LinkerPass
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 2b0c5a02958560faeff30500543b6e6d4921ac52
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324612"
---
# <a name="linkerpass-class"></a>Classe LinkerPass

::: moniker range="<=vs-2015"

Le SDK Build Insights est compatible avec Visual Studio 2017 et plus. Pour voir la documentation de ces versions, définissez le contrôle du sélecteur Visual Studio **Version** pour cet article à Visual Studio 2017 ou Visual Studio 2019. On le trouve en haut de la table des contenus sur cette page.

::: moniker-end
::: moniker range=">=vs-2017"

La `LinkerPass` classe est utilisée avec les fonctions [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)et [MatchEventStackInMemberFunction.](../functions/match-event-stack-in-member-function.md) Utilisez-le pour correspondre à un événement [PASS1](../event-table.md#pass1) ou [PASS2.](../event-table.md#pass2)

## <a name="syntax"></a>Syntaxe

```cpp
class LinkerPass : public Activity
{
public:
    LinkerPass(const RawEvent& event);
};
```

## <a name="members"></a>Membres

Avec les membres hérités de sa `LinkerPass` classe de base [d’activité,](activity.md) la classe contient les membres suivants :

### <a name="constructors"></a>Constructeurs

[LinkerPass (LinkerPass)](#linker-pass)

## <a name="linkerpass"></a><a name="linker-pass"></a>LinkerPass (LinkerPass)

```cpp
LinkerPass(const RawEvent& event);
```

### <a name="parameters"></a>Paramètres

*Événement*\
Un événement [PASS1](../event-table.md#pass1) ou [PASS2.](../event-table.md#pass2)

::: moniker-end
