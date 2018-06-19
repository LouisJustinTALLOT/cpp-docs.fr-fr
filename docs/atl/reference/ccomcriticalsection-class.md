---
title: Classe de CComCriticalSection | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComCriticalSection
- ATLCORE/ATL::CComCriticalSection
- ATLCORE/ATL::CComCriticalSection::CComCriticalSection
- ATLCORE/ATL::CComCriticalSection::Init
- ATLCORE/ATL::CComCriticalSection::Lock
- ATLCORE/ATL::CComCriticalSection::Term
- ATLCORE/ATL::CComCriticalSection::Unlock
- ATLCORE/ATL::CComCriticalSection::m_sec
dev_langs:
- C++
helpviewer_keywords:
- CComCriticalSection class
ms.assetid: 44e1edd2-90be-4bfe-9739-58e8b419e7d1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 25376aba3cfbade202d1cf95c2218e88713ac22a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32359903"
---
# <a name="ccomcriticalsection-class"></a>Classe de CComCriticalSection
Cette classe fournit des méthodes pour obtenir et de libérer la possession d’un objet de section critique.  
  
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
|[CComCriticalSection::Unlock](#unlock)|Libère la possession de l’objet de section critique.|  
  
### <a name="public-data-members"></a>Membres de données publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CComCriticalSection::m_sec](#m_sec)|A **CRITICAL_SECTION** objet.|  
  
## <a name="remarks"></a>Notes  
 `CComCriticalSection` est semblable à la classe [CComAutoCriticalSection](../../atl/reference/ccomautocriticalsection-class.md), sauf que vous devez explicitement initialiser et libérer de la section critique.  
  
 En général, vous utilisez `CComCriticalSection` via la `typedef` nom [CriticalSection](ccommultithreadmodel-class.md#criticalsection). Ce nom fait référence à `CComCriticalSection` lorsque [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) est utilisé.  

  
 Consultez [CComCritSecLock classe](../../atl/reference/ccomcritseclock-class.md) un moyen plus sûr d’utiliser cette classe que l’appel `Lock` et `Unlock` directement.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atlcore.h  
  
##  <a name="ccomcriticalsection"></a>  CComCriticalSection::CComCriticalSection  
 Constructeur.  
  
```
CComCriticalSection() throw();
```  
  
### <a name="remarks"></a>Notes  
 Définit le [m_sec](#m_sec) membre de données null **.**  
  
##  <a name="init"></a>  CComCriticalSection::Init  
 Appelle la fonction Win32 [InitializeCriticalSection](http://msdn.microsoft.com/library/windows/desktop/ms683472), qui initialise l’objet de section critique contenu dans le [m_sec](#m_sec) membre de données.  
  
```
HRESULT Init() throw();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne `S_OK` en cas de réussite, **E_OUTOFMEMORY** ou **E_FAIL** en cas d’échec.  
  
##  <a name="lock"></a>  CComCriticalSection::Lock  
 Appelle la fonction Win32 [EnterCriticalSection](http://msdn.microsoft.com/library/windows/desktop/ms682608), qui attend jusqu'à ce que le thread peut prendre possession de l’objet de section critique contenue dans le [m_sec](#m_sec) membre de données.  
  
```
HRESULT Lock() throw();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne `S_OK` en cas de réussite, **E_OUTOFMEMORY** ou **E_FAIL** en cas d’échec.  
  
### <a name="remarks"></a>Notes  
 L’objet de section critique doit tout d’abord être initialisé avec un appel à la [Init](#init) (méthode). Lorsque le code protégé a terminé l’exécution, le thread doit appeler [Unlock](#unlock) pour libérer la possession de la section critique.  
  
##  <a name="m_sec"></a>  CComCriticalSection::m_sec  
 Contient un objet de section critique qui est utilisé par tous les `CComCriticalSection` méthodes.  
  
```
CRITICAL_SECTION m_sec;
```  
  
##  <a name="term"></a>  CComCriticalSection::Term  
 Appelle la fonction Win32 [DeleteCriticalSection](http://msdn.microsoft.com/library/windows/desktop/ms682552), ce qui libère toutes les ressources utilisées par l’objet de section critique contenue dans le [m_sec](#m_sec) membre de données.  
  
```
HRESULT Term() throw();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne `S_OK`.  
  
### <a name="remarks"></a>Notes  
 Une fois `Term` a été appelée, les informations critiques section ne peut plus être utilisée pour la synchronisation.  
  
##  <a name="unlock"></a>  CComCriticalSection::Unlock  
 Appelle la fonction Win32 [LeaveCriticalSection](http://msdn.microsoft.com/library/windows/desktop/ms684169), ce qui libère la propriété de l’objet de section critique contenue dans le [m_sec](#m_sec) membre de données.  
  
```
HRESULT Unlock() throw();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne `S_OK`.  
  
### <a name="remarks"></a>Notes  
 Pour tout d’abord obtenir la propriété, le thread doit appeler le [verrou](#lock) (méthode). Chaque appel à `Lock` nécessite un appel correspondant à `Unlock` pour libérer la possession de la section critique.  
  
## <a name="see-also"></a>Voir aussi  
 [Classe de la classe CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md)   
 [Vue d’ensemble de la classe](../../atl/atl-class-overview.md)   
 [CComCritSecLock, classe](../../atl/reference/ccomcritseclock-class.md)
