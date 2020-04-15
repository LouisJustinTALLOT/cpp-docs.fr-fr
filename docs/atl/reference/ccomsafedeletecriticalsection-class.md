---
title: Classe CComSafeDeleteCriticalSection
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
ms.openlocfilehash: cb0dc440fc0e79e0023b5fbd6e4ca2345d031d3d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327371"
---
# <a name="ccomsafedeletecriticalsection-class"></a>Classe CComSafeDeleteCriticalSection

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
|[CComSafeDeleteCriticalSection:-CComSafeDeleteCriticalSection](#dtor)|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CComSafeDeleteCriticalSection::Init](#init)|Crée et initialise un objet de section critique.|
|[CComSafeDeleteCriticalSection::Lock](#lock)|Obtient la propriété de l’objet de section critique.|
|[CComSafeDeleteCriticalSection::Terme](#term)|Libère les ressources système utilisées par l’objet de section critique.|

### <a name="data-members"></a>Données membres

|||
|-|-|
|[m_bInitialized](#m_binitialized)|Indique si `CRITICAL_SECTION` l’objet interne a été paradé.|

## <a name="remarks"></a>Notes

`CComSafeDeleteCriticalSection`dérive de la classe [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md). Cependant, `CComSafeDeleteCriticalSection` fournit des mécanismes de sécurité supplémentaires sur [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md).

Lorsqu’une `CComSafeDeleteCriticalSection` instance de sort de portée ou est explicitement supprimée de la mémoire, l’objet de section critique sous-jacent sera automatiquement nettoyé s’il est toujours valide. En outre, le [CComSafeDeleteCriticalSection::Méthode de durée](#term) sortira gracieusement si l’objet de section critique sous-jacente n’a pas encore été alloué ou a déjà été libéré de la mémoire.

Voir [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md) pour plus d’informations sur les classes d’aide de section critique.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)

`CComSafeDeleteCriticalSection`

## <a name="requirements"></a>Spécifications

**En-tête:** atlcore.h

## <a name="ccomsafedeletecriticalsectionccomsafedeletecriticalsection"></a><a name="ccomsafedeletecriticalsection"></a>CComSafeDeleteCriticalSection::CComSafeDeleteCriticalSection

Constructeur.

```
CComSafeDeleteCriticalSection();
```

### <a name="remarks"></a>Notes

Définit le membre [m_bInitialized](#m_binitialized) de données à FALSE.

## <a name="ccomsafedeletecriticalsectionccomsafedeletecriticalsection"></a><a name="dtor"></a>CComSafeDeleteCriticalSection:-CComSafeDeleteCriticalSection

Destructeur.

```
~CComSafeDeleteCriticalSection() throw();
```

### <a name="remarks"></a>Notes

Libère l’objet interne `CRITICAL_SECTION` de mémoire si le membre des données [m_bInitialized](#m_binitialized) est configuré sur TRUE.

## <a name="ccomsafedeletecriticalsectioninit"></a><a name="init"></a>CComSafeDeleteCriticalSection::Init

Appelle la mise en œuvre de la classe de base de [l’Init](/visualstudio/debugger/init) et définit [m_bInitialized](#m_binitialized) à VRAI en cas de succès.

```
HRESULT Init() throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne le résultat de [CComCriticalSection::Init](../../atl/reference/ccomcriticalsection-class.md#init).

## <a name="ccomsafedeletecriticalsectionlock"></a><a name="lock"></a>CComSafeDeleteCriticalSection::Lock

Appelle la mise en œuvre de la classe de base de [Lock](ccomcriticalsection-class.md#lock).

```
HRESULT Lock();
```

### <a name="return-value"></a>Valeur de retour

Retourne le résultat de [CComCriticalSection::Lock](../../atl/reference/ccomcriticalsection-class.md#lock).

### <a name="remarks"></a>Notes

Cette méthode suppose que le [m_bInitialized](#m_binitialized) membre des données est réglé sur TRUE à l’entrée. Une affirmation est générée dans Debug construit si cette condition n’est pas remplie.

Pour plus d’informations sur le comportement de la fonction, se référer à [CComCriticalSection::Lock](../../atl/reference/ccomcriticalsection-class.md#lock).

## <a name="ccomsafedeletecriticalsectionm_binitialized"></a><a name="m_binitialized"></a>CComSafeDeleteCriticalSection::m_bInitialized

Indique si `CRITICAL_SECTION` l’objet interne a été paradé.

```
bool m_bInitialized;
```

### <a name="remarks"></a>Notes

Le `m_bInitialized` membre des données est utilisé `CRITICAL_SECTION` pour suivre la validité de l’objet sous-jacent associé à la classe [CComSafeDeleteCriticalSection.](../../atl/reference/ccomsafedeletecriticalsection-class.md) L’objet sous-jacent `CRITICAL_SECTION` ne sera pas tenté d’être libéré de la mémoire si ce drapeau n’est pas réglé sur TRUE.

## <a name="ccomsafedeletecriticalsectionterm"></a><a name="term"></a>CComSafeDeleteCriticalSection::Terme

Appelle la mise en œuvre de la classe `CRITICAL_SECTION` de base de [CComCriticalSection::Terme](../../atl/reference/ccomcriticalsection-class.md#term) si l’objet interne est valide.

```
HRESULT Term() throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne le résultat de [CComCriticalSection::Terme](../../atl/reference/ccomcriticalsection-class.md#term), ou S_OK si [m_bInitialized](#m_binitialized) a été mis à FALSE à l’entrée.

### <a name="remarks"></a>Notes

Il est sûr d’appeler cette `CRITICAL_SECTION` méthode même si l’objet interne n’est pas valide. Le destructeur de cette classe appelle cette méthode si le membre [m_bInitialized](#m_binitialized) de données est réglé sur TRUE.

## <a name="see-also"></a>Voir aussi

[Classe CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
