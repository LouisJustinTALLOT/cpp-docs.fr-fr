---
title: Classe ExpOutput
description: La référence de classe CMD Build Insights SDK ExpOutput.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- ExpOutput
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 4c8c5f2f260596c444df7841c2a3e0c65f5163f7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324818"
---
# <a name="expoutput-class"></a>Classe ExpOutput

::: moniker range="<=vs-2015"

Le SDK Build Insights est compatible avec Visual Studio 2017 et plus. Pour voir la documentation de ces versions, définissez le contrôle du sélecteur Visual Studio **Version** pour cet article à Visual Studio 2017 ou Visual Studio 2019. On le trouve en haut de la table des contenus sur cette page.

::: moniker-end
::: moniker range=">=vs-2017"

La `ExpOutput` classe est utilisée avec les fonctions [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)et [MatchEventStackInMemberFunction.](../functions/match-event-stack-in-member-function.md) Utilisez-le pour correspondre à un [événement EXP_OUTPUT.](../event-table.md#exp-output)

## <a name="syntax"></a>Syntaxe

```cpp
class ExpOutput : public FileOutput
{
public:
    ExpOutput(const RawEvent& event);
};
```

## <a name="members"></a>Membres

Avec les membres hérités de sa classe `ExpOutput` de base [FileOutput,](file-output.md) la classe contient les membres suivants :

### <a name="constructors"></a>Constructeurs

[ExpOutput (expOutput)](#exp-output)

## <a name="expoutput"></a><a name="exp-output"></a>ExpOutput (expOutput)

```cpp
ExpOutput(const RawEvent& event);
```

### <a name="parameters"></a>Paramètres

*Événement*\
Un [événement EXP_OUTPUT.](../event-table.md#exp-output)

::: moniker-end
