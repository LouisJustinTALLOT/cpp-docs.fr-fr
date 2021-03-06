---
title: Classe de fonction
description: Référence de la classe de la fonction SDK C++ Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Function
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 874477b9ca31095bfcf4ba3c7a6fd220dc073415
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92920643"
---
# <a name="function-class"></a>Classe de fonction

::: moniker range="<=msvc-140"

Le kit de développement logiciel (SDK) C++ Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de **version** de Visual Studio pour cet article sur visual studio 2017 ou visual studio 2019. Elle se trouve en haut de la table des matières sur cette page.

::: moniker-end
::: moniker range=">=msvc-150"

La `Function` classe est utilisée avec les fonctions [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)et [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) . Utilisez-le pour faire correspondre un événement de [fonction](../event-table.md#function) .

## <a name="syntax"></a>Syntaxe

```cpp
class Function : public Activity
{
public:
    Function(const RawEvent& event);

    const char* Name() const;
};
```

## <a name="members"></a>Membres

Avec les membres hérités de sa classe de base [Activity](activity.md) , la `Function` classe contient les membres suivants :

### <a name="constructors"></a>Constructeurs

[Fonction](#function)

### <a name="functions"></a>Fonctions

[Nom](#name)

## <a name="function"></a><a name="function"></a> Fonctionnalités

```cpp
Function(const RawEvent& event);
```

### <a name="parameters"></a>Paramètres

*événement*\
Événement de [fonction](../event-table.md#function) .

## <a name="name"></a><a name="name"></a> Nomme

```cpp
const char* Name() const;
```

### <a name="return-value"></a>Valeur de retour

Nom de la fonction, encodé au format UTF-8.

::: moniker-end
