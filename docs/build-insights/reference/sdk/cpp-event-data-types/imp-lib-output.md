---
title: ImpLibOutput, classe
description: Référence de la classe ImpLibOutput du kit de développement logiciel (SDK) C++ Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- ImpLibOutput
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 01adb0041a3d212acf1bb846ced9019600016cda
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92923183"
---
# <a name="impliboutput-class"></a>ImpLibOutput, classe

::: moniker range="<=msvc-140"

Le kit de développement logiciel (SDK) C++ Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de **version** de Visual Studio pour cet article sur visual studio 2017 ou visual studio 2019. Elle se trouve en haut de la table des matières sur cette page.

::: moniker-end
::: moniker range=">=msvc-150"

La `ImpLibOutput` classe est utilisée avec les fonctions [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)et [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) . Utilisez-le pour faire correspondre un événement [IMP_LIB_OUTPUT](../event-table.md#imp-lib-output) .

## <a name="syntax"></a>Syntaxe

```cpp
class ImpLibOutput : public FileOutput
{
public:
    ImpLibOutput(const RawEvent& event);
};
```

## <a name="members"></a>Membres

Avec les membres hérités de sa classe de base [FileOutput](file-output.md) , la `ImpLibOutput` classe contient les membres suivants :

### <a name="constructors"></a>Constructeurs

[ImpLibOutput](#imp-lib-output)

## <a name="impliboutput"></a><a name="imp-lib-output"></a> ImpLibOutput

```cpp
ImpLibOutput(const RawEvent& event);
```

### <a name="parameters"></a>Paramètres

*événement*\
Événement [IMP_LIB_OUTPUT](../event-table.md#imp-lib-output) .

::: moniker-end
