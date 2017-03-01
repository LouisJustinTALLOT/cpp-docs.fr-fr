---
title: CUrl classe | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL.CUrl
- CUrl
- ATL::CUrl
dev_langs:
- C++
helpviewer_keywords:
- CUrl class
ms.assetid: b3894d34-47b9-4961-9719-4197153793da
caps.latest.revision: 22
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: eda63a8dc704dd471d8078b848d95fc9fb44f58f
ms.lasthandoff: 02/24/2017

---
# <a name="curl-class"></a>Classe de cUrl
Cette classe représente une URL. Il vous permet de manipuler chaque élément de l’URL indépendamment des autres si une URL existante d’analyse de chaîne ou de création d’une chaîne à partir de zéro.  
  
> [!IMPORTANT]
>  Cette classe et ses membres ne peut pas être utilisées dans les applications qui s’exécutent dans le Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class CUrl
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CUrl::CUrl](#curl)|Constructeur.|  
|[CUrl :: ~ CUrl](#dtor)|Destructeur.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CUrl::Canonicalize](#canonicalize)|Appelez cette méthode pour convertir la chaîne d’URL au format canonique.|  
|[CUrl::Clear](#clear)|Appelez cette méthode pour effacer tous les champs URL.|  
|[CUrl::CrackUrl](#crackurl)|Appelez cette méthode pour décoder et analyser l’URL.|  
|[CUrl::CreateUrl](#createurl)|Appelez cette méthode pour créer l’URL.|  
|[CUrl::GetExtraInfo](#getextrainfo)|Appelez cette méthode pour obtenir des informations supplémentaires (telles que *texte* ou # *texte*) à partir de l’URL.|  
|[CUrl::GetExtraInfoLength](#getextrainfolength)|Appelez cette méthode pour obtenir la longueur des informations supplémentaires (telles que *texte* ou # *texte*) pour récupérer à partir de l’URL.|  
|[CUrl::GetHostName](#gethostname)|Appelez cette méthode pour obtenir le nom d’hôte de l’URL.|  
|[CUrl::GetHostNameLength](#gethostnamelength)|Appelez cette méthode pour obtenir la longueur du nom d’hôte.|  
|[CUrl::GetPassword](#getpassword)|Appelez cette méthode pour obtenir le mot de passe de l’URL.|  
|[CUrl::GetPasswordLength](#getpasswordlength)|Appelez cette méthode pour obtenir la longueur du mot de passe.|  
|[CUrl::GetPortNumber](#getportnumber)|Appelez cette méthode pour obtenir le numéro de port en termes de ATL_URL_PORT.|  
|[CUrl::GetScheme](#getscheme)|Appelez cette méthode pour obtenir le schéma d’URL.|  
|[CUrl::GetSchemeName](#getschemename)|Appelez cette méthode pour obtenir le nom de schéma d’URL.|  
|[CUrl::GetSchemeNameLength](#getschemenamelength)|Appelez cette méthode pour obtenir la longueur du nom du schéma de l’URL.|  
|[CUrl::GetUrlLength](#geturllength)|Appelez cette méthode pour obtenir la longueur d’URL.|  
|[CUrl::GetUrlPath](#geturlpath)|Appelez cette méthode pour obtenir le chemin d’accès d’URL.|  
|[CUrl::GetUrlPathLength](#geturlpathlength)|Appelez cette méthode pour obtenir la longueur de chemin d’accès d’URL.|  
|[CUrl::GetUserName](#getusername)|Appelez cette méthode pour obtenir le nom d’utilisateur de l’URL.|  
|[CUrl::GetUserNameLength](#getusernamelength)|Appelez cette méthode pour obtenir la longueur du nom d’utilisateur.|  
|[CUrl::SetExtraInfo](#setextrainfo)|Appelez cette méthode pour définir les informations supplémentaires (telles que *texte* ou # *texte*) de l’URL.|  
|[CUrl::SetHostName](#sethostname)|Appelez cette méthode pour définir le nom d’hôte.|  
|[CUrl::SetPassword](#setpassword)|Appelez cette méthode pour définir le mot de passe.|  
|[CUrl::SetPortNumber](#setportnumber)|Appelez cette méthode pour définir le numéro de port en termes de ATL_URL_PORT.|  
|[CUrl::SetScheme](#setscheme)|Appelez cette méthode pour définir le schéma d’URL.|  
|[CUrl::SetSchemeName](#setschemename)|Appelez cette méthode pour définir le nom de schéma d’URL.|  
|[CUrl::SetUrlPath](#seturlpath)|Appelez cette méthode pour définir le chemin d’accès d’URL.|  
|[CUrl::SetUserName](#setusername)|Appelez cette méthode pour définir le nom d’utilisateur.|  
  
### <a name="public-operators"></a>Op&#233;rateurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CUrl::operator =](#operator_eq)|Assigne le texte spécifié `CUrl` objet actuel `CUrl` objet.|  
  
## <a name="remarks"></a>Remarques  
 `CUrl`vous permet de manipuler les champs d’une URL, telles que le numéro de port ou de chemin d’accès. `CUrl`comprend l’URL sous la forme suivante :  
  
 \<Schéma > : / /\<UserName > :\<mot de passe > @\<nom d’hôte > :\<numéro_port > /\<UrlPath >\<ExtraInfo >  
  
 (Certains champs sont facultatifs.) Par exemple, considérez cette URL :  
  
 http://someone:secret@www.microsoft.com:80/visualc/stuff.htm#contents  
  
 [CUrl::CrackUrl](#crackurl) analyse comme suit :  
  
-   Schéma : « http » ou [ATL_URL_SCHEME_HTTP](atl-url-scheme-enum.md)  
  
-   Nom d’utilisateur : « quelqu'un »  
  
-   Mot de passe : « secret »  
  
-   Nom d’hôte : « www.microsoft.com »  
  
-   Numéro de port : 80  
  
-   UrlPath : « visualc/stuff.htm »  
  
-   ExtraInfo : « #contents »  
  
 Pour manipuler le champ UrlPath (par exemple), vous utiliseriez [GetUrlPath](#geturlpath), [GetUrlPathLength](#geturlpathlength), et [SetUrlPath](#seturlpath). Vous utiliseriez [CreateUrl](#createurl) pour créer la chaîne URL complète.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atlutil.h  
  
##  <a name="a-namecanonicalizea--curlcanonicalize"></a><a name="canonicalize"></a>CUrl::Canonicalize  
 Appelez cette méthode pour convertir la chaîne d’URL au format canonique.  
  
```
inline BOOL Canonicalize(DWORD dwFlags = 0) throw();
```  
  
### <a name="parameters"></a>Paramètres  
 `dwFlags`  
 Les indicateurs qui contrôlent la canonisation. Si aucun indicateur n’est spécifié ( `dwFlags` = 0), la méthode convertit tous les caractères non sécurisés et les séquences de métadonnées (tel que \\., \.., et \\...) pour échapper les séquences. `dwFlags`peut prendre l’une des valeurs suivantes :  
  
-   ATL_URL_BROWSER_MODE : Ne pas coder ou décoder les caractères après « # » ou « » et ne supprime pas l’espace blanc de fin après « ». Si cette valeur n’est pas spécifiée, l’URL entière est encodé et espace blanc de fin est supprimé.  
  
-   ATL_URL _DECODE : convertit toutes les séquences de XX % en caractères, y compris les séquences d’échappement, avant que l’URL est analysée.  
  
-   ATL_URL _ENCODE_PERCENT : encode des signes de pourcentage rencontrés. Par défaut, les signes de pourcentage ne sont pas encodées.  
  
-   ATL_URL _ENCODE_SPACES_ONLY : encode des espaces uniquement.  
  
-   ATL_URL _NO_ENCODE : ne convertit pas les caractères non sécurisés en séquences d’échappement.  
  
-   ATL_URL _NO_META : ne supprime pas les séquences de métadonnées (tel que «. « et ».. ») à partir de l’URL.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la valeur TRUE en cas de réussite, FALSE en cas d’échec.  
  
### <a name="remarks"></a>Remarques  
 Conversion au format canonique implique la conversion des caractères non sécurisés et les séquences d’échappement d’espaces.  
  
##  <a name="a-namecleara--curlclear"></a><a name="clear"></a>CUrl::Clear  
 Appelez cette méthode pour effacer tous les champs URL.  
  
```
inline void Clear() throw();
```  
  
##  <a name="a-namecrackurla--curlcrackurl"></a><a name="crackurl"></a>CUrl::CrackUrl  
 Appelez cette méthode pour décoder et analyser l’URL.  
  
```
BOOL CrackUrl(LPCTSTR lpszUrl, DWORD dwFlags = 0) throw();
```  
  
### <a name="parameters"></a>Paramètres  
 `lpszUrl`  
 L’URL.  
  
 `dwFlags`  
 Spécifier ATL_URL_DECODE ou ATL_URL_ESCAPE pour convertir tous les caractères d’échappement `lpszUrl` à leurs valeurs réelles après l’analyse. (Avant Visual C++ 2005, ATL_URL_DECODE convertir tous les caractères d’échappement avant l’analyse.)  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la valeur TRUE en cas de réussite, FALSE en cas d’échec.  
  
##  <a name="a-namecreateurla--curlcreateurl"></a><a name="createurl"></a>CUrl::CreateUrl  
 Cette méthode construit une chaîne d’URL à partir de champs d’un objet CUrl.  
  
```
inline BOOL CreateUrl(
    LPTSTR lpszUrl,
    DWORD* pdwMaxLength,
    DWORD dwFlags = 0) const throw();
```  
  
### <a name="parameters"></a>Paramètres  
 *lpszUrl*  
 Un mémoire tampon de chaîne pour contenir la chaîne URL complète.  
  
 `pdwMaxLength`  
 La longueur maximale de la *lpszUrl* tampon de chaîne.  
  
 `dwFlags`  
 Spécifiez ATL_URL_ESCAPE pour convertir tous les caractères d’échappement *lpszUrl* à leurs valeurs réelles.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la valeur TRUE en cas de réussite, FALSE en cas d’échec.  
  
### <a name="remarks"></a>Remarques  
 Cette méthode ajoute des champs individuels pour construire la chaîne URL complète au format suivant :  
  
 **\<schéma > : / /\<utilisateur > :\<passer > @\<domaine > :\<port >\<chemin >\<supplémentaire >**  
  
 Lors de l’appel de cette méthode, le `pdwMaxLength` le paramètre doit contenir initialement la longueur maximale de la mémoire tampon de chaîne référencée par le *lpszUrl* paramètre. La valeur de le `pdwMaxLength` paramètre est mis à la longueur réelle de la chaîne d’URL.  
  
### <a name="example"></a>Exemple  
 Cet exemple illustre la création d’un objet CUrl et l’extraction de la chaîne d’URL  
  
 [!code-cpp[NVC_ATL_Utilities&#133;](../../atl/codesnippet/cpp/curl-class_1.cpp)]  
  
##  <a name="a-namecurla--curlcurl"></a><a name="curl"></a>CUrl::CUrl  
 Constructeur.  
  
```
CUrl() throw();
CUrl(const CUrl& urlThat) throw();
```  
  
### <a name="parameters"></a>Paramètres  
 `urlThat`  
 Le `CUrl` objet à copier pour créer l’URL.  
  
##  <a name="a-namedtora--curlcurl"></a><a name="dtor"></a>CUrl :: ~ CUrl  
 Destructeur.  
  
```
~CUrl() throw();
```  
  
##  <a name="a-namegetextrainfoa--curlgetextrainfo"></a><a name="getextrainfo"></a>CUrl::GetExtraInfo  
 Appelez cette méthode pour obtenir des informations supplémentaires (telles que *texte* ou # *texte*) à partir de l’URL.  
  
```
inline LPCTSTR GetExtraInfo() const throw();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne une chaîne contenant les informations supplémentaires.  
  
##  <a name="a-namegetextrainfolengtha--curlgetextrainfolength"></a><a name="getextrainfolength"></a>CUrl::GetExtraInfoLength  
 Appelez cette méthode pour obtenir la longueur des informations supplémentaires (telles que *texte* ou # *texte*) pour récupérer à partir de l’URL.  
  
```
inline DWORD GetExtraInfoLength() const throw();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la longueur de la chaîne contenant les informations supplémentaires.  
  
##  <a name="a-namegethostnamea--curlgethostname"></a><a name="gethostname"></a>CUrl::GetHostName  
 Appelez cette méthode pour obtenir le nom d’hôte de l’URL.  
  
```
inline LPCTSTR GetHostName() const throw();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne le nom d’hôte.  
  
##  <a name="a-namegethostnamelengtha--curlgethostnamelength"></a><a name="gethostnamelength"></a>CUrl::GetHostNameLength  
 Appelez cette méthode pour obtenir la longueur du nom d’hôte.  
  
```
inline DWORD GetHostNameLength() const throw();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne l’hôte de la longueur du nom.  
  
##  <a name="a-namegetpassworda--curlgetpassword"></a><a name="getpassword"></a>CUrl::GetPassword  
 Appelez cette méthode pour obtenir le mot de passe de l’URL.  
  
```
inline LPCTSTR GetPassword() const throw();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne le mot de passe.  
  
##  <a name="a-namegetpasswordlengtha--curlgetpasswordlength"></a><a name="getpasswordlength"></a>CUrl::GetPasswordLength  
 Appelez cette méthode pour obtenir la longueur du mot de passe.  
  
```
inline DWORD GetPasswordLength() const throw();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la longueur de mot de passe.  
  
##  <a name="a-namegetportnumbera--curlgetportnumber"></a><a name="getportnumber"></a>CUrl::GetPortNumber  
 Appelez cette méthode pour obtenir le numéro de port.  
  
```
inline ATL_URL_PORT GetPortNumber() const throw();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne le numéro de port.  
  
##  <a name="a-namegetschemea--curlgetscheme"></a><a name="getscheme"></a>CUrl::GetScheme  
 Appelez cette méthode pour obtenir le schéma d’URL.  
  
```
inline ATL_URL_SCHEME GetScheme() const throw();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne le [ATL_URL_SCHEME](atl-url-scheme-enum.md) valeur décrivant le schéma de l’URL.  
  
##  <a name="a-namegetschemenamea--curlgetschemename"></a><a name="getschemename"></a>CUrl::GetSchemeName  
 Appelez cette méthode pour obtenir le nom de schéma d’URL.  
  
```
inline LPCTSTR GetSchemeName() const throw();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne le nom de schéma d’URL (par exemple, « http » ou « ftp »).  
  
##  <a name="a-namegetschemenamelengtha--curlgetschemenamelength"></a><a name="getschemenamelength"></a>CUrl::GetSchemeNameLength  
 Appelez cette méthode pour obtenir la longueur du nom du schéma de l’URL.  
  
```
inline DWORD GetSchemeNameLength() const throw();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la longueur du nom de schéma URL.  
  
##  <a name="a-namegeturllengtha--curlgeturllength"></a><a name="geturllength"></a>CUrl::GetUrlLength  
 Appelez cette méthode pour obtenir la longueur d’URL.  
  
```
inline DWORD GetUrlLength() const throw();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la longueur d’URL.  
  
##  <a name="a-namegeturlpatha--curlgeturlpath"></a><a name="geturlpath"></a>CUrl::GetUrlPath  
 Appelez cette méthode pour obtenir le chemin d’accès d’URL.  
  
```
inline LPCTSTR GetUrlPath() const throw();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne le chemin d’accès d’URL.  
  
##  <a name="a-namegeturlpathlengtha--curlgeturlpathlength"></a><a name="geturlpathlength"></a>CUrl::GetUrlPathLength  
 Appelez cette méthode pour obtenir la longueur de chemin d’accès d’URL.  
  
```
inline DWORD GetUrlPathLength() const throw();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la longueur de chemin d’accès d’URL.  
  
##  <a name="a-namegetusernamea--curlgetusername"></a><a name="getusername"></a>CUrl::GetUserName  
 Appelez cette méthode pour obtenir le nom d’utilisateur de l’URL.  
  
```
inline LPCTSTR GetUserName() const throw();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne le nom d’utilisateur.  
  
##  <a name="a-namegetusernamelengtha--curlgetusernamelength"></a><a name="getusernamelength"></a>CUrl::GetUserNameLength  
 Appelez cette méthode pour obtenir la longueur du nom d’utilisateur.  
  
```
inline DWORD GetUserNameLength() const throw();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la longueur de nom d’utilisateur.  
  
##  <a name="a-nameoperatoreqa--curloperator-"></a><a name="operator_eq"></a>CUrl::operator =  
 Assigne le texte spécifié `CUrl` objet actuel `CUrl` objet.  
  
```
CUrl& operator= (const CUrl& urlThat) throw();
```  
  
### <a name="parameters"></a>Paramètres  
 `urlThat`  
 Le `CUrl` objet à copier dans l’objet actuel.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne une référence à l’objet actuel.  
  
##  <a name="a-namesetextrainfoa--curlsetextrainfo"></a><a name="setextrainfo"></a>CUrl::SetExtraInfo  
 Appelez cette méthode pour définir les informations supplémentaires (telles que *texte* ou # *texte*) de l’URL.  
  
```
inline BOOL SetExtraInfo(LPCTSTR lpszInfo) throw();
```  
  
### <a name="parameters"></a>Paramètres  
 *lpszInfo*  
 Chaîne contenant les informations supplémentaires à inclure dans l’URL.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la valeur TRUE en cas de réussite, FALSE en cas d’échec.  
  
##  <a name="a-namesethostnamea--curlsethostname"></a><a name="sethostname"></a>CUrl::SetHostName  
 Appelez cette méthode pour définir le nom d’hôte.  
  
```
inline BOOL SetHostName(LPCTSTR lpszHost) throw();
```  
  
### <a name="parameters"></a>Paramètres  
 `lpszHost`  
 Le nom d’hôte.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la valeur TRUE en cas de réussite, FALSE en cas d’échec.  
  
##  <a name="a-namesetpassworda--curlsetpassword"></a><a name="setpassword"></a>CUrl::SetPassword  
 Appelez cette méthode pour définir le mot de passe.  
  
```
inline BOOL SetPassword(LPCTSTR lpszPass) throw();
```  
  
### <a name="parameters"></a>Paramètres  
 *lpszPass*  
 Mot de passe.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la valeur TRUE en cas de réussite, FALSE en cas d’échec.  
  
##  <a name="a-namesetportnumbera--curlsetportnumber"></a><a name="setportnumber"></a>CUrl::SetPortNumber  
 Appelez cette méthode pour définir le numéro de port.  
  
```
inline BOOL SetPortNumber(ATL_URL_PORT nPrt) throw();
```  
  
### <a name="parameters"></a>Paramètres  
 *nPrt*  
 Le numéro de port.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la valeur TRUE en cas de réussite, FALSE en cas d’échec.  
  
##  <a name="a-namesetschemea--curlsetscheme"></a><a name="setscheme"></a>CUrl::SetScheme  
 Appelez cette méthode pour définir le schéma d’URL.  
  
```
inline BOOL SetScheme(ATL_URL_SCHEME nScheme) throw();
```  
  
### <a name="parameters"></a>Paramètres  
 `nScheme`  
 Parmi les [ATL_URL_SCHEME](atl-url-scheme-enum.md) valeurs pour le schéma.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la valeur TRUE en cas de réussite, FALSE en cas d’échec.  
  
### <a name="remarks"></a>Remarques  
 Vous pouvez également définir le schéma par nom (voir [CUrl::SetSchemeName](#setschemename)).  
  
##  <a name="a-namesetschemenamea--curlsetschemename"></a><a name="setschemename"></a>CUrl::SetSchemeName  
 Appelez cette méthode pour définir le nom de schéma d’URL.  
  
```
inline BOOL SetSchemeName(LPCTSTR lpszSchm) throw();
```  
  
### <a name="parameters"></a>Paramètres  
 *lpszSchm*  
 Nom de schéma d’URL.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la valeur TRUE en cas de réussite, FALSE en cas d’échec.  
  
### <a name="remarks"></a>Remarques  
 Vous pouvez également définir le schéma en utilisant un [ATL_URL_SCHEME](atl-url-scheme-enum.md) constant (voir [CUrl::SetScheme](#setscheme)).  
  
##  <a name="a-nameseturlpatha--curlseturlpath"></a><a name="seturlpath"></a>CUrl::SetUrlPath  
 Appelez cette méthode pour définir le chemin d’accès d’URL.  
  
```
inline BOOL SetUrlPath(LPCTSTR lpszPath) throw();
```  
  
### <a name="parameters"></a>Paramètres  
 `lpszPath`  
 Le chemin d’accès de l’URL.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la valeur TRUE en cas de réussite, FALSE en cas d’échec.  
  
##  <a name="a-namesetusernamea--curlsetusername"></a><a name="setusername"></a>CUrl::SetUserName  
 Appelez cette méthode pour définir le nom d’utilisateur.  
  
```
inline BOOL SetUserName(LPCTSTR lpszUser) throw();
```  
  
### <a name="parameters"></a>Paramètres  
 *lpszUser*  
 Nom d'utilisateur.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la valeur TRUE en cas de réussite, FALSE en cas d’échec.  
  
## <a name="see-also"></a>Voir aussi  
 [Classes](../../atl/reference/atl-classes.md)

