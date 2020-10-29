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
ms.openlocfilehash: 488faf80fc073d5bd41712f66bd263e4043f978e
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92923577"
---
# <a name="front_end_file_data-structure"></a>Structure FRONT_END_FILE_DATA

::: moniker range="<=msvc-140"

Le kit de développement logiciel (SDK) C++ Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de **version** de Visual Studio pour cet article sur visual studio 2017 ou visual studio 2019. Elle se trouve en haut de la table des matières sur cette page.

::: moniker-end
::: moniker range=">=msvc-150"

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
