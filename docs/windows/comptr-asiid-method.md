---
title: Comptr::asiid, méthode | Microsoft Docs
ms.custom: ''
ms.date: 07/11/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::ComPtr::AsIID
dev_langs:
- C++
helpviewer_keywords:
- AsIID method
ms.assetid: d5a3cdb2-796d-4410-966a-847c0e8fb226
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d79707eaa3e5e93ab5c05e120d1556ee86168af2
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42607296"
---
# <a name="comptrasiid-method"></a>ComPtr::AsIID, méthode

Retourne un **ComPtr** objet qui représente l’interface identifiée par l’ID de l’interface spécifiée.

## <a name="syntax"></a>Syntaxe

```cpp
WRL_NOTHROW HRESULT AsIID(
   REFIID riid,
   _Out_ ComPtr<IUnknown>* p
) const;
```

### <a name="parameters"></a>Paramètres

*riid*  
ID d’interface.

*p*  
Si l’objet a une interface dont l’ID est égal à *riid*, un pointeur doublement indirect vers l’interface spécifiée par le *riid* paramètre ; sinon, un pointeur vers `IUnknown`.

## <a name="return-value"></a>Valeur de retour

S_OK si l'opération réussit. Sinon, une valeur HRESULT indique l'erreur.

## <a name="requirements"></a>Configuration requise

**En-tête :** client.h

**Espace de noms :** Microsoft::WRL

## <a name="see-also"></a>Voir aussi

[ComPtr, classe](../windows/comptr-class.md)