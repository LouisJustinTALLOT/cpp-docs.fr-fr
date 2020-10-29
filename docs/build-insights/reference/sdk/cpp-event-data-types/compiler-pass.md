---
title: CompilerPass, classe
description: Référence de la classe CompilerPass du kit de développement logiciel (SDK) C++ Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- CompilerPass
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: bfbfdc28870a13a9cdb19d0ec050ea2e69fe1208
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92920812"
---
# <a name="compilerpass-class"></a>CompilerPass, classe

::: moniker range="<=msvc-140"

Le kit de développement logiciel (SDK) C++ Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de **version** de Visual Studio pour cet article sur visual studio 2017 ou visual studio 2019. Elle se trouve en haut de la table des matières sur cette page.

::: moniker-end
::: moniker range=">=msvc-150"

La `CompilerPass` classe est utilisée avec les fonctions [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)et [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) . Utilisez-le pour faire correspondre un événement [BACK_END_PASS](../event-table.md#back-end-pass) ou [FRONT_END_PASS](../event-table.md#front-end-pass) .

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

Avec les membres hérités de sa classe de base [Activity](activity.md) , la `CompilerPass` classe contient les membres suivants :

### <a name="constructors"></a>Constructeurs

[CompilerPass](#compiler-pass)

### <a name="enums"></a>Énumérations

#### <a name="passcode"></a>Code secret

|Valeur|Description|
|-|-|
|FRONT_END|Réussite du serveur frontal.|
|BACK_END|Réussite de l’arrière-plan.|

### <a name="functions"></a>Fonctions

[InputSourcePath](#input-source-path)\
[OutputObjectPath](#output-object-path)\
[Code secret](#pass-code)\

## <a name="compilerpass"></a><a name="compiler-pass"></a> CompilerPass

```cpp
CompilerPass(const RawEvent& event);
```

### <a name="parameters"></a>Paramètres

*événement*\
Événement [BACK_END_PASS](../event-table.md#back-end-pass) ou [FRONT_END_PASS](../event-table.md#front-end-pass) .

## <a name="inputsourcepath"></a><a name="input-source-path"></a> InputSourcePath

```cpp
const wchar_t* InputSourcePath() const;
```

### <a name="return-value"></a>Valeur de retour

Le chemin d’accès absolu au fichier source d’entrée traité par ce compilateur passe.

## <a name="outputobjectpath"></a><a name="output-object-path"></a> OutputObjectPath

```cpp
const wchar_t* OutputObjectPath() const;
```

### <a name="return-value"></a>Valeur de retour

Le chemin d’accès absolu au fichier objet de sortie produit par ce compilateur passe.

## <a name="passcode"></a><a name="pass-code"></a> Code secret

```cpp
PassCode PassCode() const;
```

### <a name="return-value"></a>Valeur de retour

Code indiquant la passe de compilateur représentée par cet objet CompilerPass.

::: moniker-end
