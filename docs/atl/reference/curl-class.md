---
description: 'En savoir plus sur : classe de boucles'
title: Classe de la boucle
ms.date: 05/06/2019
f1_keywords:
- CUrl
- ATLUTIL/ATL::CUrl
- ATLUTIL/ATL::CUrl::CUrl
- ATLUTIL/ATL::CUrl::Canonicalize
- ATLUTIL/ATL::CUrl::Clear
- ATLUTIL/ATL::CUrl::CrackUrl
- ATLUTIL/ATL::CUrl::CreateUrl
- ATLUTIL/ATL::CUrl::GetExtraInfo
- ATLUTIL/ATL::CUrl::GetExtraInfoLength
- ATLUTIL/ATL::CUrl::GetHostName
- ATLUTIL/ATL::CUrl::GetHostNameLength
- ATLUTIL/ATL::CUrl::GetPassword
- ATLUTIL/ATL::CUrl::GetPasswordLength
- ATLUTIL/ATL::CUrl::GetPortNumber
- ATLUTIL/ATL::CUrl::GetScheme
- ATLUTIL/ATL::CUrl::GetSchemeName
- ATLUTIL/ATL::CUrl::GetSchemeNameLength
- ATLUTIL/ATL::CUrl::GetUrlLength
- ATLUTIL/ATL::CUrl::GetUrlPath
- ATLUTIL/ATL::CUrl::GetUrlPathLength
- ATLUTIL/ATL::CUrl::GetUserName
- ATLUTIL/ATL::CUrl::GetUserNameLength
- ATLUTIL/ATL::CUrl::SetExtraInfo
- ATLUTIL/ATL::CUrl::SetHostName
- ATLUTIL/ATL::CUrl::SetPassword
- ATLUTIL/ATL::CUrl::SetPortNumber
- ATLUTIL/ATL::CUrl::SetScheme
- ATLUTIL/ATL::CUrl::SetSchemeName
- ATLUTIL/ATL::CUrl::SetUrlPath
- ATLUTIL/ATL::CUrl::SetUserName
helpviewer_keywords:
- CUrl class
ms.assetid: b3894d34-47b9-4961-9719-4197153793da
ms.openlocfilehash: e8453c4dd1abbfdcb6d794b89fd55f37d7b3f286
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97140294"
---
# <a name="curl-class"></a>Classe de la boucle

Cette classe représente une URL. Elle vous permet de manipuler chaque élément de l’URL indépendamment des autres, si l’analyse d’une chaîne d’URL existante ou la génération d’une chaîne à partir de zéro.

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
class CUrl
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[Boucle :: courbure](#curl)|Constructeur.|
|[Boucle :: ~](#dtor)|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[Boucle :: Canonicalization](#canonicalize)|Appelez cette méthode pour convertir la chaîne d’URL au format canonique.|
|[Boucle :: Clear](#clear)|Appelez cette méthode pour effacer tous les champs d’URL.|
|[Boucle :: CrackUrl](#crackurl)|Appelez cette méthode pour décoder et analyser l’URL.|
|[Boucle :: CreateUrl](#createurl)|Appelez cette méthode pour créer l’URL.|
|[Boucle :: GetExtraInfo](#getextrainfo)|Appelez cette méthode pour recevoir des informations supplémentaires (telles que *Text* ou # *Text*) à partir de l’URL.|
|[Boucle :: GetExtraInfoLength](#getextrainfolength)|Appelez cette méthode pour obtenir la longueur des informations supplémentaires (telles que *Text* ou # *Text*) à récupérer à partir de l’URL.|
|[Boucle :: GetHostName](#gethostname)|Appelez cette méthode pour récupérer le nom d’hôte à partir de l’URL.|
|[Boucle :: GetHostNameLength](#gethostnamelength)|Appelez cette méthode pour connaître la longueur du nom d’hôte.|
|[Boucle :: GetPassword](#getpassword)|Appelez cette méthode pour récupérer le mot de passe à partir de l’URL.|
|[Boucle :: GetPasswordLength](#getpasswordlength)|Appelez cette méthode pour connaître la longueur du mot de passe.|
|[Boucle :: GetPortNumber](#getportnumber)|Appelez cette méthode pour récupérer le numéro de port en termes de ATL_URL_PORT.|
|[Boucle :: GetScheme](#getscheme)|Appelez cette méthode pour récupérer le schéma d’URL.|
|[Boucle :: GetSchemeName](#getschemename)|Appelez cette méthode pour récupérer le nom du schéma d’URL.|
|[Boucle :: GetSchemeNameLength](#getschemenamelength)|Appelez cette méthode pour connaître la longueur du nom du schéma d’URL.|
|[Boucle :: GetUrlLength](#geturllength)|Appelez cette méthode pour récupérer la longueur de l’URL.|
|[Boucle :: GetUrlPath](#geturlpath)|Appelez cette méthode pour récupérer le chemin d’accès de l’URL.|
|[Boucle :: GetUrlPathLength](#geturlpathlength)|Appelez cette méthode pour accéder à la longueur du chemin d’accès de l’URL.|
|[Boucle :: GetUserName](#getusername)|Appelez cette méthode pour récupérer le nom d’utilisateur à partir de l’URL.|
|[Boucle :: GetUserNameLength](#getusernamelength)|Appelez cette méthode pour connaître la longueur du nom d’utilisateur.|
|[Boucle :: SetExtraInfo](#setextrainfo)|Appelez cette méthode pour définir les informations supplémentaires (telles que *Text* ou # *Text*) de l’URL.|
|[Boucle :: SetHostName](#sethostname)|Appelez cette méthode pour définir le nom d’hôte.|
|[Boucle :: SetPassword](#setpassword)|Appelez cette méthode pour définir le mot de passe.|
|[Boucle :: SetPortNumber](#setportnumber)|Appelez cette méthode pour définir le numéro de port en termes de ATL_URL_PORT.|
|[Boucle :: SetScheme](#setscheme)|Appelez cette méthode pour définir le modèle d’URL.|
|[Boucle :: SetSchemeName](#setschemename)|Appelez cette méthode pour définir le nom du modèle d’URL.|
|[Boucle :: SetUrlPath](#seturlpath)|Appelez cette méthode pour définir le chemin d’accès de l’URL.|
|[Boucle :: SetUserName](#setusername)|Appelez cette méthode pour définir le nom d’utilisateur.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[Boucle :: Operator =](#operator_eq)|Assigne l' `CUrl` objet spécifié à l' `CUrl` objet actuel.|

## <a name="remarks"></a>Notes

`CUrl` vous permet de manipuler les champs d’une URL, tels que le chemin d’accès ou le numéro de port. `CUrl` comprend les URL de la forme suivante :

\<Scheme>://\<UserName>:\<Password>\@\<HostName>:\<PortNumber>/\<UrlPath>\<ExtraInfo>

(Certains champs sont facultatifs.) Par exemple, considérez l’URL suivante :

`http://someone:secret@www.microsoft.com:80/visualc/stuff.htm#contents`

La fonction de [boucle :: CrackUrl](#crackurl) l’analyse comme suit :

- Schéma : « http » ou [ATL_URL_SCHEME_HTTP](atl-url-scheme-enum.md)

- Nom d’utilisateur : « personne »

- Mot de passe : « secret »

- Nom d’hôte : " `www.microsoft.com` "

- Numéro_port : 80

- UrlPath : « VisualC/stuff.htm »

- ExtraInfo : « #contents »

Pour manipuler le champ UrlPath (par exemple), vous devez utiliser [GetUrlPath](#geturlpath), [GetUrlPathLength](#geturlpathlength)et [SetUrlPath](#seturlpath). Vous devez utiliser [CreateUrl](#createurl) pour créer la chaîne d’URL complète.

## <a name="requirements"></a>Spécifications

**En-tête :** atlutil. h

## <a name="curlcanonicalize"></a><a name="canonicalize"></a> Boucle :: Canonicalization

Appelez cette méthode pour convertir la chaîne d’URL au format canonique.

```
inline BOOL Canonicalize(DWORD dwFlags = 0) throw();
```

### <a name="parameters"></a>Paramètres

*dwFlags*<br/>
Indicateurs qui contrôlent la canonisation. Si aucun indicateur n’est spécifié (*dwFlags* = 0), la méthode convertit tous les caractères et séquences de métadonnées non sécurisés (tels que \\ ., \... et \\ ...) en séquences d’échappement. *dwFlags* peut prendre l’une des valeurs suivantes :

- ATL_URL_BROWSER_MODE : n’encode pas ou ne décode pas les caractères après « # » ou « » et ne supprime pas les espaces blancs de fin après « ». Si cette valeur n’est pas spécifiée, l’URL entière est encodée et l’espace blanc de fin est supprimé.

- ATL_URL _DECODE : convertit toutes les séquences% XX en caractères, y compris les séquences d’échappement, avant l’analyse de l’URL.

- ATL_URL _ENCODE_PERCENT : encode tous les signes de pourcentage rencontrés. Par défaut, les signes de pourcentage ne sont pas encodés.

- ATL_URL _ENCODE_SPACES_ONLY : encode uniquement les espaces.

- ATL_URL _NO_ENCODE : ne convertit pas les caractères non sécurisés en séquences d’échappement.

- ATL_URL _NO_META : ne supprime pas les séquences de métadonnées (telles que « . » et « .. ») de l’URL.

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur TRUE en cas de réussite, FALSe en cas d’échec.

### <a name="remarks"></a>Notes

La conversion au format canonique implique la conversion de caractères et d’espaces non sécurisés en séquences d’échappement.

## <a name="curlclear"></a><a name="clear"></a> Boucle :: Clear

Appelez cette méthode pour effacer tous les champs d’URL.

```
inline void Clear() throw();
```

## <a name="curlcrackurl"></a><a name="crackurl"></a> Boucle :: CrackUrl

Appelez cette méthode pour décoder et analyser l’URL.

```
BOOL CrackUrl(LPCTSTR lpszUrl, DWORD dwFlags = 0) throw();
```

### <a name="parameters"></a>Paramètres

*lpszUrl*<br/>
URL.

*dwFlags*<br/>
Spécifiez ATL_URL_DECODE ou ATL_URL_ESCAPE pour convertir tous les caractères d’échappement dans *lpszUrl* en leurs valeurs réelles après l’analyse. (Avant Visual C++ 2005, ATL_URL_DECODE converti tous les caractères d’échappement avant l’analyse.)

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur TRUE en cas de réussite, FALSe en cas d’échec.

## <a name="curlcreateurl"></a><a name="createurl"></a> Boucle :: CreateUrl

Cette méthode construit une chaîne d’URL à partir des champs de composant d’un objet de la boucle.

```
inline BOOL CreateUrl(
    LPTSTR lpszUrl,
    DWORD* pdwMaxLength,
    DWORD dwFlags = 0) const throw();
```

### <a name="parameters"></a>Paramètres

*lpszUrl*<br/>
Mémoire tampon de chaîne devant contenir la chaîne d’URL complète.

*pdwMaxLength*<br/>
Longueur maximale de la mémoire tampon de chaîne *lpszUrl* .

*dwFlags*<br/>
Spécifiez ATL_URL_ESCAPE pour convertir tous les caractères d’échappement dans *lpszUrl* en leurs valeurs réelles.

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur TRUE en cas de réussite, FALSe en cas d’échec.

### <a name="remarks"></a>Notes

Cette méthode ajoute ses champs individuels afin de construire la chaîne d’URL complète en utilisant le format suivant :

**\<scheme>://\<user>:\<pass>\@\<domain>:\<port>\<path>\<extra>**

Lors de l’appel de cette méthode, le paramètre *pdwMaxLength* doit initialement contenir la longueur maximale de la mémoire tampon de chaîne référencée par le paramètre *lpszUrl* . La valeur du paramètre *pdwMaxLength* sera mise à jour avec la longueur réelle de la chaîne d’URL.

### <a name="example"></a>Exemple

Cet exemple illustre la création d’un objet d’une boucle et la récupération de sa chaîne d’URL

[!code-cpp[NVC_ATL_Utilities#133](../../atl/codesnippet/cpp/curl-class_1.cpp)]

## <a name="curlcurl"></a><a name="curl"></a> Boucle :: courbure

Constructeur.

```
CUrl() throw();
CUrl(const CUrl& urlThat) throw();
```

### <a name="parameters"></a>Paramètres

*urlThat*<br/>
`CUrl`Objet à copier pour créer l’URL.

## <a name="curlcurl"></a><a name="dtor"></a> Boucle :: ~

Destructeur.

```
~CUrl() throw();
```

## <a name="curlgetextrainfo"></a><a name="getextrainfo"></a> Boucle :: GetExtraInfo

Appelez cette méthode pour recevoir des informations supplémentaires (telles que *Text* ou # *Text*) à partir de l’URL.

```
inline LPCTSTR GetExtraInfo() const throw();
```

### <a name="return-value"></a>Valeur renvoyée

Retourne une chaîne contenant les informations supplémentaires.

## <a name="curlgetextrainfolength"></a><a name="getextrainfolength"></a> Boucle :: GetExtraInfoLength

Appelez cette méthode pour obtenir la longueur des informations supplémentaires (telles que *Text* ou # *Text*) à récupérer à partir de l’URL.

```
inline DWORD GetExtraInfoLength() const throw();
```

### <a name="return-value"></a>Valeur renvoyée

Retourne la longueur de la chaîne contenant les informations supplémentaires.

## <a name="curlgethostname"></a><a name="gethostname"></a> Boucle :: GetHostName

Appelez cette méthode pour récupérer le nom d’hôte à partir de l’URL.

```
inline LPCTSTR GetHostName() const throw();
```

### <a name="return-value"></a>Valeur renvoyée

Retourne le nom d’hôte.

## <a name="curlgethostnamelength"></a><a name="gethostnamelength"></a> Boucle :: GetHostNameLength

Appelez cette méthode pour connaître la longueur du nom d’hôte.

```
inline DWORD GetHostNameLength() const throw();
```

### <a name="return-value"></a>Valeur renvoyée

Retourne la longueur du nom d’hôte.

## <a name="curlgetpassword"></a><a name="getpassword"></a> Boucle :: GetPassword

Appelez cette méthode pour récupérer le mot de passe à partir de l’URL.

```
inline LPCTSTR GetPassword() const throw();
```

### <a name="return-value"></a>Valeur renvoyée

Retourne le mot de passe.

## <a name="curlgetpasswordlength"></a><a name="getpasswordlength"></a> Boucle :: GetPasswordLength

Appelez cette méthode pour connaître la longueur du mot de passe.

```
inline DWORD GetPasswordLength() const throw();
```

### <a name="return-value"></a>Valeur renvoyée

Retourne la longueur du mot de passe.

## <a name="curlgetportnumber"></a><a name="getportnumber"></a> Boucle :: GetPortNumber

Appelez cette méthode pour récupérer le numéro de port.

```
inline ATL_URL_PORT GetPortNumber() const throw();
```

### <a name="return-value"></a>Valeur renvoyée

Retourne le numéro de port.

## <a name="curlgetscheme"></a><a name="getscheme"></a> Boucle :: GetScheme

Appelez cette méthode pour récupérer le schéma d’URL.

```
inline ATL_URL_SCHEME GetScheme() const throw();
```

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur [ATL_URL_SCHEME](atl-url-scheme-enum.md) décrivant le schéma de l’URL.

## <a name="curlgetschemename"></a><a name="getschemename"></a> Boucle :: GetSchemeName

Appelez cette méthode pour récupérer le nom du schéma d’URL.

```
inline LPCTSTR GetSchemeName() const throw();
```

### <a name="return-value"></a>Valeur renvoyée

Retourne le nom du schéma d’URL (par exemple, « http » ou « FTP »).

## <a name="curlgetschemenamelength"></a><a name="getschemenamelength"></a> Boucle :: GetSchemeNameLength

Appelez cette méthode pour connaître la longueur du nom du schéma d’URL.

```
inline DWORD GetSchemeNameLength() const throw();
```

### <a name="return-value"></a>Valeur renvoyée

Retourne la longueur du nom du schéma d’URL.

## <a name="curlgeturllength"></a><a name="geturllength"></a> Boucle :: GetUrlLength

Appelez cette méthode pour récupérer la longueur de l’URL.

```
inline DWORD GetUrlLength() const throw();
```

### <a name="return-value"></a>Valeur renvoyée

Retourne la longueur de l’URL.

## <a name="curlgeturlpath"></a><a name="geturlpath"></a> Boucle :: GetUrlPath

Appelez cette méthode pour récupérer le chemin d’accès de l’URL.

```
inline LPCTSTR GetUrlPath() const throw();
```

### <a name="return-value"></a>Valeur renvoyée

Retourne le chemin d’accès de l’URL.

## <a name="curlgeturlpathlength"></a><a name="geturlpathlength"></a> Boucle :: GetUrlPathLength

Appelez cette méthode pour accéder à la longueur du chemin d’accès de l’URL.

```
inline DWORD GetUrlPathLength() const throw();
```

### <a name="return-value"></a>Valeur renvoyée

Retourne la longueur du chemin d’accès de l’URL.

## <a name="curlgetusername"></a><a name="getusername"></a> Boucle :: GetUserName

Appelez cette méthode pour récupérer le nom d’utilisateur à partir de l’URL.

```
inline LPCTSTR GetUserName() const throw();
```

### <a name="return-value"></a>Valeur renvoyée

Retourne le nom d’utilisateur.

## <a name="curlgetusernamelength"></a><a name="getusernamelength"></a> Boucle :: GetUserNameLength

Appelez cette méthode pour connaître la longueur du nom d’utilisateur.

```
inline DWORD GetUserNameLength() const throw();
```

### <a name="return-value"></a>Valeur renvoyée

Retourne la longueur du nom d’utilisateur.

## <a name="curloperator-"></a><a name="operator_eq"></a> Boucle :: Operator =

Assigne l' `CUrl` objet spécifié à l' `CUrl` objet actuel.

```
CUrl& operator= (const CUrl& urlThat) throw();
```

### <a name="parameters"></a>Paramètres

*urlThat*<br/>
`CUrl`Objet à copier dans l’objet actuel.

### <a name="return-value"></a>Valeur renvoyée

Retourne une référence à l’objet actuel.

## <a name="curlsetextrainfo"></a><a name="setextrainfo"></a> Boucle :: SetExtraInfo

Appelez cette méthode pour définir les informations supplémentaires (telles que *Text* ou # *Text*) de l’URL.

```
inline BOOL SetExtraInfo(LPCTSTR lpszInfo) throw();
```

### <a name="parameters"></a>Paramètres

*lpszInfo*<br/>
Chaîne contenant les informations supplémentaires à inclure dans l’URL.

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur TRUE en cas de réussite, FALSe en cas d’échec.

## <a name="curlsethostname"></a><a name="sethostname"></a> Boucle :: SetHostName

Appelez cette méthode pour définir le nom d’hôte.

```
inline BOOL SetHostName(LPCTSTR lpszHost) throw();
```

### <a name="parameters"></a>Paramètres

*lpszHost*<br/>
Nom d’hôte.

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur TRUE en cas de réussite, FALSe en cas d’échec.

## <a name="curlsetpassword"></a><a name="setpassword"></a> Boucle :: SetPassword

Appelez cette méthode pour définir le mot de passe.

```
inline BOOL SetPassword(LPCTSTR lpszPass) throw();
```

### <a name="parameters"></a>Paramètres

*lpszPass*<br/>
Mot de passe.

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur TRUE en cas de réussite, FALSe en cas d’échec.

## <a name="curlsetportnumber"></a><a name="setportnumber"></a> Boucle :: SetPortNumber

Appelez cette méthode pour définir le numéro de port.

```
inline BOOL SetPortNumber(ATL_URL_PORT nPrt) throw();
```

### <a name="parameters"></a>Paramètres

*IP-HTTPS*<br/>
Le numéro de port.

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur TRUE en cas de réussite, FALSe en cas d’échec.

## <a name="curlsetscheme"></a><a name="setscheme"></a> Boucle :: SetScheme

Appelez cette méthode pour définir le modèle d’URL.

```
inline BOOL SetScheme(ATL_URL_SCHEME nScheme) throw();
```

### <a name="parameters"></a>Paramètres

*nScheme*<br/>
L’une des valeurs [ATL_URL_SCHEME](atl-url-scheme-enum.md) pour le schéma.

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur TRUE en cas de réussite, FALSe en cas d’échec.

### <a name="remarks"></a>Notes

Vous pouvez également définir le schéma par nom (consultez la section « [bouclé :: SetSchemeName](#setschemename)»).

## <a name="curlsetschemename"></a><a name="setschemename"></a> Boucle :: SetSchemeName

Appelez cette méthode pour définir le nom du modèle d’URL.

```
inline BOOL SetSchemeName(LPCTSTR lpszSchm) throw();
```

### <a name="parameters"></a>Paramètres

*lpszSchm*<br/>
Nom du schéma d’URL.

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur TRUE en cas de réussite, FALSe en cas d’échec.

### <a name="remarks"></a>Notes

Vous pouvez également définir le schéma à l’aide d’une constante [ATL_URL_SCHEME](atl-url-scheme-enum.md) (voir la rubrique [SetScheme](#setscheme)).

## <a name="curlseturlpath"></a><a name="seturlpath"></a> Boucle :: SetUrlPath

Appelez cette méthode pour définir le chemin d’accès de l’URL.

```
inline BOOL SetUrlPath(LPCTSTR lpszPath) throw();
```

### <a name="parameters"></a>Paramètres

*lpszPath*<br/>
Chemin d’accès de l’URL.

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur TRUE en cas de réussite, FALSe en cas d’échec.

## <a name="curlsetusername"></a><a name="setusername"></a> Boucle :: SetUserName

Appelez cette méthode pour définir le nom d’utilisateur.

```
inline BOOL SetUserName(LPCTSTR lpszUser) throw();
```

### <a name="parameters"></a>Paramètres

*lpszUser*<br/>
Nom d'utilisateur.

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur TRUE en cas de réussite, FALSe en cas d’échec.

## <a name="see-also"></a>Voir aussi

[Classes](../../atl/reference/atl-classes.md)
