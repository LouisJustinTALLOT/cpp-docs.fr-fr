---
title: Classe CUrl
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
ms.openlocfilehash: 3468e17b031d0a72bc56d915c689fbe4c78859e0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330475"
---
# <a name="curl-class"></a>Classe CUrl

Cette classe représente une URL. Il vous permet de manipuler chaque élément de l’URL indépendamment des autres, que ce soit l’analyse d’une chaîne URL existante ou la construction d’une chaîne à partir de zéro.

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
|[CUrl::CUrl](#curl)|Constructeur.|
|[CUrl: :CUrl](#dtor)|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CUrl::Canonicalize](#canonicalize)|Appelez cette méthode pour convertir la chaîne URL en forme canonique.|
|[CUrl::Clair](#clear)|Appelez cette méthode pour effacer tous les champs URL.|
|[CUrl::CrackUrl](#crackurl)|Appelez cette méthode pour décoder et analyser l’URL.|
|[CUrl::CreateUrl](#createurl)|Appelez cette méthode pour créer l’URL.|
|[CUrl::GetExtraInfo](#getextrainfo)|Appelez cette méthode pour obtenir des informations supplémentaires (comme *le texte* ou le *texte)* à partir de l’URL.|
|[CUrl::GetExtraInfoLength](#getextrainfolength)|Appelez cette méthode pour obtenir la longueur des informations supplémentaires (comme le *texte* ou le *texte*) à récupérer à partir de l’URL.|
|[CUrl::GetHostName](#gethostname)|Appelez cette méthode pour obtenir le nom d’hôte de l’URL.|
|[CUrl::GetHostNameLength](#gethostnamelength)|Appelez cette méthode pour obtenir la longueur du nom de l’hôte.|
|[CUrl::GetPassword](#getpassword)|Appelez cette méthode pour obtenir le mot de passe à partir de l’URL.|
|[CUrl::GetPasswordLength](#getpasswordlength)|Appelez cette méthode pour obtenir la longueur du mot de passe.|
|[CUrl::GetPortNumber](#getportnumber)|Appelez cette méthode pour obtenir le numéro de port en termes de ATL_URL_PORT.|
|[CUrl::GetScheme](#getscheme)|Appelez cette méthode pour obtenir le système d’URL.|
|[CUrl::GetSchemeName](#getschemename)|Appelez cette méthode pour obtenir le nom du système URL.|
|[CUrl::GetSchemeNameLength](#getschemenamelength)|Appelez cette méthode pour obtenir la longueur du nom du système URL.|
|[CUrl::GetUrlLength](#geturllength)|Appelez cette méthode pour obtenir la longueur de l’URL.|
|[CUrl::GetUrlPath](#geturlpath)|Appelez cette méthode pour obtenir le chemin URL.|
|[CUrl::GetUrlPathLength](#geturlpathlength)|Appelez cette méthode pour obtenir la longueur du chemin URL.|
|[CUrl::GetUserName](#getusername)|Appelez cette méthode pour obtenir le nom d’utilisateur de l’URL.|
|[CUrl::GetUserNameLength](#getusernamelength)|Appelez cette méthode pour obtenir la longueur du nom d’utilisateur.|
|[CUrl::SetExtraInfo](#setextrainfo)|Appelez cette méthode pour définir les informations supplémentaires (telles que le *texte* ou le *texte)* de l’URL.|
|[CUrl::SetHostName](#sethostname)|Appelez cette méthode pour définir le nom de l’hôte.|
|[CUrl::SetPassword](#setpassword)|Appelez cette méthode pour définir le mot de passe.|
|[CUrl::SetPortNumber](#setportnumber)|Appelez cette méthode pour définir le numéro de port en termes de ATL_URL_PORT.|
|[CUrl::SetScheme](#setscheme)|Appelez cette méthode pour définir le schéma d’URL.|
|[CUrl::SetSchemeName](#setschemename)|Appelez cette méthode pour définir le nom du schéma URL.|
|[CUrl::SetUrlPath](#seturlpath)|Appelez cette méthode pour définir le chemin DE l’URL.|
|[CUrl::SetUserName](#setusername)|Appelez cette méthode pour définir le nom d’utilisateur.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CUrl::opérateur](#operator_eq)|Assigne l’objet `CUrl` spécifié `CUrl` à l’objet actuel.|

## <a name="remarks"></a>Notes

`CUrl`vous permet de manipuler les champs d’une URL, comme le chemin ou le numéro de port. `CUrl`comprend les URL de la forme suivante :

\<Schéma\<>:// UserName>:\<Password>\@ \<HostName\<>: PortNumber>/\<UrlPath>\<ExtraInfo>

(Certains champs sont facultatifs.) Par exemple, considérez cette URL :

`http://someone:secret@www.microsoft.com:80/visualc/stuff.htm#contents`

[CUrl::CrackUrl](#crackurl) l’analyse comme suit:

- Schéma: "http" ou [ATL_URL_SCHEME_HTTP](atl-url-scheme-enum.md)

- Nom de l’utilisateur: "quelqu’un"

- Mot de passe: "secret"

- HostName:`www.microsoft.com`"

- PortNumber: 80

- UrlPath: "visualc/stuff.htm"

- ExtraInfo: "#contents"

Pour manipuler le champ UrlPath (par exemple), vous utiliseriez [GetUrlPath](#geturlpath), [GetUrlPathLength](#geturlpathlength), et [SetUrlPath](#seturlpath). Vous utiliseriez [CreateUrl](#createurl) pour créer la chaîne URL complète.

## <a name="requirements"></a>Spécifications

**En-tête:** atlutil.h

## <a name="curlcanonicalize"></a><a name="canonicalize"></a>CUrl::Canonicalize

Appelez cette méthode pour convertir la chaîne URL en forme canonique.

```
inline BOOL Canonicalize(DWORD dwFlags = 0) throw();
```

### <a name="parameters"></a>Paramètres

*dwFlags*<br/>
Les drapeaux qui contrôlent la canonisation. Si aucun drapeau n’est spécifié *(dwFlags* 0), la méthode convertit \\tous les personnages \\dangereux et les méta séquences (tels que .,., et ...) pour échapper aux séquences. *dwFlags* peut être l’une des valeurs suivantes:

- ATL_URL_BROWSER_MODE : Ne code pas ou ne décode pas les caractères après « » ou « » et n’enlève pas l’espace blanc de fuite après « ». Si cette valeur n’est pas spécifiée, l’URL entière est codée et l’espace blanc de fuite est supprimé.

- ATL_URL _DECODE : Convertit toutes les séquences de %XX en personnages, y compris les séquences d’évasion, avant que l’URL ne soit analysée.

- ATL_URL _ENCODE_PERCENT : Code les signes rencontrés. Par défaut, les signes de pourcentage ne sont pas codés.

- ATL_URL _ENCODE_SPACES_ONLY : Code uniquement les espaces.

- ATL_URL _NO_ENCODE : Ne convertit pas les caractères dangereux pour échapper aux séquences.

- ATL_URL _NO_META : Ne supprime pas les méta séquences (telles que « » et «..)de l’URL.

### <a name="return-value"></a>Valeur de retour

Retourne TRUE sur le succès, FALSE sur l’échec.

### <a name="remarks"></a>Notes

La conversion à la forme canonique implique la conversion de personnages et d’espaces dangereux pour échapper aux séquences.

## <a name="curlclear"></a><a name="clear"></a>CUrl::Clair

Appelez cette méthode pour effacer tous les champs URL.

```
inline void Clear() throw();
```

## <a name="curlcrackurl"></a><a name="crackurl"></a>CUrl::CrackUrl

Appelez cette méthode pour décoder et analyser l’URL.

```
BOOL CrackUrl(LPCTSTR lpszUrl, DWORD dwFlags = 0) throw();
```

### <a name="parameters"></a>Paramètres

*lpszUrl*<br/>
URL.

*dwFlags*<br/>
Spécifiez ATL_URL_DECODE ou ATL_URL_ESCAPE pour convertir tous les personnages *d’évasion en lpszUrl* à leurs valeurs réelles après l’analyse. (Avant Visual CMD 2005, ATL_URL_DECODE converti tous les personnages d’évasion avant d’analyser.)

### <a name="return-value"></a>Valeur de retour

Retourne TRUE sur le succès, FALSE sur l’échec.

## <a name="curlcreateurl"></a><a name="createurl"></a>CUrl::CreateUrl

Cette méthode construit une chaîne URL à partir des champs de composants d’un objet CUrl.

```
inline BOOL CreateUrl(
    LPTSTR lpszUrl,
    DWORD* pdwMaxLength,
    DWORD dwFlags = 0) const throw();
```

### <a name="parameters"></a>Paramètres

*lpszUrl*<br/>
Un tampon de chaîne pour tenir la chaîne URL complète.

*pdwMaxLength*<br/>
La longueur maximale du tampon de chaîne *lpszUrl.*

*dwFlags*<br/>
Spécifiez ATL_URL_ESCAPE pour convertir tous les personnages *d’évasion en lpszUrl* à leurs valeurs réelles.

### <a name="return-value"></a>Valeur de retour

Retourne TRUE sur le succès, FALSE sur l’échec.

### <a name="remarks"></a>Notes

Cette méthode joint ses champs individuels afin de construire la chaîne URL complète en utilisant le format suivant :

**\<schéma\<>://> utilisateur:\<passer>\@ \<> de\<domaine: \<chemin>port>>supplémentaire \<**

Lors de l’appel de cette méthode, le paramètre *pdwMaxLength* doit initialement contenir la longueur maximale de la mémoire tampon de chaîne référencée par le paramètre *lpszUrl.* La valeur du paramètre *pdwMaxLength* sera mise à jour avec la longueur réelle de la chaîne URL.

### <a name="example"></a>Exemple

Cet échantillon démontre la création d’un objet CUrl et la récupération de sa chaîne d’URL

[!code-cpp[NVC_ATL_Utilities#133](../../atl/codesnippet/cpp/curl-class_1.cpp)]

## <a name="curlcurl"></a><a name="curl"></a>CUrl::CUrl

Constructeur.

```
CUrl() throw();
CUrl(const CUrl& urlThat) throw();
```

### <a name="parameters"></a>Paramètres

*urlThat*<br/>
L’objet `CUrl` à copier pour créer l’URL.

## <a name="curlcurl"></a><a name="dtor"></a>CUrl: :CUrl

Destructeur.

```
~CUrl() throw();
```

## <a name="curlgetextrainfo"></a><a name="getextrainfo"></a>CUrl::GetExtraInfo

Appelez cette méthode pour obtenir des informations supplémentaires (comme *le texte* ou le *texte)* à partir de l’URL.

```
inline LPCTSTR GetExtraInfo() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne une chaîne contenant les informations supplémentaires.

## <a name="curlgetextrainfolength"></a><a name="getextrainfolength"></a>CUrl::GetExtraInfoLength

Appelez cette méthode pour obtenir la longueur des informations supplémentaires (comme le *texte* ou le *texte*) à récupérer à partir de l’URL.

```
inline DWORD GetExtraInfoLength() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne la longueur de la chaîne contenant les informations supplémentaires.

## <a name="curlgethostname"></a><a name="gethostname"></a>CUrl::GetHostName

Appelez cette méthode pour obtenir le nom d’hôte de l’URL.

```
inline LPCTSTR GetHostName() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne le nom de l’hôte.

## <a name="curlgethostnamelength"></a><a name="gethostnamelength"></a>CUrl::GetHostNameLength

Appelez cette méthode pour obtenir la longueur du nom de l’hôte.

```
inline DWORD GetHostNameLength() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne la longueur du nom de l’hôte.

## <a name="curlgetpassword"></a><a name="getpassword"></a>CUrl::GetPassword

Appelez cette méthode pour obtenir le mot de passe à partir de l’URL.

```
inline LPCTSTR GetPassword() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne le mot de passe.

## <a name="curlgetpasswordlength"></a><a name="getpasswordlength"></a>CUrl::GetPasswordLength

Appelez cette méthode pour obtenir la longueur du mot de passe.

```
inline DWORD GetPasswordLength() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne la longueur du mot de passe.

## <a name="curlgetportnumber"></a><a name="getportnumber"></a>CUrl::GetPortNumber

Appelez cette méthode pour obtenir le numéro de port.

```
inline ATL_URL_PORT GetPortNumber() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne le numéro de port.

## <a name="curlgetscheme"></a><a name="getscheme"></a>CUrl::GetScheme

Appelez cette méthode pour obtenir le système d’URL.

```
inline ATL_URL_SCHEME GetScheme() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne la [valeur ATL_URL_SCHEME](atl-url-scheme-enum.md) décrivant le schéma de l’URL.

## <a name="curlgetschemename"></a><a name="getschemename"></a>CUrl::GetSchemeName

Appelez cette méthode pour obtenir le nom du système URL.

```
inline LPCTSTR GetSchemeName() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne le nom du schéma URL (comme "http" ou "ftp").

## <a name="curlgetschemenamelength"></a><a name="getschemenamelength"></a>CUrl::GetSchemeNameLength

Appelez cette méthode pour obtenir la longueur du nom du système URL.

```
inline DWORD GetSchemeNameLength() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne la longueur du nom du système URL.

## <a name="curlgeturllength"></a><a name="geturllength"></a>CUrl::GetUrlLength

Appelez cette méthode pour obtenir la longueur de l’URL.

```
inline DWORD GetUrlLength() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne la longueur de l’URL.

## <a name="curlgeturlpath"></a><a name="geturlpath"></a>CUrl::GetUrlPath

Appelez cette méthode pour obtenir le chemin URL.

```
inline LPCTSTR GetUrlPath() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne le chemin URL.

## <a name="curlgeturlpathlength"></a><a name="geturlpathlength"></a>CUrl::GetUrlPathLength

Appelez cette méthode pour obtenir la longueur du chemin URL.

```
inline DWORD GetUrlPathLength() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne la longueur du chemin URL.

## <a name="curlgetusername"></a><a name="getusername"></a>CUrl::GetUserName

Appelez cette méthode pour obtenir le nom d’utilisateur de l’URL.

```
inline LPCTSTR GetUserName() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne le nom d’utilisateur.

## <a name="curlgetusernamelength"></a><a name="getusernamelength"></a>CUrl::GetUserNameLength

Appelez cette méthode pour obtenir la longueur du nom d’utilisateur.

```
inline DWORD GetUserNameLength() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne la longueur du nom d’utilisateur.

## <a name="curloperator-"></a><a name="operator_eq"></a>CUrl::opérateur

Assigne l’objet `CUrl` spécifié `CUrl` à l’objet actuel.

```
CUrl& operator= (const CUrl& urlThat) throw();
```

### <a name="parameters"></a>Paramètres

*urlThat*<br/>
L’objet `CUrl` à copier dans l’objet actuel.

### <a name="return-value"></a>Valeur de retour

Renvoie une référence à l’objet actuel.

## <a name="curlsetextrainfo"></a><a name="setextrainfo"></a>CUrl::SetExtraInfo

Appelez cette méthode pour définir les informations supplémentaires (telles que le *texte* ou le *texte)* de l’URL.

```
inline BOOL SetExtraInfo(LPCTSTR lpszInfo) throw();
```

### <a name="parameters"></a>Paramètres

*lpszInfo (en anglais)*<br/>
La chaîne contenant les informations supplémentaires à inclure dans l’URL.

### <a name="return-value"></a>Valeur de retour

Retourne TRUE sur le succès, FALSE sur l’échec.

## <a name="curlsethostname"></a><a name="sethostname"></a>CUrl::SetHostName

Appelez cette méthode pour définir le nom de l’hôte.

```
inline BOOL SetHostName(LPCTSTR lpszHost) throw();
```

### <a name="parameters"></a>Paramètres

*lpszHost (lpszHost)*<br/>
Le nom de l’hôte.

### <a name="return-value"></a>Valeur de retour

Retourne TRUE sur le succès, FALSE sur l’échec.

## <a name="curlsetpassword"></a><a name="setpassword"></a>CUrl::SetPassword

Appelez cette méthode pour définir le mot de passe.

```
inline BOOL SetPassword(LPCTSTR lpszPass) throw();
```

### <a name="parameters"></a>Paramètres

*lpszPass (en)*<br/>
Mot de passe.

### <a name="return-value"></a>Valeur de retour

Retourne TRUE sur le succès, FALSE sur l’échec.

## <a name="curlsetportnumber"></a><a name="setportnumber"></a>CUrl::SetPortNumber

Appelez cette méthode pour définir le numéro de port.

```
inline BOOL SetPortNumber(ATL_URL_PORT nPrt) throw();
```

### <a name="parameters"></a>Paramètres

*nPrt (en)*<br/>
Numéro de port.

### <a name="return-value"></a>Valeur de retour

Retourne TRUE sur le succès, FALSE sur l’échec.

## <a name="curlsetscheme"></a><a name="setscheme"></a>CUrl::SetScheme

Appelez cette méthode pour définir le schéma d’URL.

```
inline BOOL SetScheme(ATL_URL_SCHEME nScheme) throw();
```

### <a name="parameters"></a>Paramètres

*nScheme (en)*<br/>
L’une des [valeurs ATL_URL_SCHEME](atl-url-scheme-enum.md) pour le régime.

### <a name="return-value"></a>Valeur de retour

Retourne TRUE sur le succès, FALSE sur l’échec.

### <a name="remarks"></a>Notes

Vous pouvez également définir le schéma par son nom (voir [CUrl::SetSchemeName](#setschemename)).

## <a name="curlsetschemename"></a><a name="setschemename"></a>CUrl::SetSchemeName

Appelez cette méthode pour définir le nom du schéma URL.

```
inline BOOL SetSchemeName(LPCTSTR lpszSchm) throw();
```

### <a name="parameters"></a>Paramètres

*lpszSchm (en)*<br/>
Nom du schéma URL.

### <a name="return-value"></a>Valeur de retour

Retourne TRUE sur le succès, FALSE sur l’échec.

### <a name="remarks"></a>Notes

Vous pouvez également définir le schéma en utilisant une [constante ATL_URL_SCHEME](atl-url-scheme-enum.md) (voir [CUrl::SetScheme](#setscheme)).

## <a name="curlseturlpath"></a><a name="seturlpath"></a>CUrl::SetUrlPath

Appelez cette méthode pour définir le chemin DE l’URL.

```
inline BOOL SetUrlPath(LPCTSTR lpszPath) throw();
```

### <a name="parameters"></a>Paramètres

*lpszPath*<br/>
Le chemin URL.

### <a name="return-value"></a>Valeur de retour

Retourne TRUE sur le succès, FALSE sur l’échec.

## <a name="curlsetusername"></a><a name="setusername"></a>CUrl::SetUserName

Appelez cette méthode pour définir le nom d’utilisateur.

```
inline BOOL SetUserName(LPCTSTR lpszUser) throw();
```

### <a name="parameters"></a>Paramètres

*lpszUser (en)*<br/>
Nom d'utilisateur.

### <a name="return-value"></a>Valeur de retour

Retourne TRUE sur le succès, FALSE sur l’échec.

## <a name="see-also"></a>Voir aussi

[Classes](../../atl/reference/atl-classes.md)
