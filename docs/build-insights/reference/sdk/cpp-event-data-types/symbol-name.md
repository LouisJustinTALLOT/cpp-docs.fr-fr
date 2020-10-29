---
title: SymbolName, classe
description: Référence de la classe SymbolName du kit de développement logiciel (SDK) C++ Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- SymbolName
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: a749d95b3812df8b1cc0cd7d2da037e98467cefc
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92920474"
---
# <a name="symbolname-class"></a>SymbolName, classe

::: moniker range="<=msvc-140"

Le kit de développement logiciel (SDK) C++ Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de **version** de Visual Studio pour cet article sur visual studio 2017 ou visual studio 2019. Elle se trouve en haut de la table des matières sur cette page.

::: moniker-end
::: moniker range=">=msvc-150"

La `SymbolName` classe est utilisée avec les fonctions [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)et [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) . Utilisez-le pour faire correspondre un événement [SYMBOL_NAME](../event-table.md#symbol-name) .

## <a name="syntax"></a>Syntaxe

```cpp
class SymbolName : public SimpleEvent
{
public:
    SymbolName(const RawEvent& event);

    const unsigned long long&  Key() const;
    const char*                Name() const;
};
```

## <a name="members"></a>Membres

Avec les membres hérités de sa classe de base [SimpleEvent](simple-event.md) , la `SymbolName` classe contient les membres suivants :

### <a name="constructors"></a>Constructeurs

[SymbolName](#symbol-name)

### <a name="functions"></a>Fonctions

[Clé](#key) 
 [Nom](#name)

## <a name="key"></a><a name="key"></a> Essentiel

```cpp
const unsigned long long& Key() const;
```

### <a name="return-value"></a>Valeur de retour

Identificateur numérique pour le type représenté par ce symbole. Cet identificateur est unique au sein d’un test frontal du compilateur.

## <a name="name"></a><a name="name"></a> Nomme

```cpp
const char* Name() const;
```

### <a name="return-value"></a>Valeur de retour

Nom du type représenté par le symbole, encodé au format UTF-8.

## <a name="symbolname"></a><a name="symbol-name"></a> SymbolName

```cpp
SymbolName(const RawEvent& event);
```

### <a name="parameters"></a>Paramètres

*événement*\
Événement [SYMBOL_NAME](../event-table.md#symbol-name) .

::: moniker-end
