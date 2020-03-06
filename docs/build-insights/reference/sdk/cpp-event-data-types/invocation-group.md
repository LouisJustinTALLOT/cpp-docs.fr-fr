---
title: InvocationGroup, classe
description: Référence C++ de la classe InvocationGroup du kit de développement logiciel (SDK) Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- InvocationGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: b9a2bbcd2b7649b9b5703adc08ed41b272e10276
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333236"
---
# <a name="invocationgroup-class"></a>InvocationGroup, classe

::: moniker range="<=vs-2015"

Le C++ Kit de développement logiciel (SDK) Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de version de Visual Studio pour cet article sur Visual Studio 2017 ou Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

La classe `InvocationGroup` est utilisée avec les fonctions [MatchEventStack](../functions/match-event-stack.md) et [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) . Utilisez-le pour faire correspondre des groupes contenant un mélange d’événements [du compilateur](../event-table.md#compiler) et de l' [éditeur de liens](../event-table.md#linker) .

## <a name="syntax"></a>Syntaxe

```cpp
class InvocationGroup : public EventGroup<Invocation>
{
public:
    InvocationGroup(std::deque<Invocation>&& group);
};
```

## <a name="members"></a>Membres

Avec les membres hérités de son [EventGroup\<appel\>](event-group.md) classe de base, la classe `InvocationGroup` contient les membres suivants :

### <a name="constructors"></a>Constructeurs

[InvocationGroup](#invocation-group)

## <a name="invocation-group"></a>InvocationGroup

```cpp
InvocationGroup(std::deque<Invocation>&& group);
```

### <a name="parameters"></a>Paramètres

\ de *groupe*
Groupe contenant un mélange d’événements [du compilateur](../event-table.md#compiler) et de l' [éditeur de liens](../event-table.md#linker) .

::: moniker-end
