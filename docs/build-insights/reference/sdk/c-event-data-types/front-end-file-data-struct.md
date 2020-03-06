---
title: Structure FRONT_END_FILE_DATA
description: Référence C++ de la structure du kit de développement logiciel (SDK) de Build Insights FRONT_END_FILE_DATA.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- FRONT_END_FILE_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 33232a0f83566e58e64964e84961a7ade2de7b7c
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333740"
---
# <a name="front_end_file_data-structure"></a>Structure FRONT_END_FILE_DATA

::: moniker range="<=vs-2015"

Le C++ Kit de développement logiciel (SDK) Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de version de Visual Studio pour cet article sur Visual Studio 2017 ou Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

La structure `FRONT_END_FILE_DATA` décrit le traitement d’un fichier par le compilateur frontal.

## <a name="syntax"></a>Syntaxe

```cpp
typedef struct FRONT_END_FILE_DATA_TAG
{
    const char*         Path;

} FRONT_END_FILE_DATA;
```

## <a name="members"></a>Membres

|  |  |
|--|--|
| `Path` | Le chemin d’accès absolu du fichier, encodé au format UTF-8. |

::: moniker-end
