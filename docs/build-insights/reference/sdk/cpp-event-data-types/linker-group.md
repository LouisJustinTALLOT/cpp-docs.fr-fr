---
title: LinkerGroup, classe
description: Référence C++ de la classe LinkerGroup du kit de développement logiciel (SDK) Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- LinkerGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 95b0dcc3a771ec07ee60185a79a5ddbc29434b5d
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333208"
---
# <a name="linkergroup-class"></a>LinkerGroup, classe

::: moniker range="<=vs-2015"

Le C++ Kit de développement logiciel (SDK) Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de version de Visual Studio pour cet article sur Visual Studio 2017 ou Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

La classe `LinkerGroup` est utilisée avec les fonctions [MatchEventStack](../functions/match-event-stack.md) et [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) . Utilisez-le pour faire correspondre des groupes d’événements de l' [éditeur de liens](../event-table.md#linker) .

## <a name="syntax"></a>Syntaxe

```cpp
class LinkerGroup : public EventGroup<Linker>
{
public:
    LinkerGroup(std::deque<Linker>&& group);
};
```

## <a name="members"></a>Membres

Avec les membres hérités de son [EventGroup\<linker\>](event-group.md) classe de base, la classe `LinkerGroup` contient les membres suivants :

### <a name="constructors"></a>Constructeurs

[LinkerGroup](#linker-group)

## <a name="linker-group"></a>LinkerGroup

```cpp
LinkerGroup(std::deque<Linker>&& group);
```

### <a name="parameters"></a>Paramètres

\ de *groupe*
Groupe d’événements de l' [éditeur de liens](../event-table.md#linker) .

::: moniker-end
