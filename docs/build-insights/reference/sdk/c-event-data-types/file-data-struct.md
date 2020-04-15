---
title: structure FILE_DATA
description: La référence de structure de construction SDK FILE_DATA de CMD Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- FILE_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 6b7b0129c54fa4b1d5285bafb38761da45bab4e5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325588"
---
# <a name="file_data-structure"></a>structure FILE_DATA

::: moniker range="<=vs-2015"

Le SDK Build Insights est compatible avec Visual Studio 2017 et plus. Pour voir la documentation de ces versions, définissez le contrôle du sélecteur Visual Studio **Version** pour cet article à Visual Studio 2017 ou Visual Studio 2019. On le trouve en haut de la table des contenus sur cette page.

::: moniker-end
::: moniker range=">=vs-2017"

La `FILE_DATA` structure décrit une entrée ou une sortie de fichier.

## <a name="syntax"></a>Syntaxe

```cpp
typedef struct FILE_DATA_TAG
{
    const wchar_t*      Path;
    int                 TypeCode;

} FILE_DATA;
```

## <a name="members"></a>Membres

|  |  |
|--|--|
| `Path` | Le chemin absolu du fichier |
| `TypeCode` | Un code décrivant le type de fichier. Pour plus d’informations, voir [FILE_TYPE_CODE](file-type-code-enum.md). |

::: moniker-end
