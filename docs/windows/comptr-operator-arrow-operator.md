---
title: ComPtr::operator -&gt; opérateur | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::ComPtr::operator->
dev_langs:
- C++
helpviewer_keywords:
- operator-> operator
ms.assetid: 7b7faefd-d1e4-4f31-a77d-17a42e0d6b6a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 417fd11017f9f70ee8cc247898e23741488ae5e7
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42599986"
---
# <a name="comptroperator-gt-operator"></a>ComPtr::operator -&gt; opérateur

Récupère un pointeur vers le type spécifié par le paramètre de modèle actuel.

## <a name="syntax"></a>Syntaxe

```cpp
WRL_NOTHROW Microsoft::WRL::Details::RemoveIUnknown<InterfaceType>* operator->() const;
```

## <a name="return-value"></a>Valeur de retour

Pointeur vers le type spécifié par le nom de type de modèle actuel.

## <a name="remarks"></a>Notes

Cette fonction d’assistance supprime provoquée par l’utilisation de la macro STDMETHOD une surcharge inutile. Cette fonction effectue `IUnknown` types **privé** au lieu de **virtuel**.

## <a name="requirements"></a>Configuration requise

**En-tête :** client.h

**Espace de noms :** Microsoft::WRL

## <a name="see-also"></a>Voir aussi

[ComPtr, classe](../windows/comptr-class.md)