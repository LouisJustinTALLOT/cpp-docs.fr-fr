---
title: RelogA (RelogA)
description: La référence de fonction CMD Build Insights SDK RelogA.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- RelogA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 5a772b1156fc69eeef39514afe401c549c3b7c38
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323851"
---
# <a name="reloga"></a>RelogA (RelogA)

::: moniker range="<=vs-2015"

Le SDK Build Insights est compatible avec Visual Studio 2017 et plus. Pour voir la documentation de ces versions, définissez le contrôle du sélecteur Visual Studio **Version** pour cet article à Visual Studio 2017 ou Visual Studio 2019. On le trouve en haut de la table des contenus sur cette page.

::: moniker-end
::: moniker range=">=vs-2017"

La `RelogA` fonction est utilisée pour lire les événements MSVC à partir d’une trace event Tracing for Windows (ETW) et les écrire dans une nouvelle trace ETW modifiée.

## <a name="syntax"></a>Syntaxe

```cpp
enum RESULT_CODE RelogA(
    const char*             inputLogFile,
    const char*             outputLogFile,
    const RELOG_DESCRIPTOR* relogDescriptor);
```

### <a name="parameters"></a>Paramètres

*inputLogFile (en)*\
L’entrée ETW trace que vous souhaitez lire les événements à partir.

*sortieLogFile*\
Le fichier dans lequel écrire les nouveaux événements.

*relogDescriptor*\
Pointeur vers un [objet RELOG_DESCRIPTOR.](../other-types/relog-descriptor-struct.md) Utilisez cet objet pour configurer la session de réinstruation.

### <a name="return-value"></a>Valeur de retour

Un code de résultat de [l’enum RESULT_CODE.](../other-types/result-code-enum.md)

::: moniker-end
