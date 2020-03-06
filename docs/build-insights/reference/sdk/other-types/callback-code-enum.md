---
title: Énumération CALLBACK_CODE
description: Le C++ Kit de développement logiciel (SDK) de Build Insights CALLBACK_CODE référence Enum.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- CALLBACK_CODE
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 68eaa9aa04d2f0a55ac12fb7dde14a080188a38d
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332466"
---
# <a name="callback_code-enum"></a>Énumération CALLBACK_CODE

::: moniker range="<=vs-2015"

Le C++ Kit de développement logiciel (SDK) Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de version de Visual Studio pour cet article sur Visual Studio 2017 ou Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

L’énumération `CALLBACK_CODE` est utilisée pour contrôler le déroulement d’une session d’analyse ou de rejournalisation. Retournez une valeur CALLBACK_CODE à partir des fonctions dans [ANALYSIS_CALLBACKS](analysis-callbacks-struct.md) ou [RELOG_CALLBACKS](relog-callbacks-struct.md) pour contrôler ce qui doit se passer ensuite.

## <a name="members"></a>Membres

| Name | Valeur | Description |
|--|--|--|
| `CALLBACK_CODE_ANALYSIS_SUCCESS` | 1 (0x00000001) | Poursuivez normalement la session d’analyse ou de rejournalisation actuelle. |
| `CALLBACK_CODE_ANALYSIS_FAILURE` | 2 (0x00000002) | Annulez l’analyse actuelle ou la session de rejournalisation et signalez une erreur. |
| `CALLBACK_CODE_ANALYSIS_CANCEL` | 4 (0x00000004) | Annulez la session d’analyse ou de rejournalisation en cours. |

::: moniker-end
