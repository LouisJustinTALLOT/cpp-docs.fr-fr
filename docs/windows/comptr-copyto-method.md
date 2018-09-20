---
title: Comptr::CopyTo, méthode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::ComPtr::CopyTo
dev_langs:
- C++
helpviewer_keywords:
- CopyTo method
ms.assetid: 8801bc49-6db4-4393-a55f-a701ae3b8718
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c9b84cbcc970183222ed06752dc61b5672615868
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46405383"
---
# <a name="comptrcopyto-method"></a>ComPtr::CopyTo, méthode

Copie de l’interface actuelle ou spécifiée associée à cet **ComPtr** pour le pointeur spécifié.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT CopyTo(
   _Deref_out_ InterfaceType** ptr
);

HRESULT CopyTo(
   REFIID riid,
   _Deref_out_ void** ptr
) const;

template<typename U>
HRESULT CopyTo(
   _Deref_out_ U** ptr
) const;
```

### <a name="parameters"></a>Paramètres

*U*<br/>
Un nom de type.

*ptr*<br/>
Lorsque cette opération se termine, un pointeur vers l’interface demandée.

*riid*<br/>
ID d’interface.

## <a name="return-value"></a>Valeur de retour

S_OK en cas de réussite ; Sinon, un HRESULT qui indique la raison pour laquelle le caractère implicite `QueryInterface` échouée de l’opération.

## <a name="remarks"></a>Notes

La première fonction retourne une copie d’un pointeur vers l’interface associée à cet **ComPtr**. Cette fonction retourne toujours S_OK.

La deuxième fonction effectue une `QueryInterface` opération sur l’interface associée à cet **ComPtr** pour l’interface spécifiée par le *riid* paramètre.

La troisième fonction effectue une `QueryInterface` opération sur l’interface associée à cet **ComPtr** pour l’interface sous-jacente de la *U* paramètre.

## <a name="requirements"></a>Configuration requise

**En-tête :** client.h

**Espace de noms :** Microsoft::WRL

## <a name="see-also"></a>Voir aussi

[ComPtr, classe](../windows/comptr-class.md)