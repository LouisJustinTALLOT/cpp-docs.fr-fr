---
title: Classe BackEndPass
description: La référence de classe CMD Build Insights SDK BackEndPass.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- BackEndPass
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 2b4b1a219abdbe418efaab4537f1c6dc9a22afb3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325242"
---
# <a name="backendpass-class"></a>Classe BackEndPass

::: moniker range="<=vs-2015"

Le SDK Build Insights est compatible avec Visual Studio 2017 et plus. Pour voir la documentation de ces versions, définissez le contrôle du sélecteur Visual Studio **Version** pour cet article à Visual Studio 2017 ou Visual Studio 2019. On le trouve en haut de la table des contenus sur cette page.

::: moniker-end
::: moniker range=">=vs-2017"

La `BackEndPass` classe est utilisée avec les fonctions [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)et [MatchEventStackInMemberFunction.](../functions/match-event-stack-in-member-function.md) Utilisez-le pour correspondre à un [événement BACK_END_PASS.](../event-table.md#back-end-pass)

## <a name="syntax"></a>Syntaxe

```cpp
class BackEndPass : public CompilerPass
{
public:
    BackEndPass(const RawEvent& event);
};
```

## <a name="members"></a>Membres

Avec les membres hérités de sa classe `BackEndPass` de base [CompilerPass,](compiler-pass.md) la classe contient les membres suivants :

### <a name="constructors"></a>Constructeurs

[BackEndPass (BackEndPass)](#back-end-pass)

## <a name="backendpass"></a><a name="back-end-pass"></a>BackEndPass (BackEndPass)

```cpp
BackEndPass(const RawEvent& event);
```

### <a name="parameters"></a>Paramètres

*Événement*\
Un [événement BACK_END_PASS.](../event-table.md#back-end-pass)

::: moniker-end
