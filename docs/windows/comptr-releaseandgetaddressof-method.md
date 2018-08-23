---
title: Comptr::releaseandgetaddressof, méthode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::ComPtr::ReleaseAndGetAddressOf
dev_langs:
- C++
helpviewer_keywords:
- ReleaseAndGetAddressOf method
ms.assetid: 3751dcb4-d50e-432c-89e4-e736be34d434
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e3efdce7cde39431a8d6f097aace2ed2f5a66b4d
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42589945"
---
# <a name="comptrreleaseandgetaddressof-method"></a>ComPtr::ReleaseAndGetAddressOf, méthode

Libère l’interface associée à cet **ComPtr** , puis récupère l’adresse de la [ptr_](../windows/comptr-ptr-data-member.md) membre de données, qui contient un pointeur vers l’interface qui a été publiée.

## <a name="syntax"></a>Syntaxe

```cpp
T** ReleaseAndGetAddressOf();
```

## <a name="return-value"></a>Valeur de retour

L’adresse de la [ptr_](../windows/comptr-ptr-data-member.md) membre de données de ce **ComPtr**.

## <a name="requirements"></a>Configuration requise

**En-tête :** client.h

**Espace de noms :** Microsoft::WRL

## <a name="see-also"></a>Voir aussi

[ComPtr, classe](../windows/comptr-class.md)  
[ComPtr::ptr_, données de membre](../windows/comptr-ptr-data-member.md)