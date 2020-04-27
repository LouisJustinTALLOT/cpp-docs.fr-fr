---
title: CAtlException, classe
ms.date: 11/04/2016
f1_keywords:
- CAtlException
- ATLEXCEPT/ATL::CAtlException
- ATLEXCEPT/ATL::CAtlException::CAtlException
- ATLEXCEPT/ATL::CAtlException::m_hr
helpviewer_keywords:
- CAtlException class
ms.assetid: 3fd7b041-f70d-4292-b947-0d70781d95a8
ms.openlocfilehash: f09d9b2f46233cf356f5ade8a5b90e08a213d276
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168200"
---
# <a name="catlexception-class"></a>CAtlException, classe

Cette classe définit une exception ATL.

## <a name="syntax"></a>Syntaxe

```cpp
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
|[CAtlException :: Operator HRESULT](#operator_hresult)|Effectue un cast de l’objet actuel en une valeur HRESULT.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CAtlException :: m_hr](#m_hr)|Variable de type HRESULT créée par l’objet et utilisée pour stocker la condition d’erreur.|

## <a name="remarks"></a>Notes

Un `CAtlException` objet représente une condition d’exception liée à une opération ATL. La `CAtlException` classe comprend un membre de données public qui stocke le code d’état indiquant la raison de l’exception et un opérateur de cast qui vous permet de traiter l’exception comme s’il s’agissait d’un HRESULT.

En général, vous appelez `AtlThrow` plutôt que de créer un `CAtlException` objet directement.

## <a name="requirements"></a>Spécifications

**En-tête :** atlexcept. h

## <a name="catlexceptioncatlexception"></a><a name="catlexception"></a>CAtlException::CAtlException

Constructeur.

```cpp
CAtlException(HRESULT hr) throw();
CAtlException() throw();
```

### <a name="parameters"></a>Paramètres

*h*<br/>
Code d'erreur HRESULT.

## <a name="catlexceptionoperator-hresult"></a><a name="operator_hresult"></a>CAtlException :: Operator HRESULT

Effectue un cast de l’objet actuel en une valeur HRESULT.

```cpp
operator HRESULT() const throw ();
```

## <a name="catlexceptionm_hr"></a><a name="m_hr"></a>CAtlException :: m_hr

Données membres HRESULT.

```cpp
HRESULT m_hr;
```

### <a name="remarks"></a>Notes

Membre de données qui stocke la condition d’erreur. La valeur HRESULT est définie par le constructeur, [CAtlException :: CAtlException](#catlexception).

## <a name="see-also"></a>Voir aussi

[AtlThrow](debugging-and-error-reporting-global-functions.md#atlthrow)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
