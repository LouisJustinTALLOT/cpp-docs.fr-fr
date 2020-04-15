---
title: Classe CComPtr
description: Guide de référence de la classe CComPtr (ATL) de la bibliothèque Microsoft CMD Active Template Library (ATL).
ms.date: 02/07/2020
f1_keywords:
- CComPtr
- ATLBASE/ATL::CComPtr
- ATLBASE/ATL::CComPtr::CComPtr
helpviewer_keywords:
- CComPtr class
ms.assetid: 22d9ea8d-ed66-4c34-940f-141db11e83bd
ms.openlocfilehash: 855466225db2672755658dcbbc9a266d09e0e7be
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327523"
---
# <a name="ccomptr-class"></a>Classe CComPtr

Une classe de pointeur intelligent pour la gestion des pointeurs d’interface COM.

## <a name="syntax"></a>Syntaxe

```cpp
template<class T>
class CComPtr
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Une interface COM spécifiant le type de pointeur à stocker.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CComPtr::CComPtr](#ccomptr)|Constructeur.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CComPtr::opérateur](#operator_eq)|Assigne un pointeur au pointeur du membre.|

## <a name="remarks"></a>Notes

ATL `CComPtr` utilise et [CComQIPtr](../../atl/reference/ccomqiptr-class.md) pour gérer les pointeurs d’interface COM. Les deux sont dérivés de [CComPtrBase](../../atl/reference/ccomptrbase-class.md), et les deux font le comptage automatique de référence.

Les `CComPtr` classes et [CComQIPtr](../../atl/reference/ccomqiptr-class.md) peuvent aider à éliminer les fuites de mémoire en effectuant un comptage automatique des références.  Les fonctions suivantes font toutes les deux les mêmes opérations logiques. Cependant, la deuxième version peut être moins sujette `CComPtr` aux erreurs parce qu’elle utilise la classe :

[!code-cpp[NVC_ATL_Utilities#130](../../atl/codesnippet/cpp/ccomptr-class_1.cpp)]

[!code-cpp[NVC_ATL_Utilities#131](../../atl/codesnippet/cpp/ccomptr-class_2.cpp)]

Dans Debug construit, lien atlsd.lib pour le traçage du code.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CComPtrBase (en)](../../atl/reference/ccomptrbase-class.md)

`CComPtr`

## <a name="requirements"></a>Spécifications

**En-tête:** atlbase.h

## <a name="ccomptrccomptr"></a><a name="ccomptr"></a>CComPtr::CComPtr

Constructeur.

```cpp
CComPtr() throw ();
CComPtr(T* lp) throw ();
CComPtr (const CComPtr<T>& lp) throw ();
```

### <a name="parameters"></a>Paramètres

*Lp*<br/>
Utilisé pour initialiser le pointeur d’interface.

*T*<br/>
Une interface COM.

### <a name="remarks"></a>Notes

Les constructeurs qui prennent `AddRef` un argument appel sur *lp*, si ce n’est pas un pointeur nul. Un objet possédé non `Release` nul reçoit un appel sur la destruction de l’objet CComPtr, ou si un nouvel objet est attribué à l’objet CComPtr.

## <a name="ccomptroperator-"></a><a name="operator_eq"></a>CComPtr::opérateur

Opérateur d'assignation.

```cpp
T* operator= (T* lp) throw ();
T* operator= (const CComPtr<T>& lp) throw ();
```

### <a name="return-value"></a>Valeur de retour

Retourne un pointeur `CComPtr` à l’objet mis à jour

### <a name="remarks"></a>Notes

Cette opération AddRefs le nouvel objet et libère l’objet existant, si l’on existe.

## <a name="see-also"></a>Voir aussi

[CComPtr::CComPtr](#ccomptr)<br/>
[CComQIPtr::CComQIPtr](../../atl/reference/ccomqiptr-class.md#ccomqiptr)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
