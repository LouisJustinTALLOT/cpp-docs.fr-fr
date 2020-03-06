---
title: FileOutput, classe
description: Référence C++ de la classe FileOutput du kit de développement logiciel (SDK) Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- FileOutput
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 1c4053d0378ddb9d5dd061bbc9889c454dc9b52c
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333341"
---
# <a name="fileoutput-class"></a>FileOutput, classe

::: moniker range="<=vs-2015"

Le C++ Kit de développement logiciel (SDK) Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de version de Visual Studio pour cet article sur Visual Studio 2017 ou Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

La classe `FileOutput` est utilisée avec les fonctions [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)et [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) . Utilisez-le pour faire correspondre un événement [EXECUTABLE_IMAGE_OUTPUT](../event-table.md#executable-image-output), [EXP_OUTPUT](../event-table.md#exp-output), [IMP_LIB_OUTPUT](../event-table.md#imp-lib-output), [LIB_OUTPUT](../event-table.md#lib-output)ou [OBJ_OUTPUT](../event-table.md#obj-output) .

## <a name="syntax"></a>Syntaxe

```cpp
class FileOutput : public SimpleEvent
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

    FileOutput(const RawEvent& event);

    const wchar_t* Path() const;
    Type           Type() const;
};
```

## <a name="members"></a>Membres

Avec les membres hérités de sa classe de base [SimpleEvent](simple-event.md) , la classe `FileOutput` contient les membres suivants :

### <a name="constructors"></a>Constructeurs

[FileOutput](#file-output)

### <a name="functions"></a>Fonctions

[Type](#type) de
[path](#path)

## <a name="file-output"></a>FileOutput

```cpp
FileOutput(const RawEvent& event);
```

### <a name="parameters"></a>Paramètres

*event*\
Événement [EXECUTABLE_IMAGE_OUTPUT](../event-table.md#executable-image-output), [EXP_OUTPUT](../event-table.md#exp-output), [IMP_LIB_OUTPUT](../event-table.md#imp-lib-output), [LIB_OUTPUT](../event-table.md#lib-output)ou [OBJ_OUTPUT](../event-table.md#obj-output) .

## <a name="path"></a> Path

```cpp
const wchar_t Path() const;
```

### <a name="return-value"></a>Valeur de retour

Chemin d’accès absolu au fichier de sortie.

## <a name="type"></a>Entrer

```cpp
Type Type() const;
```

### <a name="return-value"></a>Valeur de retour

Code décrivant le type de fichier de sortie.

::: moniker-end
