---
description: 'En savoir plus sur : classe CComObjectStack'
title: CComObjectStack, classe
ms.date: 11/04/2016
f1_keywords:
- CComObjectStack
- ATLCOM/ATL::CComObjectStack
- ATLCOM/ATL::CComObjectStack::CComObjectStack
- ATLCOM/ATL::CComObjectStack::AddRef
- ATLCOM/ATL::CComObjectStack::QueryInterface
- ATLCOM/ATL::CComObjectStack::Release
- ATLCOM/ATL::CComObjectStack::m_hResFinalConstruct
helpviewer_keywords:
- CComObjectStack class
ms.assetid: 3da72c40-c834-45f6-bb76-6ac204028d80
ms.openlocfilehash: 5713601a765ad9ff1c32992d1f9c517dd86affca
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97142413"
---
# <a name="ccomobjectstack-class"></a>CComObjectStack, classe

Cette classe crée un objet COM temporaire et lui fournit une implémentation squelettique de `IUnknown` .

## <a name="syntax"></a>Syntaxe

```
template <class  Base>
class CComObjectStack : public Base
```

#### <a name="parameters"></a>Paramètres

*Base*<br/>
Votre classe, dérivée de [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) ou [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md), ainsi que de toute autre interface que vous souhaitez prendre en charge sur l’objet.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CComObjectStack::CComObjectStack](#ccomobjectstack)|Constructeur.|
|[CComObjectStack :: ~ CComObjectStack](#dtor)|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CComObjectStack :: AddRef](#addref)|Retourne zéro. En mode débogage, appelle `_ASSERTE` .|
|[CComObjectStack :: QueryInterface](#queryinterface)|Retourne E_NOINTERFACE. En mode débogage, appelle `_ASSERTE` .|
|[CComObjectStack :: Release](#release)|Retourne zéro. En mode débogage, appelle `_ASSERTE` . ~|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CComObjectStack :: m_hResFinalConstruct](#m_hresfinalconstruct)|Contient le HRESULT retourné pendant la construction de l' `CComObjectStack` objet.|

## <a name="remarks"></a>Notes

`CComObjectStack` est utilisé pour créer un objet COM temporaire et fournir à l’objet une implémentation squelettique de `IUnknown` . En général, l’objet est utilisé en tant que variable locale dans une fonction (autrement dit, fait l’objet d’un push dans la pile). Étant donné que l’objet est détruit à la fin de la fonction, le décompte de références n’est pas effectué pour améliorer l’efficacité.

L’exemple suivant montre comment créer un objet COM utilisé à l’intérieur d’une fonction :

[!code-cpp[NVC_ATL_COM#42](../../atl/codesnippet/cpp/ccomobjectstack-class_1.cpp)]

L’objet temporaire fait l’objet d' `Tempobj` un push dans la pile et disparaît automatiquement à la fin de la fonction.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`Base`

`CComObjectStack`

## <a name="requirements"></a>Spécifications

**En-tête :** atlcom. h

## <a name="ccomobjectstackaddref"></a><a name="addref"></a> CComObjectStack :: AddRef

Retourne zéro.

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>Valeur renvoyée

Retourne zéro.

### <a name="remarks"></a>Notes

En mode débogage, appelle `_ASSERTE` .

## <a name="ccomobjectstackccomobjectstack"></a><a name="ccomobjectstack"></a> CComObjectStack::CComObjectStack

Constructeur.

```
CComObjectStack(void* = NULL);
```

### <a name="remarks"></a>Notes

Appelle `FinalConstruct` , puis définit [m_hResFinalConstruct](#m_hresfinalconstruct) sur le HRESULT retourné par `FinalConstruct` . Si vous n’avez pas dérivé votre classe de base de [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md), vous devez fournir votre propre `FinalConstruct` méthode. Le destructeur appelle `FinalRelease`.

## <a name="ccomobjectstackccomobjectstack"></a><a name="dtor"></a> CComObjectStack :: ~ CComObjectStack

Destructeur.

```
CComObjectStack();
```

### <a name="remarks"></a>Notes

Libère toutes les ressources allouées et appelle [FinalRelease](ccomobjectrootex-class.md#finalrelease).

## <a name="ccomobjectstackm_hresfinalconstruct"></a><a name="m_hresfinalconstruct"></a> CComObjectStack :: m_hResFinalConstruct

Contient le HRESULT retourné par l’appel `FinalConstruct` pendant la construction de l' `CComObjectStack` objet.

```
HRESULT    m_hResFinalConstruct;
```

## <a name="ccomobjectstackqueryinterface"></a><a name="queryinterface"></a> CComObjectStack :: QueryInterface

Retourne E_NOINTERFACE.

```
HRESULT    QueryInterface(REFIID, void**);
```

### <a name="return-value"></a>Valeur renvoyée

Retourne E_NOINTERFACE.

### <a name="remarks"></a>Notes

En mode débogage, appelle `_ASSERTE` .

## <a name="ccomobjectstackrelease"></a><a name="release"></a> CComObjectStack :: Release

Retourne zéro.

```
STDMETHOD_(ULONG, Release)();
```

### <a name="return-value"></a>Valeur renvoyée

Retourne zéro.

### <a name="remarks"></a>Notes

En mode débogage, appelle `_ASSERTE` .

## <a name="see-also"></a>Voir aussi

[CComAggObject, classe](../../atl/reference/ccomaggobject-class.md)<br/>
[CComObject, classe](../../atl/reference/ccomobject-class.md)<br/>
[CComObjectGlobal, classe](../../atl/reference/ccomobjectglobal-class.md)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
