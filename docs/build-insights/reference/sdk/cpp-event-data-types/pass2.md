---
title: Pass2, classe
description: Référence C++ de la classe pass2 du kit de développement logiciel (SDK) Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Pass2
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 0deca0a06a74e4728cb2c78657bf5e077b42878b
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333075"
---
# <a name="pass2-class"></a>Pass2, classe

::: moniker range="<=vs-2015"

Le C++ Kit de développement logiciel (SDK) Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de version de Visual Studio pour cet article sur Visual Studio 2017 ou Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

La classe `Pass2` est utilisée avec les fonctions [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)et [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) . Utilisez-le pour faire correspondre un événement [pass2](../event-table.md#pass2) .

## <a name="syntax"></a>Syntaxe

```cpp
class Pass2 : public LinkerPass
{
public:
    Pass2(const RawEvent& event);
};
```

## <a name="members"></a>Membres

Avec les membres hérités de sa classe de base [LinkerPass](linker-pass.md) , la classe `Pass2` contient les membres suivants :

### <a name="constructors"></a>Constructeurs

[Pass2](#pass2)

## <a name="pass2"></a>Pass2

```cpp
Pass2(const RawEvent& event);
```

### <a name="parameters"></a>Paramètres

*event*\
Événement [pass2](../event-table.md#pass2) .

::: moniker-end
