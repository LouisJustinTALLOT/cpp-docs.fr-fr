---
title: Classe FrontEndFile
description: La référence de classe CMD Build Insights SDK FrontEndFile.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- FrontEndFile
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: c40137724279ea2fd615729db39f0ac5c907b79e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324757"
---
# <a name="frontendfile-class"></a>Classe FrontEndFile

::: moniker range="<=vs-2015"

Le SDK Build Insights est compatible avec Visual Studio 2017 et plus. Pour voir la documentation de ces versions, définissez le contrôle du sélecteur Visual Studio **Version** pour cet article à Visual Studio 2017 ou Visual Studio 2019. On le trouve en haut de la table des contenus sur cette page.

::: moniker-end
::: moniker range=">=vs-2017"

La `FrontEndFile` classe est utilisée avec les fonctions [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)et [MatchEventStackInMemberFunction.](../functions/match-event-stack-in-member-function.md) Utilisez-le pour correspondre à un [événement FRONT_END_FILE.](../event-table.md#front-end-file)

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

Avec les membres hérités de sa `FrontEndFile` classe de base [d’activité,](activity.md) la classe contient les membres suivants :

### <a name="constructors"></a>Constructeurs

[FrontEndFile (FrontEndFile)](#front-end-file)

### <a name="functions"></a>Fonctions

[Chemin d’accès](#path)

## <a name="frontendfile"></a><a name="front-end-file"></a>FrontEndFile (FrontEndFile)

```cpp
FrontEndFile(const RawEvent& event);
```

### <a name="parameters"></a>Paramètres

*Événement*\
Un [événement FRONT_END_FILE.](../event-table.md#front-end-file)

## <a name="path"></a><a name="path"></a>Chemin

```cpp
const char* Path() const;
```

### <a name="return-value"></a>Valeur de retour

Le chemin absolu vers le fichier, codé dans UTF-8.

::: moniker-end
