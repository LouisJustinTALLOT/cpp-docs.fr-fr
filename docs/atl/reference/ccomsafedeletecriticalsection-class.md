---
description: 'En savoir plus sur : classe CComSafeDeleteCriticalSection'
title: CComSafeDeleteCriticalSection, classe
ms.date: 11/04/2016
f1_keywords:
- CComSafeDeleteCriticalSection
- ATLCORE/ATL::CComSafeDeleteCriticalSection
- ATLCORE/ATL::CComSafeDeleteCriticalSection::CComSafeDeleteCriticalSection
- ATLCORE/ATL::CComSafeDeleteCriticalSection::Init
- ATLCORE/ATL::CComSafeDeleteCriticalSection::Lock
- ATLCORE/ATL::CComSafeDeleteCriticalSection::Term
- ATLCORE/ATL::m_bInitialized
helpviewer_keywords:
- CComSafeDeleteCriticalSection class
ms.assetid: 4d2932c4-ba8f-48ec-8664-1db8bed01314
ms.openlocfilehash: 73e27fb267cbfc8cde248c7ac896d29de2a91f77
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97142167"
---
# <a name="ccomsafedeletecriticalsection-class"></a>CComSafeDeleteCriticalSection, classe

Cette classe fournit des méthodes pour obtenir et libérer la propriété d’un objet de section critique.

## <a name="syntax"></a>Syntaxe

```
class CComSafeDeleteCriticalSection : public CComCriticalSection
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CComSafeDeleteCriticalSection::CComSafeDeleteCriticalSection](#ccomsafedeletecriticalsection)|Constructeur.|
|[CComSafeDeleteCriticalSection :: ~ CComSafeDeleteCriticalSection](#dtor)|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CComSafeDeleteCriticalSection :: init](#init)|Crée et initialise un objet de section critique.|
|[CComSafeDeleteCriticalSection :: Lock](#lock)|Obtient la propriété de l’objet de section critique.|
|[CComSafeDeleteCriticalSection :: term](#term)|Libère les ressources système utilisées par l’objet de section critique.|

### <a name="data-members"></a>Données membres

|Membre de données|Description|
|-|-|
|[m_bInitialized](#m_binitialized)|Signale si l' `CRITICAL_SECTION` objet interne a été initialisé.|

## <a name="remarks"></a>Notes

`CComSafeDeleteCriticalSection` dérive de la classe [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md). Toutefois, `CComSafeDeleteCriticalSection` fournit des mécanismes de sécurité supplémentaires sur [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md).

Lorsqu’une instance de `CComSafeDeleteCriticalSection` est hors de portée ou est supprimée explicitement de la mémoire, l’objet de section critique sous-jacent est automatiquement nettoyé s’il est toujours valide. En outre, la méthode [CComSafeDeleteCriticalSection :: term](#term) s’arrête correctement si l’objet de section critique sous-jacent n’a pas encore été alloué ou a déjà été libéré de la mémoire.

Pour plus d’informations sur les classes d’assistance de section critique, consultez [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md) .

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)

`CComSafeDeleteCriticalSection`

## <a name="requirements"></a>Spécifications

**En-tête :** atlcore. h

## <a name="ccomsafedeletecriticalsectionccomsafedeletecriticalsection"></a><a name="ccomsafedeletecriticalsection"></a> CComSafeDeleteCriticalSection::CComSafeDeleteCriticalSection

Constructeur.

```
CComSafeDeleteCriticalSection();
```

### <a name="remarks"></a>Notes

Affecte la valeur FALSe au membre de données [m_bInitialized](#m_binitialized) .

## <a name="ccomsafedeletecriticalsectionccomsafedeletecriticalsection"></a><a name="dtor"></a> CComSafeDeleteCriticalSection :: ~ CComSafeDeleteCriticalSection

Destructeur.

```
~CComSafeDeleteCriticalSection() throw();
```

### <a name="remarks"></a>Notes

Libère l' `CRITICAL_SECTION` objet interne de la mémoire si le membre de données [m_bInitialized](#m_binitialized) a la valeur true.

## <a name="ccomsafedeletecriticalsectioninit"></a><a name="init"></a> CComSafeDeleteCriticalSection :: init

Appelle l’implémentation de la classe de base de [init](/visualstudio/debugger/init) et définit [m_bInitialized](#m_binitialized) sur true en cas de réussite.

```
HRESULT Init() throw();
```

### <a name="return-value"></a>Valeur renvoyée

Retourne le résultat de [CComCriticalSection :: init](../../atl/reference/ccomcriticalsection-class.md#init).

## <a name="ccomsafedeletecriticalsectionlock"></a><a name="lock"></a> CComSafeDeleteCriticalSection :: Lock

Appelle l’implémentation de la classe de base de [Lock](ccomcriticalsection-class.md#lock).

```
HRESULT Lock();
```

### <a name="return-value"></a>Valeur renvoyée

Retourne le résultat de [CComCriticalSection :: Lock](../../atl/reference/ccomcriticalsection-class.md#lock).

### <a name="remarks"></a>Notes

Cette méthode suppose que le membre de données [m_bInitialized](#m_binitialized) a la valeur true lors de l’entrée. Une assertion est générée dans les versions Debug si cette condition n’est pas remplie.

Pour plus d’informations sur le comportement de la fonction, consultez [CComCriticalSection :: Lock](../../atl/reference/ccomcriticalsection-class.md#lock).

## <a name="ccomsafedeletecriticalsectionm_binitialized"></a><a name="m_binitialized"></a> CComSafeDeleteCriticalSection :: m_bInitialized

Signale si l' `CRITICAL_SECTION` objet interne a été initialisé.

```
bool m_bInitialized;
```

### <a name="remarks"></a>Notes

Le `m_bInitialized` membre de données est utilisé pour assurer le suivi de la validité de l’objet sous-jacent `CRITICAL_SECTION` associé à la classe [CComSafeDeleteCriticalSection](../../atl/reference/ccomsafedeletecriticalsection-class.md) . L’objet sous-jacent n' `CRITICAL_SECTION` est pas tenté d’être libéré de la mémoire si cet indicateur n’a pas la valeur true.

## <a name="ccomsafedeletecriticalsectionterm"></a><a name="term"></a> CComSafeDeleteCriticalSection :: term

Appelle l’implémentation de la classe de base de [CComCriticalSection :: term](../../atl/reference/ccomcriticalsection-class.md#term) si l' `CRITICAL_SECTION` objet interne est valide.

```
HRESULT Term() throw();
```

### <a name="return-value"></a>Valeur renvoyée

Retourne le résultat de [CComCriticalSection :: term](../../atl/reference/ccomcriticalsection-class.md#term), ou S_OK si [m_bInitialized](#m_binitialized) a la valeur false lors de l’entrée.

### <a name="remarks"></a>Notes

Il est possible d’appeler cette méthode en toute sécurité même si l' `CRITICAL_SECTION` objet interne n’est pas valide. Le destructeur de cette classe appelle cette méthode si le membre de données [m_bInitialized](#m_binitialized) a la valeur true.

## <a name="see-also"></a>Voir aussi

[CComCriticalSection, classe](../../atl/reference/ccomcriticalsection-class.md)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
