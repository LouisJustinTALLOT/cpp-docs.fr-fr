---
title: Weakref::CopyTo, méthode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::WeakRef::CopyTo
dev_langs:
- C++
helpviewer_keywords:
- CopyTo method
ms.assetid: f83de6da-b3d4-41a6-9845-cd725ecf3b75
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 791e9040d9e35c7dfb657cca38e26c01e86c86c4
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42594419"
---
# <a name="weakrefcopyto-method"></a>WeakRef::CopyTo, méthode

Assigne un pointeur vers une interface, si disponible, à la variable pointeur spécifiée.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT CopyTo(
   REFIID riid,
   _Deref_out_ IInspectable** ptr
);

template<typename U>
HRESULT CopyTo(
   _Deref_out_ U** ptr
);

HRESULT CopyTo(
   _Deref_out_ IWeakReference** ptr
);
```

### <a name="parameters"></a>Paramètres

*U*  
Pointeur un `IInspectable` interface. Une erreur est générée si *U* n’est pas dérivé `IInspectable`.

*riid*  
ID d’interface. Une erreur est générée si *riid* n’est pas dérivé `IWeakReference`.

*ptr*  
Un pointeur doublement indirect vers `IInspectable` ou `IWeakReference`.

## <a name="return-value"></a>Valeur de retour

S_OK en cas de succès. Sinon, valeur HRESULT qui décrit l’erreur. Pour plus d’informations, consultez **Notes**.

## <a name="remarks"></a>Notes

La valeur de retour S_OK signifie que cette opération a réussi, mais elle n’indique pas si la référence faible a été résolue en une référence forte. Ce paramètre de test si S_OK est retourné, *p* est un nom fort référence ; autrement dit, le paramètre *p* n’est pas égal à **nullptr**.

À compter dans le SDK Windows 10, cette méthode n’affecte pas la **WeakRef** l’instance à **nullptr** si la référence faible n’a pas pu être obtenue, vous devez donc éviter la vérification de code qui vérifie si weakref est pour des erreurs **nullptr**. Au lieu de cela, vérifiez *ptr* pour **nullptr**.

## <a name="requirements"></a>Configuration requise

**En-tête :** client.h

**Espace de noms :** Microsoft::WRL

## <a name="see-also"></a>Voir aussi

[WeakRef, classe](../windows/weakref-class.md)