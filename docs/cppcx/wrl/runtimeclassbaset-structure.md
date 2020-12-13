---
description: 'En savoir plus sur : structure RuntimeClassBaseT'
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
ms.openlocfilehash: 48f03a5d54eba455b60646ed47c48e228f07863e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97135289"
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
Champ d’indicateurs qui spécifie un ou plusieurs énumérateurs [RuntimeClassType](runtimeclasstype-enumeration.md) .

## <a name="remarks"></a>Notes

Fournit des méthodes d’assistance pour les `QueryInterface` opérations et l’obtention des ID d’interface.

## <a name="members"></a>Membres

### <a name="protected-methods"></a>Méthodes protégées

Nom                                                         | Description
------------------------------------------------------------ | -----------------------------------------------------------------------------
[RuntimeClassBaseT :: Asiid,](#asiid)                           | Récupère un pointeur vers l’ID d’interface spécifié.
[RuntimeClassBaseT :: Getimplementediids,](#getimplementediids) | Récupère un tableau des ID d’interface qui sont implémentés par un type spécifié.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`RuntimeClassBaseT`

## <a name="requirements"></a>Spécifications

**En-tête :** Implements. h

**Espace de noms :** Microsoft :: WRL ::D étails

## <a name="runtimeclassbasetasiid"></a><a name="asiid"></a> RuntimeClassBaseT :: Asiid,

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
Type qui implémente l’ID d’interface spécifié par le paramètre *riid*.

*implémente*<br/>
Variable du type spécifié par le paramètre de modèle *T*.

*riid*<br/>
ID d’interface à récupérer.

*ppvObject*<br/>
Si cette opération réussit, pointeur vers un pointeur vers l’interface spécifiée par le paramètre *riid*.

### <a name="return-value"></a>Valeur renvoyée

S_OK en cas de réussite ; Sinon, HRESULT qui décrit l’erreur.

### <a name="remarks"></a>Notes

Récupère un pointeur vers l’ID d’interface spécifié.

## <a name="runtimeclassbasetgetimplementediids"></a><a name="getimplementediids"></a> RuntimeClassBaseT :: Getimplementediids,

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
Type du paramètre *Implements* .

*implémente*<br/>
Pointeur vers le type spécifié par le paramètre *T*.

*Iidcount,*<br/>
Nombre maximal d’ID d’interface à récupérer.

*IID*<br/>
Si cette opération se termine correctement, un tableau des ID d’interface implémenté par le type *T*.

### <a name="return-value"></a>Valeur renvoyée

S_OK en cas de réussite ; Sinon, HRESULT qui décrit l’erreur.

### <a name="remarks"></a>Notes

Récupère un tableau des ID d’interface qui sont implémentés par un type spécifié.
