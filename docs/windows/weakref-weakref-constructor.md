---
title: Weakref::weakref, constructeur | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::WeakRef::WeakRef
dev_langs:
- C++
helpviewer_keywords:
- WeakRef, constructor
ms.assetid: 589f87e0-8dcc-4e82-aab2-f2f66f1ec47c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d7c8bc81040ce8d4c1cea7497f9d1371fbb9d41f
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42611608"
---
# <a name="weakrefweakref-constructor"></a>WeakRef::WeakRef, constructeur

Initialise une nouvelle instance de la **WeakRef** classe.

## <a name="syntax"></a>Syntaxe

```cpp
WeakRef();
WeakRef(
   decltype(__nullptr)  
);

WeakRef(
   _In_opt_ IWeakReference* ptr
);

WeakRef(
   const ComPtr<IWeakReference>& ptr
);

WeakRef(
   const WeakRef& ptr
);

WeakRef(
   _Inout_ WeakRef&& ptr
);
```

### <a name="parameters"></a>Paramètres

*ptr*  
Un pointeur, une référence ou une référence rvalue à un objet existant qui initialise actuel **WeakRef** objet.

## <a name="remarks"></a>Notes

Le premier constructeur initialise vide **WeakRef** objet. Le deuxième constructeur initialise un **WeakRef** objet d’un pointeur vers le `IWeakReference` interface. Le troisième constructeur initialise un **WeakRef** objet à partir d’une référence à un `ComPtr<IWeakReference>` objet. Les quatrième et cinquième constructeurs initialisent un **WeakRef** objet à partir d’un autre **WeakRef** objet.

## <a name="requirements"></a>Configuration requise

**En-tête :** client.h

**Espace de noms :** Microsoft::WRL

## <a name="see-also"></a>Voir aussi

[WeakRef, classe](../windows/weakref-class.md)