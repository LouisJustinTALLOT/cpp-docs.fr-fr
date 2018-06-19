---
title: Classe de CTokenPrivileges | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CTokenPrivileges
- ATLSECURITY/ATL::CTokenPrivileges
- ATLSECURITY/ATL::CTokenPrivileges::CTokenPrivileges
- ATLSECURITY/ATL::CTokenPrivileges::Add
- ATLSECURITY/ATL::CTokenPrivileges::Delete
- ATLSECURITY/ATL::CTokenPrivileges::DeleteAll
- ATLSECURITY/ATL::CTokenPrivileges::GetCount
- ATLSECURITY/ATL::CTokenPrivileges::GetDisplayNames
- ATLSECURITY/ATL::CTokenPrivileges::GetLength
- ATLSECURITY/ATL::CTokenPrivileges::GetLuidsAndAttributes
- ATLSECURITY/ATL::CTokenPrivileges::GetNamesAndAttributes
- ATLSECURITY/ATL::CTokenPrivileges::GetPTOKEN_PRIVILEGES
- ATLSECURITY/ATL::CTokenPrivileges::LookupPrivilege
dev_langs:
- C++
helpviewer_keywords:
- CTokenPrivileges class
ms.assetid: 89590105-f001-4014-870d-142926091231
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f6c9886b79739f42329b0f306c8bce6afc2d9fa0
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32366508"
---
# <a name="ctokenprivileges-class"></a>Classe de CTokenPrivileges
Cette classe est un wrapper pour le **TOKEN_PRIVILEGES** structure.  
  
> [!IMPORTANT]
>  Cette classe et ses membres ne peut pas être utilisées dans les applications qui s’exécutent dans le Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class CTokenPrivileges
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CTokenPrivileges::CTokenPrivileges](#ctokenprivileges)|Constructeur.|  
|[CTokenPrivileges :: ~ CTokenPrivileges](#dtor)|Destructeur.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CTokenPrivileges::Add](#add)|Ajoute un ou plusieurs des privilèges pour le `CTokenPrivileges` objet.|  
|[CTokenPrivileges::Delete](#delete)|Supprime un privilège à partir de la `CTokenPrivileges` objet.|  
|[CTokenPrivileges::DeleteAll](#deleteall)|Supprime tous les privilèges à partir de la `CTokenPrivileges` objet.|  
|[CTokenPrivileges::GetCount](#getcount)|Retourne le nombre d’entrées de privilège dans le `CTokenPrivileges` objet.|  
|[CTokenPrivileges::GetDisplayNames](#getdisplaynames)|Récupère noms complets pour les privilèges contenus dans le `CTokenPrivileges` objet.|  
|[CTokenPrivileges::GetLength](#getlength)|Retourne la taille de mémoire tampon en octets requis pour conserver le **TOKEN_PRIVILEGES** structure représentée par la `CTokenPrivileges` objet.|  
|[CTokenPrivileges::GetLuidsAndAttributes](#getluidsandattributes)|Récupère les identificateurs uniques local (LUID) et les indicateurs d’attribut à partir de la `CTokenPrivileges` objet.|  
|[CTokenPrivileges::GetNamesAndAttributes](#getnamesandattributes)|Récupère les noms de privilèges et les indicateurs d’attribut à partir de la `CTokenPrivileges` objet.|  
|[CTokenPrivileges::GetPTOKEN_PRIVILEGES](#getptoken_privileges)|Retourne un pointeur vers le **TOKEN_PRIVILEGES** structure.|  
|[CTokenPrivileges::LookupPrivilege](#lookupprivilege)|Récupère l’attribut associé à un nom de privilège.|  
  
### <a name="public-operators"></a>Op&#233;rateurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CTokenPrivileges::operator les TOKEN_PRIVILEGES const *](#operator_const_token_privileges__star)|Convertit une valeur en un pointeur vers le **TOKEN_PRIVILEGES** structure.|  
|[CTokenPrivileges::operator =](#operator_eq)|Opérateur d'assignation.|  
  
## <a name="remarks"></a>Notes  
 Un [jeton d’accès](http://msdn.microsoft.com/library/windows/desktop/aa374909) est un objet qui décrit le contexte de sécurité d’un processus ou thread et est alloué à chaque utilisateur connecté à un système Windows.  
  
 Le jeton d’accès est utilisé pour décrire les différents privilèges de sécurité accordées à chaque utilisateur. Un privilège se compose d’un nombre 64 bits appelé identificateur unique local ( [LUID](http://msdn.microsoft.com/library/windows/desktop/aa379261)) et une chaîne de descripteur.  
  
 Le `CTokenPrivileges` classe est un wrapper pour le [TOKEN_PRIVILEGES](http://msdn.microsoft.com/library/windows/desktop/aa379630) structurer et contient 0 ou plus de privilèges. Des privilèges peuvent être ajoutés, supprimés ou interrogé à l’aide des méthodes de la classe fourni.  
  
 Pour obtenir une présentation du modèle de contrôle d’accès dans Windows, consultez [le contrôle d’accès](http://msdn.microsoft.com/library/windows/desktop/aa374860) dans le Kit de développement logiciel Windows.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atlsecurity.h  
  
##  <a name="add"></a>  CTokenPrivileges::Add  
 Ajoute un ou plusieurs des privilèges pour le `CTokenPrivileges` objet jeton d’accès.  
  
```
bool Add(LPCTSTR pszPrivilege, bool bEnable) throw(...);  
void Add(const TOKEN_PRIVILEGES& rPrivileges) throw(...);
```  
  
### <a name="parameters"></a>Paramètres  
 `pszPrivilege`  
 Pointeur vers une chaîne se terminant par null qui spécifie le nom du privilège, tel que défini dans le Windows NT. Fichier d’en-tête H.  
  
 `bEnable`  
 Si la valeur est true, le privilège est activé. Si la valeur est false, le privilège est désactivé.  
  
 `rPrivileges`  
 Référence à un [TOKEN_PRIVILEGES](http://msdn.microsoft.com/library/windows/desktop/aa379630) structure. Les privilèges et les attributs sont copiés à partir de cette structure et ajoutés à la `CTokenPrivileges` objet.  
  
### <a name="return-value"></a>Valeur de retour  
 La première forme de cette méthode retourne la valeur true si les privilèges sont correctement ajouté, false dans le cas contraire.  
  
##  <a name="ctokenprivileges"></a>  CTokenPrivileges::CTokenPrivileges  
 Constructeur.  
  
```
CTokenPrivileges() throw();
CTokenPrivileges(const CTokenPrivileges& rhs) throw(... );  
CTokenPrivileges(const TOKEN_PRIVILEGES& rPrivileges) throw(...);
```  
  
### <a name="parameters"></a>Paramètres  
 `rhs`  
 Le `CTokenPrivileges` objet à attribuer au nouvel objet.  
  
 `rPrivileges`  
 Le [TOKEN_PRIVILEGES](http://msdn.microsoft.com/library/windows/desktop/aa379630) à attribuer à la nouvelle structure `CTokenPrivileges` objet.  
  
### <a name="remarks"></a>Notes  
 Le `CTokenPrivileges` objet peut éventuellement être créé à l’aide un **TOKEN_PRIVILEGES** précédemment définie ou structure `CTokenPrivileges` objet.  
  
##  <a name="dtor"></a>  CTokenPrivileges :: ~ CTokenPrivileges  
 Destructeur.  
  
```
virtual ~CTokenPrivileges() throw();
```  
  
### <a name="remarks"></a>Notes  
 Le destructeur libère toutes les ressources attribuées.  
  
##  <a name="delete"></a>  CTokenPrivileges::Delete  
 Supprime un privilège à partir de la `CTokenPrivileges` objet jeton d’accès.  
  
```
bool Delete(LPCTSTR pszPrivilege) throw();
```  
  
### <a name="parameters"></a>Paramètres  
 `pszPrivilege`  
 Pointeur vers une chaîne se terminant par null qui spécifie le nom du privilège, tel que défini dans le Windows NT. Fichier d’en-tête H. Par exemple, ce paramètre peut spécifier la constante SE_SECURITY_NAME ou sa chaîne correspondante, « SeSecurityPrivilege ».  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la valeur true si le privilège a été supprimé avec succès.  
  
### <a name="remarks"></a>Notes  
 Cette méthode est utile en tant qu’outil de création de jetons limités.  
  
##  <a name="deleteall"></a>  CTokenPrivileges::DeleteAll  
 Supprime tous les privilèges à partir de la `CTokenPrivileges` objet jeton d’accès.  
  
```
void DeleteAll() throw();
```  
  
### <a name="remarks"></a>Notes  
 Supprime tous les privilèges contenus dans le `CTokenPrivileges` objet jeton d’accès.  
  
##  <a name="getdisplaynames"></a>  CTokenPrivileges::GetDisplayNames  
 Récupère noms complets pour les privilèges contenus dans le `CTokenPrivileges` objet jeton d’accès.  
  
```
void GetDisplayNames(CNames* pDisplayNames) const throw(...);
```  
  
### <a name="parameters"></a>Paramètres  
 `pDisplayNames`  
 Pointeur vers un tableau d'objets `CString`. **Enregistrements CNAME** est défini comme un typedef : **CTokenPrivileges::CAtlArray\<CString >**.  
  
### <a name="remarks"></a>Notes  
 Le paramètre `pDisplayNames` est un pointeur vers un tableau de `CString` objets afin de recevront les noms d’affichage correspondant aux privilèges contenus dans le `CTokenPrivileges` objet. Cette méthode récupère les noms d’affichage uniquement pour les privilèges spécifiés dans la section définie par les privilèges de Windows NT. H.  
  
 Cette méthode récupère un nom affichable : par exemple, si le nom d’attribut est SE_REMOTE_SHUTDOWN_NAME, le nom complet est « Forcer l’arrêt à partir d’un système distant ». Pour obtenir le nom du système, utilisez [CTokenPrivileges::GetNamesAndAttributes](#getnamesandattributes).  
  
##  <a name="getcount"></a>  CTokenPrivileges::GetCount  
 Retourne le nombre d’entrées de privilège dans le `CTokenPrivileges` objet.  
  
```
UINT GetCount() const throw();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne le nombre de privilèges contenus dans le `CTokenPrivileges` objet.  
  
##  <a name="getlength"></a>  CTokenPrivileges::GetLength  
 Retourne la longueur de la `CTokenPrivileges` objet.  
  
```
UINT GetLength() const throw();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne le nombre d’octets requis pour conserver un **TOKEN_PRIVILEGES** structure représentée par la `CTokenPrivileges` objet, y compris toutes les entrées de privilège qu’elle contient.  
  
##  <a name="getluidsandattributes"></a>  CTokenPrivileges::GetLuidsAndAttributes  
 Récupère les identificateurs uniques local (LUID) et les indicateurs d’attribut à partir de la `CTokenPrivileges` objet.  
  
```
void GetLuidsAndAttributes(
    CLUIDArray* pPrivileges,
    CAttributes* pAttributes = NULL) const throw(...);
```  
  
### <a name="parameters"></a>Paramètres  
 `pPrivileges`  
 Pointeur vers un tableau de [LUID](http://msdn.microsoft.com/library/windows/desktop/aa379261) objets. **CLUIDArray** est un typedef défini en tant que **CAtlArray\<LUID > CLUIDArray**.  
  
 `pAttributes`  
 Pointeur vers un tableau d’objets DWORD. Si ce paramètre est omis ou NULL, les attributs ne sont pas récupérées. **CAttributes** est un typedef défini en tant que **CAtlArray \<DWORD > CAttributes**.  
  
### <a name="remarks"></a>Notes  
 Cette méthode énumérera tous les privilèges contenus dans le `CTokenPrivileges` objet du jeton d’accès et placer la liste des LUID individuels et (facultativement) les indicateurs d’attributs dans des objets de tableau.  
  
##  <a name="getnamesandattributes"></a>  CTokenPrivileges::GetNamesAndAttributes  
 Récupère les nom et l’attribut indicateurs à partir de la `CTokenPrivileges` objet.  
  
```
void GetNamesAndAttributes(
    CNames* pNames,
    CAttributes* pAttributes = NULL) const throw(...);
```  
  
### <a name="parameters"></a>Paramètres  
 *pNames*  
 Pointeur vers un tableau de `CString` objets. **Enregistrements CNAME** est un typedef défini en tant que **CAtlArray \<CString > CNAME**.  
  
 `pAttributes`  
 Pointeur vers un tableau d’objets DWORD. Si ce paramètre est omis ou NULL, les attributs ne sont pas récupérées. **CAttributes** est un typedef défini en tant que **CAtlArray \<DWORD > CAttributes**.  
  
### <a name="remarks"></a>Notes  
 Cette méthode énumérera tous les privilèges contenus dans le `CTokenPrivileges` objet, en plaçant le nom et (facultativement) les indicateurs d’attributs dans des objets de tableau.  
  
 Cette méthode récupère le nom d’attribut, plutôt que le nom peut être affichée : par exemple, si le nom d’attribut est SE_REMOTE_SHUTDOWN_NAME, le nom du système est « SeRemoteShutdownPrivilege. » Pour obtenir le nom peut être affichée, utilisez la méthode [CTokenPrivileges::GetDisplayNames](#getdisplaynames).  
  
##  <a name="getptoken_privileges"></a>  CTokenPrivileges::GetPTOKEN_PRIVILEGES  
 Retourne un pointeur vers le **TOKEN_PRIVILEGES** structure.  
  
```
const TOKEN_PRIVILEGES* GetPTOKEN_PRIVILEGES() const throw(...);
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne un pointeur vers le [TOKEN_PRIVILEGES](http://msdn.microsoft.com/library/windows/desktop/aa379630) structure.  
  
##  <a name="lookupprivilege"></a>  CTokenPrivileges::LookupPrivilege  
 Récupère l’attribut associé à un nom de privilège.  
  
```
bool LookupPrivilege(
    LPCTSTR pszPrivilege,
    DWORD* pdwAttributes = NULL) const throw(...);
```  
  
### <a name="parameters"></a>Paramètres  
 `pszPrivilege`  
 Pointeur vers une chaîne se terminant par null qui spécifie le nom du privilège, tel que défini dans le Windows NT. Fichier d’en-tête H. Par exemple, ce paramètre peut spécifier la constante SE_SECURITY_NAME ou sa chaîne correspondante, « SeSecurityPrivilege ».  
  
 `pdwAttributes`  
 Pointeur vers une variable qui reçoit les attributs.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la valeur true si l’attribut est récupérée avec succès, false dans le cas contraire.  
  
##  <a name="operator_eq"></a>  CTokenPrivileges::operator =  
 Opérateur d'assignation.  
  
```
CTokenPrivileges& operator= (const TOKEN_PRIVILEGES& rPrivileges) throw(...);  
CTokenPrivileges& operator= (const CTokenPrivileges& rhs) throw(...);
```  
  
### <a name="parameters"></a>Paramètres  
 `rPrivileges`  
 Le [TOKEN_PRIVILEGES](http://msdn.microsoft.com/library/windows/desktop/aa379630) structure à attribuer à la `CTokenPrivileges` objet.  
  
 `rhs`  
 Le `CTokenPrivileges` objet à attribuer à l’objet.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la mise à jour `CTokenPrivileges` objet.  
  
##  <a name="operator_const_token_privileges__star"></a>  CTokenPrivileges::operator les TOKEN_PRIVILEGES const *  
 Convertit une valeur en un pointeur vers le **TOKEN_PRIVILEGES** structure.  
  
```  
operator const TOKEN_PRIVILEGES *() const throw(...);
```  
  
### <a name="remarks"></a>Notes  
 Convertit une valeur en un pointeur vers le [TOKEN_PRIVILEGES](http://msdn.microsoft.com/library/windows/desktop/aa379630) structure.  
  
## <a name="see-also"></a>Voir aussi  
 [Exemple de sécurité](../../visual-cpp-samples.md)   
 [TOKEN_PRIVILEGES](http://msdn.microsoft.com/library/windows/desktop/aa379630)   
 [LUID](http://msdn.microsoft.com/library/windows/desktop/aa379261)   
 [LUID_AND_ATTRIBUTES](http://msdn.microsoft.com/library/windows/desktop/aa379263)   
 [Vue d’ensemble de la classe](../../atl/atl-class-overview.md)   
 [Fonctions globales de sécurité](../../atl/reference/security-global-functions.md)
