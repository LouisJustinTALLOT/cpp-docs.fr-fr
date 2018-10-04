---
title: Runtimeclassbaset, Structure | Microsoft Docs
ms.custom: ''
ms.date: 10/03/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::RuntimeClassBaseT
- implements/Microsoft::WRL::Details::RuntimeClassBaseT::AsIID
- implements/Microsoft::WRL::Details::RuntimeClassBaseT::GetImplementedIIDS
dev_langs:
- C++
helpviewer_keywords:
- Microsoft::WRL::Details::RuntimeClassBaseT structure
- Microsoft::WRL::Details::RuntimeClassBaseT::AsIID method
- Microsoft::WRL::Details::RuntimeClassBaseT::GetImplementedIIDS method
ms.assetid: a62775fb-3359-4f45-9ff1-c07fa8da464b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9c46e89dc11f4c6fe216cfd61c3222a9c52d9e45
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48789135"
---
# <a name="runtimeclassbaset-structure"></a>RuntimeClassBaseT, structure

Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.

## <a name="syntax"></a>Syntaxe

```cpp
template <unsigned int RuntimeClassTypeT>
friend struct Details::RuntimeClassBaseT;
```

### <a name="parameters"></a>Paramètres

*RuntimeClassTypeT*<br/>
Un champ d’indicateurs qui spécifie un ou plusieurs [RuntimeClassType](../windows/runtimeclasstype-enumeration.md) énumérateurs.

## <a name="remarks"></a>Notes

Fournit des méthodes d’assistance pour `QueryInterface` opérations et l’obtention des ID d’interface.

## <a name="members"></a>Membres

### <a name="protected-methods"></a>Méthodes protégées

Nom                                                         | Description
------------------------------------------------------------ | -----------------------------------------------------------------------------
[RuntimeClassBaseT::AsIID](#asiid)                           | Récupère un pointeur vers l’ID de l’interface spécifiée.
[RuntimeClassBaseT::GetImplementedIIDS](#getimplementediids) | Récupère un tableau d’ID qui sont implémentées par un type spécifié d’interface.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`RuntimeClassBaseT`

## <a name="requirements"></a>Configuration requise

**En-tête :** implements.h

**Namespace :** Microsoft::WRL::Details

## <a name="asiid"></a>RuntimeClassBaseT::AsIID

Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.

```cpp
template<typename T>
__forceinline static HRESULT AsIID(
   _In_ T* implements,
   REFIID riid,
   _Deref_out_ void **ppvObject
);
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Un type qui implémente l’ID d’interface spécifié par le paramètre *riid*.

*Implémente*<br/>
Une variable du type spécifié par le paramètre de modèle *T*.

*riid*<br/>
L’ID d’interface à récupérer.

*ppvObject*<br/>
Si cette opération réussite, un pointeur-à-un-pointeur vers l’interface spécifiée par le paramètre *riid*.

### <a name="return-value"></a>Valeur de retour

S_OK en cas de réussite ; Sinon, une valeur HRESULT qui décrit l’erreur.

### <a name="remarks"></a>Notes

Récupère un pointeur vers l’ID de l’interface spécifiée.

## <a name="getimplementediids"></a>RuntimeClassBaseT::GetImplementedIIDS

Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.

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

### <a name="return-value"></a>Valeur de retour

S_OK en cas de réussite ; Sinon, une valeur HRESULT qui décrit l’erreur.

### <a name="remarks"></a>Notes

Récupère un tableau d’ID qui sont implémentées par un type spécifié d’interface.
