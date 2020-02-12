---
title: CComPtr (classe)
description: Guide de référence de la C++ classe Microsoft Active Template Library (ATL) CComPtr.
ms.date: 02/07/2020
f1_keywords:
- CComPtr
- ATLBASE/ATL::CComPtr
- ATLBASE/ATL::CComPtr::CComPtr
helpviewer_keywords:
- CComPtr class
ms.assetid: 22d9ea8d-ed66-4c34-940f-141db11e83bd
ms.openlocfilehash: 74a12b460f55a782fa2747b02f7d00287786fae6
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77127403"
---
# <a name="ccomptr-class"></a>CComPtr (classe)

Classe de pointeur intelligent pour la gestion des pointeurs d’interface COM.

## <a name="syntax"></a>Syntaxe

```cpp
template<class T>
class CComPtr
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Interface COM spécifiant le type de pointeur à stocker.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Name|Description|
|----------|-----------------|
|[CComPtr :: CComPtr](#ccomptr)|Constructeur.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Name|Description|
|----------|-----------------|
|[CComPtr :: Operator =](#operator_eq)|Assigne un pointeur au pointeur membre.|

## <a name="remarks"></a>Notes

ATL utilise `CComPtr` et [CComQIPtr](../../atl/reference/ccomqiptr-class.md) pour gérer les pointeurs d’interface com. Les deux sont dérivés de [CComPtrBase](../../atl/reference/ccomptrbase-class.md), et les deux effectuent le décompte de références automatique.

Les classes `CComPtr` et [CComQIPtr](../../atl/reference/ccomqiptr-class.md) peuvent vous aider à éliminer les fuites de mémoire en effectuant un décompte de références automatique.  Les fonctions suivantes effectuent les mêmes opérations logiques. Toutefois, la deuxième version peut être moins sujette aux erreurs, car elle utilise la classe `CComPtr` :

[!code-cpp[NVC_ATL_Utilities#130](../../atl/codesnippet/cpp/ccomptr-class_1.cpp)]

[!code-cpp[NVC_ATL_Utilities#131](../../atl/codesnippet/cpp/ccomptr-class_2.cpp)]

Dans les versions Debug, liez atlsd. lib pour le traçage de code.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CComPtrBase](../../atl/reference/ccomptrbase-class.md)

`CComPtr`

## <a name="requirements"></a>Spécifications

**En-tête :** atlbase. h

## <a name="ccomptr"></a>CComPtr :: CComPtr

Constructeur.

```cpp
CComPtr() throw ();
CComPtr(T* lp) throw ();
CComPtr (const CComPtr<T>& lp) throw ();
```

### <a name="parameters"></a>Paramètres

*Aid*<br/>
Utilisé pour initialiser le pointeur d’interface.

*T*<br/>
Interface COM.

### <a name="remarks"></a>Notes

Les constructeurs qui acceptent un appel d’argument `AddRef` sur *LP*, s’il ne s’agit pas d’un pointeur null. Un objet détenu non null obtient un `Release` appel sur la destruction de l’objet CComPtr, ou si un nouvel objet est assigné à l’objet CComPtr.

## <a name="operator_eq"></a>CComPtr :: Operator =

Opérateur d'assignation.

```cpp
T* operator= (T* lp) throw ();
T* operator= (const CComPtr<T>& lp) throw ();
```

### <a name="return-value"></a>Valeur de retour

Retourne un pointeur vers l’objet `CComPtr` mis à jour

### <a name="remarks"></a>Notes

Cette opération AddRefs le nouvel objet et libère l’objet existant, s’il en existe un.

## <a name="see-also"></a>Voir aussi

[CComPtr :: CComPtr](#ccomptr)<br/>
[CComQIPtr :: CComQIPtr](../../atl/reference/ccomqiptr-class.md#ccomqiptr)<br/>
[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
