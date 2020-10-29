---
title: LinkerGroup, classe
description: Référence de la classe LinkerGroup du kit de développement logiciel (SDK) C++ Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- LinkerGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 8a818cf7524405d4e2f29a1987e93b77371607cc
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92923116"
---
# <a name="linkergroup-class"></a>LinkerGroup, classe

::: moniker range="<=msvc-140"

Le kit de développement logiciel (SDK) C++ Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de **version** de Visual Studio pour cet article sur visual studio 2017 ou visual studio 2019. Elle se trouve en haut de la table des matières sur cette page.

::: moniker-end
::: moniker range=">=msvc-150"

La `LinkerGroup` classe est utilisée avec les fonctions [MatchEventStack](../functions/match-event-stack.md) et [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) . Utilisez-le pour faire correspondre des groupes d’événements de l' [éditeur de liens](../event-table.md#linker) .

## <a name="syntax"></a>Syntaxe

```cpp
class LinkerGroup : public EventGroup<Linker>
{
public:
    LinkerGroup(std::deque<Linker>&& group);
};
```

## <a name="members"></a>Membres

Avec les membres hérités de sa classe de base [EventGroup \<Linker\> ](event-group.md) , la `LinkerGroup` classe contient les membres suivants :

### <a name="constructors"></a>Constructeurs

[LinkerGroup](#linker-group)

## <a name="linkergroup"></a><a name="linker-group"></a> LinkerGroup

```cpp
LinkerGroup(std::deque<Linker>&& group);
```

### <a name="parameters"></a>Paramètres

*Communauté*\
Groupe d’événements de l' [éditeur de liens](../event-table.md#linker) .

::: moniker-end
