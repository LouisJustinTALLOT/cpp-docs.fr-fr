---
title: Énumération FILE_TYPE_CODE
description: Le kit de développement logiciel (SDK) C++ Build Insights FILE_TYPE_CODE référence Enum.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- FILE_TYPE_CODE
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: ddd625829e94786c0daddf0e78b914e225b2ecfb
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92921021"
---
# <a name="file_type_code-enum"></a>Énumération FILE_TYPE_CODE

::: moniker range="<=msvc-140"

Le kit de développement logiciel (SDK) C++ Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de **version** de Visual Studio pour cet article sur visual studio 2017 ou visual studio 2019. Elle se trouve en haut de la table des matières sur cette page.

::: moniker-end
::: moniker range=">=msvc-150"

L' `FILE_TYPE_CODE` énumération décrit le type d’un fichier.

## <a name="members"></a>Membres

| Nom | Valeur | Description |
|--|--|--|
| `FILE_TYPE_CODE_OTHER` | 0 (0x00000000) | Type de fichier non listé dans cet Enum. |
| `FILE_TYPE_CODE_OBJ` | 1 (0x00000001) | Fichier d’objet ( \* . obj). |
| `FILE_TYPE_CODE_EXECUTABLE_IMAGE` | 2 (0x00000002) | Fichier exécutable ( \* . exe) ou dll ( \* . dll). |
| `FILE_TYPE_CODE_LIB` | 3 (0x00000003) | Fichier de bibliothèque statique (*. lib). |
| `FILE_TYPE_CODE_IMP_LIB` | 4 (0x00000004) | Une bibliothèque d’importation (*. lib) |
| `FILE_TYPE_CODE_EXP` | 5 (0x00000005) | Fichier d’exportation (*. exp). |

## <a name="remarks"></a>Notes

::: moniker-end
