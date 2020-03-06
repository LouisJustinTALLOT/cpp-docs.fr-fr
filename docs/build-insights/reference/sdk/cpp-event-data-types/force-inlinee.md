---
title: ForceInlinee, classe
description: Référence C++ de la classe ForceInlinee du kit de développement logiciel (SDK) Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- ForceInlinee
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 7d3cce13601a0b3edbcd2b57664b2d0d94a7d3df
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333334"
---
# <a name="forceinlinee-class"></a>ForceInlinee, classe

::: moniker range="<=vs-2015"

Le C++ Kit de développement logiciel (SDK) Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de version de Visual Studio pour cet article sur Visual Studio 2017 ou Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

La classe `ForceInlinee` est utilisée avec les fonctions [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)et [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) . Utilisez-le pour faire correspondre un événement [FORCE_INLINEE](../event-table.md#force-inlinee) .

## <a name="syntax"></a>Syntaxe

```cpp
class ForceInlinee : public SimpleEvent
{
public:
    ForceInlinee(const RawEvent& event);

    const char*             Name() const;
    const unsigned short&   Size() const;
};
```

## <a name="members"></a>Membres

Avec les membres hérités de sa classe de base [SimpleEvent](simple-event.md) , la classe `ForceInlinee` contient les membres suivants :

### <a name="constructors"></a>Constructeurs

[ForceInlinee](#force-inlinee)

### <a name="functions"></a>Fonctions

[Nom](#name)
[taille](#size)

## <a name="force-inlinee"></a>ForceInlinee

```cpp
ForceInlinee(const RawEvent& event);
```

### <a name="parameters"></a>Paramètres

*event*\
Événement [FORCE_INLINEE](../event-table.md#force-inlinee) .

## <a name="name"></a> Name

```cpp
const char* Name() const;
```

### <a name="return-value"></a>Valeur de retour

Nom de la fonction forcée forcée, encodée au format UTF-8.

## <a name="size"></a>Corps

```cpp
const unsigned short& Size() const;
```

### <a name="return-value"></a>Valeur de retour

Taille de la fonction forcée forcée, sous la forme d’un nombre d’instructions intermédiaires.

::: moniker-end
