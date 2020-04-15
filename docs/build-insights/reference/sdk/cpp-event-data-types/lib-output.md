---
title: Classe LibOutput
description: La référence de classe CMD Build Insights SDK LibOutput.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- LibOutput
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: fda7b471759a9c49937214bb2176473226668776
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324622"
---
# <a name="liboutput-class"></a>Classe LibOutput

::: moniker range="<=vs-2015"

Le SDK Build Insights est compatible avec Visual Studio 2017 et plus. Pour voir la documentation de ces versions, définissez le contrôle du sélecteur Visual Studio **Version** pour cet article à Visual Studio 2017 ou Visual Studio 2019. On le trouve en haut de la table des contenus sur cette page.

::: moniker-end
::: moniker range=">=vs-2017"

La `LibOutput` classe est utilisée avec les fonctions [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)et [MatchEventStackInMemberFunction.](../functions/match-event-stack-in-member-function.md) Utilisez-le pour correspondre à un [événement LIB_OUTPUT.](../event-table.md#lib-output)

## <a name="syntax"></a>Syntaxe

```cpp
class LibOutput : public FileOutput
{
public:
    LibOutput(const RawEvent& event);
};
```

## <a name="members"></a>Membres

Avec les membres hérités de sa classe `LibOutput` de base [FileOutput,](file-output.md) la classe contient les membres suivants :

### <a name="constructors"></a>Constructeurs

[LibOutput (LibOutput)](#lib-output)

## <a name="liboutput"></a><a name="lib-output"></a>LibOutput (LibOutput)

```cpp
LibOutput(const RawEvent& event);
```

### <a name="parameters"></a>Paramètres

*Événement*\
Un [événement LIB_OUTPUT.](../event-table.md#lib-output)

::: moniker-end
