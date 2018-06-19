---
title: Classe de CSacl | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CSacl
- ATLSECURITY/ATL::CSacl
- ATLSECURITY/ATL::CSacl::CSacl
- ATLSECURITY/ATL::CSacl::AddAuditAce
- ATLSECURITY/ATL::CSacl::GetAceCount
- ATLSECURITY/ATL::CSacl::RemoveAce
- ATLSECURITY/ATL::CSacl::RemoveAllAces
dev_langs:
- C++
helpviewer_keywords:
- CSacl class
ms.assetid: 8624889b-aebc-4183-9d29-a20f07837f05
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 116e66d36dde016ef902a0b345eec33e46177b6c
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32363582"
---
# <a name="csacl-class"></a>Classe de CSacl
Cette classe est un wrapper pour une structure SACL (liste de contrôle d’accès système).  
  
> [!IMPORTANT]
>  Cette classe et ses membres ne peut pas être utilisées dans les applications qui s’exécutent dans le Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class CSacl : public CAcl
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CSacl::CSacl](#csacl)|Constructeur.|  
|[CSacl::~CSacl](#dtor)|Destructeur.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CSacl::AddAuditAce](#addauditace)|Ajoute une entrée de contrôle d’accès (ACE) d’audit à le `CSacl` objet.|  
|[CSacl::GetAceCount](#getacecount)|Retourne le nombre d’entrées de contrôle d’accès (ACE) dans le `CSacl` objet.|  
|[CSacl::RemoveAce](#removeace)|Supprime un ACE spécifique (entrée de contrôle d’accès) de la **CSacl** objet.|  
|[CSacl::RemoveAllAces](#removeallaces)|Supprime tous les ACE contenues dans le `CSacl` objet.|  
  
### <a name="public-operators"></a>Op&#233;rateurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CSacl::operator =](#operator_eq)|Opérateur d'assignation.|  
  
## <a name="remarks"></a>Notes  
 Une liste (SACL) contient des entrées de contrôle d’accès (ACE) qui spécifient les types de tentatives d’accès qui génèrent des enregistrements d’audit dans le journal des événements de sécurité d’un contrôleur de domaine. Notez qu’une liste (SACL) génère des entrées de journal uniquement sur le contrôleur de domaine où la tentative d’accès s’est produite, et non sur chaque contrôleur de domaine qui contient un réplica de l’objet.  
  
 Pour définir ou récupérer la liste SACL dans le descripteur de sécurité d’un objet, le privilège SE_SECURITY_NAME doit être activé dans le jeton d’accès de la thread en cours. Le groupe Administrateurs dispose de ce privilège accordé par défaut, et il peut être accordée aux autres utilisateurs ou groupes. Avoir le privilège accordé n’est pas tout ce qui est requis : avant de pouvoir effectuer l’opération définie par le privilège, le privilège doit être activé dans le jeton d’accès de sécurité afin de prendre effet. Le modèle permet de privilèges pour être activé uniquement pour les opérations de système spécifique, puis désactivé lorsqu’ils ne sont plus nécessaires. Consultez [AtlGetSacl](security-global-functions.md#atlgetsacl) et [AtlSetSacl](security-global-functions.md#atlsetsacl) pour obtenir des exemples de l’activation SE_SECURITY_NAME.  
  
 Utilisez les méthodes de la classe pour ajouter, supprimer, créer et supprimer des entrées à partir de la **SACL** objet. Voir aussi [AtlGetSacl](security-global-functions.md#atlgetsacl) et [AtlSetSacl](security-global-functions.md#atlsetsacl).  
  
 Pour obtenir une présentation du modèle de contrôle d’accès dans Windows, consultez [le contrôle d’accès](http://msdn.microsoft.com/library/windows/desktop/aa374860) dans le Kit de développement logiciel Windows.  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CAcl](../../atl/reference/cacl-class.md)  
  
 `CSacl`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atlsecurity.h  
  
##  <a name="addauditace"></a>  CSacl::AddAuditAce  
 Ajoute une entrée de contrôle d’accès (ACE) d’audit à le `CSacl` objet.  
  
```
bool AddAuditAce(
    const CSid& rSid,
    ACCESS_MASK AccessMask,
    bool bSuccess,
    bool bFailure,
    BYTE AceFlags = 0) throw(...);

bool AddAuditAce(
    const CSid& rSid,
    ACCESS_MASK AccessMask,
    bool bSuccess,
    bool bFailure,
    BYTE AceFlags,
    const GUID* pObjectType,
    const GUID* pInheritedObjectType) throw(...);
```  
  
### <a name="parameters"></a>Paramètres  
 `rSid`  
 Le [CSid](../../atl/reference/csid-class.md) objet.  
  
 `AccessMask`  
 Spécifie le masque de droits d’accès à auditer spécifié `CSid` objet.  
  
 `bSuccess`  
 Spécifie si les tentatives d’accès autorisés sont vérifiés. Définissez cet indicateur sur True pour activer l’audit ; Sinon, affectez-lui la valeur false.  
  
 *bFailure*  
 Spécifie si les tentatives d’accès refusé sont vérifiés. Définissez cet indicateur sur True pour activer l’audit ; Sinon, affectez-lui la valeur false.  
  
 `AceFlags`  
 Un ensemble de bits indicateurs qui contrôlent l’héritage des ACE.  
  
 `pObjectType`  
 Type d'objet.  
  
 `pInheritedObjectType`  
 Le type d’objet hérité.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne **true** si l’ACE est ajoutée à la `CSacl` objet, **false** en cas d’échec.  
  
### <a name="remarks"></a>Notes  
 A `CSacl` objet contient des entrées de contrôle d’accès (ACE) qui spécifient les types de tentatives d’accès qui génèrent des enregistrements d’audit dans le journal des événements de sécurité. Cette méthode ajoute ce type d’ACE pour le `CSacl` objet.  
  
 Consultez [ACE_HEADER](http://msdn.microsoft.com/library/windows/desktop/aa374919) pour obtenir une description des indicateurs différents qui peuvent être définies dans le `AceFlags` paramètre.  
  
##  <a name="csacl"></a>  CSacl::CSacl  
 Constructeur.  
  
```
CSacl() throw();
CSacl(const ACL& rhs) throw(...);
```  
  
### <a name="parameters"></a>Paramètres  
 `rhs`  
 Existant **ACL** structure (liste de contrôle d’accès).  
  
### <a name="remarks"></a>Notes  
 Le `CSacl` objet peut être éventuellement créé à l’aide d’un fichier **ACL** structure. Assurez-vous que ce paramètre est une liste de contrôle d’accès système (SACL) et non une liste de contrôle d’accès discrétionnaire (DACL). Dans les versions debug, si une liste DACL est fournie une assertion se produit. Dans les versions release, toutes les entrées dans une liste DACL sont ignorées.  
  
##  <a name="dtor"></a>  CSacl::~CSacl  
 Destructeur.  
  
```
~CSacl() throw();
```  
  
### <a name="remarks"></a>Notes  
 Le destructeur libère les ressources acquises par l’objet, y compris toutes les entrées de contrôle d’accès (ACE).  
  
##  <a name="getacecount"></a>  CSacl::GetAceCount  
 Retourne le nombre d’entrées de contrôle d’accès (ACE) dans le `CSacl` objet.  
  
```
UINT GetAceCount() const throw();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne le nombre d’entrées contenues dans le `CSacl` objet.  
  
##  <a name="operator_eq"></a>  CSacl::operator =  
 Opérateur d'assignation.  
  
```
CSacl& operator=(const ACL& rhs) throw(...);
```  
  
### <a name="parameters"></a>Paramètres  
 `rhs`  
 Le **ACL** (liste de contrôle d’accès) pour affecter à l’objet existant.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne une référence à la mise à jour `CSacl` objet. Vérifiez que le **ACL** paramètre est en fait une liste de contrôle d’accès système (SACL) et non une liste de contrôle d’accès discrétionnaire (DACL). Dans les versions debug une assertion se produit et dans les versions release le **ACL** paramètre sera ignoré.  
  
##  <a name="removeace"></a>  CSacl::RemoveAce  
 Supprime un ACE spécifique (entrée de contrôle d’accès) de la **CSacl** objet.  
  
```
void RemoveAce(UINT nIndex) throw();
```  
  
### <a name="parameters"></a>Paramètres  
 `nIndex`  
 Index de l’entrée ACE à supprimer.  
  
### <a name="remarks"></a>Notes  
 Cette méthode est dérivée de [CAtlArray::RemoveAt](../../atl/reference/catlarray-class.md#removeat).  
  
##  <a name="removeallaces"></a>  CSacl::RemoveAllAces  
 Supprime toutes les entrées de contrôle d’accès (ACE) contenues dans le `CSacl` objet.  
  
```
void RemoveAllAces() throw();
```  
  
### <a name="remarks"></a>Notes  
 Supprime chaque **ACE** structure (le cas échéant) dans le `CSacl` objet.  
  
## <a name="see-also"></a>Voir aussi  
 [Classe de CAcl](../../atl/reference/cacl-class.md)   
 [ACL](http://msdn.microsoft.com/library/windows/desktop/aa374872)   
 [ACE](http://msdn.microsoft.com/library/windows/desktop/aa374868)   
 [Vue d’ensemble de la classe](../../atl/atl-class-overview.md)   
 [Fonctions globales de sécurité](../../atl/reference/security-global-functions.md)
