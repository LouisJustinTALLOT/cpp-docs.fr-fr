---
title: CommandLine (classe)
description: Référence C++ de classe de la ligne de commande SDK de build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- CommandLine
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: ff16646920fe77f7f3b4cb8a194a38984c3e6c32
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333509"
---
# <a name="commandline-class"></a>CommandLine (classe)

::: moniker range="<=vs-2015"

Le C++ Kit de développement logiciel (SDK) Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de version de Visual Studio pour cet article sur Visual Studio 2017 ou Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

La classe `CommandLine` est utilisée avec les fonctions [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)et [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) . Utilisez-le pour faire correspondre un événement [COMMAND_LINE](../event-table.md#command-line) .

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

Avec les membres hérités de sa classe de base [SimpleEvent](simple-event.md) , la classe `CommandLine` contient les membres suivants :

### <a name="constructors"></a>Constructeurs

[CommandLine](#command-line)

### <a name="functions"></a>Fonctions

[Valeur](#value)

## <a name="command-line"></a>CommandLine

```cpp
CommandLine(const RawEvent& event);
```

### <a name="parameters"></a>Paramètres

*event*\
Événement [COMMAND_LINE](../event-table.md#command-line) .

## <a name="value"></a>Ajoutée

```cpp
const wchar_t Value() const;
```

### <a name="return-value"></a>Valeur de retour

Chaîne contenant une ligne de commande. La valeur comprend les arguments obtenus à partir d’un fichier réponse et des variables d’environnement telles que CL, \_CL\_, Link et \_lien\_.

::: moniker-end
