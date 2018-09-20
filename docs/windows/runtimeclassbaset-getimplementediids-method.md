---
title: Runtimeclassbaset::getimplementediids, méthode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::RuntimeClassBaseT::GetImplementedIIDS
dev_langs:
- C++
helpviewer_keywords:
- GetImplementedIIDS method
ms.assetid: adae54da-521d-4add-87f5-242fbd85f33b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 15db0be600d61992d48c2f1cf90d6543057b5090
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46376070"
---
# <a name="runtimeclassbasetgetimplementediids-method"></a>RuntimeClassBaseT::GetImplementedIIDS, méthode

Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.

## <a name="syntax"></a>Syntaxe

```cpp
template<typename T>
__forceinline static HRESULT GetImplementedIIDS(
   _In_ T* implements,
   _Out_ ULONG *iidCount,
   _Deref_out_ _Deref_post_cap_(*iidCount) IID **iids
);
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Le type de la *implémente* paramètre.

*Implémente*<br/>
Pointeur vers le type spécifié par le paramètre *T*.

*iidCount*<br/>
Le nombre maximal d’ID d’interface à récupérer.

*IID*<br/>
Si cette opération termine avec succès, un tableau de l’ID implémentées par type d’interface *T*.

## <a name="return-value"></a>Valeur de retour

S_OK en cas de réussite ; Sinon, une valeur HRESULT qui décrit l’erreur.

## <a name="remarks"></a>Notes

Récupère un tableau d’ID qui sont implémentées par un type spécifié d’interface.

## <a name="requirements"></a>Configuration requise

**En-tête :** implements.h

**Namespace :** Microsoft::WRL::Details

## <a name="see-also"></a>Voir aussi

[RuntimeClassBaseT, structure](../windows/runtimeclassbaset-structure.md)