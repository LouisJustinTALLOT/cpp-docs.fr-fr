---
title: Comptrref::releaseandgetaddressof, méthode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::Details::ComPtrRef::ReleaseAndGetAddressOf
dev_langs:
- C++
helpviewer_keywords:
- ReleaseAndGetAddressOf method
ms.assetid: 004aac42-e135-41ce-8d1d-4c5969d55004
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 48c9c748b80bb7900d57e1e0c0aff68d8e1f4ec1
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46424961"
---
# <a name="comptrrefreleaseandgetaddressof-method"></a>ComPtrRef::ReleaseAndGetAddressOf, méthode

Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.

## <a name="syntax"></a>Syntaxe

```cpp
InterfaceType** ReleaseAndGetAddressOf();
```

## <a name="return-value"></a>Valeur de retour

Pointeur vers l’interface qui a été représenté par supprimés **ComPtrRef** objet.

## <a name="remarks"></a>Notes

Supprime l’actuel **ComPtrRef** de l’objet et retourne un pointeur-à-un-pointeur vers l’interface qui a été représenté par le **ComPtrRef** objet.

## <a name="requirements"></a>Configuration requise

**En-tête :** client.h

**Namespace :** Microsoft::WRL::Details

## <a name="see-also"></a>Voir aussi

[ComPtrRef, classe](../windows/comptrref-class.md)<br/>
[Microsoft::WRL::Details, espace de noms](../windows/microsoft-wrl-details-namespace.md)