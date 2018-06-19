---
title: Classe de CTokenGroups | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CTokenGroups
- ATLSECURITY/ATL::CTokenGroups
- ATLSECURITY/ATL::CTokenGroups::CTokenGroups
- ATLSECURITY/ATL::CTokenGroups::Add
- ATLSECURITY/ATL::CTokenGroups::Delete
- ATLSECURITY/ATL::CTokenGroups::DeleteAll
- ATLSECURITY/ATL::CTokenGroups::GetCount
- ATLSECURITY/ATL::CTokenGroups::GetLength
- ATLSECURITY/ATL::CTokenGroups::GetPTOKEN_GROUPS
- ATLSECURITY/ATL::CTokenGroups::GetSidsAndAttributes
- ATLSECURITY/ATL::CTokenGroups::LookupSid
dev_langs:
- C++
helpviewer_keywords:
- CTokenGroups class
ms.assetid: 2ab08076-4b08-4487-bc70-ec6dee304190
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8ccf73cdeac0e7522551c6ddb7bef6b0122297ca
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32365492"
---
# <a name="ctokengroups-class"></a>Classe de CTokenGroups
Cette classe est un wrapper pour le **TOKEN_GROUPS** structure.  
  
> [!IMPORTANT]
>  Cette classe et ses membres ne peut pas être utilisées dans les applications qui s’exécutent dans le Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class CTokenGroups
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CTokenGroups::CTokenGroups](#ctokengroups)|Constructeur.|  
|[CTokenGroups::~CTokenGroups](#dtor)|Destructeur.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CTokenGroups::Add](#add)|Ajoute un `CSid` ou existante **TOKEN_GROUPS** structure le `CTokenGroups` objet.|  
|[CTokenGroups::Delete](#delete)|Supprime un `CSid` et ses attributs associés à partir de la `CTokenGroups` objet.|  
|[CTokenGroups::DeleteAll](#deleteall)|Supprime tous les `CSid` objets et leurs attributs associés à partir de la `CTokenGroups` objet.|  
|[CTokenGroups::GetCount](#getcount)|Retourne le nombre de `CSid` objets et attributs associés contenus dans le **CTokenGroups** objet.|  
|[CTokenGroups::GetLength](#getlength)|Retourne la taille de la `CTokenGroups` objet.|  
|[CTokenGroups::GetPTOKEN_GROUPS](#getptoken_groups)|Récupère un pointeur vers le **TOKEN_GROUPS** structure.|  
|[CTokenGroups::GetSidsAndAttributes](#getsidsandattributes)|Récupère le `CSid` objets et attributs appartenant à la `CTokenGroups` objet.|  
|[CTokenGroups::LookupSid](#lookupsid)|Récupère les attributs associés à un `CSid` objet.|  
  
### <a name="public-operators"></a>Op&#233;rateurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CTokenGroups::operator les TOKEN_GROUPS const *](#operator_const_token_groups__star)|Les casts le `CTokenGroups` objet vers un pointeur vers le **TOKEN_GROUPS** structure.|  
|[CTokenGroups::operator =](#operator_eq)|Opérateur d'assignation.|  
  
## <a name="remarks"></a>Notes  
 Un [jeton d’accès](http://msdn.microsoft.com/library/windows/desktop/aa374909) est un objet qui décrit le contexte de sécurité d’un processus ou thread et est alloué à chaque utilisateur connecté à un système Windows.  
  
 Le **CTokenGroups** classe est un wrapper pour le [TOKEN_GROUPS](http://msdn.microsoft.com/library/windows/desktop/aa379624) structure, contenant des informations sur les identificateurs de sécurité (SID de) groupe dans un jeton d’accès.  
  
 Pour obtenir une présentation du modèle de contrôle d’accès dans Windows, consultez [le contrôle d’accès](http://msdn.microsoft.com/library/windows/desktop/aa374860) dans le Kit de développement logiciel Windows.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atlsecurity.h  
  
##  <a name="add"></a>  CTokenGroups::Add  
 Ajoute un `CSid` ou existante **TOKEN_GROUPS** structure le `CTokenGroups` objet.  
  
```
void Add(const CSid& rSid, DWORD dwAttributes) throw(... );  
void Add(const TOKEN_GROUPS& rTokenGroups) throw(...);
```  
  
### <a name="parameters"></a>Paramètres  
 `rSid`  
 A [CSid](../../atl/reference/csid-class.md) objet.  
  
 `dwAttributes`  
 Les attributs à associer à la `CSid` objet.  
  
 *rTokenGroups*  
 A [TOKEN_GROUPS](http://msdn.microsoft.com/library/windows/desktop/aa379624) structure.  
  
### <a name="remarks"></a>Notes  
 Ces méthodes ajoutent un ou plusieurs `CSid` objets et leurs attributs associés à le `CTokenGroups` objet.  
  
##  <a name="ctokengroups"></a>  CTokenGroups::CTokenGroups  
 Constructeur.  
  
```
CTokenGroups() throw();
CTokenGroups(const CTokenGroups& rhs) throw(... );  
CTokenGroups(const TOKEN_GROUPS& rhs) throw(...);
```  
  
### <a name="parameters"></a>Paramètres  
 `rhs`  
 Le `CTokenGroups` objet ou [TOKEN_GROUPS](http://msdn.microsoft.com/library/windows/desktop/aa379624) structure permettant de construire le `CTokenGroups` objet.  
  
### <a name="remarks"></a>Notes  
 Le `CTokenGroups` objet peut éventuellement être créé à l’aide un **TOKEN_GROUPS** précédemment définie ou structure `CTokenGroups` objet.  
  
##  <a name="dtor"></a>  CTokenGroups::~CTokenGroups  
 Destructeur.  
  
```
virtual ~CTokenGroups() throw();
```  
  
### <a name="remarks"></a>Notes  
 Le destructeur libère toutes les ressources attribuées.  
  
##  <a name="delete"></a>  CTokenGroups::Delete  
 Supprime un `CSid` et ses attributs associés à partir de la `CTokenGroups` objet.  
  
```
bool Delete(const CSid& rSid) throw();
```  
  
### <a name="parameters"></a>Paramètres  
 `rSid`  
 Le [CSid](../../atl/reference/csid-class.md) objet pour lequel l’identificateur de sécurité (SID) et les attributs doivent être supprimés.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne true si le `CSid` est supprimée, false dans le cas contraire.  
  
##  <a name="deleteall"></a>  CTokenGroups::DeleteAll  
 Supprime tous les `CSid` objets et leurs attributs associés à partir de la `CTokenGroups` objet.  
  
```
void DeleteAll() throw();
```  
  
##  <a name="getcount"></a>  CTokenGroups::GetCount  
 Retourne le nombre de `CSid` objets contenus dans `CTokenGroups`.  
  
```
UINT GetCount() const throw();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne le nombre de [CSid](../../atl/reference/csid-class.md) objets et leurs attributs associés contenus dans le `CTokenGroups` objet.  
  
##  <a name="getlength"></a>  CTokenGroups::GetLength  
 Retourne la taille de la **CTokenGroup** objet.  
  
```
UINT GetLength() const throw();
```  
  
### <a name="remarks"></a>Notes  
 Retourne la taille totale de la **CTokenGroup** objet, en octets.  
  
##  <a name="getptoken_groups"></a>  CTokenGroups::GetPTOKEN_GROUPS  
 Récupère un pointeur vers le **TOKEN_GROUPS** structure.  
  
```
const TOKEN_GROUPS* GetPTOKEN_GROUPS() const throw(...);
```  
  
### <a name="return-value"></a>Valeur de retour  
 Récupère un pointeur vers le [TOKEN_GROUPS](http://msdn.microsoft.com/library/windows/desktop/aa379624) structure appartenant à la `CTokenGroups` objet jeton d’accès.  
  
##  <a name="getsidsandattributes"></a>  CTokenGroups::GetSidsAndAttributes  
 Récupère le `CSid` objets et (facultativement) les attributs appartenant à la `CTokenGroups` objet.  
  
```
void GetSidsAndAttributes(
    CSid::CSidArray* pSids,
    CAtlArray<DWORD>* pAttributes = NULL) const throw(...);
```  
  
### <a name="parameters"></a>Paramètres  
 `pSids`  
 Pointeur vers un tableau de [CSid](../../atl/reference/csid-class.md) objets.  
  
 `pAttributes`  
 Pointeur vers un tableau de valeurs de type DWORD. Si ce paramètre est omis ou NULL, les attributs ne sont pas récupérées.  
  
### <a name="remarks"></a>Notes  
 Cette méthode énumérera tous les `CSid` objets contenus dans le `CTokenGroups` de l’objet et placer les et (facultativement) les indicateurs d’attributs dans les objets array.  
  
##  <a name="lookupsid"></a>  CTokenGroups::LookupSid  
 Récupère les attributs associés à un `CSid` objet.  
  
```
bool LookupSid(  
    const CSid& rSid,
    DWORD* pdwAttributes = NULL) const throw();
```  
  
### <a name="parameters"></a>Paramètres  
 `rSid`  
 Le [CSid](../../atl/reference/csid-class.md) objet.  
  
 `pdwAttributes`  
 Pointeur vers un DWORD qui acceptera les `CSid` attribut de l’objet. Si cet argument est omis ou NULL, l’attribut n’est pas récupérée.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne true si le `CSid` est trouvé, false dans le cas contraire.  
  
### <a name="remarks"></a>Notes  
 Paramètre `pdwAttributes` à NULL offre un moyen permettant de confirmer l’existence de la `CSid` sans accéder à l’attribut. Notez que cette méthode ne doit pas être utilisée pour vérifier les droits d’accès. Les applications doivent utiliser à la place la [CAccessToken::CheckTokenMembership](../../atl/reference/caccesstoken-class.md#checktokenmembership) (méthode).  
  
##  <a name="operator_eq"></a>  CTokenGroups::operator =  
 Opérateur d'assignation.  
  
```
CTokenGroups& operator= (const TOKEN_GROUPS& rhs) throw(...);  
CTokenGroups& operator= (const CTokenGroups& rhs) throw(...);
```  
  
### <a name="parameters"></a>Paramètres  
 `rhs`  
 Le `CTokenGroups` objet ou [TOKEN_GROUPS](http://msdn.microsoft.com/library/windows/desktop/aa379624) structure à attribuer à la `CTokenGroups` objet.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la mise à jour `CTokenGroups` objet.  
  
##  <a name="operator_const_token_groups__star"></a>  CTokenGroups::operator les TOKEN_GROUPS const *  
 Convertit une valeur en un pointeur vers le **TOKEN_GROUPS** structure.  
  
```  
operator const TOKEN_GROUPS *() const throw(...);
```  
  
### <a name="remarks"></a>Notes  
 Convertit une valeur en un pointeur vers le [TOKEN_GROUPS](http://msdn.microsoft.com/library/windows/desktop/aa379624) structure.  
  
## <a name="see-also"></a>Voir aussi  
 [Exemple de sécurité](../../visual-cpp-samples.md)   
 [Classe de CSid](../../atl/reference/csid-class.md)   
 [Vue d’ensemble de la classe](../../atl/atl-class-overview.md)   
 [Fonctions globales de sécurité](../../atl/reference/security-global-functions.md)
