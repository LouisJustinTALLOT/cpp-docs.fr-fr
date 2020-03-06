---
title: Classe de fonction
description: Référence C++ de la classe de fonction SDK de build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Function
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 3ff66119007ed7172fed7e824287ab8617c70973
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333257"
---
# <a name="function-class"></a>Classe de fonction

::: moniker range="<=vs-2015"

Le C++ Kit de développement logiciel (SDK) Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de version de Visual Studio pour cet article sur Visual Studio 2017 ou Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

La classe `Function` est utilisée avec les fonctions [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)et [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) . Utilisez-le pour faire correspondre un événement de [fonction](../event-table.md#function) .

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

Avec les membres hérités de sa classe de base [Activity](activity.md) , la classe `Function` contient les membres suivants :

### <a name="constructors"></a>Constructeurs

[Fonction](#function)

### <a name="functions"></a>Fonctions

[Nom](#name)

## <a name="function"></a>Fonctionnalités

```cpp
Function(const RawEvent& event);
```

### <a name="parameters"></a>Paramètres

*event*\
Événement de [fonction](../event-table.md#function) .

## <a name="name"></a> Name

```cpp
const char* Name() const;
```

### <a name="return-value"></a>Valeur de retour

Nom de la fonction, encodé au format UTF-8.

::: moniker-end
