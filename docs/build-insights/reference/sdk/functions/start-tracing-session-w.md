---
title: StartTracingSessionW
description: Référence de la fonction StartTracingSessionW du kit de développement logiciel (SDK) C++ Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- StartTracingSessionW
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: d89bd6d040f9786539c9be08b9da0813d3bb2c82
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92922737"
---
# <a name="starttracingsessionw"></a>StartTracingSessionW

::: moniker range="<=msvc-140"

Le kit de développement logiciel (SDK) C++ Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de **version** de Visual Studio pour cet article sur visual studio 2017 ou visual studio 2019. Elle se trouve en haut de la table des matières sur cette page.

::: moniker-end
::: moniker range=">=msvc-150"

La `StartTracingSessionW` fonction démarre une session de suivi. Les exécutables qui appellent cette fonction doivent avoir des privilèges d’administrateur.

## <a name="syntax"></a>Syntaxe

```cpp
enum RESULT_CODE StartTracingSessionW(
    const wchar_t*                 sessionName,
    const TRACING_SESSION_OPTIONS* options);
```

### <a name="parameters"></a>Paramètres

*Session*\
Nom de la session de suivi à démarrer. Utilisez le même nom lors de l’appel de [StopTracingSessionW](stop-tracing-session-w.md)ou de toute autre fonction STOP trace.

*Options*\
Pointeur vers un objet [TRACING_SESSION_OPTIONS](../other-types/tracing-session-options-struct.md) . Utilisez cet objet pour sélectionner les événements qui doivent être collectés par la session de suivi.

### <a name="return-value"></a>Valeur de retour

Code de résultat de l’énumération [RESULT_CODE](../other-types/result-code-enum.md) .

::: moniker-end
