---
title: Classe ObjOutput
description: La référence de classe CMD Build Insights SDK ObjOutput.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- ObjOutput
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 194253e8995401114e2529b868b36c9823510a4f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324491"
---
# <a name="objoutput-class"></a>Classe ObjOutput

::: moniker range="<=vs-2015"

Le SDK Build Insights est compatible avec Visual Studio 2017 et plus. Pour voir la documentation de ces versions, définissez le contrôle du sélecteur Visual Studio **Version** pour cet article à Visual Studio 2017 ou Visual Studio 2019. On le trouve en haut de la table des contenus sur cette page.

::: moniker-end
::: moniker range=">=vs-2017"

La `ObjOutput` classe est utilisée avec les fonctions [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)et [MatchEventStackInMemberFunction.](../functions/match-event-stack-in-member-function.md) Utilisez-le pour correspondre à un [événement OBJ_OUTPUT.](../event-table.md#obj-output)

## <a name="syntax"></a>Syntaxe

```cpp
class ObjOutput : public FileOutput
{
public:
    ObjOutput(const RawEvent& event);
};
```

## <a name="members"></a>Membres

Avec les membres hérités de sa classe `ObjOutput` de base [FileOutput,](file-output.md) la classe contient les membres suivants :

### <a name="constructors"></a>Constructeurs

[ObjOutput (ObjOutput)](#obj-output)

## <a name="objoutput"></a><a name="obj-output"></a>ObjOutput (ObjOutput)

```cpp
ObjOutput(const RawEvent& event);
```

### <a name="parameters"></a>Paramètres

*Événement*\
Un [événement OBJ_OUTPUT.](../event-table.md#obj-output)

::: moniker-end
