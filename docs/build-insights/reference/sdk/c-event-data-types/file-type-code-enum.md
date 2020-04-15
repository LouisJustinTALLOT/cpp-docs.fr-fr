---
title: FILE_TYPE_CODE enum
description: La référence enum de build Insights CMD Build Insights FILE_TYPE_CODE.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- FILE_TYPE_CODE
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: dea603a072d7b2f472112a75b2e9ccded78399a9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325561"
---
# <a name="file_type_code-enum"></a>FILE_TYPE_CODE enum

::: moniker range="<=vs-2015"

Le SDK Build Insights est compatible avec Visual Studio 2017 et plus. Pour voir la documentation de ces versions, définissez le contrôle du sélecteur Visual Studio **Version** pour cet article à Visual Studio 2017 ou Visual Studio 2019. On le trouve en haut de la table des contenus sur cette page.

::: moniker-end
::: moniker range=">=vs-2017"

L’enum `FILE_TYPE_CODE` décrit le type de fichier.

## <a name="members"></a>Membres

| Nom | Valeur | Description |
|--|--|--|
| `FILE_TYPE_CODE_OTHER` | 0 (0x000000000) | Un type de fichier non répertorié dans cet enum. |
| `FILE_TYPE_CODE_OBJ` | 1 (0x00000001) | Un fichier\*objet (.obj). |
| `FILE_TYPE_CODE_EXECUTABLE_IMAGE` | 2 (0x0000002) | Un fichier\*exécutable (.exe) ou DLL (.dll).\* |
| `FILE_TYPE_CODE_LIB` | 3 (0x00000003) | Un fichier de bibliothèque statique (.lib). |
| `FILE_TYPE_CODE_IMP_LIB` | 4 (0x00000004) | Une bibliothèque d’importation (.lib) |
| `FILE_TYPE_CODE_EXP` | 5 (0x0000005) | Un fichier d’exportation ( exp). |

## <a name="remarks"></a>Notes

::: moniker-end
