---
title: FileOutput, classe
description: Référence de la classe FileOutput du kit de développement logiciel (SDK) C++ Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- FileOutput
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 65e23715d8ac47a8653215e8bd3ee7a43bbe80a3
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92923244"
---
# <a name="fileoutput-class"></a>FileOutput, classe

::: moniker range="<=msvc-140"

Le kit de développement logiciel (SDK) C++ Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de **version** de Visual Studio pour cet article sur visual studio 2017 ou visual studio 2019. Elle se trouve en haut de la table des matières sur cette page.

::: moniker-end
::: moniker range=">=msvc-150"

La `FileOutput` classe est utilisée avec les fonctions [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)et [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) . Utilisez-le pour faire correspondre un événement [EXECUTABLE_IMAGE_OUTPUT](../event-table.md#executable-image-output), [EXP_OUTPUT](../event-table.md#exp-output), [IMP_LIB_OUTPUT](../event-table.md#imp-lib-output), [LIB_OUTPUT](../event-table.md#lib-output)ou [OBJ_OUTPUT](../event-table.md#obj-output) .

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

Avec les membres hérités de sa classe de base [SimpleEvent](simple-event.md) , la `FileOutput` classe contient les membres suivants :

### <a name="constructors"></a>Constructeurs

[FileOutput](#file-output)

### <a name="functions"></a>Fonctions

[Chemin d’accès](#path) 
 [Type](#type)

## <a name="fileoutput"></a><a name="file-output"></a> FileOutput

```cpp
FileOutput(const RawEvent& event);
```

### <a name="parameters"></a>Paramètres

*événement*\
Événement [EXECUTABLE_IMAGE_OUTPUT](../event-table.md#executable-image-output), [EXP_OUTPUT](../event-table.md#exp-output), [IMP_LIB_OUTPUT](../event-table.md#imp-lib-output), [LIB_OUTPUT](../event-table.md#lib-output)ou [OBJ_OUTPUT](../event-table.md#obj-output) .

## <a name="path"></a><a name="path"></a> Path

```cpp
const wchar_t Path() const;
```

### <a name="return-value"></a>Valeur de retour

Chemin d’accès absolu au fichier de sortie.

## <a name="type"></a>Type <a name="type"></a>

```cpp
Type Type() const;
```

### <a name="return-value"></a>Valeur de retour

Code décrivant le type de fichier de sortie.

::: moniker-end
