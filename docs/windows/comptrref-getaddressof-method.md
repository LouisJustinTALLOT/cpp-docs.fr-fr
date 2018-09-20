---
title: Comptrref::getaddressof, méthode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::Details::ComPtrRef::GetAddressOf
dev_langs:
- C++
helpviewer_keywords:
- GetAddressOf method
ms.assetid: 797df323-a2fa-412b-ab60-32cce3721096
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a0f35bbe2bdc0d0c8d3500e6b157da542458b1fe
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46421013"
---
# <a name="comptrrefgetaddressof-method"></a>ComPtrRef::GetAddressOf, méthode

Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.

## <a name="syntax"></a>Syntaxe

```cpp
InterfaceType* const * GetAddressOf() const;
```

## <a name="return-value"></a>Valeur de retour

Adresse d’un pointeur vers l’interface représentée par l’actuel **ComPtrRef** objet.

## <a name="remarks"></a>Notes

Récupère l’adresse d’un pointeur vers l’interface représentée par l’actuel **ComPtrRef** objet.

## <a name="requirements"></a>Configuration requise

**En-tête :** client.h

**Namespace :** Microsoft::WRL::Details

## <a name="see-also"></a>Voir aussi

[ComPtrRef, classe](../windows/comptrref-class.md)<br/>
[Microsoft::WRL::Details, espace de noms](../windows/microsoft-wrl-details-namespace.md)