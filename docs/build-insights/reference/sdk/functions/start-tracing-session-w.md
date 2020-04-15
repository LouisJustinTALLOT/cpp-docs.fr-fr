---
title: StartTracingSessionW
description: La référence de fonction SDK StartTracingSessionW.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- StartTracingSessionW
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: af67c3be50cb19ccbfb7fe286e5d61cd1d241bf8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323795"
---
# <a name="starttracingsessionw"></a>StartTracingSessionW

::: moniker range="<=vs-2015"

Le SDK Build Insights est compatible avec Visual Studio 2017 et plus. Pour voir la documentation de ces versions, définissez le contrôle du sélecteur Visual Studio **Version** pour cet article à Visual Studio 2017 ou Visual Studio 2019. On le trouve en haut de la table des contenus sur cette page.

::: moniker-end
::: moniker range=">=vs-2017"

La `StartTracingSessionW` fonction commence une session de traçage. Les exécutables qui appellent cette fonction doivent avoir des privilèges d’administrateur.

## <a name="syntax"></a>Syntaxe

```cpp
enum RESULT_CODE StartTracingSessionW(
    const wchar_t*                 sessionName,
    const TRACING_SESSION_OPTIONS* options);
```

### <a name="parameters"></a>Paramètres

*sessionName*\
Le nom de la session de traçage pour commencer. Utilisez le même nom lorsque vous appelez [StopTracingSessionW](stop-tracing-session-w.md), ou toute autre fonction de trace d’arrêt.

*Options*\
Pointeur vers un [objet TRACING_SESSION_OPTIONS.](../other-types/tracing-session-options-struct.md) Utilisez cet objet pour sélectionner les événements qui doivent être collectés par la session de traçage.

### <a name="return-value"></a>Valeur de retour

Un code de résultat de [l’enum RESULT_CODE.](../other-types/result-code-enum.md)

::: moniker-end
