---
title: CompilerPass, classe
description: Référence C++ de la classe CompilerPass du kit de développement logiciel (SDK) Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- CompilerPass
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 3c2fa1c2c4be8aaf5bec77b383f93a4b033ca8e3
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333474"
---
# <a name="compilerpass-class"></a>CompilerPass, classe

::: moniker range="<=vs-2015"

Le C++ Kit de développement logiciel (SDK) Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de version de Visual Studio pour cet article sur Visual Studio 2017 ou Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

La classe `CompilerPass` est utilisée avec les fonctions [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)et [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) . Utilisez-le pour faire correspondre un événement [BACK_END_PASS](../event-table.md#back-end-pass) ou [FRONT_END_PASS](../event-table.md#front-end-pass) .

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

Avec les membres hérités de sa classe de base [Activity](activity.md) , la classe `CompilerPass` contient les membres suivants :

### <a name="constructors"></a>Constructeurs

[CompilerPass](#compiler-pass)

### <a name="enums"></a>Enums

#### <a name="passcode"></a>Code secret

|||
|-|-|
|FRONT_END|Réussite du serveur frontal.|
|BACK_END|Réussite de l’arrière-plan.|

### <a name="functions"></a>Fonctions

[InputSourcePath](#input-source-path)\
[OutputObjectPath](#output-object-path)\
\ du [code secret](#pass-code)

## <a name="compiler-pass"></a>CompilerPass

```cpp
CompilerPass(const RawEvent& event);
```

### <a name="parameters"></a>Paramètres

*event*\
Événement [BACK_END_PASS](../event-table.md#back-end-pass) ou [FRONT_END_PASS](../event-table.md#front-end-pass) .

## <a name="input-source-path"></a>InputSourcePath

```cpp
const wchar_t* InputSourcePath() const;
```

### <a name="return-value"></a>Valeur de retour

Le chemin d’accès absolu au fichier source d’entrée traité par ce compilateur passe.

## <a name="output-object-path"></a>OutputObjectPath

```cpp
const wchar_t* OutputObjectPath() const;
```

### <a name="return-value"></a>Valeur de retour

Le chemin d’accès absolu au fichier objet de sortie produit par ce compilateur passe.

## <a name="pass-code"></a>Code secret

```cpp
PassCode PassCode() const;
```

### <a name="return-value"></a>Valeur de retour

Code indiquant la passe de compilateur représentée par cet objet CompilerPass.

::: moniker-end
