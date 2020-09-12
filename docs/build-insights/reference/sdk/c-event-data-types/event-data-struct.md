---
title: Structure EVENT_DATA
description: Le kit de développement logiciel (SDK) C++ Build Insights EVENT_DATA référence de la structure.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- EVENT_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 468fc30d337e5cfc5ab90f7558904fc90588c3df
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2020
ms.locfileid: "90041820"
---
# <a name="event_data-structure"></a>Structure EVENT_DATA

::: moniker range="<=vs-2015"

Le kit de développement logiciel (SDK) C++ Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de **version** de Visual Studio pour cet article sur visual studio 2017 ou visual studio 2019. Elle se trouve en haut de la table des matières sur cette page.

::: moniker-end
::: moniker range=">=vs-2017"

La `EVENT_DATA` structure décrit un événement reçu à partir d’une session d’analyse ou de rejournalisation. Ces sessions sont démarrées en appelant les fonctions [analyze](../functions/analyze.md), [Analysis](../functions/analyze-a.md), [AnalyzeW](../functions/analyze-w.md), [relog](../functions/relog.md), [RelogA](../functions/relog-a.md)ou [RelogW](../functions/relog-w.md) .

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

| Nom | Description |
|--|--|
| `EventId` | Nombre qui identifie l’événement. Pour obtenir la liste des identificateurs d’événements, consultez [event_id](event-id-enum.md). |
| `EventInstanceId` | Numéro qui identifie de façon unique l’événement actuel à l’intérieur d’une trace. Cette valeur ne change pas lors de l’analyse ou de la rejournalisation de la même trace plusieurs fois. Utilisez ce champ pour identifier le même événement dans plusieurs analyses ou rejournalisation sur la même trace. |
| `TickFrequency` | Nombre de graduations par seconde à utiliser lors de l’évaluation d’une durée mesurée en graduations. |
| `StartTimestamp` | Lorsque l’événement est une *activité*, ce champ est défini sur une valeur de graduation capturée au moment du démarrage de l’activité. Si cet événement est un *événement simple*, ce champ est défini sur une valeur de graduation capturée au moment où l’événement s’est produit. |
| `StopTimestamp` | Lorsque l’événement est une *activité*, ce champ est défini sur une valeur de graduation capturée au moment de l’arrêt de l’activité. Si l’événement Stop n’a pas encore été reçu pour cette activité, ce champ a la valeur zéro. Si cet événement est un *événement simple*, ce champ a la valeur zéro. |
| `ExclusiveDurationTicks` | Si cet événement est une *activité*, ce champ est défini sur le nombre de graduations qui se sont produites directement dans cette activité. Le nombre de cycles qui se sont produits dans une activité enfant est exclu. Ce champ a la valeur zéro pour les *événements simples*. |
| `CPUTicks` | Si cet événement est une *activité*, ce champ est défini sur le nombre de cycles de processeur qui se sont produits pendant cette activité. Un battement de l’UC est différent d’un battement normal. Les cycles de l’UC sont comptabilisés uniquement lorsque le processeur exécute du code dans une activité. Les cycles de l’UC ne sont pas comptabilisés lorsque le thread associé à l’activité est en veille. Ce champ a la valeur zéro pour les *événements simples*. |
| `ExclusiveCPUTicks` | Ce champ a la même signification que `CPUTicks` , sauf qu’il n’inclut pas les cycles de processeur qui se sont produits dans les activités enfants. Ce champ a la valeur zéro pour les *événements simples*. |
| `WallClockTimeResponsibilityTicks` | Si cet événement est une *activité*, ce champ est défini sur un nombre de cycles qui représente la contribution de cette activité à l’heure d’horloge globale. Un cycle de responsabilité de l’heure du mur est différent d’un battement normal. La responsabilité de l’horloge du mur prend en compte le parallélisme entre les activités. Par exemple, deux activités parallèles peuvent avoir une durée de 50 cycles et la même heure de début et de fin. Dans ce cas, les deux sont affectées à la responsabilité du temps horloge de 25 graduations. Ce champ a la valeur zéro pour les *événements simples*. |
| `ExclusiveWallClockTimeResponsibilityTicks` | Ce champ a la même signification que `WallClockTimeResponsibilityTicks` , à la différence près qu’il n’inclut pas les graduations de la responsabilité de l’heure du mur des activités enfants. Ce champ a la valeur zéro pour les *événements simples*. |
| `Data` | Pointe vers des données supplémentaires stockées dans l’événement. Le type de données pointé est différent selon le `EventId` champ. |
| `ProcessId` | Identificateur du processus dans lequel l’événement s’est produit. |
| `ThreadId` | Identificateur du thread dans lequel l’événement s’est produit. |
| `ProcessorIndex` | Numéro de processeur indexé à zéro sur lequel l’événement s’est produit. |
| `EventName` | Chaîne ANSI contenant le nom de l’entité identifiée par `EventId` . |
| `EventWideName` | Chaîne étendue contenant le nom de l’entité identifiée par `EventId` . |

## <a name="remarks"></a>Remarques

De nombreux champs dans `EVENT_DATA` contiennent des nombres de battements. C++ Build Insights utilise le compteur de performance de la fenêtre comme source des battements. Un nombre de cycles doit être utilisé avec le `TickFrequency` champ pour le convertir en une unité de temps appropriée, telle que des secondes. Consultez l’exemple ci-dessous pour effectuer cette conversion. `EVENT_DATA` ne contient pas de champ pour le nombre de cycles réguliers d’une activité. Pour obtenir cette valeur, soustraire `StartTimestamp` de `StopTimestamp` . `EVENT_DATA` est une structure destinée à être utilisée par les utilisateurs de l’API C. Pour les utilisateurs de l’API C++, les classes comme [Event](../cpp-event-data-types/event.md) effectuent automatiquement des conversions temporelles.

La valeur du `EVENT_DATA` `Data` champ dépend de la valeur de son `EventId` champ. La valeur de `Data` est décrite dans le tableau ci-dessous. Certains identificateurs d’entité peuvent manquer dans le tableau ci-dessous. Dans ce cas, le `Data` champ est défini sur **`nullptr`** ou sur zéro.

| Valeur `EventId` | Type vers lequel pointe `Data` |
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

## <a name="tick-conversion-example"></a>Exemple de conversion Tick

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
