---
title: Classe FrontEndPass
description: La référence de classe CMD Build Insights SDK FrontEndPass.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- FrontEndPass
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 137f553f1e495b7658ae89e69a48cec6b1988a81
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324729"
---
# <a name="frontendpass-class"></a>Classe FrontEndPass

::: moniker range="<=vs-2015"

Le SDK Build Insights est compatible avec Visual Studio 2017 et plus. Pour voir la documentation de ces versions, définissez le contrôle du sélecteur Visual Studio **Version** pour cet article à Visual Studio 2017 ou Visual Studio 2019. On le trouve en haut de la table des contenus sur cette page.

::: moniker-end
::: moniker range=">=vs-2017"

La `FrontEndPass` classe est utilisée avec les fonctions [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)et [MatchEventStackInMemberFunction.](../functions/match-event-stack-in-member-function.md) Utilisez-le pour correspondre à un [événement FRONT_END_PASS.](../event-table.md#front-end-pass)

## <a name="syntax"></a>Syntaxe

```cpp
class FrontEndPass : public CompilerPass
{
public:
    FrontEndPass(const RawEvent& event);
};
```

## <a name="members"></a>Membres

Avec les membres hérités de sa classe `FrontEndPass` de base [CompilerPass,](compiler-pass.md) la classe contient les membres suivants :

### <a name="constructors"></a>Constructeurs

[FrontEndPass (frontEndPass)](#front-end-pass)

## <a name="frontendpass"></a><a name="front-end-pass"></a>FrontEndPass (frontEndPass)

```cpp
FrontEndPass(const RawEvent& event);
```

### <a name="parameters"></a>Paramètres

*Événement*\
Un [événement FRONT_END_PASS.](../event-table.md#front-end-pass)

::: moniker-end
