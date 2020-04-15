---
title: Classe LinkerGroup
description: La référence de classe CMD Build Insights SDK LinkerGroup.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- LinkerGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: c59d62938e5bd7b839ad12a321a03510e708e0fd
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324650"
---
# <a name="linkergroup-class"></a>Classe LinkerGroup

::: moniker range="<=vs-2015"

Le SDK Build Insights est compatible avec Visual Studio 2017 et plus. Pour voir la documentation de ces versions, définissez le contrôle du sélecteur Visual Studio **Version** pour cet article à Visual Studio 2017 ou Visual Studio 2019. On le trouve en haut de la table des contenus sur cette page.

::: moniker-end
::: moniker range=">=vs-2017"

La `LinkerGroup` classe est utilisée avec les fonctions [MatchEventStack](../functions/match-event-stack.md) et [MatchEventStackInMemberFunction.](../functions/match-event-stack-in-member-function.md) Utilisez-le pour faire correspondre des groupes d’événements [LINKER.](../event-table.md#linker)

## <a name="syntax"></a>Syntaxe

```cpp
class LinkerGroup : public EventGroup<Linker>
{
public:
    LinkerGroup(std::deque<Linker>&& group);
};
```

## <a name="members"></a>Membres

Avec les membres hérités de sa classe `LinkerGroup` de base [EventGroup\<\> Linker,](event-group.md) la classe contient les membres suivants :

### <a name="constructors"></a>Constructeurs

[LinkerGroup (linkerGroup)](#linker-group)

## <a name="linkergroup"></a><a name="linker-group"></a>LinkerGroup (linkerGroup)

```cpp
LinkerGroup(std::deque<Linker>&& group);
```

### <a name="parameters"></a>Paramètres

*Groupe*\
Un groupe d’événements [LINKER.](../event-table.md#linker)

::: moniker-end
