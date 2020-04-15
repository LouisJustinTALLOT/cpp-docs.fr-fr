---
title: Classe CompilerPass
description: La référence de classe CMD Build Insights SDK CompilerPass.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- CompilerPass
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 11af981b647d5183f88dad024d90c0ef4f8a28bc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325044"
---
# <a name="compilerpass-class"></a>Classe CompilerPass

::: moniker range="<=vs-2015"

Le SDK Build Insights est compatible avec Visual Studio 2017 et plus. Pour voir la documentation de ces versions, définissez le contrôle du sélecteur Visual Studio **Version** pour cet article à Visual Studio 2017 ou Visual Studio 2019. On le trouve en haut de la table des contenus sur cette page.

::: moniker-end
::: moniker range=">=vs-2017"

La `CompilerPass` classe est utilisée avec les fonctions [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)et [MatchEventStackInMemberFunction.](../functions/match-event-stack-in-member-function.md) Utilisez-le pour faire correspondre un [événement BACK_END_PASS](../event-table.md#back-end-pass) ou [FRONT_END_PASS.](../event-table.md#front-end-pass)

## <a name="syntax"></a>Syntaxe

```cpp
class CompilerPass : public Activity
{
public:
    enum class PassCode
    {
        FRONT_END,
        BACK_END
    };

    CompilerPass(const RawEvent& event);

    PassCode       PassCode() const;
    const wchar_t* InputSourcePath() const;
    const wchar_t* OutputObjectPath() const;
};
```

## <a name="members"></a>Membres

Avec les membres hérités de sa `CompilerPass` classe de base [d’activité,](activity.md) la classe contient les membres suivants :

### <a name="constructors"></a>Constructeurs

[CompilerPass (CompilerPass)](#compiler-pass)

### <a name="enums"></a>Enums

#### <a name="passcode"></a>Code

|||
|-|-|
|FRONT_END|La passe avant.|
|BACK_END|La passe en back-end.|

### <a name="functions"></a>Fonctions

[InputSourcePath (en)](#input-source-path)\
[OutputObjectPath (en)](#output-object-path)\
[Code](#pass-code)\

## <a name="compilerpass"></a><a name="compiler-pass"></a>CompilerPass (CompilerPass)

```cpp
CompilerPass(const RawEvent& event);
```

### <a name="parameters"></a>Paramètres

*Événement*\
Un [événement BACK_END_PASS](../event-table.md#back-end-pass) ou [FRONT_END_PASS.](../event-table.md#front-end-pass)

## <a name="inputsourcepath"></a><a name="input-source-path"></a>InputSourcePath (en)

```cpp
const wchar_t* InputSourcePath() const;
```

### <a name="return-value"></a>Valeur de retour

Le chemin absolu vers le fichier source d’entrée traité par ce pass compilateur.

## <a name="outputobjectpath"></a><a name="output-object-path"></a>OutputObjectPath (en)

```cpp
const wchar_t* OutputObjectPath() const;
```

### <a name="return-value"></a>Valeur de retour

Le chemin absolu vers le fichier d’objet de sortie produit par ce pass compilateur.

## <a name="passcode"></a><a name="pass-code"></a>Code

```cpp
PassCode PassCode() const;
```

### <a name="return-value"></a>Valeur de retour

Un code indiquant quel pas de compilateur est représenté par cet objet CompilerPass.

::: moniker-end
