---
title: Classe BottomUp
description: La référence de classe CMD Build Insights SDK BottomUp.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- BottomUp
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 1cfe25aaa5736b9e2ba55a577e64958a6b9f113b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325214"
---
# <a name="bottomup-class"></a>Classe BottomUp

::: moniker range="<=vs-2015"

Le SDK Build Insights est compatible avec Visual Studio 2017 et plus. Pour voir la documentation de ces versions, définissez le contrôle du sélecteur Visual Studio **Version** pour cet article à Visual Studio 2017 ou Visual Studio 2019. On le trouve en haut de la table des contenus sur cette page.

::: moniker-end
::: moniker range=">=vs-2017"

La `BottomUp` classe est utilisée avec les fonctions [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)et [MatchEventStackInMemberFunction.](../functions/match-event-stack-in-member-function.md) Utilisez-le pour correspondre à un [événement BOTTOM_UP.](../event-table.md#bottom-up)

## <a name="syntax"></a>Syntaxe

```cpp
class BottomUp : public Activity
{
public:
    BottomUp(const RawEvent& event);
};
```

## <a name="members"></a>Membres

Avec les membres hérités de sa `BottomUp` classe de base [d’activité,](activity.md) la classe contient les membres suivants :

### <a name="constructors"></a>Constructeurs

[BottomUp (bottomUp)](#bottom-up)

## <a name="bottomup"></a><a name="bottom-up"></a>BottomUp (bottomUp)

```cpp
BottomUp(const RawEvent& event);
```

### <a name="parameters"></a>Paramètres

*Événement*\
Un [événement BOTTOM_UP.](../event-table.md#bottom-up)

::: moniker-end
