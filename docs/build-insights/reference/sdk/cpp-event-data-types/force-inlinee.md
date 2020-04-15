---
title: Classe ForceInlinee
description: La référence de classe SDK ForceInlinee build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- ForceInlinee
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: c6a1af0384197a0a3b6062ad9ef30537c348190d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324782"
---
# <a name="forceinlinee-class"></a>Classe ForceInlinee

::: moniker range="<=vs-2015"

Le SDK Build Insights est compatible avec Visual Studio 2017 et plus. Pour voir la documentation de ces versions, définissez le contrôle du sélecteur Visual Studio **Version** pour cet article à Visual Studio 2017 ou Visual Studio 2019. On le trouve en haut de la table des contenus sur cette page.

::: moniker-end
::: moniker range=">=vs-2017"

La `ForceInlinee` classe est utilisée avec les fonctions [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)et [MatchEventStackInMemberFunction.](../functions/match-event-stack-in-member-function.md) Utilisez-le pour correspondre à un [événement FORCE_INLINEE.](../event-table.md#force-inlinee)

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

Avec les membres hérités de sa classe `ForceInlinee` de base [SimpleEvent,](simple-event.md) la classe contient les membres suivants :

### <a name="constructors"></a>Constructeurs

[ForceInlinee](#force-inlinee)

### <a name="functions"></a>Fonctions

[Name](#name)
[Taille](#size) du nom

## <a name="forceinlinee"></a><a name="force-inlinee"></a>ForceInlinee

```cpp
ForceInlinee(const RawEvent& event);
```

### <a name="parameters"></a>Paramètres

*Événement*\
Un [événement FORCE_INLINEE.](../event-table.md#force-inlinee)

## <a name="name"></a><a name="name"></a>Nom

```cpp
const char* Name() const;
```

### <a name="return-value"></a>Valeur de retour

Le nom de la fonction inlinée par la force, codé dans UTF-8.

## <a name="size"></a><a name="size"></a>Taille

```cpp
const unsigned short& Size() const;
```

### <a name="return-value"></a>Valeur de retour

La taille de la fonction inlinée par la force, en tant que comptage d’instructions intermédiaires.

::: moniker-end
