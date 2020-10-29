---
title: Classe de l’éditeur de liens
description: Référence de classe de l’éditeur de liens du kit de développement logiciel (SDK) C++ Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Linker
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: cf5544d725c12db8962d888944d4a281387207fa
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92923087"
---
# <a name="linker-class"></a>Classe de l’éditeur de liens

::: moniker range="<=msvc-140"

Le kit de développement logiciel (SDK) C++ Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de **version** de Visual Studio pour cet article sur visual studio 2017 ou visual studio 2019. Elle se trouve en haut de la table des matières sur cette page.

::: moniker-end
::: moniker range=">=msvc-150"

La `Linker` classe est utilisée avec les fonctions [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)et [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) . Utilisez-le pour établir une correspondance avec un événement de l' [éditeur de liens](../event-table.md#linker) .

## <a name="syntax"></a>Syntaxe

```cpp
class Linker : public Invocation
{
public:
    Linker(const RawEvent& event);
};
```

## <a name="members"></a>Membres

Avec les membres hérités de sa classe de base d' [appel](invocation.md) , la `Linker` classe contient les membres suivants :

### <a name="constructors"></a>Constructeurs

[Éditeur de liens](#linker)

## <a name="linker"></a><a name="linker"></a> Éditeur

```cpp
Linker(const RawEvent& event);
```

### <a name="parameters"></a>Paramètres

*événement*\
Événement de l' [éditeur de liens](../event-table.md#linker) .

::: moniker-end
