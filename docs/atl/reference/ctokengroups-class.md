---
title: CTokenGroups, classe | Microsoft Docs
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
ms.openlocfilehash: 72fd8530a05bb0b61af266ca78a1c2fa6716ee6b
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2018
ms.locfileid: "43206614"
---
# <a name="ctokengroups-class"></a>CTokenGroups, classe
Cette classe est un wrapper pour le `TOKEN_GROUPS` structure.  
  
> [!IMPORTANT]
>  Cette classe et ses membres ne peut pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.  
  
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
|[CTokenGroups::Add](#add)|Ajoute un `CSid` ou existant `TOKEN_GROUPS` structure le `CTokenGroups` objet.|  
|[CTokenGroups::Delete](#delete)|Supprime un `CSid` et ses attributs associés à partir de la `CTokenGroups` objet.|  
|[CTokenGroups::DeleteAll](#deleteall)|Supprime tous les `CSid` objets et leurs attributs associés à partir de la `CTokenGroups` objet.|  
|[CTokenGroups::GetCount](#getcount)|Retourne le nombre de `CSid` objets et attributs associés contenus dans le `CTokenGroups` objet.|  
|[CTokenGroups::GetLength](#getlength)|Retourne la taille de la `CTokenGroups` objet.|  
|[CTokenGroups::GetPTOKEN_GROUPS](#getptoken_groups)|Récupère un pointeur vers le `TOKEN_GROUPS` structure.|  
|[CTokenGroups::GetSidsAndAttributes](#getsidsandattributes)|Récupère le `CSid` objets et attributs appartenant à la `CTokenGroups` objet.|  
|[CTokenGroups::LookupSid](#lookupsid)|Récupère les attributs associés à un `CSid` objet.|  
  
### <a name="public-operators"></a>Op&#233;rateurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[TOKEN_GROUPS const CTokenGroups::operator *](#operator_const_token_groups__star)|Les casts le `CTokenGroups` objet vers un autre pointeur vers le `TOKEN_GROUPS` structure.|  
|[CTokenGroups::operator =](#operator_eq)|Opérateur d'assignation.|  
  
## <a name="remarks"></a>Notes  
 Un [jeton d’accès](/windows/desktop/SecAuthZ/access-tokens) est un objet qui décrit le contexte de sécurité d’un processus ou un thread et est alloué à chaque utilisateur connecté à un système Windows.  
  
 Le `CTokenGroups` classe est un wrapper pour le [TOKEN_GROUPS](/windows/desktop/api/winnt/ns-winnt-_token_groups) structure, contenant des informations sur les identificateurs de sécurité (SID de) groupe dans un jeton d’accès.  
  
 Pour une présentation du modèle de contrôle d’accès dans Windows, consultez [contrôle d’accès](/windows/desktop/SecAuthZ/access-control) dans le SDK Windows.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** atlsecurity.h  
  
##  <a name="add"></a>  CTokenGroups::Add  
 Ajoute un `CSid` ou existant `TOKEN_GROUPS` structure le `CTokenGroups` objet.  
  
```
void Add(const CSid& rSid, DWORD dwAttributes) throw(... );  
void Add(const TOKEN_GROUPS& rTokenGroups) throw(...);
```  
  
### <a name="parameters"></a>Paramètres  
 *rSid*  
 Un [CSid](../../atl/reference/csid-class.md) objet.  
  
 *dwAttributes*  
 Les attributs à associer à la `CSid` objet.  
  
 *rTokenGroups*  
 Un [TOKEN_GROUPS](/windows/desktop/api/winnt/ns-winnt-_token_groups) structure.  
  
### <a name="remarks"></a>Notes  
 Ces méthodes ajoutent un ou plusieurs `CSid` objets et leurs attributs associés à la `CTokenGroups` objet.  
  
##  <a name="ctokengroups"></a>  CTokenGroups::CTokenGroups  
 Constructeur.  
  
```
CTokenGroups() throw();
CTokenGroups(const CTokenGroups& rhs) throw(... );  
CTokenGroups(const TOKEN_GROUPS& rhs) throw(...);
```  
  
### <a name="parameters"></a>Paramètres  
 *terme de droite*  
 Le `CTokenGroups` objet ou [TOKEN_GROUPS](/windows/desktop/api/winnt/ns-winnt-_token_groups) structure permettant de construire le `CTokenGroups` objet.  
  
### <a name="remarks"></a>Notes  
 Le `CTokenGroups` objet peut éventuellement être créé à l’aide un `TOKEN_GROUPS` précédemment définie ou structure `CTokenGroups` objet.  
  
##  <a name="dtor"></a>  CTokenGroups::~CTokenGroups  
 Destructeur.  
  
```
virtual ~CTokenGroups() throw();
```  
  
### <a name="remarks"></a>Notes  
 Le destructeur libère toutes les ressources allouées.  
  
##  <a name="delete"></a>  CTokenGroups::Delete  
 Supprime un `CSid` et ses attributs associés à partir de la `CTokenGroups` objet.  
  
```
bool Delete(const CSid& rSid) throw();
```  
  
### <a name="parameters"></a>Paramètres  
 *rSid*  
 Le [CSid](../../atl/reference/csid-class.md) objet pour lequel l’identificateur de sécurité (SID) et les attributs doivent être supprimés.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne true si le `CSid` est supprimée, false sinon.  
  
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
 Retourne la taille de la `CTokenGroup` objet.  
  
```
UINT GetLength() const throw();
```  
  
### <a name="remarks"></a>Notes  
 Retourne la taille totale de la `CTokenGroup` objet, en octets.  
  
##  <a name="getptoken_groups"></a>  CTokenGroups::GetPTOKEN_GROUPS  
 Récupère un pointeur vers le `TOKEN_GROUPS` structure.  
  
```
const TOKEN_GROUPS* GetPTOKEN_GROUPS() const throw(...);
```  
  
### <a name="return-value"></a>Valeur de retour  
 Récupère un pointeur vers le [TOKEN_GROUPS](/windows/desktop/api/winnt/ns-winnt-_token_groups) structure appartenant à la `CTokenGroups` objet de jeton d’accès.  
  
##  <a name="getsidsandattributes"></a>  CTokenGroups::GetSidsAndAttributes  
 Récupère le `CSid` objets et (éventuellement) les attributs appartenant à la `CTokenGroups` objet.  
  
```
void GetSidsAndAttributes(
    CSid::CSidArray* pSids,
    CAtlArray<DWORD>* pAttributes = NULL) const throw(...);
```  
  
### <a name="parameters"></a>Paramètres  
 *pSids*  
 Pointeur vers un tableau de [CSid](../../atl/reference/csid-class.md) objets.  
  
 *pAttributes*  
 Pointeur vers un tableau de valeurs de type DWORD. Si ce paramètre est omis ou NULL, les attributs ne sont pas récupérées.  
  
### <a name="remarks"></a>Notes  
 Cette méthode énumérera tous les `CSid` objets contenus dans le `CTokenGroups` de l’objet et de placer les et (éventuellement) les indicateurs d’attribut dans les objets de tableau.  
  
##  <a name="lookupsid"></a>  CTokenGroups::LookupSid  
 Récupère les attributs associés à un `CSid` objet.  
  
```
bool LookupSid(  
    const CSid& rSid,
    DWORD* pdwAttributes = NULL) const throw();
```  
  
### <a name="parameters"></a>Paramètres  
 *rSid*  
 Le [CSid](../../atl/reference/csid-class.md) objet.  
  
 *pdwAttributes*  
 Pointeur vers une valeur DWORD qui acceptera le `CSid` attribut de l’objet. Si cet argument est omis ou NULL, l’attribut ne sera pas récupéré.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne true si le `CSid` est trouvée, false sinon.  
  
### <a name="remarks"></a>Notes  
 Paramètre *pdwAttributes* à NULL offre un moyen permettant de confirmer l’existence de la `CSid` sans accéder à l’attribut. Notez que cette méthode ne doit pas être utilisée pour vérifier les droits d’accès. Les applications doivent utiliser à la place la [CAccessToken::CheckTokenMembership](../../atl/reference/caccesstoken-class.md#checktokenmembership) (méthode).  
  
##  <a name="operator_eq"></a>  CTokenGroups::operator =  
 Opérateur d'assignation.  
  
```
CTokenGroups& operator= (const TOKEN_GROUPS& rhs) throw(...);  
CTokenGroups& operator= (const CTokenGroups& rhs) throw(...);
```  
  
### <a name="parameters"></a>Paramètres  
 *terme de droite*  
 Le `CTokenGroups` objet ou [TOKEN_GROUPS](/windows/desktop/api/winnt/ns-winnt-_token_groups) structure à affecter à la `CTokenGroups` objet.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la mise à jour `CTokenGroups` objet.  
  
##  <a name="operator_const_token_groups__star"></a>  TOKEN_GROUPS const CTokenGroups::operator *  
 Convertit une valeur en un pointeur vers le `TOKEN_GROUPS` structure.  
  
```  
operator const TOKEN_GROUPS *() const throw(...);
```  
  
### <a name="remarks"></a>Notes  
 Convertit une valeur en un pointeur vers le [TOKEN_GROUPS](/windows/desktop/api/winnt/ns-winnt-_token_groups) structure.  
  
## <a name="see-also"></a>Voir aussi  
 [Exemple de sécurité](../../visual-cpp-samples.md)   
 [CSid, classe](../../atl/reference/csid-class.md)   
 [Vue d’ensemble de la classe](../../atl/atl-class-overview.md)   
 [Fonctions globales de sécurité](../../atl/reference/security-global-functions.md)
