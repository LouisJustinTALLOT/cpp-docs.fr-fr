---
title: EventSource::InvokeAll, méthode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::EventSource::InvokeAll
dev_langs:
- C++
helpviewer_keywords:
- InvokeAll method
ms.assetid: 1506618f-0421-4428-a4d0-4ea2b10a3bf6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 57450abdef0a6b25731405e092520ec5589972a1
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42613733"
---
# <a name="eventsourceinvokeall-method"></a>EventSource::InvokeAll, méthode

Appelle chaque gestionnaire d’événements associé actuel [EventSource](../windows/eventsource-class.md) avec les types d’arguments spécifiés et les arguments de l’objet.

## <a name="syntax"></a>Syntaxe

```cpp
void InvokeAll();
template <
   typename T0
>
void InvokeAll(
   T0arg0
);
template <
   typename T0,
   typename T1
>
void InvokeAll(
   T0arg0,
   T1arg1
);
template <
   typename T0,
   typename T1,
   typename T2
>
void InvokeAll(
   T0arg0,
   T1arg1,
   T2arg2
);
template <
   typename T0,
   typename T1,
   typename T2,
   typename T3
>
void InvokeAll(
   T0arg0,
   T1arg1,
   T2arg2,
   T3arg3
);
template <
   typename T0,
   typename T1,
   typename T2,
   typename T3,
   typename T4
>
void InvokeAll(
   T0arg0,
   T1arg1,
   T2arg2,
   T3arg3,
   T4arg4
);
template <
   typename T0,
   typename T1,
   typename T2,
   typename T3,
   typename T4,
   typename T5
>
void InvokeAll(
   T0arg0,
   T1arg1,
   T2arg2,
   T3arg3,
   T4arg4,
   T5arg5
);
template <
   typename T0,
   typename T1,
   typename T2,
   typename T3,
   typename T4,
   typename T5,
   typename T6
>
void InvokeAll(
   T0arg0,
   T1arg1,
   T2arg2,
   T3arg3,
   T4arg4,
   T5arg5,
   T6arg6
);
template <
   typename T0,
   typename T1,
   typename T2,
   typename T3,
   typename T4,
   typename T5,
   typename T6,
   typename T7
>
void InvokeAll(
   T0arg0,
   T1arg1,
   T2arg2,
   T3arg3,
   T4arg4,
   T5arg5,
   T6arg6,
   T7arg7
);
template <
   typename T0,
   typename T1,
   typename T2,
   typename T3,
   typename T4,
   typename T5,
   typename T6,
   typename T7,
   typename T8
>
void InvokeAll(
   T0arg0,
   T1arg1,
   T2arg2,
   T3arg3,
   T4arg4,
   T5arg5,
   T6arg6,
   T7arg7,
   T8arg8
);
template <
   typename T0,
   typename T1,
   typename T2,
   typename T3,
   typename T4,
   typename T5,
   typename T6,
   typename T7,
   typename T8,
   typename T9
>
void InvokeAll(
   T0arg0,
   T1arg1,
   T2arg2,
   T3arg3,
   T4arg4,
   T5arg5,
   T6arg6,
   T7arg7,
   T8arg8,
   T9arg9
);
```

### <a name="parameters"></a>Paramètres

*T0*  
Le type de l’argument de gestionnaire d’événements zeroth.

*T1*  
Le type du premier argument de gestionnaire d’événements.

*T2*  
Le type du deuxième argument de gestionnaire d’événements.

*T3*  
Le type du troisième argument de gestionnaire d’événements.

*T4*  
Le type du quatrième argument de gestionnaire d’événements.

*T5*  
Le type du cinquième argument de gestionnaire d’événements.

*T6*  
Le type du sixième argument de gestionnaire d’événements.

*T7*  
Le type du septième argument de gestionnaire d’événements.

*T8*  
Le type de l’argument de gestionnaire d’événements huitième.

*T9*  
Le type du neuvième argument de gestionnaire d’événements.

*arg0*  
L’argument Gestionnaire d’événement zeroth.

*arg1*  
Le premier argument de gestionnaire de l’événement.

*Arg2*  
Le deuxième argument de gestionnaire de l’événement.

*Arg3*  
Le troisième argument de gestionnaire de l’événement.

*Arg4*  
Le quatrième argument de gestionnaire de l’événement.

*Arg5*  
Le cinquième argument de gestionnaire de l’événement.

*Arg6*  
Sixième argument de gestionnaire d’événements.

*Arg7*  
Septième argument de gestionnaire d’événements.

*Arg8*  
Argument d’événement huitième gestionnaire.

*Arg9*  
Neuvième argument de gestionnaire d’événements.

## <a name="requirements"></a>Configuration requise

**En-tête :** event.h

**Espace de noms :** Microsoft::WRL

## <a name="see-also"></a>Voir aussi
[EventSource, classe](../windows/eventsource-class.md)