---
title: RuntimeClassBaseT, structure
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::RuntimeClassBaseT
- implements/Microsoft::WRL::Details::RuntimeClassBaseT::AsIID
- implements/Microsoft::WRL::Details::RuntimeClassBaseT::GetImplementedIIDS
helpviewer_keywords:
- Microsoft::WRL::Details::RuntimeClassBaseT structure
- Microsoft::WRL::Details::RuntimeClassBaseT::AsIID method
- Microsoft::WRL::Details::RuntimeClassBaseT::GetImplementedIIDS method
ms.assetid: a62775fb-3359-4f45-9ff1-c07fa8da464b
ms.openlocfilehash: 06a9f73e00d541b0e5bcbe20c57befe4a67c5132
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375721"
---
# <a name="runtimeclassbaset-structure"></a>RuntimeClassBaseT, structure

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

## <a name="syntax"></a>Syntaxe

```cpp
template <unsigned int RuntimeClassTypeT>
friend struct Details::RuntimeClassBaseT;
```

### <a name="parameters"></a>Paramètres

*RuntimeClassTypeT*<br/>
Un champ de drapeaux qui spécifie un ou plusieurs enumérateurs [RuntimeClassType.](runtimeclasstype-enumeration.md)

## <a name="remarks"></a>Notes

Fournit des méthodes `QueryInterface` d’aide pour les opérations et l’obtention d’interfaces ID.

## <a name="members"></a>Membres

### <a name="protected-methods"></a>Méthodes protégées

Nom                                                         | Description
------------------------------------------------------------ | -----------------------------------------------------------------------------
[RuntimeClassBaseT::AsIID](#asiid)                           | Récupère un pointeur sur l’id d’interface spécifié.
[RuntimeClassBaset::GetImplementedIIDS](#getimplementediids) | Récupère une gamme d’interfaces qui sont implémentées par un type spécifié.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`RuntimeClassBaseT`

## <a name="requirements"></a>Spécifications

**En-tête:** implements.h

**Espace nom:** Microsoft::WRL::Details

## <a name="runtimeclassbasetasiid"></a><a name="asiid"></a>RuntimeClassBaseT::AsIID

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

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
Un type qui implémente l’interface ID spécifiée par *paramètre riid*.

*Implémente*<br/>
Une variable du type spécifiée par le paramètre du modèle *T*.

*riid*<br/>
L’interface ID à récupérer.

*ppvObject*<br/>
Si cette opération est réussie, un pointeur-à-un-pointeur à l’interface spécifiée par le *paramètre riid*.

### <a name="return-value"></a>Valeur de retour

S_OK en cas de succès; autrement, un HRESULT qui décrit l’erreur.

### <a name="remarks"></a>Notes

Récupère un pointeur sur l’id d’interface spécifié.

## <a name="runtimeclassbasetgetimplementediids"></a><a name="getimplementediids"></a>RuntimeClassBaset::GetImplementedIIDS

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

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
Le type de *paramètre des impléments.*

*Implémente*<br/>
Pointeur sur le type spécifié par le paramètre *T*.

*iidCompte*<br/>
Le nombre maximum d’interfaces iD à récupérer.

*iids*<br/>
Si cette opération se termine avec succès, un tableau des interfaces ID implémentées par type *T*.

### <a name="return-value"></a>Valeur de retour

S_OK en cas de succès; autrement, un HRESULT qui décrit l’erreur.

### <a name="remarks"></a>Notes

Récupère une gamme d’interfaces qui sont implémentées par un type spécifié.
