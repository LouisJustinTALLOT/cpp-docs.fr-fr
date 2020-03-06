---
title: Classe de sortie
description: Référence C++ de classe du kit de développement logiciel (SDK) de build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- LibOutput
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 9ec0d8de5302d9893aedd28661b2234150e82e08
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333215"
---
# <a name="liboutput-class"></a>Classe de sortie

::: moniker range="<=vs-2015"

Le C++ Kit de développement logiciel (SDK) Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de version de Visual Studio pour cet article sur Visual Studio 2017 ou Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

La classe `LibOutput` est utilisée avec les fonctions [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)et [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) . Utilisez-le pour faire correspondre un événement [LIB_OUTPUT](../event-table.md#lib-output) .

## <a name="syntax"></a>Syntaxe

```cpp
class LibOutput : public FileOutput
{
public:
    LibOutput(const RawEvent& event);
};
```

## <a name="members"></a>Membres

Avec les membres hérités de sa classe de base [FileOutput](file-output.md) , la classe `LibOutput` contient les membres suivants :

### <a name="constructors"></a>Constructeurs

[Liboutput](#lib-output)

## <a name="lib-output"></a>Liboutput

```cpp
LibOutput(const RawEvent& event);
```

### <a name="parameters"></a>Paramètres

*event*\
Événement [LIB_OUTPUT](../event-table.md#lib-output) .

::: moniker-end
