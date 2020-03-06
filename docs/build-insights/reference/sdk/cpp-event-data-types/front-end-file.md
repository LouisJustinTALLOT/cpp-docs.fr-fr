---
title: FrontEndFile, classe
description: Référence C++ de la classe FrontEndFile du kit de développement logiciel (SDK) Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- FrontEndFile
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 094b1326765e0e8edb00534ecb3d94c46702d4ec
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333285"
---
# <a name="frontendfile-class"></a>FrontEndFile, classe

::: moniker range="<=vs-2015"

Le C++ Kit de développement logiciel (SDK) Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de version de Visual Studio pour cet article sur Visual Studio 2017 ou Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

La classe `FrontEndFile` est utilisée avec les fonctions [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)et [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) . Utilisez-le pour faire correspondre un événement [FRONT_END_FILE](../event-table.md#front-end-file) .

## <a name="syntax"></a>Syntaxe

```cpp
class FrontEndFile : public Activity
{
public:
    FrontEndFile(const RawEvent& event);

    const char* Path() const;
};
```

## <a name="members"></a>Membres

Avec les membres hérités de sa classe de base [Activity](activity.md) , la classe `FrontEndFile` contient les membres suivants :

### <a name="constructors"></a>Constructeurs

[FrontEndFile](#front-end-file)

### <a name="functions"></a>Fonctions

[Chemin d’accès](#path)

## <a name="front-end-file"></a>FrontEndFile

```cpp
FrontEndFile(const RawEvent& event);
```

### <a name="parameters"></a>Paramètres

*event*\
Événement [FRONT_END_FILE](../event-table.md#front-end-file) .

## <a name="path"></a> Path

```cpp
const char* Path() const;
```

### <a name="return-value"></a>Valeur de retour

Chemin d’accès absolu au fichier encodé au format UTF-8.

::: moniker-end
