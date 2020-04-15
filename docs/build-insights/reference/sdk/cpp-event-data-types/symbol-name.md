---
title: Classe SymbolName
description: La référence de classe SDK SymbolName build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- SymbolName
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 1306fb43d6c2140a75b36c5f142532916cf26ae4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324354"
---
# <a name="symbolname-class"></a>Classe SymbolName

::: moniker range="<=vs-2015"

Le SDK Build Insights est compatible avec Visual Studio 2017 et plus. Pour voir la documentation de ces versions, définissez le contrôle du sélecteur Visual Studio **Version** pour cet article à Visual Studio 2017 ou Visual Studio 2019. On le trouve en haut de la table des contenus sur cette page.

::: moniker-end
::: moniker range=">=vs-2017"

La `SymbolName` classe est utilisée avec les fonctions [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)et [MatchEventStackInMemberFunction.](../functions/match-event-stack-in-member-function.md) Utilisez-le pour correspondre à un [événement SYMBOL_NAME.](../event-table.md#symbol-name)

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

Avec les membres hérités de sa classe `SymbolName` de base [SimpleEvent,](simple-event.md) la classe contient les membres suivants :

### <a name="constructors"></a>Constructeurs

[SymbolName (symbolname)](#symbol-name)

### <a name="functions"></a>Fonctions

[Key](#key)
[Nom](#name) clé

## <a name="key"></a><a name="key"></a>Clé

```cpp
const unsigned long long& Key() const;
```

### <a name="return-value"></a>Valeur de retour

Un identifiant numérique pour le type représenté par ce symbole. Cet identifiant est unique dans un pass frontale compilateur.

## <a name="name"></a><a name="name"></a>Nom

```cpp
const char* Name() const;
```

### <a name="return-value"></a>Valeur de retour

Le nom du type représenté par le symbole, codé dans UTF-8.

## <a name="symbolname"></a><a name="symbol-name"></a>SymbolName (symbolname)

```cpp
SymbolName(const RawEvent& event);
```

### <a name="parameters"></a>Paramètres

*Événement*\
Un [événement SYMBOL_NAME.](../event-table.md#symbol-name)

::: moniker-end
