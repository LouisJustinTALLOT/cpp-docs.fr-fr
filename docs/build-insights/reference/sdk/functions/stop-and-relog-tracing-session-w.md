---
title: StopAndRelogTracingSessionW
description: La référence de fonction SDK StopAndRelogTracingSessionW.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- StopAndRelogTracingSessionW
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: c542ba8f313f30cf5adb069dd02cf3db29ffc532
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323689"
---
# <a name="stopandrelogtracingsessionw"></a>StopAndRelogTracingSessionW

::: moniker range="<=vs-2015"

Le SDK Build Insights est compatible avec Visual Studio 2017 et plus. Pour voir la documentation de ces versions, définissez le contrôle du sélecteur Visual Studio **Version** pour cet article à Visual Studio 2017 ou Visual Studio 2019. On le trouve en haut de la table des contenus sur cette page.

::: moniker-end
::: moniker range=">=vs-2017"

La `StopAndRelogTracingSessionW` fonction arrête une séance de traçage en cours et enregistre la trace résultante dans un fichier temporaire. Une session de re-enregistrement est alors immédiatement commencée à utiliser le fichier temporaire comme entrée. La trace relogged finale produite par la session de relogging est enregistrée dans un fichier spécifié par l’appelant. Les exécutables qui appellent cette fonction doivent avoir des privilèges d’administrateur.

## <a name="syntax"></a>Syntaxe

```cpp
enum RESULT_CODE StopAndRelogTracingSessionW(
    const wchar_t*              sessionName,
    const wchar_t*              outputLogFile,
    TRACING_SESSION_STATISTICS* statistics,
    const RELOG_DESCRIPTOR*     relogDescriptor);
```

### <a name="parameters"></a>Paramètres

*sessionName*\
Le nom de la séance de traçage pour s’arrêter. Utilisez le même nom de session que celui passé à [StartTracingSession](start-tracing-session.md), [StartTracingSessionA](start-tracing-session-a.md), ou [StartTracingSessionW](start-tracing-session-w.md).

*sortieLogFile*\
Le fichier dans lequel écrire la trace relogged produite par la session de relogging.

*Statistiques*\
Pointeur vers un [objet TRACING_SESSION_STATISTICS.](../other-types/tracing-session-statistics-struct.md) `StopAndRelogTracingSessionW`écrit des statistiques de collecte de traces dans cet objet avant de revenir.

*analyseDescripteur*\
Pointeur vers un [objet RELOG_DESCRIPTOR.](../other-types/analysis-descriptor-struct.md) Utilisez cet objet pour configurer la session `StopAndRelogTracingSessionW`de relogging qui a commencé par .

### <a name="return-value"></a>Valeur de retour

Un code de résultat de [l’enum RESULT_CODE.](../other-types/result-code-enum.md)

::: moniker-end
