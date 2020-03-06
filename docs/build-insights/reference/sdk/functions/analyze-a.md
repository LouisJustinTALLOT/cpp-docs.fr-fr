---
title: Analyse
description: Référence C++ de la fonction du kit de développement logiciel (SDK) de build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- AnalyzeA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 9f5a7b91bf0cd6fd45f97880a99e1f56a85d74ed
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332914"
---
# <a name="analyzea"></a>Analyse

::: moniker range="<=vs-2015"

Le C++ Kit de développement logiciel (SDK) Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de version de Visual Studio pour cet article sur Visual Studio 2017 ou Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

La fonction `AnalyzeA` est utilisée pour analyser les événements MSVC lus à partir d’une trace de Suivi d’v nements pour Windows d’entrée (ETW).

## <a name="syntax"></a>Syntaxe

```cpp
enum RESULT_CODE AnalyzeA(
    const char*                inputLogFile,
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
