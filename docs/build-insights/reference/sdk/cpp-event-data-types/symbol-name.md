---
title: SymbolName, classe
description: Référence C++ de la classe SymbolName du kit de développement logiciel (SDK) Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- SymbolName
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: b5e9a9b22db99c099b9f7dc1813fb335358a83e8
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332998"
---
# <a name="symbolname-class"></a>SymbolName, classe

::: moniker range="<=vs-2015"

Le C++ Kit de développement logiciel (SDK) Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de version de Visual Studio pour cet article sur Visual Studio 2017 ou Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

La classe `SymbolName` est utilisée avec les fonctions [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)et [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) . Utilisez-le pour faire correspondre un événement [SYMBOL_NAME](../event-table.md#symbol-name) .

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

Avec les membres hérités de sa classe de base [SimpleEvent](simple-event.md) , la classe `SymbolName` contient les membres suivants :

### <a name="constructors"></a>Constructeurs

[SymbolName](#symbol-name)

### <a name="functions"></a>Fonctions

[Nom](#name) de la
de [clé](#key)

## <a name="key"></a>Essentiel

```cpp
const unsigned long long& Key() const;
```

### <a name="return-value"></a>Valeur de retour

Identificateur numérique pour le type représenté par ce symbole. Cet identificateur est unique au sein d’un test frontal du compilateur.

## <a name="name"></a> Name

```cpp
const char* Name() const;
```

### <a name="return-value"></a>Valeur de retour

Nom du type représenté par le symbole, encodé au format UTF-8.

## <a name="symbol-name"></a>SymbolName

```cpp
SymbolName(const RawEvent& event);
```

### <a name="parameters"></a>Paramètres

*event*\
Événement [SYMBOL_NAME](../event-table.md#symbol-name) .

::: moniker-end
