---
title: Énumération TRANSLATION_UNIT_PASS_CODE
description: Le kit de développement logiciel (SDK) C++ Build Insights TRANSLATION_UNIT_PASS_CODE référence Enum.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TRANSLATION_UNIT_PASS_CODE
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 31f3e16ce6d9aa8c3c9db6cf9c11069dc3ec22fe
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92920916"
---
# <a name="translation_unit_pass_code-enum"></a>Énumération TRANSLATION_UNIT_PASS_CODE

::: moniker range="<=msvc-140"

Le kit de développement logiciel (SDK) C++ Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de **version** de Visual Studio pour cet article sur visual studio 2017 ou visual studio 2019. Elle se trouve en haut de la table des matières sur cette page.

::: moniker-end
::: moniker range=">=msvc-150"

`TRANSLATION_UNIT_PASS_CODE`Enum.

## <a name="members"></a>Membres

| Nom | Valeur | Description |
|--|--|--|
| `TRANSLATION_UNIT_PASS_CODE_FRONT_END` | 0 (0x00000000) | L’étape frontale, responsable de l’analyse du code source et de sa conversion en langage intermédiaire. |
| `TRANSLATION_UNIT_PASS_CODE_BACK_END` | 1 (0x00000001) | L’étape principale, responsable de l’optimisation du langage intermédiaire et de sa conversion en code machine. |

## <a name="remarks"></a>Notes

Utilisé par les fonctions du kit de développement logiciel (SDK) C.

::: moniker-end
