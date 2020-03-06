---
title: BackEndPass, classe
description: Référence C++ de la classe BackEndPass du kit de développement logiciel (SDK) Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- BackEndPass
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: c159fa09b5d8a4156fc6bd886fc36da09a66db73
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333544"
---
# <a name="backendpass-class"></a>BackEndPass, classe

::: moniker range="<=vs-2015"

Le C++ Kit de développement logiciel (SDK) Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de version de Visual Studio pour cet article sur Visual Studio 2017 ou Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

La classe `BackEndPass` est utilisée avec les fonctions [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)et [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) . Utilisez-le pour faire correspondre un événement [BACK_END_PASS](../event-table.md#back-end-pass) .

## <a name="syntax"></a>Syntaxe

```cpp
class BackEndPass : public CompilerPass
{
public:
    BackEndPass(const RawEvent& event);
};
```

## <a name="members"></a>Membres

Avec les membres hérités de sa classe de base [CompilerPass](compiler-pass.md) , la classe `BackEndPass` contient les membres suivants :

### <a name="constructors"></a>Constructeurs

[BackEndPass](#back-end-pass)

## <a name="back-end-pass"></a>BackEndPass

```cpp
BackEndPass(const RawEvent& event);
```

### <a name="parameters"></a>Paramètres

*event*\
Événement [BACK_END_PASS](../event-table.md#back-end-pass) .

::: moniker-end
