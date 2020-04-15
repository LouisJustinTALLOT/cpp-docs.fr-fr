---
title: structure EVENT_DATA
description: La référence de structure de construction SDK EVENT_DATA de CMD Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- EVENT_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 8ce396febe278c5e7c34fe170939c9522913f92a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325596"
---
# <a name="event_data-structure"></a>structure EVENT_DATA

::: moniker range="<=vs-2015"

Le SDK Build Insights est compatible avec Visual Studio 2017 et plus. Pour voir la documentation de ces versions, définissez le contrôle du sélecteur Visual Studio **Version** pour cet article à Visual Studio 2017 ou Visual Studio 2019. On le trouve en haut de la table des contenus sur cette page.

::: moniker-end
::: moniker range=">=vs-2017"

La `EVENT_DATA` structure décrit un événement reçu d’une séance d’analyse ou de relogging. Ces sessions sont commencées par appeler les fonctions [Analyze](../functions/analyze.md), [AnalyzeA](../functions/analyze-a.md), [AnalyzeW](../functions/analyze-w.md), [Relog](../functions/relog.md) [, RelogA](../functions/relog-a.md), ou [RelogW.](../functions/relog-w.md)

## <a name="syntax"></a>Syntaxe

```cpp
typedef struct EVENT_DATA_TAG
{
    unsigned short          EventId;
    unsigned long long      EventInstanceId;

    long long               TickFrequency;
    long long               StartTimestamp;
    long long               StopTimestamp;
    long long               ExclusiveDurationTicks;
    long long               CPUTicks;
    long long               ExclusiveCPUTicks;
    long long               WallClockTimeResponsibilityTicks;
    long long               ExclusiveWallClockTimeResponsibilityTicks;

    const void*             Data;

    unsigned long           ProcessId;
    unsigned long           ThreadId;
    unsigned short          ProcessorIndex;

    const char*             EventName;
    const wchar_t*          EventWideName;

} EVENT_DATA;
```

## <a name="members"></a>Membres

|  |  |
|--|--|
| `EventId` | Un numéro qui identifie l’événement. Pour une liste d’identifiants d’événements, voir [EVENT_ID](event-id-enum.md). |
| `EventInstanceId` | Un nombre qui identifie de façon unique l’événement actuel à l’intérieur d’une trace. Cette valeur ne change pas lors de l’analyse ou de la réinstruisation de la même trace plusieurs fois. Utilisez ce champ pour identifier le même événement dans plusieurs analyses ou relogging passes sur la même trace. |
| `TickFrequency` | Le nombre de tiques par seconde à utiliser lors de l’évaluation d’une durée mesurée en tiques. |
| `StartTimestamp` | Lorsque l’événement est une *activité,* ce champ est réglé à une valeur de tique capturée au moment où l’activité a commencé. Si cet événement est un *événement simple,* ce champ est réglé à une valeur de tique capturée au moment de l’événement s’est produit. |
| `StopTimestamp` | Lorsque l’événement est une *activité,* ce champ est réglé à une valeur de tique capturée au moment où l’activité s’est arrêtée. Si l’événement d’arrêt n’a pas encore été reçu pour cette activité, ce champ est réglé à zéro. Si cet événement est un *événement simple,* ce champ est réglé à zéro. |
| `ExclusiveDurationTicks` | Si cet événement est une *activité,* ce champ est réglé sur le nombre de tiques qui se sont produites directement dans cette activité. Le nombre de tiques qui se sont produites dans une activité enfantine est exclu. Ce champ est réglé à zéro pour *Simple Events*. |
| `CPUTicks` | Si cet événement est une *activité,* ce champ est réglé sur le nombre de tiques CPU qui se sont produites au cours de cette activité. Une tique CPU est différente d’une tique régulière. Les tiques CPU ne sont comptées que lorsque le processeur exécute du code dans une activité. Les tiques CPU ne sont pas comptées lorsque le fil associé à l’activité dort. Ce champ est réglé à zéro pour *Simple Events*. |
| `ExclusiveCPUTicks` | Ce champ a le `CPUTicks`même sens que , sauf qu’il n’inclut pas les tiques CPU qui ont eu lieu dans les activités des enfants. Ce champ est réglé à zéro pour *Simple Events*. |
| `WallClockTimeResponsibilityTicks` | Si cet événement est une *activité,* ce champ est réglé sur un nombre de tiques qui représente la contribution de cette activité à l’heure globale de l’horloge murale. Une tique de responsabilité temporelle de l’horloge murale est différente d’une tique régulière. Les tiques de temps de l’horloge de mur tiennent compte du parallélisme entre les activités. Par exemple, deux activités parallèles peuvent avoir une durée de 50 tiques et le même temps de départ et d’arrêt. Dans ce cas, les deux seront attribués une responsabilité de temps de l’horloge murale de 25 tiques. Ce champ est réglé à zéro pour *Simple Events*. |
| `ExclusiveWallClockTimeResponsibilityTicks` | Ce domaine a le `WallClockTimeResponsibilityTicks`même sens que, sauf qu’il n’inclut pas les tiques de responsabilité de temps de l’horloge de mur des activités d’enfants. Ce champ est réglé à zéro pour *Simple Events*. |
| `Data` | Points vers des données supplémentaires stockées dans l’événement. Le type de données indiquées est `EventId` différent, selon le champ. |
| `ProcessId` | L’identifiant pour le processus dans lequel l’événement s’est produit. |
| `ThreadId` | L’identifiant pour le fil dans lequel l’événement s’est produit. |
| `ProcessorIndex` | Le numéro de processeur indexé à zéro sur lequel l’événement s’est produit. |
| `EventName` | Une chaîne ANSI contenant le nom `EventId`de l’entité identifiée par . |
| `EventWideName` | Une large chaîne contenant le nom `EventId`de l’entité identifiée par . |

## <a name="remarks"></a>Notes

De nombreux `EVENT_DATA` champs dans contiennent des nombres de tiques. Build Insights utilise le compteur de performances de Window comme source de tiques. Un nombre de tiques `TickFrequency` doit être utilisé avec le champ pour la convertir en une unité de temps appropriée comme les secondes. Voir l’exemple ci-dessous pour effectuer cette conversion. `EVENT_DATA`ne contient pas de champ pour le nombre régulier de tiques d’une activité. Pour obtenir cette valeur, soustrayez `StartTimestamp` de `StopTimestamp`. `EVENT_DATA`est une structure qui est destinée à être utilisée par les utilisateurs de C API. Pour les utilisateurs d’API, des cours comme [Event](../cpp-event-data-types/event.md) font automatiquement des conversions de temps.

La valeur `EVENT_DATA` `Data` du champ dépend de `EventId` la valeur de son champ. La valeur `Data` de est décrite dans le tableau ci-dessous. Certains identificateurs d’entité peuvent être absents du tableau ci-dessous. Dans ce cas, le `Data` `nullptr` champ est réglé à ou à zéro.

| Valeur `EventId` | Type pointé du doigt par`Data` |
|--|--|
| `EVENT_ID_BACK_END_PASS` | [CL_PASS_DATA](cl-pass-data-struct.md) |
| `EVENT_ID_COMMAND_LINE` | `const wchar_t` |
| `EVENT_ID_COMPILER` | [INVOCATION_DATA](invocation-data-struct.md) |
| `EVENT_ID_ENVIRONMENT_VARIABLE` | [NAME_VALUE_PAIR_DATA](name-value-pair-data-struct.md) |
| `EVENT_ID_EXECUTABLE_IMAGE_OUTPUT` | [FILE_DATA](file-data-struct.md) |
| `EVENT_ID_EXP_OUTPUT` | [FILE_DATA](file-data-struct.md) |
| `EVENT_ID_FILE_INPUT` | [FILE_DATA](file-data-struct.md) |
| `EVENT_ID_FORCE_INLINE` | [FUNCTION_FORCE_INLINEE_DATA](function-force-inlinee-data-struct.md) |
| `EVENT_ID_FRONT_END_FILE` | [FRONT_END_FILE_DATA](front-end-file-data-struct.md) |
| `EVENT_ID_FRONT_END_PASS` | [CL_PASS_DATA](cl-pass-data-struct.md) |
| `EVENT_ID_FUNCTION` | [FUNCTION_DATA](function-data-struct.md) |
| `EVENT_ID_IMP_LIB_OUTPUT` | [FILE_DATA](file-data-struct.md) |
| `EVENT_ID_LIB_OUTPUT` | [FILE_DATA](file-data-struct.md) |
| `EVENT_ID_LINKER` | [INVOCATION_DATA](invocation-data-struct.md) |
| `EVENT_ID_OBJ_OUTPUT` | [FILE_DATA](file-data-struct.md) |
| `EVENT_ID_SYMBOL_NAME` | [SYMBOL_NAME_DATA](symbol-name-data-struct.md) |
| `EVENT_ID_TEMPLATE_INSTANTIATION` | [TEMPLATE_INSTANTIATION_DATA](template-instantiation-data-struct.md) |

## <a name="tick-conversion-example"></a>Exemple de conversion de tiques

```cpp
//
// We have the elapsed number of ticks, along with the
// number of ticks per second. We use these values
// to convert to the number of elapsed microseconds.
// To guard against loss-of-precision, we convert
// to microseconds *before* dividing by ticks-per-second.
//

long long ConvertDurationToMicroseconds(const sruct EVENT_DATA& eventData)
{
    long long duration = eventData.StopTimestamp - eventData.StartTimestamp;
    long long duration *= 1000000;
    return duration / eventData.TickFrequency;
}
```

::: moniker-end
