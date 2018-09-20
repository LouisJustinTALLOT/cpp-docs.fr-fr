---
title: WeakReference::Resolve, méthode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::WeakReference::Resolve
dev_langs:
- C++
helpviewer_keywords:
- Resolve method
ms.assetid: fc65a4b7-48a0-4d64-a793-37f566fdd8e7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 1e0873b366c84e89b23ddbaa6c64f6b484f921e0
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46446333"
---
# <a name="weakreferenceresolve-method"></a>WeakReference::Resolve, méthode

Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.

## <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD(Resolve)  
   (REFIID riid,
   _Deref_out_opt_ IInspectable **ppvObject
);
```

### <a name="parameters"></a>Paramètres

*riid*<br/>
ID d’interface.

*ppvObject*<br/>
Lorsque cette opération se termine, une copie de la référence forte actuelle si le nombre de référence forte est différente de zéro.

## <a name="return-value"></a>Valeur de retour

- S_OK si cette opération réussit et le nombre de référence forte est égal à zéro. Le *ppvObject* paramètre est défini sur **nullptr**.

- S_OK si cette opération réussit et le nombre de référence forte est différent de zéro. Le *ppvObject* paramètre est défini sur la référence forte.

- Sinon, un HRESULT qui indique la raison pour laquelle cette opération a échoué.

## <a name="remarks"></a>Notes

Définit le pointeur spécifié à la valeur actuelle de la référence forte si le nombre de référence forte est différente de zéro.

## <a name="requirements"></a>Configuration requise

**En-tête :** implements.h

**Namespace :** Microsoft::WRL::Details

## <a name="see-also"></a>Voir aussi

[WeakReference, classe1](../windows/weakreference-class1.md)<br/>
[Microsoft::WRL::Details, espace de noms](../windows/microsoft-wrl-details-namespace.md)