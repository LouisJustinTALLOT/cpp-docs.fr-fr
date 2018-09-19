---
title: Ccomobjectstack, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComObjectStack
- ATLCOM/ATL::CComObjectStack
- ATLCOM/ATL::CComObjectStack::CComObjectStack
- ATLCOM/ATL::CComObjectStack::AddRef
- ATLCOM/ATL::CComObjectStack::QueryInterface
- ATLCOM/ATL::CComObjectStack::Release
- ATLCOM/ATL::CComObjectStack::m_hResFinalConstruct
dev_langs:
- C++
helpviewer_keywords:
- CComObjectStack class
ms.assetid: 3da72c40-c834-45f6-bb76-6ac204028d80
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 277951a5425a75c9769c5a2c4104421303f677c2
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46065334"
---
# <a name="ccomobjectstack-class"></a>Ccomobjectstack, classe

Cette classe crée un objet COM temporaire et il fournit une implémentation squelette de `IUnknown`.

## <a name="syntax"></a>Syntaxe

```
template <class  Base>
class CComObjectStack : public Base
```

#### <a name="parameters"></a>Paramètres

*base de*<br/>
Votre classe, dérivée de [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) ou [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md), ainsi que toute autre interface souhaitées prendre en charge sur l’objet.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CComObjectStack::CComObjectStack](#ccomobjectstack)|Constructeur.|
|[CComObjectStack :: ~ CComObjectStack](#dtor)|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CComObjectStack::AddRef](#addref)|Retourne zéro. En mode débogage, appelle `_ASSERTE`.|
|[CComObjectStack::QueryInterface](#queryinterface)|Retourne E_NOINTERFACE. En mode débogage, appelle `_ASSERTE`.|
|[CComObjectStack::Release](#release)|Retourne zéro. En mode débogage, appelle `_ASSERTE`. ~|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CComObjectStack::m_hResFinalConstruct](#m_hresfinalconstruct)|Contient le HRESULT retourné pendant la construction de la `CComObjectStack` objet.|

## <a name="remarks"></a>Notes

`CComObjectStack` est utilisé pour créer un objet COM temporaire et fournir l’objet une implémentation squelette de `IUnknown`. En règle générale, l’objet est utilisé comme une variable locale dans une fonction (qui est, placée sur la pile). Étant donné que l’objet est détruit lorsque la fonction se termine, le décompte de références n’est pas effectuée pour accroître l’efficacité.

L’exemple suivant montre comment créer un objet COM utilisé dans une fonction :

[!code-cpp[NVC_ATL_COM#42](../../atl/codesnippet/cpp/ccomobjectstack-class_1.cpp)]

L’objet temporaire `Tempobj` est placé sur la pile et disparaît automatiquement lorsque la fonction se termine.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`Base`

`CComObjectStack`

## <a name="requirements"></a>Configuration requise

**En-tête :** atlcom.h

##  <a name="addref"></a>  CComObjectStack::AddRef

Retourne zéro.

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>Valeur de retour

Retourne zéro.

### <a name="remarks"></a>Notes

En mode débogage, appelle `_ASSERTE`.

##  <a name="ccomobjectstack"></a>  CComObjectStack::CComObjectStack

Constructeur.

```
CComObjectStack(void* = NULL);
```

### <a name="remarks"></a>Notes

Appels `FinalConstruct` et définit ensuite [m_hResFinalConstruct](#m_hresfinalconstruct) au HRESULT retourné par `FinalConstruct`. Si vous n’avez pas dérivé votre classe de base à partir de [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md), vous devez fournir votre propre `FinalConstruct` (méthode). Le destructeur appelle `FinalRelease`.

##  <a name="dtor"></a>  CComObjectStack :: ~ CComObjectStack

Destructeur.

```
CComObjectStack();
```

### <a name="remarks"></a>Notes

Libère toutes les ressources allouées et appels [FinalRelease](ccomobjectrootex-class.md#finalrelease).

##  <a name="m_hresfinalconstruct"></a>  CComObjectStack::m_hResFinalConstruct

Contient le HRESULT retourné en appelant `FinalConstruct` pendant la construction de la `CComObjectStack` objet.

```
HRESULT    m_hResFinalConstruct;
```

##  <a name="queryinterface"></a>  CComObjectStack::QueryInterface

Retourne E_NOINTERFACE.

```
HRESULT    QueryInterface(REFIID, void**);
```

### <a name="return-value"></a>Valeur de retour

Retourne E_NOINTERFACE.

### <a name="remarks"></a>Notes

En mode débogage, appelle `_ASSERTE`.

##  <a name="release"></a>  CComObjectStack::Release

Retourne zéro.

```
STDMETHOD_(ULONG, Release)();
```

### <a name="return-value"></a>Valeur de retour

Retourne zéro.

### <a name="remarks"></a>Notes

En mode débogage, appelle `_ASSERTE`.

## <a name="see-also"></a>Voir aussi

[CComAggObject, classe](../../atl/reference/ccomaggobject-class.md)<br/>
[CComObject, classe](../../atl/reference/ccomobject-class.md)<br/>
[CComObjectGlobal, classe](../../atl/reference/ccomobjectglobal-class.md)<br/>
[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
