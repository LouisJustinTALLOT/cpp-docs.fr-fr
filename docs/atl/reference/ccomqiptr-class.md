---
description: 'En savoir plus sur : classe CComQIPtr'
title: CComQIPtr, classe
ms.date: 11/04/2016
f1_keywords:
- CComQIPtr
- ATLCOMCLI/ATL::CComQIPtr
- ATLCOMCLI/ATL::CComQIPtr::CComQIPtr
helpviewer_keywords:
- CComQIPtr class
ms.assetid: 969cacb5-05b6-4af4-b683-24911d70242d
ms.openlocfilehash: e5af938cd7b2bbae3b091eac5323d3455ce1cf02
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97142322"
---
# <a name="ccomqiptr-class"></a>CComQIPtr, classe

Classe de pointeur intelligent pour la gestion des pointeurs d’interface COM.

## <a name="syntax"></a>Syntaxe

```
template<class T, const IID* piid= &__uuidof(T)>
class CComQIPtr: public CComPtr<T>
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Interface COM spécifiant le type de pointeur à stocker.

*piid*<br/>
Pointeur vers l’IID de *T*.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CComQIPtr :: CComQIPtr](#ccomqiptr)|Constructeur.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CComQIPtr :: Operator =](#operator_eq)|Assigne un pointeur au pointeur membre.|

## <a name="remarks"></a>Notes

ATL utilise `CComQIPtr` et [CComPtr](../../atl/reference/ccomptr-class.md) pour gérer les pointeurs d’interface com, qui dérivent tous les deux de [CComPtrBase](../../atl/reference/ccomptrbase-class.md). Les deux classes effectuent un décompte de références automatique via les appels à `AddRef` et `Release` . Les opérateurs surchargés gèrent les opérations de pointeur.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CComPtrBase](../../atl/reference/ccomptrbase-class.md)

[CComPtr](../../atl/reference/ccomptr-class.md)

`CComQIPtr`

## <a name="requirements"></a>Spécifications

**En-tête :** atlcomcli. h

## <a name="ccomqiptrccomqiptr"></a><a name="ccomqiptr"></a> CComQIPtr :: CComQIPtr

Constructeur.

```
CComQIPtr() throw();
CComQIPtr(T* lp) throw();
CComQIPtr(IUnknown* lp) throw();
CComQIPtr(const CComQIPtr<T, piid>& lp) throw();
```

### <a name="parameters"></a>Paramètres

*Aid*<br/>
Utilisé pour initialiser le pointeur d’interface.

*T*<br/>
Interface COM.

*piid*<br/>
Pointeur vers l’IID de *T*.

## <a name="ccomqiptroperator-"></a><a name="operator_eq"></a> CComQIPtr :: Operator =

Opérateur d’assignation.

```
T* operator= (T* lp) throw();
T* operator= (const CComQIPtr<T, piid>& lp) throw();
T* operator= (IUnknown* lp) throw();
```

### <a name="parameters"></a>Paramètres

*Aid*<br/>
Utilisé pour initialiser le pointeur d’interface.

*T*<br/>
Interface COM.

*piid*<br/>
Pointeur vers l’IID de *T*.

### <a name="return-value"></a>Valeur renvoyée

Retourne un pointeur vers l’objet mis à jour `CComQIPtr` .

## <a name="see-also"></a>Voir aussi

[CComPtr :: CComPtr](../../atl/reference/ccomptr-class.md#ccomptr)<br/>
[CComQIPtr :: CComQIPtr](#ccomqiptr)<br/>
[CComPtrBase, classe](../../atl/reference/ccomptrbase-class.md)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)<br/>
[CComQIPtrElementTraits, classe](../../atl/reference/ccomqiptrelementtraits-class.md)
