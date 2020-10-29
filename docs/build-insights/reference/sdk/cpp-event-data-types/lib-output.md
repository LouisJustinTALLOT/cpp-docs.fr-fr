---
title: Classe de sortie
description: Référence de classe de sortie du kit de développement logiciel (SDK) de build Insights C++.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- LibOutput
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 7cb759403a3e9b922ffa861b3938bcb874adac32
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92920617"
---
# <a name="liboutput-class"></a>Classe de sortie

::: moniker range="<=msvc-140"

Le kit de développement logiciel (SDK) C++ Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de **version** de Visual Studio pour cet article sur visual studio 2017 ou visual studio 2019. Elle se trouve en haut de la table des matières sur cette page.

::: moniker-end
::: moniker range=">=msvc-150"

La `LibOutput` classe est utilisée avec les fonctions [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)et [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) . Utilisez-le pour faire correspondre un événement [LIB_OUTPUT](../event-table.md#lib-output) .

## <a name="syntax"></a>Syntaxe

```cpp
class LibOutput : public FileOutput
{
public:
    LibOutput(const RawEvent& event);
};
```

## <a name="members"></a>Membres

Avec les membres hérités de sa classe de base [FileOutput](file-output.md) , la `LibOutput` classe contient les membres suivants :

### <a name="constructors"></a>Constructeurs

[LibOutput](#lib-output)

## <a name="liboutput"></a><a name="lib-output"></a> Liboutput

```cpp
LibOutput(const RawEvent& event);
```

### <a name="parameters"></a>Paramètres

*événement*\
Événement [LIB_OUTPUT](../event-table.md#lib-output) .

::: moniker-end
