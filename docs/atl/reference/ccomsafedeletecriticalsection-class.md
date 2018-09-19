---
title: Ccomsafedeletecriticalsection, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComSafeDeleteCriticalSection
- ATLCORE/ATL::CComSafeDeleteCriticalSection
- ATLCORE/ATL::CComSafeDeleteCriticalSection::CComSafeDeleteCriticalSection
- ATLCORE/ATL::CComSafeDeleteCriticalSection::Init
- ATLCORE/ATL::CComSafeDeleteCriticalSection::Lock
- ATLCORE/ATL::CComSafeDeleteCriticalSection::Term
- ATLCORE/ATL::m_bInitialized
dev_langs:
- C++
helpviewer_keywords:
- CComSafeDeleteCriticalSection class
ms.assetid: 4d2932c4-ba8f-48ec-8664-1db8bed01314
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4b9c82f1d9b4b1a46d134b94842fffe56f457afa
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46118635"
---
# <a name="ccomsafedeletecriticalsection-class"></a>Ccomsafedeletecriticalsection, classe

Cette classe fournit des méthodes pour obtenir et de libérer de la propriété d’un objet de section critique.

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
|[CComSafeDeleteCriticalSection::Init](#init)|Crée et initialise un objet de section critique.|
|[CComSafeDeleteCriticalSection::Lock](#lock)|Obtient la propriété de l’objet de section critique.|
|[CComSafeDeleteCriticalSection::Term](#term)|Libère les ressources système utilisées par l’objet de section critique.|

### <a name="data-members"></a>Membres de données

|||
|-|-|
|[m_bInitialized](#m_binitialized)|Indicateurs si interne `CRITICAL_SECTION` objet a été initialisé.|

## <a name="remarks"></a>Notes

`CComSafeDeleteCriticalSection` dérive de la classe [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md). Toutefois, `CComSafeDeleteCriticalSection` fournit des mécanismes de sécurité supplémentaires sur [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md).

Lorsqu’une instance de `CComSafeDeleteCriticalSection` est hors de portée ou est explicitement supprimé de la mémoire, l’objet de section critique sous-jacent est automatiquement nettoyé s’il est toujours valide. En outre, le [CComSafeDeleteCriticalSection::Term](#term) méthode se termine normalement si l’objet de section critique sous-jacent n’a pas encore été alloué ou a déjà été libéré de la mémoire.

Consultez [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md) pour plus d’informations sur les classes d’assistance de section critique.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)

`CComSafeDeleteCriticalSection`

## <a name="requirements"></a>Configuration requise

**En-tête :** atlcore.h

##  <a name="ccomsafedeletecriticalsection"></a>  CComSafeDeleteCriticalSection::CComSafeDeleteCriticalSection

Constructeur.

```
CComSafeDeleteCriticalSection();
```

### <a name="remarks"></a>Notes

Définit le [m_bInitialized](#m_binitialized) données membres à FALSE.

##  <a name="dtor"></a>  CComSafeDeleteCriticalSection :: ~ CComSafeDeleteCriticalSection

Destructeur.

```
~CComSafeDeleteCriticalSection() throw();
```

### <a name="remarks"></a>Notes

Libère l’interne `CRITICAL_SECTION` de l’objet de la mémoire si le [m_bInitialized](#m_binitialized) membre de données est défini sur TRUE.

##  <a name="init"></a>  CComSafeDeleteCriticalSection::Init

Appelle l’implémentation de classe de base de [Init](/visualstudio/debugger/init) et définit [m_bInitialized](#m_binitialized) sur TRUE si l’opération réussit.

```
HRESULT Init() throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne le résultat de [CComCriticalSection::Init](../../atl/reference/ccomcriticalsection-class.md#init).

##  <a name="lock"></a>  CComSafeDeleteCriticalSection::Lock

Appelle l’implémentation de classe de base de [verrou](ccomcriticalsection-class.md#lock).  

```
HRESULT Lock();
```

### <a name="return-value"></a>Valeur de retour

Retourne le résultat de [CComCriticalSection::Lock](../../atl/reference/ccomcriticalsection-class.md#lock).

### <a name="remarks"></a>Notes

Cette méthode suppose la [m_bInitialized](#m_binitialized) membre de données est défini sur TRUE lors de l’entrée. Une assertion est générée dans les versions Debug si cette condidtion n’est pas remplie.

Pour plus d’informations sur le comportement de la fonction, consultez [CComCriticalSection::Lock](../../atl/reference/ccomcriticalsection-class.md#lock).

##  <a name="m_binitialized"></a>  CComSafeDeleteCriticalSection::m_bInitialized

Indicateurs si interne `CRITICAL_SECTION` objet a été initialisé.

```
bool m_bInitialized;
```

### <a name="remarks"></a>Notes

Le `m_bInitialized` membre de données est utilisé pour effectuer le suivi de la validité de l’objet sous-jacent `CRITICAL_SECTION` objet associé à la [CComSafeDeleteCriticalSection](../../atl/reference/ccomsafedeletecriticalsection-class.md) classe. Sous-jacent `CRITICAL_SECTION` objet ne sera pas tenté à libérer de la mémoire si cet indicateur n’est pas défini sur TRUE.

##  <a name="term"></a>  CComSafeDeleteCriticalSection::Term

Appelle l’implémentation de classe de base de [CComCriticalSection::Term](../../atl/reference/ccomcriticalsection-class.md#term) si interne `CRITICAL_SECTION` objet est valide.

```
HRESULT Term() throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne le résultat de [CComCriticalSection::Term](../../atl/reference/ccomcriticalsection-class.md#term), ou S_OK si [m_bInitialized](#m_binitialized) avait pour valeur FALSE lors de l’entrée.

### <a name="remarks"></a>Notes

Il est déconseillé d’appeler ce même si de méthode interne `CRITICAL_SECTION` objet n’est pas valide. Le destructeur de cette classe appelle cette méthode si le [m_bInitialized](#m_binitialized) membre de données est défini sur TRUE.

## <a name="see-also"></a>Voir aussi

[CComCriticalSection, classe](../../atl/reference/ccomcriticalsection-class.md)<br/>
[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
