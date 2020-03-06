---
title: InjectEvent
description: Référence C++ de la fonction InjectEvent du kit de développement logiciel (SDK) Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- InjectEvent
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 7b53eb71cf7a2ae40d04dbc3f8b5829f2737aba4
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332844"
---
# <a name="injectevent"></a>InjectEvent

::: moniker range="<=vs-2015"

Le C++ Kit de développement logiciel (SDK) Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de version de Visual Studio pour cet article sur Visual Studio 2017 ou Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

La fonction `InjectEvent` est appelée dans un journal qui implémente l’interface [IRelogger](../other-types/irelogger-class.md) . Il est utilisé pour écrire un événement Suivi d’v nements pour Windows (ETW) dans le fichier de trace de sortie d’une session de rejournalisation.

## <a name="syntax"></a>Syntaxe

```cpp
void InjectEvent(
    const void* relogSession,
    LPCGUID providerId,
    PCEVENT_DESCRIPTOR eventDescriptor,
    unsigned long processId,
    unsigned long threadId,
    unsigned short processorIndex,
    long long timestamp,
    unsigned char* data,
    unsigned long byteCount);
```

### <a name="parameters"></a>Paramètres

*relogSession*\
Pointeur vers la session de rejournalisation. Une session de rejournalisation est fournie aux rejournalisation qui implémentent l’interface `IRelogger`. Pour plus d’informations, consultez [IRelogger](../other-types/irelogger-class.md).

*providerId*\
GUID du fournisseur Suivi d’v nements pour Windows (ETW) sous lequel l’événement ETW est reenregistré.

*eventDescriptor*\
Descripteur d’événement ETW pour l’événement ETW qui est reenregistré.

*ID* de l'\
Identificateur de processus (PID) de l’événement ETW qui est reenregistré.

\ *ThreadID*
Identificateur de thread (TID) pour l’événement ETW qui est reenregistré.

*processorIndex*\
Index du processeur pour l’événement ETW qui est reenregistré.

*horodateur*\
Horodateur de l’événement ETW qui est reenregistré.

\ de *données*
Pointeur vers les données qui doivent être incluses dans l’événement ETW rejournalisé.

\ *byteCount*
Taille des données, en octets, pointées par les *données*.

## <a name="remarks"></a>Notes

Pour plus d’informations sur les concepts ETW, tels que le *GUID du fournisseur* et le *descripteur d’événement*, consultez la [documentation ETW](/windows/win32/etw/about-event-tracing). Pour plus d’informations sur le démarrage d’une session de rejournalisation avec le C++ Kit de développement logiciel (SDK) Build Insights, consultez [relog](relog.md).

::: moniker-end
