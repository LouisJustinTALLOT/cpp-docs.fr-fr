---
title: InjectEvent
description: Référence de la fonction InjectEvent du kit de développement logiciel (SDK) C++ Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- InjectEvent
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: b4d85f17a6d553d9dffa727824e6d4de94518645
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92922843"
---
# <a name="injectevent"></a>InjectEvent

::: moniker range="<=msvc-140"

Le kit de développement logiciel (SDK) C++ Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de **version** de Visual Studio pour cet article sur visual studio 2017 ou visual studio 2019. Elle se trouve en haut de la table des matières sur cette page.

::: moniker-end
::: moniker range=">=msvc-150"

La `InjectEvent` fonction est appelée dans un journal qui implémente l’interface [IRelogger](../other-types/irelogger-class.md) . Il est utilisé pour écrire un événement Suivi d’v nements pour Windows (ETW) dans le fichier de trace de sortie d’une session de rejournalisation.

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
Pointeur vers la session de rejournalisation. Une session de rejournalisation est fournie aux rejournalisation qui implémentent l' `IRelogger` interface. Pour plus d’informations, consultez [IRelogger](../other-types/irelogger-class.md).

*providerId*\
GUID du fournisseur Suivi d’v nements pour Windows (ETW) sous lequel l’événement ETW est reenregistré.

*eventDescriptor*\
Descripteur d’événement ETW pour l’événement ETW qui est reenregistré.

*processId*\
Identificateur de processus (PID) de l’événement ETW qui est reenregistré.

*threadId*\
Identificateur de thread (TID) pour l’événement ETW qui est reenregistré.

*processorIndex*\
Index du processeur pour l’événement ETW qui est reenregistré.

*confirmé*\
Horodateur de l’événement ETW qui est reenregistré.

*métadonnée*\
Pointeur vers les données qui doivent être incluses dans l’événement ETW rejournalisé.

*byteCount*\
Taille des données, en octets, pointées par les *données* .

## <a name="remarks"></a>Notes

Pour plus d’informations sur les concepts ETW, tels que le *GUID du fournisseur* et le *descripteur d’événement* , consultez la [documentation ETW](/windows/win32/etw/about-event-tracing). Pour plus d’informations sur le démarrage d’une session de rejournalisation avec le kit de développement logiciel (SDK) Build Insights C++, consultez [relog](relog.md).

::: moniker-end
