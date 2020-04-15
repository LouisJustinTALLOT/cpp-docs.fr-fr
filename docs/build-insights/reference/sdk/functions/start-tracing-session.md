---
title: StartTracingSession
description: La référence de la fonction SDK StartTracingSession.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- StartTracingSession
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 6da81ce54948e5ddbacfc9af50f1be12736fdba7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323736"
---
# <a name="starttracingsession"></a>StartTracingSession

::: moniker range="<=vs-2015"

Le SDK Build Insights est compatible avec Visual Studio 2017 et plus. Pour voir la documentation de ces versions, définissez le contrôle du sélecteur Visual Studio **Version** pour cet article à Visual Studio 2017 ou Visual Studio 2019. On le trouve en haut de la table des contenus sur cette page.

::: moniker-end
::: moniker range=">=vs-2017"

La `StartTracingSession` fonction commence une session de traçage. Les exécutables qui appellent cette fonction doivent avoir des privilèges d’administrateur.

## <a name="syntax"></a>Syntaxe

```cpp
RESULT_CODE StartTracingSession(
    const char*                    sessionName,
    const TRACING_SESSION_OPTIONS& options);

RESULT_CODE StartTracingSession(
    const wchar_t*                 sessionName,
    const TRACING_SESSION_OPTIONS& options);
```

### <a name="parameters"></a>Paramètres

*sessionName*\
Le nom de la session de traçage pour commencer. Utilisez le même nom lorsque vous appelez [StopTracingSession](stop-tracing-session.md) ou toute autre fonction de trace d’arrêt.

*Options*\
Pointeur vers un [objet TRACING_SESSION_OPTIONS.](../other-types/tracing-session-options-struct.md) Utilisez cet objet pour sélectionner les événements qui doivent être collectés par la session de traçage.

### <a name="return-value"></a>Valeur de retour

Un code de résultat de [l’enum RESULT_CODE.](../other-types/result-code-enum.md)

::: moniker-end
