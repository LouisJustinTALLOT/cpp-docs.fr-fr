---
title: TemplateInstantiationGroup, classe
description: Référence C++ de la classe TemplateInstantiationGroup du kit de développement logiciel (SDK) Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TemplateInstantiationGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 281088b4c6cbd39b2fb7677180a7966b490ec3ac
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332991"
---
# <a name="templateinstantiationgroup-class"></a>TemplateInstantiationGroup, classe

::: moniker range="<=vs-2015"

Le C++ Kit de développement logiciel (SDK) Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de version de Visual Studio pour cet article sur Visual Studio 2017 ou Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

La classe `TemplateInstantiationGroup` est utilisée avec les fonctions [MatchEventStack](../functions/match-event-stack.md) et [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) . Utilisez-le pour faire correspondre des groupes d’événements [TEMPLATE_INSTANTIATION](../event-table.md#template-instantiation) .

## <a name="syntax"></a>Syntaxe

```cpp
class TemplateInstantiationGroup : public EventGroup<TemplateInstantiation>
{
public:
    TemplateInstantiationGroup(std::deque<TemplateInstantiation>&& group);
};
```

## <a name="members"></a>Membres

Avec les membres hérités de sa classe de base [EventGroup\<TemplateInstantiation\>](event-group.md) , la classe `TemplateInstantiationGroup` contient les membres suivants :

### <a name="constructors"></a>Constructeurs

[TemplateInstantiationGroup](#template-instantiation-group)

## <a name="template-instantiation-group"></a>TemplateInstantiationGroup

```cpp
TemplateInstantiationGroup(std::deque<TemplateInstantiation>&& group);
```

### <a name="parameters"></a>Paramètres

\ de *groupe*
Groupe d’événements de [TEMPLATE_INSTANTIATION](../event-table.md#template-instantiation) .

::: moniker-end
