---
title: AnalyzeW
description: Référence de la fonction AnalyzeW du kit de développement logiciel (SDK) C++ Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- AnalyzeW
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: a75668e0fc9d356315f5f0b3156a909187415521
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92922856"
---
# <a name="analyzew"></a>AnalyzeW

::: moniker range="<=msvc-140"

Le kit de développement logiciel (SDK) C++ Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de **version** de Visual Studio pour cet article sur visual studio 2017 ou visual studio 2019. Elle se trouve en haut de la table des matières sur cette page.

::: moniker-end
::: moniker range=">=msvc-150"

La `AnalyzeW` fonction est utilisée pour analyser les événements MSVC lus à partir d’une trace d’suivi d’v nements pour Windows d’entrée (ETW).

## <a name="syntax"></a>Syntaxe

```cpp
enum RESULT_CODE AnalyzeW(
    const wchar_t*             inputLogFile,
    const ANALYSIS_DESCRIPTOR* analysisDescriptor);
```

### <a name="parameters"></a>Paramètres

*inputLogFile*\
Trace ETW d’entrée à partir de laquelle vous souhaitez lire les événements.

*analysisDescriptor*\
Pointeur vers un objet [ANALYSIS_DESCRIPTOR](../other-types/analysis-descriptor-struct.md) . Utilisez cet objet pour configurer l’analyse.

### <a name="return-value"></a>Valeur de retour

Code de résultat de l’énumération [RESULT_CODE](../other-types/result-code-enum.md) .

::: moniker-end
