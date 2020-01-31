---
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
ms.openlocfilehash: da83bc5d0c2ebb79aee07f30069144368169fc26
ms.sourcegitcommit: b8c22e6d555cf833510753cba7a368d57e5886db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76821647"
---
# <a name="ccomsafedeletecriticalsection-class"></a>CComSafeDeleteCriticalSection, classe

Cette classe fournit des méthodes pour obtenir et libérer la propriété d’un objet de section critique.

## <a name="syntax"></a>Syntaxe

```
class CComSafeDeleteCriticalSection : public CComCriticalSection
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Constructeurs publics

|Name|Description|
|----------|-----------------|
|[CComSafeDeleteCriticalSection::CComSafeDeleteCriticalSection](#ccomsafedeletecriticalsection)|Constructeur.|
|[CComSafeDeleteCriticalSection::~CComSafeDeleteCriticalSection](#dtor)|Destructeur.|

### <a name="public-methods"></a>Méthodes publiques

|Name|Description|
|----------|-----------------|
|[CComSafeDeleteCriticalSection::Init](#init)|Crée et initialise un objet de section critique.|
|[CComSafeDeleteCriticalSection::Lock](#lock)|Obtient la propriété de l’objet de section critique.|
|[CComSafeDeleteCriticalSection::Term](#term)|Libère les ressources système utilisées par l’objet de section critique.|

### <a name="data-members"></a>Membres de données

|||
|-|-|
|[m_bInitialized](#m_binitialized)|Signale si l’objet `CRITICAL_SECTION` interne a été initialisé.|

## <a name="remarks"></a>Notes

`CComSafeDeleteCriticalSection` dérive de la classe [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md). Toutefois, `CComSafeDeleteCriticalSection` fournit des mécanismes de sécurité supplémentaires sur [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md).

Lorsqu’une instance de `CComSafeDeleteCriticalSection` est hors de portée ou est supprimée de la mémoire de manière explicite, l’objet de section critique sous-jacent est automatiquement nettoyé s’il est toujours valide. En outre, la méthode [CComSafeDeleteCriticalSection :: term](#term) s’arrête correctement si l’objet de section critique sous-jacent n’a pas encore été alloué ou a déjà été libéré de la mémoire.

Pour plus d’informations sur les classes d’assistance de section critique, consultez [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md) .

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)

`CComSafeDeleteCriticalSection`

## <a name="requirements"></a>Configuration requise pour

**En-tête :** atlcore. h

##  <a name="ccomsafedeletecriticalsection"></a>  CComSafeDeleteCriticalSection::CComSafeDeleteCriticalSection

Constructeur.

```
CComSafeDeleteCriticalSection();
```

### <a name="remarks"></a>Notes

Affecte la valeur FALSe au membre de données [m_bInitialized](#m_binitialized) .

##  <a name="dtor"></a>  CComSafeDeleteCriticalSection::~CComSafeDeleteCriticalSection

Destructeur.

```
~CComSafeDeleteCriticalSection() throw();
```

### <a name="remarks"></a>Notes

Libère l’objet `CRITICAL_SECTION` interne de la mémoire si le membre de données [m_bInitialized](#m_binitialized) a la valeur true.

##  <a name="init"></a>  CComSafeDeleteCriticalSection::Init

Appelle l’implémentation de la classe de base de [init](/visualstudio/debugger/init) et définit [m_bInitialized](#m_binitialized) sur true en cas de réussite.

```
HRESULT Init() throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne le résultat de [CComCriticalSection :: init](../../atl/reference/ccomcriticalsection-class.md#init).

##  <a name="lock"></a>  CComSafeDeleteCriticalSection::Lock

Appelle l’implémentation de la classe de base de [Lock](ccomcriticalsection-class.md#lock).

```
HRESULT Lock();
```

### <a name="return-value"></a>Valeur de retour

Retourne le résultat de [CComCriticalSection :: Lock](../../atl/reference/ccomcriticalsection-class.md#lock).

### <a name="remarks"></a>Notes

Cette méthode suppose que le membre de données [m_bInitialized](#m_binitialized) a la valeur true lors de l’entrée. Une assertion est générée dans les versions Debug si cette condition n’est pas remplie.

Pour plus d’informations sur le comportement de la fonction, consultez [CComCriticalSection :: Lock](../../atl/reference/ccomcriticalsection-class.md#lock).

##  <a name="m_binitialized"></a>  CComSafeDeleteCriticalSection::m_bInitialized

Signale si l’objet `CRITICAL_SECTION` interne a été initialisé.

```
bool m_bInitialized;
```

### <a name="remarks"></a>Notes

Le membre de données `m_bInitialized` est utilisé pour assurer le suivi de la validité de l’objet `CRITICAL_SECTION` sous-jacent associé à la classe [CComSafeDeleteCriticalSection](../../atl/reference/ccomsafedeletecriticalsection-class.md) . L’objet `CRITICAL_SECTION` sous-jacent n’est pas tenté d’être libéré de la mémoire si cet indicateur n’a pas la valeur TRUE.

##  <a name="term"></a>  CComSafeDeleteCriticalSection::Term

Appelle l’implémentation de la classe de base de [CComCriticalSection :: term](../../atl/reference/ccomcriticalsection-class.md#term) si l’objet interne `CRITICAL_SECTION` est valide.

```
HRESULT Term() throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne le résultat de [CComCriticalSection :: term](../../atl/reference/ccomcriticalsection-class.md#term), ou S_OK si [m_bInitialized](#m_binitialized) a la valeur false lors de l’entrée.

### <a name="remarks"></a>Notes

Il est possible d’appeler cette méthode en toute sécurité même si l’objet interne `CRITICAL_SECTION` n’est pas valide. Le destructeur de cette classe appelle cette méthode si le membre de données [m_bInitialized](#m_binitialized) a la valeur true.

## <a name="see-also"></a>Voir aussi

[CComCriticalSection, classe](../../atl/reference/ccomcriticalsection-class.md)<br/>
[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
