---
title: Classe InvocationGroup
description: La référence de classe CMD Build Insights SDK InvocationGroup.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- InvocationGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: ff5a73d5304a21c314c0fc5ce442e0ffc23b28fd
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324692"
---
# <a name="invocationgroup-class"></a>Classe InvocationGroup

::: moniker range="<=vs-2015"

Le SDK Build Insights est compatible avec Visual Studio 2017 et plus. Pour voir la documentation de ces versions, définissez le contrôle du sélecteur Visual Studio **Version** pour cet article à Visual Studio 2017 ou Visual Studio 2019. On le trouve en haut de la table des contenus sur cette page.

::: moniker-end
::: moniker range=">=vs-2017"

La `InvocationGroup` classe est utilisée avec les fonctions [MatchEventStack](../functions/match-event-stack.md) et [MatchEventStackInMemberFunction.](../functions/match-event-stack-in-member-function.md) Utilisez-le pour faire correspondre les groupes contenant un mélange d’événements [COMPILER](../event-table.md#compiler) et [LINKER.](../event-table.md#linker)

## <a name="syntax"></a>Syntaxe

```cpp
class InvocationGroup : public EventGroup<Invocation>
{
public:
    InvocationGroup(std::deque<Invocation>&& group);
};
```

## <a name="members"></a>Membres

Avec les membres hérités de sa classe de `InvocationGroup` base [EventGroup\<\> Invocation,](event-group.md) la classe contient les membres suivants :

### <a name="constructors"></a>Constructeurs

[Groupe d’invocation](#invocation-group)

## <a name="invocationgroup"></a><a name="invocation-group"></a>Groupe d’invocation

```cpp
InvocationGroup(std::deque<Invocation>&& group);
```

### <a name="parameters"></a>Paramètres

*Groupe*\
Un groupe contenant un mélange d’événements [COMPILER](../event-table.md#compiler) et [LINKER.](../event-table.md#linker)

::: moniker-end
