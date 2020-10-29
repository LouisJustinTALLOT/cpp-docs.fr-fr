---
title: Classe d’appel
description: Référence de la classe d’appel du kit de développement logiciel (SDK) C++ Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Invocation
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: dfd463c7b9ca72dc14ad74b3759fdd1e3730d5a9
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92923145"
---
# <a name="invocation-class"></a>Classe d’appel

::: moniker range="<=msvc-140"

Le kit de développement logiciel (SDK) C++ Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de **version** de Visual Studio pour cet article sur visual studio 2017 ou visual studio 2019. Elle se trouve en haut de la table des matières sur cette page.

::: moniker-end
::: moniker range=">=msvc-150"

La `Invocation` classe est utilisée avec les fonctions [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)et [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) . Utilisez-le pour faire correspondre un [compilateur](../event-table.md#compiler) ou un événement de l' [éditeur de liens](../event-table.md#linker) .

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

Avec les membres hérités de sa classe de base [Activity](activity.md) , la `Invocation` classe contient les membres suivants :

### <a name="constructors"></a>Constructeurs

[Invocation](#invocation)

### <a name="functions"></a>Fonctions

[Trajectoire d’outil](#tool-path) 
 [Toolversion la valeur](#tool-version) 
 [ToolVersionString](#tool-version-string) 
 [Type](#type) 
 [WorkingDirectory](#working-directory)

## <a name="invocation"></a><a name="invocation"></a> Appel

```cpp
Invocation(const RawEvent& event);
```

### <a name="parameters"></a>Paramètres

*événement*\
Événement [du compilateur](../event-table.md#compiler) ou de l' [éditeur de liens](../event-table.md#linker) .

## <a name="toolpath"></a><a name="tool-path"></a> Outil

```cpp
const wchar_t* ToolPath() const;
```

### <a name="return-value"></a>Valeur de retour

Chemin d’accès absolu à l’outil appelé.

## <a name="toolversion"></a><a name="tool-version"></a> Toolversion la valeur

```cpp
const INVOCATION_VERSION_DATA& ToolVersion() const;
```

### <a name="return-value"></a>Valeur de retour

Version de l’outil qui a été appelée, en tant que référence de [INVOCATION_VERSION_DATA](../c-event-data-types/invocation-version-data-struct.md) .

## <a name="toolversionstring"></a><a name="tool-version-string"></a> ToolVersionString

```cpp
const char* ToolVersionString() const;
```

### <a name="return-value"></a>Valeur de retour

Version de l’outil qui a été appelée, sous la forme d’une chaîne ANSI.

## <a name="type"></a>Type <a name="type"></a>

```cpp
Type Type() const;
```

### <a name="return-value"></a>Valeur de retour

Code indiquant l’outil qui a été appelé.

## <a name="workingdirectory"></a><a name="working-directory"></a> WorkingDirectory

```cpp
const wchar_t* WorkingDirectory() const;
```

### <a name="return-value"></a>Valeur de retour

Chemin d’accès absolu au répertoire dans lequel l’outil a été appelé.

::: moniker-end
