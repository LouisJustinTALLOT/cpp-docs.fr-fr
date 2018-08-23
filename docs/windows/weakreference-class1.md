---
title: WeakReference, Classe1 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::WeakReference
dev_langs:
- C++
helpviewer_keywords:
- WeakReference class
ms.assetid: 3f4c956b-dbbd-49b1-8cfa-9509a9956c97
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a9b7270a03192a6fcf53f0c2ecfd1af07a216243
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42595529"
---
# <a name="weakreference-class1"></a>WeakReference, Classe1

Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.

## <a name="syntax"></a>Syntaxe

```cpp
class WeakReference;
```

## <a name="remarks"></a>Notes

Représente un *référence faible* qui peut être utilisé avec le Windows Runtime ou le COM classique. Une référence faible représente un objet qui peut être accessible ou non.

Un **WeakReference** objet conserve un *référence forte*, qui est un pointeur vers un objet et un *décompte de références fort*, qui est le nombre de copies de la forte référence qui ont été distribuées par le `Resolve()` (méthode). Bien que le nombre de référence forte est différente de zéro, la référence forte est valide et l’objet est accessible. Lorsque le nombre de référence forte devient égal à zéro, la référence forte n’est pas valide et l’objet n’est pas accessible.

Un **WeakReference** objet est généralement utilisé pour représenter un objet dont l’existence est contrôlée par un thread externe ou une application. Par exemple, construisez un **WeakReference** objet à partir d’une référence à un objet fichier. Pendant que le fichier est ouvert, la référence forte est valide, mais si le fichier est fermé, la référence forte devient non valide.

Le **WeakReference** méthodes sont thread-safe.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[WeakReference::WeakReference, constructeur](../windows/weakreference-weakreference-constructor.md)|Initialise une nouvelle instance de la **WeakReference** classe.|
|[WeakReference::~WeakReference, destructeur](../windows/weakreference-tilde-weakreference-destructor.md)|Annule l’initialisation (détruit) l’instance actuelle de la **WeakReference** classe.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[WeakReference::DecrementStrongReference, méthode](../windows/weakreference-decrementstrongreference-method.md)|Décrémente le fort décompte de références actuel **WeakReference** objet.|
|[WeakReference::IncrementStrongReference, méthode](../windows/weakreference-incrementstrongreference-method.md)|Incrémente le nombre de référence forte d’actuel **WeakReference** objet.|
|[WeakReference::Resolve, méthode](../windows/weakreference-resolve-method.md)|Définit le pointeur spécifié à la valeur actuelle de la référence forte si le nombre de référence forte est différente de zéro.|
|[WeakReference::SetUnknown, méthode](../windows/weakreference-setunknown-method.md)|Définit la référence forte d’actuel **WeakReference** objet au pointeur d’interface spécifié.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`WeakReference`

## <a name="requirements"></a>Configuration requise

**En-tête :** implements.h

**Namespace :** Microsoft::WRL::Details

## <a name="see-also"></a>Voir aussi

[Microsoft::WRL::Details, espace de noms](../windows/microsoft-wrl-details-namespace.md)