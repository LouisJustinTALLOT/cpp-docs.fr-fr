---
title: InjecterEvent
description: La référence de fonction CMD Build Insights SDK InjectEvent.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- InjectEvent
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: c82aad5923eff60e5c72ceccaa39aa136f942665
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324040"
---
# <a name="injectevent"></a>InjecterEvent

::: moniker range="<=vs-2015"

Le SDK Build Insights est compatible avec Visual Studio 2017 et plus. Pour voir la documentation de ces versions, définissez le contrôle du sélecteur Visual Studio **Version** pour cet article à Visual Studio 2017 ou Visual Studio 2019. On le trouve en haut de la table des contenus sur cette page.

::: moniker-end
::: moniker range=">=vs-2017"

La `InjectEvent` fonction est appelée dans un relogger implémentant l’interface [IRelogger.](../other-types/irelogger-class.md) Il est utilisé pour écrire un événement Event Tracing for Windows (ETW) dans le fichier trace de sortie d’une session de relogging.

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
Un pointeur à la session de relogging. Une session de reloglogging est fournie `IRelogger` aux reloggers qui implémentent l’interface. Pour plus d’informations, voir [IRelogger](../other-types/irelogger-class.md).

*providerId*\
Un event Tracing for Windows (ETW) fournisseur GUID en vertu de laquelle l’événement ETW est relogged.

*Eventdescriptor*\
Le descripteur d’événements ETW pour l’événement ETW qui est relogged.

*Processid*\
L’identifiant de processus (PID) pour l’événement ETW qui est relogged.

*threadId*\
L’identifiant de thread (TID) pour l’événement ETW qui est relogged.

*processeurIndex*\
L’indice de processeur pour l’événement ETW qui est relogged.

*Timestamp*\
L’ampoule pour l’événement ETW qui est relogged.

*Données*\
Un pointeur sur les données qui devraient être incluses dans l’événement ETW relogged.

*Bytecount*\
La taille des données, dans les octets, indiquée par *les données*.

## <a name="remarks"></a>Notes

Pour plus d’informations sur les concepts ETW, tels que *le fournisseur GUID* et *le descripteur d’événements*, voir la [documentation ETW](/windows/win32/etw/about-event-tracing). Pour plus de détails sur la façon de commencer une session de relogging avec le SDK Build Insights, voir [Relog](relog.md).

::: moniker-end
