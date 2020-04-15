---
title: Classe CComObjectStack
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
ms.openlocfilehash: 8c3fd56635da8b80c84f6151009586b7bd2b4341
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327574"
---
# <a name="ccomobjectstack-class"></a>Classe CComObjectStack

Cette classe crée un objet COM temporaire et lui `IUnknown`fournit une mise en œuvre squelettique de .

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
|[CComObjectStack: CComObjectStack](#dtor)|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CComObjectStack::AddRef](#addref)|Retourne zéro. En mode débogé, appels `_ASSERTE`.|
|[CComObjectStack::QueryInterface](#queryinterface)|Retourne E_NOINTERFACE. En mode débogé, appels `_ASSERTE`.|
|[CComObjectStack::Libération](#release)|Retourne zéro. En mode débogé, appels `_ASSERTE`. ~|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CComObjectStack::m_hResFinalConstruct](#m_hresfinalconstruct)|Contient le HRESULT retourné `CComObjectStack` pendant la construction de l’objet.|

## <a name="remarks"></a>Notes

`CComObjectStack`est utilisé pour créer un objet COM temporaire et fournir `IUnknown`à l’objet une mise en œuvre squelettique de . Typiquement, l’objet est utilisé comme une variable locale dans une fonction (c’est-à-dire, poussé sur la pile). Puisque l’objet est détruit lorsque la fonction se termine, le comptage de référence n’est pas effectué pour augmenter l’efficacité.

L’exemple suivant montre comment créer un objet COM utilisé à l’intérieur d’une fonction :

[!code-cpp[NVC_ATL_COM#42](../../atl/codesnippet/cpp/ccomobjectstack-class_1.cpp)]

L’objet `Tempobj` temporaire est poussé sur la pile et disparaît automatiquement lorsque la fonction se termine.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`Base`

`CComObjectStack`

## <a name="requirements"></a>Spécifications

**En-tête:** atlcom.h

## <a name="ccomobjectstackaddref"></a><a name="addref"></a>CComObjectStack::AddRef

Retourne zéro.

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>Valeur de retour

Retourne zéro.

### <a name="remarks"></a>Notes

En mode débogé, appels `_ASSERTE`.

## <a name="ccomobjectstackccomobjectstack"></a><a name="ccomobjectstack"></a>CComObjectStack::CComObjectStack

Constructeur.

```
CComObjectStack(void* = NULL);
```

### <a name="remarks"></a>Notes

Appels, `FinalConstruct` puis met [m_hResFinalConstruct](#m_hresfinalconstruct) à la HRESULT retourné par `FinalConstruct`. Si vous n’avez pas dérivé votre classe de base de `FinalConstruct` [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md), vous devez fournir votre propre méthode. Le destructeur appelle `FinalRelease`.

## <a name="ccomobjectstackccomobjectstack"></a><a name="dtor"></a>CComObjectStack: CComObjectStack

Destructeur.

```
CComObjectStack();
```

### <a name="remarks"></a>Notes

Libère toutes les ressources allouées et appelle [FinalRelease](ccomobjectrootex-class.md#finalrelease).

## <a name="ccomobjectstackm_hresfinalconstruct"></a><a name="m_hresfinalconstruct"></a>CComObjectStack::m_hResFinalConstruct

Contient le HRESULT `FinalConstruct` retourné de `CComObjectStack` l’appel pendant la construction de l’objet.

```
HRESULT    m_hResFinalConstruct;
```

## <a name="ccomobjectstackqueryinterface"></a><a name="queryinterface"></a>CComObjectStack::QueryInterface

Retourne E_NOINTERFACE.

```
HRESULT    QueryInterface(REFIID, void**);
```

### <a name="return-value"></a>Valeur de retour

Retourne E_NOINTERFACE.

### <a name="remarks"></a>Notes

En mode débogé, appels `_ASSERTE`.

## <a name="ccomobjectstackrelease"></a><a name="release"></a>CComObjectStack::Libération

Retourne zéro.

```
STDMETHOD_(ULONG, Release)();
```

### <a name="return-value"></a>Valeur de retour

Retourne zéro.

### <a name="remarks"></a>Notes

En mode débogé, appels `_ASSERTE`.

## <a name="see-also"></a>Voir aussi

[Classe CComAggObject](../../atl/reference/ccomaggobject-class.md)<br/>
[Classe CComObject](../../atl/reference/ccomobject-class.md)<br/>
[Classe CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
