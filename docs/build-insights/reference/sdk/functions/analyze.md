---
title: Analyser
description: La référence de fonction de build Insights SDK Analyze.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Analyze
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 08b3643270cc785b3fbea36720d192b4a1473104
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324106"
---
# <a name="analyze"></a>Analyser

::: moniker range="<=vs-2015"

Le SDK Build Insights est compatible avec Visual Studio 2017 et plus. Pour voir la documentation de ces versions, définissez le contrôle du sélecteur Visual Studio **Version** pour cet article à Visual Studio 2017 ou Visual Studio 2019. On le trouve en haut de la table des contenus sur cette page.

::: moniker-end
::: moniker range=">=vs-2017"

La `Analyze` fonction est utilisée pour analyser une trace de traçage d’événements pour Windows (ETW) obtenue à partir de MSVC tout en traçant une version C. Les événements de la trace ETW sont transmis séquentiellement à un groupe d’analyseur fourni par l’appelant. Cette fonction prend en charge les analyses multi-pass qui permettent de transmettre le flux d’événements au groupe d’analyseur plusieurs fois de suite.

## <a name="syntax"></a>Syntaxe

```cpp
template <typename... TAnalyzerGroupMembers>
RESULT_CODE Analyze(
    const char*                                   inputLogFile,
    unsigned                                      numberOfPasses,
    StaticAnalyzerGroup<TAnalyzerGroupMembers...> analyzerGroup);

template <typename... TAnalyzerGroupMembers>
RESULT_CODE Analyze(
    const wchar_t*                                inputLogFile,
    unsigned                                      numberOfPasses,
    StaticAnalyzerGroup<TAnalyzerGroupMembers...> analyzerGroup);
```

### <a name="parameters"></a>Paramètres

*TAnalyzerGroupMembers*\
Ce paramètre est toujours déduit.

*inputLogFile (en)*\
L’entrée ETW trace que vous souhaitez lire les événements à partir.

*numberOfPasses (en)*\
Le nombre d’analyses passe pour exécuter sur la trace d’entrée. La trace passe par le groupe d’analyseur fourni une fois par passage d’analyse.

*analyseurGroup*\
Le groupe d’analyseur utilisé pour l’analyse. Appelez [MakeStaticAnalyzerGroup](make-static-analyzer-group.md) pour créer un groupe d’analyseurs. Pour utiliser un groupe d’analyseur dynamique obtenu de [MakeDynamicAnalyzerGroup](make-dynamic-analyzer-group.md), d’abord l’encapsuler à l’intérieur d’un groupe d’analyseur statique en passant son adresse à `MakeStaticAnalyzerGroup`.

### <a name="return-value"></a>Valeur de retour

Un code de résultat de [l’enum RESULT_CODE.](../other-types/result-code-enum.md)

::: moniker-end
