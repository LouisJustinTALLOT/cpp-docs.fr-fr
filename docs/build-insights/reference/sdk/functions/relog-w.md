---
title: RelogW (RelogW)
description: La référence de fonction CMD Build Insights SDK RelogW.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- RelogW
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: c5d5f6e35c7cd24d2324ce1d8a0434d9048b1d85
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323813"
---
# <a name="relogw"></a>RelogW (RelogW)

::: moniker range="<=vs-2015"

Le SDK Build Insights est compatible avec Visual Studio 2017 et plus. Pour voir la documentation de ces versions, définissez le contrôle du sélecteur Visual Studio **Version** pour cet article à Visual Studio 2017 ou Visual Studio 2019. On le trouve en haut de la table des contenus sur cette page.

::: moniker-end
::: moniker range=">=vs-2017"

La `RelogW` fonction est utilisée pour lire les événements MSVC à partir d’une trace d’entrée Event Tracing for Windows (ETW) et les écrire dans une nouvelle trace ETW modifiée.

## <a name="syntax"></a>Syntaxe

```cpp
enum RESULT_CODE RelogW(
    const wchar_t*          inputLogFile,
    const wchar_t*          outputLogFile,
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
