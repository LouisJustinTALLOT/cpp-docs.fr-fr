---
title: AnalyseW
description: La référence de fonction SDK AnalyzeW de construction de CMD Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- AnalyzeW
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 64d68e4c10c0b77c3e6b08b1ec23735e38a377a1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324157"
---
# <a name="analyzew"></a>AnalyseW

::: moniker range="<=vs-2015"

Le SDK Build Insights est compatible avec Visual Studio 2017 et plus. Pour voir la documentation de ces versions, définissez le contrôle du sélecteur Visual Studio **Version** pour cet article à Visual Studio 2017 ou Visual Studio 2019. On le trouve en haut de la table des contenus sur cette page.

::: moniker-end
::: moniker range=">=vs-2017"

La `AnalyzeW` fonction est utilisée pour analyser les événements MSVC lus à partir d’une trace de traçage d’événements d’entrée pour Windows (ETW).

## <a name="syntax"></a>Syntaxe

```cpp
enum RESULT_CODE AnalyzeW(
    const wchar_t*             inputLogFile,
    const ANALYSIS_DESCRIPTOR* analysisDescriptor);
```

### <a name="parameters"></a>Paramètres

*inputLogFile (en)*\
L’entrée ETW trace que vous souhaitez lire les événements à partir.

*analyseDescripteur*\
Pointeur vers un objet [ANALYSIS_DESCRIPTOR.](../other-types/analysis-descriptor-struct.md) Utilisez cet objet pour configurer l’analyse.

### <a name="return-value"></a>Valeur de retour

Un code de résultat de [l’enum RESULT_CODE.](../other-types/result-code-enum.md)

::: moniker-end
