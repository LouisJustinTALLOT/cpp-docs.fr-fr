---
title: Classe de CDacl | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CDacl
- ATLSECURITY/ATL::CDacl
- ATLSECURITY/ATL::CDacl::CDacl
- ATLSECURITY/ATL::CDacl::AddAllowedAce
- ATLSECURITY/ATL::CDacl::AddDeniedAce
- ATLSECURITY/ATL::CDacl::GetAceCount
- ATLSECURITY/ATL::CDacl::RemoveAce
- ATLSECURITY/ATL::CDacl::RemoveAllAces
dev_langs:
- C++
helpviewer_keywords:
- CDacl class
ms.assetid: 2dc76616-6362-4967-b6cf-e2d39ca37ddd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2724eebd218cea2795d483351ef91b34c9f1bf39
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32364768"
---
# <a name="cdacl-class"></a>Classe de CDacl
Cette classe est un wrapper pour une structure de la liste DACL (liste de contrôle d’accès discrétionnaire).  
  
> [!IMPORTANT]
>  Cette classe et ses membres ne peut pas être utilisées dans les applications qui s’exécutent dans le Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class CDacl : public CAcl
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CDacl::CDacl](#cdacl)|Constructeur.|  
|[CDacl::~CDacl](#dtor)|Destructeur.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CDacl::AddAllowedAce](#addallowedace)|Ajoute un ACE autorisée (entrée de contrôle d’accès) pour le `CDacl` objet.|  
|[CDacl::AddDeniedAce](#adddeniedace)|Ajoute un ACE refusé à le `CDacl` objet.|  
|[CDacl::GetAceCount](#getacecount)|Retourne le nombre d’ACE (entrées de contrôle d’accès) dans le `CDacl` objet.|  
|[CDacl::RemoveAce](#removeace)|Supprime un ACE spécifique (entrée de contrôle d’accès) de la `CDacl` objet.|  
|[CDacl::RemoveAllAces](#removeallaces)|Supprime tous les ACE contenues dans le `CDacl` objet.|  
  
### <a name="public-operators"></a>Op&#233;rateurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CDacl::operator =](#operator_eq)|Opérateur d'assignation.|  
  
## <a name="remarks"></a>Notes  
 Descripteur de sécurité d’un objet peut contenir une liste DACL. Une liste DACL contient zéro ou plusieurs entrées (contrôle d’accès) qui identifient les utilisateurs et groupes qui peuvent accéder à l’objet. Si une liste DACL est vide (autrement dit, elle contient zéro ACE), aucun accès n’est accordé explicitement, donc l’accès est refusé implicitement. Toutefois, si le descripteur de sécurité d’un objet ne dispose pas d’une liste DACL, l’objet n’est pas protégée et tout le monde dispose d’accès complet.  
  
 Pour récupérer la liste DACL d’un objet, vous devez être propriétaire de l’objet ou avoir accès READ_CONTROL à l’objet. Pour modifier la liste DACL d’un objet, vous devez disposer de l’accès à l’objet WRITE_DAC.  
  
 Utilisez les méthodes de classe fournies pour créer, ajouter, supprimer et supprimer des entrées à partir de la `CDacl` objet. Voir aussi [AtlGetDacl](security-global-functions.md#atlgetdacl) et [AtlSetDacl](security-global-functions.md#atlsetdacl).  
  
 Pour obtenir une présentation du modèle de contrôle d’accès dans Windows, consultez [le contrôle d’accès](http://msdn.microsoft.com/library/windows/desktop/aa374860) dans le Kit de développement logiciel Windows.  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CAcl](../../atl/reference/cacl-class.md)  
  
 `CDacl`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atlsecurity.h  
  
##  <a name="addallowedace"></a>  CDacl::AddAllowedAce  
 Ajoute un ACE autorisée (entrée de contrôle d’accès) pour le `CDacl` objet.  
  
```
bool AddAllowedAce(  
    const CSid& rSid,
    ACCESS_MASK AccessMask,
    BYTE AceFlags = 0) throw(...);

bool AddAllowedAce(  
    const CSid& rSid,
    ACCESS_MASK AccessMask,
    BYTE AceFlags,
    const GUID* pObjectType,
    const GUID* pInheritedObjectType) throw(...);
```  
  
### <a name="parameters"></a>Paramètres  
 `rSid`  
 A [CSid](../../atl/reference/csid-class.md) objet.  
  
 `AccessMask`  
 Spécifie le masque de droits d’accès soit autorisé spécifié `CSid` objet.  
  
 `AceFlags`  
 Un ensemble de bits indicateurs qui contrôlent l’héritage des ACE.  
  
 `pObjectType`  
 Type d'objet.  
  
 `pInheritedObjectType`  
 Le type d’objet hérité.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne **true** si l’ACE est ajoutée à la `CDacl` objet, **false** en cas d’échec.  
  
### <a name="remarks"></a>Notes  
 A `CDacl` objet contient zéro ou plusieurs entrées (contrôle d’accès) qui identifient les utilisateurs et groupes qui peuvent accéder à l’objet. Cette méthode ajoute un ACE qui autorise l’accès à la `CDacl` objet.  
  
 Consultez [ACE_HEADER](http://msdn.microsoft.com/library/windows/desktop/aa374919) pour obtenir une description des indicateurs différents qui peuvent être définies dans le `AceFlags` paramètre.  
  
##  <a name="adddeniedace"></a>  CDacl::AddDeniedAce  
 Ajoute un ACE refusé (entrée de contrôle d’accès) pour le `CDacl` objet.  
  
```
bool AddDeniedAce(  
    const CSid& rSid,
    ACCESS_MASK AccessMask,
    BYTE AceFlags = 0) throw(...);

bool AddDeniedAce(
    const CSid& rSid,
    ACCESS_MASK AccessMask,
    BYTE AceFlags,
    const GUID* pObjectType,
    const GUID* pInheritedObjectType) throw(...);
```  
  
### <a name="parameters"></a>Paramètres  
 `rSid`  
 Objet `CSid`.  
  
 `AccessMask`  
 Spécifie le masque de droits d’accès doit être refusé spécifié `CSid` objet.  
  
 `AceFlags`  
 Un ensemble de bits indicateurs qui contrôlent l’héritage des ACE. La valeur par défaut est 0 dans la première forme de la méthode.  
  
 `pObjectType`  
 Type d'objet.  
  
 `pInheritedObjectType`  
 Le type d’objet hérité.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne **true** si l’ACE est ajoutée à la `CDacl` objet, **false** en cas d’échec.  
  
### <a name="remarks"></a>Notes  
 A `CDacl` objet contient zéro ou plusieurs entrées (contrôle d’accès) qui identifient les utilisateurs et groupes qui peuvent accéder à l’objet. Cette méthode ajoute un ACE qui refuse l’accès à la `CDacl` objet.  
  
 Consultez [ACE_HEADER](http://msdn.microsoft.com/library/windows/desktop/aa374919) pour obtenir une description des indicateurs différents qui peuvent être définies dans le `AceFlags` paramètre.  
  
##  <a name="cdacl"></a>  CDacl::CDacl  
 Constructeur.  
  
```
CDacl (const ACL& rhs) throw(...);  
CDacl () throw();
```  
  
### <a name="parameters"></a>Paramètres  
 `rhs`  
 Existant **ACL** structure (liste de contrôle d’accès).  
  
### <a name="remarks"></a>Notes  
 Le `CDacl` objet peut être éventuellement créé à l’aide d’un fichier **ACL** structure. Il est important de noter que seule une liste DACL (liste de contrôle d’accès discrétionnaire), et pas une liste (SACL) (liste de contrôle d’accès système), doit être passé en tant que ce paramètre. Dans les versions debug, en passant une liste (SACL) entraîne une assertion. Dans les versions release, en passant une liste (SACL) entraîne l’ACE (entrées de contrôle d’accès) dans la liste ACL est ignoré, et aucune erreur ne se produira.  
  
##  <a name="dtor"></a>  CDacl::~CDacl  
 Destructeur.  
  
```
~CDacl () throw();
```  
  
### <a name="remarks"></a>Notes  
 Le destructeur libère les ressources acquises par l’objet, y compris toutes les ACE (entrées de contrôle d’accès) à l’aide de [CDacl::RemoveAllAces](#removeallaces).  
  
##  <a name="getacecount"></a>  CDacl::GetAceCount  
 Retourne le nombre d’ACE (entrées de contrôle d’accès) dans le `CDacl` objet.  
  
```
UINT GetAceCount() const throw();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne le nombre d’entrées contenues dans le `CDacl` objet.  
  
##  <a name="operator_eq"></a>  CDacl::operator =  
 Opérateur d'assignation.  
  
```
CDacl& operator= (const ACL& rhs) throw(...);
```  
  
### <a name="parameters"></a>Paramètres  
 `rhs`  
 La liste ACL (liste de contrôle d’accès) pour affecter à l’objet existant.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne une référence à la mise à jour `CDacl` objet.  
  
### <a name="remarks"></a>Notes  
 Vous devez vous assurer que vous passez une liste DACL (liste de contrôle d’accès discrétionnaire) uniquement à cette fonction. En passant une liste SACL (liste de contrôle d’accès système) pour cette fonction provoque une assertion dans les versions debug, mais n’entraînera aucune erreur dans les versions release.  
  
##  <a name="removeace"></a>  CDacl::RemoveAce  
 Supprime un ACE spécifique (entrée de contrôle d’accès) de la `CDacl` objet.  
  
```
void RemoveAce(UINT nIndex) throw();
```  
  
### <a name="parameters"></a>Paramètres  
 `nIndex`  
 Index de l’entrée ACE à supprimer.  
  
### <a name="remarks"></a>Notes  
 Cette méthode est dérivée de [CAtlArray::RemoveAt](../../atl/reference/catlarray-class.md#removeat).  
  
##  <a name="removeallaces"></a>  CDacl::RemoveAllAces  
 Supprime tous les ACE (entrées de contrôle d’accès) contenues dans le `CDacl` objet.  
  
```
void RemoveAllAces() throw();
```  
  
### <a name="remarks"></a>Notes  
 Supprime chaque **ACE** structure (entrée de contrôle d’accès) (le cas échéant) dans le `CDacl` objet.  
  
## <a name="see-also"></a>Voir aussi  
 [Exemple de sécurité](../../visual-cpp-samples.md)   
 [Classe de CAcl](../../atl/reference/cacl-class.md)   
 [ACL](http://msdn.microsoft.com/library/windows/desktop/aa374872)   
 [ACE](http://msdn.microsoft.com/library/windows/desktop/aa374868)   
 [Vue d’ensemble de la classe](../../atl/atl-class-overview.md)   
 [Fonctions globales de sécurité](../../atl/reference/security-global-functions.md)
