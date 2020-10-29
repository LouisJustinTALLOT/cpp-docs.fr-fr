---
title: Énumération CALLBACK_CODE
description: Le kit de développement logiciel (SDK) C++ Build Insights CALLBACK_CODE référence Enum.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- CALLBACK_CODE
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 146d191d0b642ad538f5a314016b41fdbdf26113
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92922589"
---
# <a name="callback_code-enum"></a>Énumération CALLBACK_CODE

::: moniker range="<=msvc-140"

Le kit de développement logiciel (SDK) C++ Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de **version** de Visual Studio pour cet article sur visual studio 2017 ou visual studio 2019. Elle se trouve en haut de la table des matières sur cette page.

::: moniker-end
::: moniker range=">=msvc-150"

L' `CALLBACK_CODE` énumération est utilisée pour contrôler le déroulement d’une session d’analyse ou de rejournalisation. Retournez une valeur CALLBACK_CODE à partir des fonctions dans [ANALYSIS_CALLBACKS](analysis-callbacks-struct.md) ou [RELOG_CALLBACKS](relog-callbacks-struct.md) pour contrôler ce qui doit se passer ensuite.

## <a name="members"></a>Membres

| Nom | Valeur | Description |
|--|--|--|
| `CALLBACK_CODE_ANALYSIS_SUCCESS` | 1 (0x00000001) | Poursuivez normalement la session d’analyse ou de rejournalisation actuelle. |
| `CALLBACK_CODE_ANALYSIS_FAILURE` | 2 (0x00000002) | Annulez l’analyse actuelle ou la session de rejournalisation et signalez une erreur. |
| `CALLBACK_CODE_ANALYSIS_CANCEL` | 4 (0x00000004) | Annulez la session d’analyse ou de rejournalisation en cours. |

::: moniker-end
