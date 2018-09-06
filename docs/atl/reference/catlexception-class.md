---
title: Catlexception, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CAtlException
- ATLEXCEPT/ATL::CAtlException
- ATLEXCEPT/ATL::CAtlException::CAtlException
- ATLEXCEPT/ATL::CAtlException::m_hr
dev_langs:
- C++
helpviewer_keywords:
- CAtlException class
ms.assetid: 3fd7b041-f70d-4292-b947-0d70781d95a8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 338943e2168930bc48f02ef9ddbf36f738965078
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43763371"
---
# <a name="catlexception-class"></a>Catlexception, classe

Cette classe définit une exception ATL.

## <a name="syntax"></a>Syntaxe

```
class CAtlException
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CAtlException::CAtlException](#catlexception)|Constructeur.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CAtlException::operator HRESULT](#operator_hresult)|Convertit l’objet actuel à une valeur HRESULT.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CAtlException::m_hr](#m_hr)|La variable de type HRESULT créé par l’objet et permet de stocker la condition d’erreur.|

## <a name="remarks"></a>Notes

Un `CAtlException` objet représente une condition d’exception liée à une opération de ATL. Le `CAtlException` classe inclut un membre de données publiques qui stocke le code d’état indiquant la raison de l’exception et un opérateur de conversion qui vous permet de traiter l’exception comme s’il s’agissait d’une valeur HRESULT.

En règle générale, vous appellerez `AtlThrow` au lieu de créer un `CAtlException` directement l’objet.

## <a name="requirements"></a>Configuration requise

**En-tête :** atlexcept.h

##  <a name="catlexception"></a>  CAtlException::CAtlException

Constructeur.

```
CAtlException(HRESULT hr) throw();
CAtlException() throw();
```

### <a name="parameters"></a>Paramètres

*ressources humaines*  
Le code d’erreur HRESULT.

##  <a name="operator_hresult"></a>  CAtlException::operator HRESULT

Convertit l’objet actuel à une valeur HRESULT.

```  
operator HRESULT() const throw ();
```

##  <a name="m_hr"></a>  CAtlException::m_hr

Le membre de données HRESULT.

```
HRESULT m_hr;
```

### <a name="remarks"></a>Notes

Le membre de données qui stocke la condition d’erreur. La valeur HRESULT est définie par le constructeur, [CAtlException::CAtlException](#catlexception).

## <a name="see-also"></a>Voir aussi

[AtlThrow](debugging-and-error-reporting-global-functions.md#atlthrow)   
[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
