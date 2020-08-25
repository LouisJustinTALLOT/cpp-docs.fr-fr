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
ms.openlocfilehash: 054bdf75dcfca42b8c202565fb44df671f17f912
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88831617"
---
# <a name="compilerpass-class"></a>CompilerPass, classe

::: moniker range="<=vs-2015"

Le kit de développement logiciel (SDK) C++ Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de **version** de Visual Studio pour cet article sur visual studio 2017 ou visual studio 2019. Elle se trouve en haut de la table des matières sur cette page.

::: moniker-end
::: moniker range=">=vs-2017"

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

### <a name="functions"></a>Functions

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

### <a name="return-value"></a>Valeur renvoyée

Le chemin d’accès absolu au fichier source d’entrée traité par ce compilateur passe.

## <a name="outputobjectpath"></a><a name="output-object-path"></a> OutputObjectPath

```cpp
const wchar_t* OutputObjectPath() const;
```

### <a name="return-value"></a>Valeur renvoyée

Le chemin d’accès absolu au fichier objet de sortie produit par ce compilateur passe.

## <a name="passcode"></a><a name="pass-code"></a> Code secret

```cpp
PassCode PassCode() const;
```

### <a name="return-value"></a>Valeur renvoyée

Code indiquant la passe de compilateur représentée par cet objet CompilerPass.

::: moniker-end
