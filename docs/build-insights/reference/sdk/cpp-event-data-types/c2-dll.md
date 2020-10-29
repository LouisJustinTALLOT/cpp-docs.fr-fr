---
title: C2DLL, classe
description: Référence de la classe C2DLL du kit de développement logiciel (SDK) C++ Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- C2DLL
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 81aa4722d918646a0275099879bfee567ebc8f22
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92923376"
---
# <a name="c2dll-class"></a>C2DLL, classe

::: moniker range="<=msvc-140"

Le kit de développement logiciel (SDK) C++ Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de **version** de Visual Studio pour cet article sur visual studio 2017 ou visual studio 2019. Elle se trouve en haut de la table des matières sur cette page.

::: moniker-end
::: moniker range=">=msvc-150"

La `C2DLL` classe est utilisée avec les fonctions [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)et [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) . Utilisez-le pour faire correspondre un événement [C2_DLL](../event-table.md#c2-dll) .

## <a name="syntax"></a>Syntaxe

```cpp
class C2DLL : public Activity
{
public:
    C2DLL(const RawEvent& event);
};
```

## <a name="members"></a>Membres

Avec les membres hérités de sa classe de base [Activity](activity.md) , la `C2DLL` classe contient les membres suivants :

### <a name="constructors"></a>Constructeurs

[C2DLL](#c2-dll)

## <a name="c2dll"></a><a name="c2-dll"></a> C2DLL

```cpp
C2DLL(const RawEvent& event);
```

### <a name="parameters"></a>Paramètres

*événement*\
Événement [C2_DLL](../event-table.md#c2-dll) .

::: moniker-end
