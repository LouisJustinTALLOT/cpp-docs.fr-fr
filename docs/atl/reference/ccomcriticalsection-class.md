---
title: CComCriticalSection, classe
ms.date: 11/04/2016
f1_keywords:
- CComCriticalSection
- ATLCORE/ATL::CComCriticalSection
- ATLCORE/ATL::CComCriticalSection::CComCriticalSection
- ATLCORE/ATL::CComCriticalSection::Init
- ATLCORE/ATL::CComCriticalSection::Lock
- ATLCORE/ATL::CComCriticalSection::Term
- ATLCORE/ATL::CComCriticalSection::Unlock
- ATLCORE/ATL::CComCriticalSection::m_sec
helpviewer_keywords:
- CComCriticalSection class
ms.assetid: 44e1edd2-90be-4bfe-9739-58e8b419e7d1
ms.openlocfilehash: f3a4b50f8dd9bc460a209c47497e720529c40e58
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57276089"
---
# <a name="ccomcriticalsection-class"></a>CComCriticalSection, classe

Cette classe fournit des méthodes pour obtenir et de libérer de la propriété d’un objet de section critique.

## <a name="syntax"></a>Syntaxe

```
class CComCriticalSection
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CComCriticalSection::CComCriticalSection](#ccomcriticalsection)|Constructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CComCriticalSection::Init](#init)|Crée et initialise un objet de section critique.|
|[CComCriticalSection::Lock](#lock)|Obtient la propriété de l’objet de section critique.|
|[CComCriticalSection::Term](#term)|Libère les ressources système utilisées par l’objet de section critique.|
|[CComCriticalSection::Unlock](#unlock)|Libère la propriété de l’objet de section critique.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CComCriticalSection::m_sec](#m_sec)|Un objet CRITICAL_SECTION.|

## <a name="remarks"></a>Notes

`CComCriticalSection` est semblable à la classe [CComAutoCriticalSection](../../atl/reference/ccomautocriticalsection-class.md), sauf que vous devez explicitement initialiser et libèrera la section critique.

En général, vous utilisez `CComCriticalSection` via la **typedef** nom [CriticalSection](ccommultithreadmodel-class.md#criticalsection). Ce nom fait référence à `CComCriticalSection` lorsque [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) est utilisé.

Consultez [ccomcritseclock, classe](../../atl/reference/ccomcritseclock-class.md) pour un moyen plus sûr d’utiliser cette classe que l’appel `Lock` et `Unlock` directement.

## <a name="requirements"></a>Spécifications

**En-tête :** atlcore.h

##  <a name="ccomcriticalsection"></a>  CComCriticalSection::CComCriticalSection

Constructeur.

```
CComCriticalSection() throw();
```

### <a name="remarks"></a>Notes

Définit le [m_sec](#m_sec) membre de données avec la valeur NULL.

##  <a name="init"></a>  CComCriticalSection::Init

Appelle la fonction Win32 [InitializeCriticalSection](/windows/desktop/api/synchapi/nf-synchapi-initializecriticalsection), ce qui initialise l’objet de section critique contenue dans le [m_sec](#m_sec) membre de données.

```
HRESULT Init() throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, E_OUTOFMEMORY ou E_FAIL en cas d’échec.

##  <a name="lock"></a>  CComCriticalSection::Lock

Appelle la fonction Win32 [EnterCriticalSection](/windows/desktop/api/synchapi/nf-synchapi-entercriticalsection), qui attend que le thread peut prendre possession de l’objet de section critique contenue dans le [m_sec](#m_sec) membre de données.

```
HRESULT Lock() throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, E_OUTOFMEMORY ou E_FAIL en cas d’échec.

### <a name="remarks"></a>Notes

L’objet de section critique doit tout d’abord être initialisé avec un appel à la [Init](#init) (méthode). Lorsque le code protégé a terminé l’exécution, le thread doit appeler [Unlock](#unlock) libère la propriété de la section critique.

##  <a name="m_sec"></a>  CComCriticalSection::m_sec

Contient un objet de section critique qui est utilisé par tous les `CComCriticalSection` méthodes.

```
CRITICAL_SECTION m_sec;
```

##  <a name="term"></a>  CComCriticalSection::Term

Appelle la fonction Win32 [DeleteCriticalSection](/windows/desktop/api/synchapi/nf-synchapi-deletecriticalsection), ce qui libère toutes les ressources utilisées par l’objet de section critique contenue dans le [m_sec](#m_sec) membre de données.

```
HRESULT Term() throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne S_OK.

### <a name="remarks"></a>Notes

Une fois `Term` a été appelée, la critique section peut ne plus être utilisée pour la synchronisation.

##  <a name="unlock"></a>  CComCriticalSection::Unlock

Appelle la fonction Win32 [LeaveCriticalSection](/windows/desktop/api/synchapi/nf-synchapi-leavecriticalsection), ce qui libère la propriété de l’objet de section critique contenue dans le [m_sec](#m_sec) membre de données.

```
HRESULT Unlock() throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne S_OK.

### <a name="remarks"></a>Notes

Pour tout d’abord obtenir la propriété, le thread doit appeler le [verrou](#lock) (méthode). Chaque appel à `Lock` nécessite un appel correspondant à `Unlock` libère la propriété de la section critique.

## <a name="see-also"></a>Voir aussi

[CComFakeCriticalSection, classe](../../atl/reference/ccomfakecriticalsection-class.md)<br/>
[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)<br/>
[CComCritSecLock, classe](../../atl/reference/ccomcritseclock-class.md)
