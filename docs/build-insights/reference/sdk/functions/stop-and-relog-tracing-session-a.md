---
title: StopAndRelogTracingSessionA
description: Référence de la fonction StopAndRelogTracingSessionA du kit de développement logiciel (SDK) C++ Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- StopAndRelogTracingSessionA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: de69ca379c6f0ef46e23d2b4a78c72518e997572
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92919967"
---
# <a name="stopandrelogtracingsessiona"></a>StopAndRelogTracingSessionA

::: moniker range="<=msvc-140"

Le kit de développement logiciel (SDK) C++ Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de **version** de Visual Studio pour cet article sur visual studio 2017 ou visual studio 2019. Elle se trouve en haut de la table des matières sur cette page.

::: moniker-end
::: moniker range=">=msvc-150"

La `StopAndRelogTracingSessionA` fonction arrête une session de suivi en cours et enregistre le suivi résultant dans un fichier temporaire. Une session de rejournalisation est ensuite immédiatement démarrée en utilisant le fichier temporaire comme entrée. La dernière trace rejournalisée produite par la session de rejournalisation est enregistrée dans un fichier spécifié par l’appelant. Les exécutables qui appellent cette fonction doivent avoir des privilèges d’administrateur.

## <a name="syntax"></a>Syntaxe

```cpp
enum RESULT_CODE StopAndRelogTracingSessionA(
    const char*                 sessionName,
    const char*                 outputLogFile,
    TRACING_SESSION_STATISTICS* statistics,
    const RELOG_DESCRIPTOR*     relogDescriptor);
```

### <a name="parameters"></a>Paramètres

*Session*\
Nom de la session de suivi à arrêter. Utilisez le même nom de session que celui passé à [StartTracingSession](start-tracing-session.md), [StartTracingSessionA](start-tracing-session-a.md)ou [StartTracingSessionW](start-tracing-session-w.md).

*outputLogFile*\
Fichier dans lequel écrire le suivi reconnecté généré par la session de rejournalisation.

*portent*\
Pointeur vers un objet [TRACING_SESSION_STATISTICS](../other-types/tracing-session-statistics-struct.md) . `StopAndRelogTracingSessionA` écrit les statistiques de collection de traces dans cet objet avant de retourner.

*analysisDescriptor*\
Pointeur vers un objet [RELOG_DESCRIPTOR](../other-types/analysis-descriptor-struct.md) . Utilisez cet objet pour configurer la session de rejournalisation qui est démarrée par `StopAndRelogTracingSessionA` .

### <a name="return-value"></a>Valeur de retour

Code de résultat de l’énumération [RESULT_CODE](../other-types/result-code-enum.md) .

::: moniker-end
