---
title: CommandLine (classe)
description: Référence à la classe CommandLine du SDK C++ Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- CommandLine
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 5214f2970329510088184dc3092db66607f4d67e
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92923331"
---
# <a name="commandline-class"></a>CommandLine (classe)

::: moniker range="<=msvc-140"

Le kit de développement logiciel (SDK) C++ Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de **version** de Visual Studio pour cet article sur visual studio 2017 ou visual studio 2019. Elle se trouve en haut de la table des matières sur cette page.

::: moniker-end
::: moniker range=">=msvc-150"

La `CommandLine` classe est utilisée avec les fonctions [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)et [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) . Utilisez-le pour faire correspondre un événement [COMMAND_LINE](../event-table.md#command-line) .

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

Avec les membres hérités de sa classe de base [SimpleEvent](simple-event.md) , la `CommandLine` classe contient les membres suivants :

### <a name="constructors"></a>Constructeurs

[CommandLine](#command-line)

### <a name="functions"></a>Fonctions

[Valeur](#value)

## <a name="commandline"></a><a name="command-line"></a> CommandLine

```cpp
CommandLine(const RawEvent& event);
```

### <a name="parameters"></a>Paramètres

*événement*\
Événement [COMMAND_LINE](../event-table.md#command-line) .

## <a name="value"></a><a name="value"></a> Valeur

```cpp
const wchar_t Value() const;
```

### <a name="return-value"></a>Valeur de retour

Chaîne contenant une ligne de commande. La valeur comprend les arguments obtenus à partir d’un fichier réponse et des variables d’environnement telles que CL, \_ CL \_ , Link et \_ Link \_ .

::: moniker-end
