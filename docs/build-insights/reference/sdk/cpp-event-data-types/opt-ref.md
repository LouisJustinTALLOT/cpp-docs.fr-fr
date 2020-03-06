---
title: OptRef, classe
description: Référence C++ de la classe OptRef du kit de développement logiciel (SDK) Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- OptRef
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: c2abad6489012250862bc0721663572d03261bd4
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333103"
---
# <a name="optref-class"></a>OptRef, classe

::: moniker range="<=vs-2015"

Le C++ Kit de développement logiciel (SDK) Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de version de Visual Studio pour cet article sur Visual Studio 2017 ou Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

La classe `OptRef` est utilisée avec les fonctions [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)et [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) . Utilisez-le pour faire correspondre un événement [OPT_REF](../event-table.md#opt-ref) .

## <a name="syntax"></a>Syntaxe

```cpp
class OptRef : public Activity
{
public:
    OptRef(const RawEvent& event);
};
```

## <a name="members"></a>Membres

Avec les membres hérités de sa classe de base [Activity](activity.md) , la classe `OptRef` contient les membres suivants :

### <a name="constructors"></a>Constructeurs

[OptRef](#opt-ref)

## <a name="opt-ref"></a>OptRef

```cpp
OptRef(const RawEvent& event);
```

### <a name="parameters"></a>Paramètres

*event*\
Événement [OPT_REF](../event-table.md#opt-ref) .

::: moniker-end
