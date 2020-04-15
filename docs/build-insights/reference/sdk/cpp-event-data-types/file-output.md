---
title: Classe FileOutput
description: La référence de classe CMD Build Insights SDK FileOutput.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- FileOutput
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 37823da8a4aaac0ce4094583b8aee8ac1eb04aaa
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324803"
---
# <a name="fileoutput-class"></a>Classe FileOutput

::: moniker range="<=vs-2015"

Le SDK Build Insights est compatible avec Visual Studio 2017 et plus. Pour voir la documentation de ces versions, définissez le contrôle du sélecteur Visual Studio **Version** pour cet article à Visual Studio 2017 ou Visual Studio 2019. On le trouve en haut de la table des contenus sur cette page.

::: moniker-end
::: moniker range=">=vs-2017"

La `FileOutput` classe est utilisée avec les fonctions [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)et [MatchEventStackInMemberFunction.](../functions/match-event-stack-in-member-function.md) Utilisez-le pour correspondre à un [EXECUTABLE_IMAGE_OUTPUT](../event-table.md#executable-image-output), [EXP_OUTPUT](../event-table.md#exp-output), [IMP_LIB_OUTPUT](../event-table.md#imp-lib-output), [LIB_OUTPUT](../event-table.md#lib-output), ou [OBJ_OUTPUT](../event-table.md#obj-output) événement.

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

Avec les membres hérités de sa classe `FileOutput` de base [SimpleEvent,](simple-event.md) la classe contient les membres suivants :

### <a name="constructors"></a>Constructeurs

[FichierOutput](#file-output)

### <a name="functions"></a>Fonctions

[Type de](#path)
[chemin](#type)

## <a name="fileoutput"></a><a name="file-output"></a>FichierOutput

```cpp
FileOutput(const RawEvent& event);
```

### <a name="parameters"></a>Paramètres

*Événement*\
Un [EXECUTABLE_IMAGE_OUTPUT](../event-table.md#executable-image-output), [EXP_OUTPUT](../event-table.md#exp-output), [IMP_LIB_OUTPUT](../event-table.md#imp-lib-output), [LIB_OUTPUT](../event-table.md#lib-output), ou [OBJ_OUTPUT](../event-table.md#obj-output) événement.

## <a name="path"></a><a name="path"></a>Chemin

```cpp
const wchar_t Path() const;
```

### <a name="return-value"></a>Valeur de retour

Le chemin absolu vers le fichier de sortie.

## <a name="type"></a>Type <a name="type"></a>

```cpp
Type Type() const;
```

### <a name="return-value"></a>Valeur de retour

Un code décrivant le type de fichier de sortie.

::: moniker-end
