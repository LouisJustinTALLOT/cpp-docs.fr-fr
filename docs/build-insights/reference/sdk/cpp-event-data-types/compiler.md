---
title: Classe de compilateur
description: La référence de la classe compilateur SDK Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Compiler
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 9b0a2622c4bc0bc19d7222977fe24c060ee8709e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325029"
---
# <a name="compiler-class"></a>Classe de compilateur

::: moniker range="<=vs-2015"

Le SDK Build Insights est compatible avec Visual Studio 2017 et plus. Pour voir la documentation de ces versions, définissez le contrôle du sélecteur Visual Studio **Version** pour cet article à Visual Studio 2017 ou Visual Studio 2019. On le trouve en haut de la table des contenus sur cette page.

::: moniker-end
::: moniker range=">=vs-2017"

La `Compiler` classe est utilisée avec les fonctions [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)et [MatchEventStackInMemberFunction.](../functions/match-event-stack-in-member-function.md) Utilisez-le pour correspondre à un événement [COMPILER.](../event-table.md#compiler)

## <a name="syntax"></a>Syntaxe

```cpp
class Compiler : public Invocation
{
public:
    Compiler(const RawEvent& event);
};
```

## <a name="members"></a>Membres

Avec les membres hérités de sa classe `Compiler` de base [d’Invocation,](invocation.md) la classe contient les membres suivants :

### <a name="constructors"></a>Constructeurs

[Compilateur](#compiler)

## <a name="compiler"></a><a name="compiler"></a>Compilateur

```cpp
Compiler(const RawEvent& event);
```

### <a name="parameters"></a>Paramètres

*Événement*\
Un événement [COMPILER.](../event-table.md#compiler)

::: moniker-end
