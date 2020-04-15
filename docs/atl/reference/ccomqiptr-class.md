---
title: Classe CComQIPtr
ms.date: 11/04/2016
f1_keywords:
- CComQIPtr
- ATLCOMCLI/ATL::CComQIPtr
- ATLCOMCLI/ATL::CComQIPtr::CComQIPtr
helpviewer_keywords:
- CComQIPtr class
ms.assetid: 969cacb5-05b6-4af4-b683-24911d70242d
ms.openlocfilehash: 2b1d8b92fbc5e95a5061956bafc4922d249a6f18
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327417"
---
# <a name="ccomqiptr-class"></a>Classe CComQIPtr

Une classe de pointeur intelligent pour la gestion des pointeurs d’interface COM.

## <a name="syntax"></a>Syntaxe

```
template<class T, const IID* piid= &__uuidof(T)>
class CComQIPtr: public CComPtr<T>
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Une interface COM spécifiant le type de pointeur à stocker.

*piid*<br/>
Un pointeur à l’IID de *T*.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CComQIPtr::CComQIPtr](#ccomqiptr)|Constructeur.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CComQIPtr::opérateur](#operator_eq)|Assigne un pointeur au pointeur du membre.|

## <a name="remarks"></a>Notes

ATL `CComQIPtr` utilise et [CComPtr](../../atl/reference/ccomptr-class.md) pour gérer les pointeurs d’interface COM, qui dérivent tous deux de [CComPtrBase](../../atl/reference/ccomptrbase-class.md). Les deux classes effectuent `AddRef` le `Release`comptage automatique des références par le biais d’appels vers et . Les opérateurs surchargés gèrent les opérations de pointeur.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CComPtrBase (en)](../../atl/reference/ccomptrbase-class.md)

[CComPtr (en)](../../atl/reference/ccomptr-class.md)

`CComQIPtr`

## <a name="requirements"></a>Spécifications

**En-tête:** atlcomcli.h

## <a name="ccomqiptrccomqiptr"></a><a name="ccomqiptr"></a>CComQIPtr::CComQIPtr

Constructeur.

```
CComQIPtr() throw();
CComQIPtr(T* lp) throw();
CComQIPtr(IUnknown* lp) throw();
CComQIPtr(const CComQIPtr<T, piid>& lp) throw();
```

### <a name="parameters"></a>Paramètres

*Lp*<br/>
Utilisé pour initialiser le pointeur d’interface.

*T*<br/>
Une interface COM.

*piid*<br/>
Un pointeur à l’IID de *T*.

## <a name="ccomqiptroperator-"></a><a name="operator_eq"></a>CComQIPtr::opérateur

L’opérateur de l’affectation.

```
T* operator= (T* lp) throw();
T* operator= (const CComQIPtr<T, piid>& lp) throw();
T* operator= (IUnknown* lp) throw();
```

### <a name="parameters"></a>Paramètres

*Lp*<br/>
Utilisé pour initialiser le pointeur d’interface.

*T*<br/>
Une interface COM.

*piid*<br/>
Un pointeur à l’IID de *T*.

### <a name="return-value"></a>Valeur de retour

Retourne un pointeur `CComQIPtr` à l’objet mis à jour.

## <a name="see-also"></a>Voir aussi

[CComPtr::CComPtr](../../atl/reference/ccomptr-class.md#ccomptr)<br/>
[CComQIPtr::CComQIPtr](#ccomqiptr)<br/>
[Classe CComPtrBase](../../atl/reference/ccomptrbase-class.md)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)<br/>
[Classe CComQIPtrElraits](../../atl/reference/ccomqiptrelementtraits-class.md)
