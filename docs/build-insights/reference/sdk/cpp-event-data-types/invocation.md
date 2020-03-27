---
title: Classe d’appel
description: Référence C++ de la classe d’appel du kit de développement logiciel (SDK) Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Invocation
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 0c4698300a3eeaf77210ad74f84b0c0cd219b457
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333229"
---
# <a name="invocation-class"></a>Classe d’appel

::: moniker range="<=vs-2015"

Le C++ Kit de développement logiciel (SDK) Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de version de Visual Studio pour cet article sur Visual Studio 2017 ou Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

La classe `Invocation` est utilisée avec les fonctions [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)et [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) . Utilisez-le pour faire correspondre un [compilateur](../event-table.md#compiler) ou un événement de l' [éditeur de liens](../event-table.md#linker) .

## <a name="syntax"></a>Syntaxe

```cpp
class Invocation : public Activity
{
    const INVOCATION_DATA* data_;

public:
    enum class Type
    {
        CL      = MSVC_TOOL_CODE_CL,
        LINK    = MSVC_TOOL_CODE_LINK
    };

    Invocation(const RawEvent& event);

    Type             Type() const;
    const char*      ToolVersionString() const;
    const wchar_t*   WorkingDirectory() const;
    const wchar_t*   ToolPath() const;

    const INVOCATION_VERSION_DATA& ToolVersion() const;
};
```

## <a name="members"></a>Membres

Avec les membres hérités de sa classe de base [Activity](activity.md) , la classe `Invocation` contient les membres suivants :

### <a name="constructors"></a>Constructeurs

[Invocation](#invocation)

### <a name="functions"></a>Fonctions

[ToolPath](#tool-path)
[ToolVersion](#tool-version)
[ToolVersionString](#tool-version-string)
[Type](#type)
[WorkingDirectory](#working-directory)

## <a name="invocation"></a><a name="invocation"></a>Appel

```cpp
Invocation(const RawEvent& event);
```

### <a name="parameters"></a>Paramètres

*event*\
Événement [du compilateur](../event-table.md#compiler) ou de l' [éditeur de liens](../event-table.md#linker) .

## <a name="toolpath"></a><a name="tool-path"></a>Outil

```cpp
const wchar_t* ToolPath() const;
```

### <a name="return-value"></a>Valeur de retour

Chemin d’accès absolu à l’outil appelé.

## <a name="toolversion"></a><a name="tool-version"></a>Toolversion la valeur

```cpp
const INVOCATION_VERSION_DATA& ToolVersion() const;
```

### <a name="return-value"></a>Valeur de retour

Version de l’outil qui a été appelée, en tant que référence de [INVOCATION_VERSION_DATA](../c-event-data-types/invocation-version-data-struct.md) .

## <a name="toolversionstring"></a><a name="tool-version-string"></a>ToolVersionString

```cpp
const char* ToolVersionString() const;
```

### <a name="return-value"></a>Valeur de retour

Version de l’outil qui a été appelée, sous la forme d’une chaîne ANSI.

## <a name="type"></a><a name="type"></a>Entrer

```cpp
Type Type() const;
```

### <a name="return-value"></a>Valeur de retour

Code indiquant l’outil qui a été appelé.

## <a name="workingdirectory"></a><a name="working-directory"></a>WorkingDirectory

```cpp
const wchar_t* WorkingDirectory() const;
```

### <a name="return-value"></a>Valeur de retour

Chemin d’accès absolu au répertoire dans lequel l’outil a été appelé.

::: moniker-end
