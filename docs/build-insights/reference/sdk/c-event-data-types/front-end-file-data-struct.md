---
title: Structure FRONT_END_FILE_DATA
description: Le kit de développement logiciel (SDK) C++ Build Insights FRONT_END_FILE_DATA référence de la structure.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- FRONT_END_FILE_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: c2519bfd478776f54cee59ba08b83ea00b96beff
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2020
ms.locfileid: "90041755"
---
# <a name="front_end_file_data-structure"></a>Structure FRONT_END_FILE_DATA

::: moniker range="<=vs-2015"

Le kit de développement logiciel (SDK) C++ Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de **version** de Visual Studio pour cet article sur visual studio 2017 ou visual studio 2019. Elle se trouve en haut de la table des matières sur cette page.

::: moniker-end
::: moniker range=">=vs-2017"

La `FRONT_END_FILE_DATA` structure décrit le traitement d’un fichier par le compilateur frontal.

## <a name="syntax"></a>Syntaxe

```cpp
typedef struct FRONT_END_FILE_DATA_TAG
{
    const char*         Path;

} FRONT_END_FILE_DATA;
```

## <a name="members"></a>Membres

| Nom | Description |
|--|--|
| `Path` | Le chemin d’accès absolu du fichier, encodé au format UTF-8. |

::: moniker-end
