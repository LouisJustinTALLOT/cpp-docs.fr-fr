---
title: Classe CAtlException
ms.date: 11/04/2016
f1_keywords:
- CAtlException
- ATLEXCEPT/ATL::CAtlException
- ATLEXCEPT/ATL::CAtlException::CAtlException
- ATLEXCEPT/ATL::CAtlException::m_hr
helpviewer_keywords:
- CAtlException class
ms.assetid: 3fd7b041-f70d-4292-b947-0d70781d95a8
ms.openlocfilehash: 6da56e4d6c443520eb6f857624a5923e71a1e580
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318992"
---
# <a name="catlexception-class"></a>Classe CAtlException

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
|[CAtlException::opérateur HRESULT](#operator_hresult)|Lance l’objet actuel à une valeur HRESULT.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CAtlException::m_hr](#m_hr)|La variable de type HRESULT créée par l’objet et utilisée pour stocker l’état d’erreur.|

## <a name="remarks"></a>Notes

Un `CAtlException` objet représente une condition d’exception liée à une opération ATL. La `CAtlException` classe comprend un membre public de données qui stocke le code d’état indiquant la raison de l’exception et un opérateur de distribution qui vous permet de traiter l’exception comme s’il s’agissait d’un HRESULT.

En général, vous `AtlThrow` appellez `CAtlException` plutôt que de créer un objet directement.

## <a name="requirements"></a>Spécifications

**En-tête:** atlexcept.h

## <a name="catlexceptioncatlexception"></a><a name="catlexception"></a>CAtlException::CAtlException

Constructeur.

```
CAtlException(HRESULT hr) throw();
CAtlException() throw();
```

### <a name="parameters"></a>Paramètres

*Hr*<br/>
Code d'erreur HRESULT.

## <a name="catlexceptionoperator-hresult"></a><a name="operator_hresult"></a>CAtlException::opérateur HRESULT

Lance l’objet actuel à une valeur HRESULT.

```
operator HRESULT() const throw ();
```

## <a name="catlexceptionm_hr"></a><a name="m_hr"></a>CAtlException::m_hr

Le membre des données HRESULT.

```
HRESULT m_hr;
```

### <a name="remarks"></a>Notes

Le membre des données qui stocke l’état d’erreur. La valeur HRESULT est définie par le constructeur, [CAtlException::CAtlException](#catlexception).

## <a name="see-also"></a>Voir aussi

[AtlThrow](debugging-and-error-reporting-global-functions.md#atlthrow)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
