---
title: FileInput, classe
description: Référence C++ de la classe FileInput du kit de développement logiciel (SDK) Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- FileInput
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: bea2cf72ca2a83a9cd630f8a9ccefb87dd4b7ff1
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333348"
---
# <a name="fileinput-class"></a>FileInput, classe

::: moniker range="<=vs-2015"

Le C++ Kit de développement logiciel (SDK) Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de version de Visual Studio pour cet article sur Visual Studio 2017 ou Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

La classe `FileInput` est utilisée avec les fonctions [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)et [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) . Utilisez-le pour faire correspondre un événement [FILE_INPUT](../event-table.md#file-input) .

## <a name="syntax"></a>Syntaxe

```cpp
class FileInput : public SimpleEvent
{
public:
    enum class Type
    {
        OTHER               = FILE_TYPE_CODE_OTHER,
        OBJ                 = FILE_TYPE_CODE_OBJ,
        EXECUTABLE_IMAGE    = FILE_TYPE_CODE_EXECUTABLE_IMAGE,
        LIB                 = FILE_TYPE_CODE_LIB,
        IMP_LIB             = FILE_TYPE_CODE_IMP_LIB,
        EXP                 = FILE_TYPE_CODE_EXP
    };

    FileInput(const RawEvent& event);

    const wchar_t* Path() const;
    Type           Type() const;
};
```

## <a name="members"></a>Membres

Avec les membres hérités de sa classe de base [SimpleEvent](simple-event.md) , la classe `FileInput` contient les membres suivants :

### <a name="constructors"></a>Constructeurs

[FileInput](#file-input)

### <a name="functions"></a>Fonctions

[Type](#type) de
[path](#path)

## <a name="file-input"></a>FileInput

```cpp
FileInput(const RawEvent& event);
```

### <a name="parameters"></a>Paramètres

*event*\
Événement [FILE_INPUT](../event-table.md#file-input) .

## <a name="path"></a> Path

```cpp
const wchar_t Path() const;
```

### <a name="return-value"></a>Valeur de retour

Chemin d’accès absolu au fichier d’entrée.

## <a name="type"></a>Entrer

```cpp
Type Type() const;
```

### <a name="return-value"></a>Valeur de retour

Code décrivant le type du fichier d’entrée.

::: moniker-end
