---
title: ForceInlinee, classe
description: Référence de la classe ForceInlinee du kit de développement logiciel (SDK) C++ Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- ForceInlinee
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 53fff7b6cfd37ba3e3211dd072c1ce3386d00fda
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92920669"
---
# <a name="forceinlinee-class"></a>ForceInlinee, classe

::: moniker range="<=msvc-140"

Le kit de développement logiciel (SDK) C++ Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de **version** de Visual Studio pour cet article sur visual studio 2017 ou visual studio 2019. Elle se trouve en haut de la table des matières sur cette page.

::: moniker-end
::: moniker range=">=msvc-150"

La `ForceInlinee` classe est utilisée avec les fonctions [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)et [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) . Utilisez-le pour faire correspondre un événement [FORCE_INLINEE](../event-table.md#force-inlinee) .

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

Avec les membres hérités de sa classe de base [SimpleEvent](simple-event.md) , la `ForceInlinee` classe contient les membres suivants :

### <a name="constructors"></a>Constructeurs

[ForceInlinee](#force-inlinee)

### <a name="functions"></a>Fonctions

[Nom](#name) 
 [Taille](#size)

## <a name="forceinlinee"></a><a name="force-inlinee"></a> ForceInlinee

```cpp
ForceInlinee(const RawEvent& event);
```

### <a name="parameters"></a>Paramètres

*événement*\
Événement [FORCE_INLINEE](../event-table.md#force-inlinee) .

## <a name="name"></a><a name="name"></a> Nomme

```cpp
const char* Name() const;
```

### <a name="return-value"></a>Valeur de retour

Nom de la fonction forcée forcée, encodée au format UTF-8.

## <a name="size"></a><a name="size"></a> Corps

```cpp
const unsigned short& Size() const;
```

### <a name="return-value"></a>Valeur de retour

Taille de la fonction forcée forcée, sous la forme d’un nombre d’instructions intermédiaires.

::: moniker-end
