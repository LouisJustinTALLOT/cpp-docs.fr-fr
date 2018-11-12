---
title: CComQIPtr, classe
ms.date: 11/04/2016
f1_keywords:
- CComQIPtr
- ATLCOMCLI/ATL::CComQIPtr
- ATLCOMCLI/ATL::CComQIPtr::CComQIPtr
helpviewer_keywords:
- CComQIPtr class
ms.assetid: 969cacb5-05b6-4af4-b683-24911d70242d
ms.openlocfilehash: c231d4d83a3030ea63e781e6f3d185270a483ccc
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50624924"
---
# <a name="ccomqiptr-class"></a>CComQIPtr, classe

Une classe de pointeur intelligent pour la gestion des pointeurs d’interface COM.

## <a name="syntax"></a>Syntaxe

```
template<class T, const IID* piid= &__uuidof(T)>
class CComQIPtr: public CComPtr<T>
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Une interface COM qui spécifie le type de pointeur à stocker.

*piid*<br/>
Un pointeur vers l’IID de *T*.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CComQIPtr::CComQIPtr](#ccomqiptr)|Constructeur.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CComQIPtr::operator =](#operator_eq)|Assigne un pointeur vers le pointeur de membre.|

## <a name="remarks"></a>Notes

ATL utilise `CComQIPtr` et [CComPtr](../../atl/reference/ccomptr-class.md) pour gérer les pointeurs d’interface COM, qui dérivent de [CComPtrBase](../../atl/reference/ccomptrbase-class.md). Les deux classes effectuent le décompte automatique via des appels aux `AddRef` et `Release`. Les opérateurs surchargés gérer les opérations de pointeur.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CComPtrBase](../../atl/reference/ccomptrbase-class.md)

[CComPtr](../../atl/reference/ccomptr-class.md)

`CComQIPtr`

## <a name="requirements"></a>Configuration requise

**En-tête :** atlcomcli.h

##  <a name="ccomqiptr"></a>  CComQIPtr::CComQIPtr

Constructeur.

```
CComQIPtr() throw();
CComQIPtr(T* lp) throw();
CComQIPtr(IUnknown* lp) throw();
CComQIPtr(const CComQIPtr<T, piid>& lp) throw();
```

### <a name="parameters"></a>Paramètres

*LP*<br/>
Utilisé pour initialiser le pointeur d’interface.

*T*<br/>
Une interface COM.

*piid*<br/>
Un pointeur vers l’IID de *T*.

##  <a name="operator_eq"></a>  CComQIPtr::operator =

L’opérateur d’assignation.

```
T* operator= (T* lp) throw();
T* operator= (const CComQIPtr<T, piid>& lp) throw();
T* operator= (IUnknown* lp) throw();
```

### <a name="parameters"></a>Paramètres

*LP*<br/>
Utilisé pour initialiser le pointeur d’interface.

*T*<br/>
Une interface COM.

*piid*<br/>
Un pointeur vers l’IID de *T*.

### <a name="return-value"></a>Valeur de retour

Retourne un pointeur vers la mise à jour `CComQIPtr` objet.

## <a name="see-also"></a>Voir aussi

[CComPtr::CComPtr](../../atl/reference/ccomptr-class.md#ccomptr)<br/>
[CComQIPtr::CComQIPtr](#ccomqiptr)<br/>
[CComPtrBase, classe](../../atl/reference/ccomptrbase-class.md)<br/>
[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)<br/>
[CComQIPtrElementTraits, classe](../../atl/reference/ccomqiptrelementtraits-class.md)
