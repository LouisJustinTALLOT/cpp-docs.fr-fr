---
title: Classe OptRef
description: La référence de classe CMD Build Insights SDK OptRef.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- OptRef
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: dca8cc62eed4b7136f88ed5ba6a1a168b2de56c3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324441"
---
# <a name="optref-class"></a>Classe OptRef

::: moniker range="<=vs-2015"

Le SDK Build Insights est compatible avec Visual Studio 2017 et plus. Pour voir la documentation de ces versions, définissez le contrôle du sélecteur Visual Studio **Version** pour cet article à Visual Studio 2017 ou Visual Studio 2019. On le trouve en haut de la table des contenus sur cette page.

::: moniker-end
::: moniker range=">=vs-2017"

La `OptRef` classe est utilisée avec les fonctions [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)et [MatchEventStackInMemberFunction.](../functions/match-event-stack-in-member-function.md) Utilisez-le pour correspondre à un [événement OPT_REF.](../event-table.md#opt-ref)

## <a name="syntax"></a>Syntaxe

```cpp
class OptRef : public Activity
{
public:
    OptRef(const RawEvent& event);
};
```

## <a name="members"></a>Membres

Avec les membres hérités de sa `OptRef` classe de base [d’activité,](activity.md) la classe contient les membres suivants :

### <a name="constructors"></a>Constructeurs

[OptRef (en)](#opt-ref)

## <a name="optref"></a><a name="opt-ref"></a>OptRef (en)

```cpp
OptRef(const RawEvent& event);
```

### <a name="parameters"></a>Paramètres

*Événement*\
Un [événement OPT_REF.](../event-table.md#opt-ref)

::: moniker-end
