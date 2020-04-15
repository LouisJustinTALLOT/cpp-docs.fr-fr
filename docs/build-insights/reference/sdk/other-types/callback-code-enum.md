---
title: CALLBACK_CODE enum
description: La référence enum de L’ouvrage de construction de la CMD Build Insights CALLBACK_CODE.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- CALLBACK_CODE
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: d0d3dcc70040f562cd40755188e545f709a807b5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329194"
---
# <a name="callback_code-enum"></a>CALLBACK_CODE enum

::: moniker range="<=vs-2015"

Le SDK Build Insights est compatible avec Visual Studio 2017 et plus. Pour voir la documentation de ces versions, définissez le contrôle du sélecteur Visual Studio **Version** pour cet article à Visual Studio 2017 ou Visual Studio 2019. On le trouve en haut de la table des contenus sur cette page.

::: moniker-end
::: moniker range=">=vs-2017"

L’enum `CALLBACK_CODE` est utilisé contrôler le flux d’une analyse ou de relogging session. Retournez une valeur CALLBACK_CODE des fonctions dans [ANALYSIS_CALLBACKS](analysis-callbacks-struct.md) ou [RELOG_CALLBACKS](relog-callbacks-struct.md) pour contrôler ce qui devrait se passer ensuite.

## <a name="members"></a>Membres

| Nom | Valeur | Description |
|--|--|--|
| `CALLBACK_CODE_ANALYSIS_SUCCESS` | 1 (0x00000001) | Poursuivez l’analyse actuelle ou reloggingez la session normalement. |
| `CALLBACK_CODE_ANALYSIS_FAILURE` | 2 (0x0000002) | Annuler l’analyse en cours ou la session de relogging et signaler une erreur. |
| `CALLBACK_CODE_ANALYSIS_CANCEL` | 4 (0x00000004) | Annuler l’analyse en cours ou la session de relogging. |

::: moniker-end
