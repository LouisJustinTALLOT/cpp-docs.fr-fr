---
title: Classe Linker
description: La référence de classe CMD Build Insights SDK Linker.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Linker
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: e5d4c0c3841377fc2e029c23d5cbbd076c8029cc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324602"
---
# <a name="linker-class"></a>Classe Linker

::: moniker range="<=vs-2015"

Le SDK Build Insights est compatible avec Visual Studio 2017 et plus. Pour voir la documentation de ces versions, définissez le contrôle du sélecteur Visual Studio **Version** pour cet article à Visual Studio 2017 ou Visual Studio 2019. On le trouve en haut de la table des contenus sur cette page.

::: moniker-end
::: moniker range=">=vs-2017"

La `Linker` classe est utilisée avec les fonctions [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)et [MatchEventStackInMemberFunction.](../functions/match-event-stack-in-member-function.md) Utilisez-le pour correspondre à un événement [LINKER.](../event-table.md#linker)

## <a name="syntax"></a>Syntaxe

```cpp
class Linker : public Invocation
{
public:
    Linker(const RawEvent& event);
};
```

## <a name="members"></a>Membres

Avec les membres hérités de sa classe `Linker` de base [d’Invocation,](invocation.md) la classe contient les membres suivants :

### <a name="constructors"></a>Constructeurs

[Éditeur de liens](#linker)

## <a name="linker"></a><a name="linker"></a>Linker

```cpp
Linker(const RawEvent& event);
```

### <a name="parameters"></a>Paramètres

*Événement*\
Un événement [LINKER.](../event-table.md#linker)

::: moniker-end
