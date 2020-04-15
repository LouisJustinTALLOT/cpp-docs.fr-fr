---
title: Cours d’invocation
description: La référence de classe d’invocation de CMD Build Insights SDK.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Invocation
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: fcb087d46ea445251b0108f811545a44c26f421e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324642"
---
# <a name="invocation-class"></a>Cours d’invocation

::: moniker range="<=vs-2015"

Le SDK Build Insights est compatible avec Visual Studio 2017 et plus. Pour voir la documentation de ces versions, définissez le contrôle du sélecteur Visual Studio **Version** pour cet article à Visual Studio 2017 ou Visual Studio 2019. On le trouve en haut de la table des contenus sur cette page.

::: moniker-end
::: moniker range=">=vs-2017"

La `Invocation` classe est utilisée avec les fonctions [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)et [MatchEventStackInMemberFunction.](../functions/match-event-stack-in-member-function.md) Utilisez-le pour correspondre à un événement [COMPILER](../event-table.md#compiler) ou [LINKER.](../event-table.md#linker)

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

Avec les membres hérités de sa `Invocation` classe de base [d’activité,](activity.md) la classe contient les membres suivants :

### <a name="constructors"></a>Constructeurs

[Invocation](#invocation)

### <a name="functions"></a>Fonctions

[ToolPath](#tool-path)
[ToolVersion](#tool-version)
[ToolVersionString](#tool-version-string)
[Type](#type)
[WorkingDirectory](#working-directory)

## <a name="invocation"></a><a name="invocation"></a>Invocation

```cpp
Invocation(const RawEvent& event);
```

### <a name="parameters"></a>Paramètres

*Événement*\
Un événement [COMPILER](../event-table.md#compiler) ou [LINKER.](../event-table.md#linker)

## <a name="toolpath"></a><a name="tool-path"></a>ToolPath (en)

```cpp
const wchar_t* ToolPath() const;
```

### <a name="return-value"></a>Valeur de retour

Le chemin absolu vers l’outil qui a été invoqué.

## <a name="toolversion"></a><a name="tool-version"></a>ToolVersion

```cpp
const INVOCATION_VERSION_DATA& ToolVersion() const;
```

### <a name="return-value"></a>Valeur de retour

La version de l’outil qui a été invoquée, comme une [référence INVOCATION_VERSION_DATA.](../c-event-data-types/invocation-version-data-struct.md)

## <a name="toolversionstring"></a><a name="tool-version-string"></a>ToolVersionString (en)

```cpp
const char* ToolVersionString() const;
```

### <a name="return-value"></a>Valeur de retour

La version de l’outil qui a été invoqué, comme une chaîne ANSI.

## <a name="type"></a>Type <a name="type"></a>

```cpp
Type Type() const;
```

### <a name="return-value"></a>Valeur de retour

Un code indiquant l’outil qui a été invoqué.

## <a name="workingdirectory"></a><a name="working-directory"></a>Direction de travail

```cpp
const wchar_t* WorkingDirectory() const;
```

### <a name="return-value"></a>Valeur de retour

Le chemin absolu vers le répertoire dans lequel l’outil a été invoqué.

::: moniker-end
