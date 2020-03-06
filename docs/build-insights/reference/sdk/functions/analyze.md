---
title: Analyser
description: Référence C++ de la fonction d’analyse du kit de développement logiciel (SDK) Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Analyze
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 49161641d1cff1c64261d95bb2caace2f802543a
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332865"
---
# <a name="analyze"></a>Analyser

::: moniker range="<=vs-2015"

Le C++ Kit de développement logiciel (SDK) Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de version de Visual Studio pour cet article sur Visual Studio 2017 ou Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

La fonction `Analyze` est utilisée pour analyser une trace Suivi d’v nements pour Windows (ETW) obtenue à partir de MSVC tout C++ en traçant une build. Les événements de la trace ETW sont transférés de manière séquentielle à un groupe d’analyseur fourni par l’appelant. Cette fonction prend en charge les analyses à plusieurs passes qui autorisent le transfert des flux d’événements vers le groupe de l’analyseur plusieurs fois dans une ligne.

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

*inputLogFile*\
Trace ETW d’entrée à partir de laquelle vous souhaitez lire les événements.

*numberOfPasses*\
Nombre de passes d’analyse à exécuter sur la trace d’entrée. La trace est passée par le groupe d’analyseur fourni une fois par passe d’analyse.

*analyzerGroup*\
Groupe de l’analyseur utilisé pour l’analyse. Appelez [MakeStaticAnalyzerGroup](make-static-analyzer-group.md) pour créer un groupe d’analyseur. Pour utiliser un groupe d’analyseur dynamique obtenu à partir de [MakeDynamicAnalyzerGroup](make-dynamic-analyzer-group.md), encapsulez-le d’abord à l’intérieur d’un groupe d’analyseur statique en passant son adresse à `MakeStaticAnalyzerGroup`.

### <a name="return-value"></a>Valeur de retour

Code de résultat de l’énumération [RESULT_CODE](../other-types/result-code-enum.md) .

::: moniker-end
