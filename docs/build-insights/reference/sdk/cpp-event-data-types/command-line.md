---
title: Classe CommandLine
description: La référence de classe CMD Build Insights SDK CommandLine.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- CommandLine
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: b35d688acf06579cc27f2fee053ef58032e204e0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325061"
---
# <a name="commandline-class"></a>Classe CommandLine

::: moniker range="<=vs-2015"

Le SDK Build Insights est compatible avec Visual Studio 2017 et plus. Pour voir la documentation de ces versions, définissez le contrôle du sélecteur Visual Studio **Version** pour cet article à Visual Studio 2017 ou Visual Studio 2019. On le trouve en haut de la table des contenus sur cette page.

::: moniker-end
::: moniker range=">=vs-2017"

La `CommandLine` classe est utilisée avec les fonctions [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)et [MatchEventStackInMemberFunction.](../functions/match-event-stack-in-member-function.md) Utilisez-le pour correspondre à un [événement COMMAND_LINE.](../event-table.md#command-line)

## <a name="syntax"></a>Syntaxe

```cpp
class CommandLine : public SimpleEvent
{
public:
    CommandLine(const RawEvent& event);

    const wchar_t* Value() const;
};
```

## <a name="members"></a>Membres

Avec les membres hérités de sa classe `CommandLine` de base [SimpleEvent,](simple-event.md) la classe contient les membres suivants :

### <a name="constructors"></a>Constructeurs

[Commandline](#command-line)

### <a name="functions"></a>Fonctions

[Valeur](#value)

## <a name="commandline"></a><a name="command-line"></a>Commandline

```cpp
CommandLine(const RawEvent& event);
```

### <a name="parameters"></a>Paramètres

*Événement*\
Un [événement COMMAND_LINE.](../event-table.md#command-line)

## <a name="value"></a><a name="value"></a> Valeur

```cpp
const wchar_t Value() const;
```

### <a name="return-value"></a>Valeur de retour

Une chaîne contenant une ligne de commande. La valeur comprend les arguments obtenus à partir d’un \_\_fichier de \_réponse\_et de variables de l’environnement tels qu’un CL, CL , Link et LINK .

::: moniker-end
