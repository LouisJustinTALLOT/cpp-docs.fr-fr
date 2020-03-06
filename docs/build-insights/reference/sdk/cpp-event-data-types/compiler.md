---
title: Classe du compilateur
description: Référence C++ de classe du compilateur SDK de build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Compiler
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: a63a0bad1ab6063d5986fec77b5135f500ded1ce
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333460"
---
# <a name="compiler-class"></a>Classe du compilateur

::: moniker range="<=vs-2015"

Le C++ Kit de développement logiciel (SDK) Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de version de Visual Studio pour cet article sur Visual Studio 2017 ou Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

La classe `Compiler` est utilisée avec les fonctions [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)et [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) . Utilisez-le pour faire correspondre un événement [du compilateur](../event-table.md#compiler) .

## <a name="syntax"></a>Syntaxe

```cpp
class Compiler : public Invocation
{
public:
    Compiler(const RawEvent& event);
};
```

## <a name="members"></a>Membres

Avec les membres hérités de sa classe de base d' [appel](invocation.md) , la classe `Compiler` contient les membres suivants :

### <a name="constructors"></a>Constructeurs

[Compiler](#compiler)

## <a name="compiler"></a>Compiler

```cpp
Compiler(const RawEvent& event);
```

### <a name="parameters"></a>Paramètres

*event*\
Événement [du compilateur](../event-table.md#compiler) .

::: moniker-end
