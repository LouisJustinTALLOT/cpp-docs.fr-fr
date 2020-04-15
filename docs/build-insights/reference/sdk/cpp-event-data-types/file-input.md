---
title: Classe FileInput
description: La référence de classe CMD Build Insights SDK FileInput.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- FileInput
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 642236d3e67465ed38508cb24c8cd698ae880065
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324796"
---
# <a name="fileinput-class"></a>Classe FileInput

::: moniker range="<=vs-2015"

Le SDK Build Insights est compatible avec Visual Studio 2017 et plus. Pour voir la documentation de ces versions, définissez le contrôle du sélecteur Visual Studio **Version** pour cet article à Visual Studio 2017 ou Visual Studio 2019. On le trouve en haut de la table des contenus sur cette page.

::: moniker-end
::: moniker range=">=vs-2017"

La `FileInput` classe est utilisée avec les fonctions [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)et [MatchEventStackInMemberFunction.](../functions/match-event-stack-in-member-function.md) Utilisez-le pour correspondre à un [événement FILE_INPUT.](../event-table.md#file-input)

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

Avec les membres hérités de sa classe `FileInput` de base [SimpleEvent,](simple-event.md) la classe contient les membres suivants :

### <a name="constructors"></a>Constructeurs

[FichierInput](#file-input)

### <a name="functions"></a>Fonctions

[Type de](#path)
[chemin](#type)

## <a name="fileinput"></a><a name="file-input"></a>FichierInput

```cpp
FileInput(const RawEvent& event);
```

### <a name="parameters"></a>Paramètres

*Événement*\
Un [événement FILE_INPUT.](../event-table.md#file-input)

## <a name="path"></a><a name="path"></a>Chemin

```cpp
const wchar_t Path() const;
```

### <a name="return-value"></a>Valeur de retour

Le chemin absolu vers le fichier d’entrée.

## <a name="type"></a>Type <a name="type"></a>

```cpp
Type Type() const;
```

### <a name="return-value"></a>Valeur de retour

Un code décrivant le type de fichier d’entrée.

::: moniker-end
