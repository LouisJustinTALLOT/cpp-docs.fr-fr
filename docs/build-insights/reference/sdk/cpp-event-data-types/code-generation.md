---
title: Classe CodeGeneration
description: La référence de classe de la classe CMD Build Insights SDK CodeGeneration.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- CodeGeneration
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 27149d60cc6970843ef2ecccbaf25472f002e35f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325068"
---
# <a name="codegeneration-class"></a>Classe CodeGeneration

::: moniker range="<=vs-2015"

Le SDK Build Insights est compatible avec Visual Studio 2017 et plus. Pour voir la documentation de ces versions, définissez le contrôle du sélecteur Visual Studio **Version** pour cet article à Visual Studio 2017 ou Visual Studio 2019. On le trouve en haut de la table des contenus sur cette page.

::: moniker-end
::: moniker range=">=vs-2017"

La `CodeGeneration` classe est utilisée avec les fonctions [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)et [MatchEventStackInMemberFunction.](../functions/match-event-stack-in-member-function.md) Utilisez-le pour correspondre à un [événement CODE_GENERATION.](../event-table.md#code-generation)

## <a name="syntax"></a>Syntaxe

```cpp
class CodeGeneration : public Activity
{
public:
    CodeGeneration(const RawEvent& event);
};
```

## <a name="members"></a>Membres

Avec les membres hérités de sa `CodeGeneration` classe de base [d’activité,](activity.md) la classe contient les membres suivants :

### <a name="constructors"></a>Constructeurs

[La génération de code](#code-generation)

## <a name="codegeneration"></a><a name="code-generation"></a>La génération de code

```cpp
CodeGeneration(const RawEvent& event);
```

### <a name="parameters"></a>Paramètres

*Événement*\
Un [événement CODE_GENERATION.](../event-table.md#code-generation)

::: moniker-end
