---
title: Mutex::mutex, constructeur | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Mutex::Mutex
dev_langs:
- C++
helpviewer_keywords:
- Mutex, constructor
ms.assetid: 504afcdc-775a-4c98-a06f-4fb4663eba3f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 62a1fc796188c38dfbd3aff004eba15b7e30ea89
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42600503"
---
# <a name="mutexmutex-constructor"></a>Mutex::Mutex, constructeur

Initialise une nouvelle instance de la **Mutex** classe.

## <a name="syntax"></a>Syntaxe

```cpp
explicit Mutex(
   HANDLE h
);

Mutex(
   _Inout_ Mutex&& h
);
```

### <a name="parameters"></a>Paramètres

*h*  
Un handle ou une référence rvalue à un handle, pour un **Mutex** objet.

## <a name="remarks"></a>Notes

Le premier constructeur initialise un **Mutex** objet à partir du handle spécifié. Le deuxième constructeur initialise un **Mutex** objet à partir du handle spécifié, puis passe la propriété du mutex actuel **Mutex** objet.

## <a name="requirements"></a>Configuration requise

**En-tête :** corewrappers.h

**Namespace :** Microsoft::WRL::Wrappers

## <a name="see-also"></a>Voir aussi
[Mutex (classe)](../windows/mutex-class1.md)