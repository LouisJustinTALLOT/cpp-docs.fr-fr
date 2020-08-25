---
title: Fonctions de l’utilitaire HTTP ATL
ms.date: 11/04/2016
ms.assetid: 4db57ef2-31fa-4696-bbeb-79a9035033ed
ms.openlocfilehash: d2e30f940ded0bf355000cd42ff46a67662b54f5
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88833983"
---
# <a name="atl-http-utility-functions"></a>Fonctions de l’utilitaire HTTP ATL

Ces fonctions prennent en charge la manipulation des URL.

|Fonction|Description|
|-|-|
|[AtlCanonicalizeUrl](#atlcanonicalizeurl)|Canonicalizes une URL, qui comprend la conversion de caractères et d’espaces non sécurisés en séquences d’échappement.|
|[AtlCombineUrl](#atlcombineurl)|Combine une URL de base et une URL relative en une URL canonique unique.|
|[AtlEscapeUrl](#atlescapeurl)|Convertit tous les caractères non sécurisés en séquences d’échappement.|
|[AtlGetDefaultUrlPort](#atlgetdefaulturlport)|Obtient le numéro de port par défaut associé à un protocole ou un schéma Internet particulier.|
|[AtlIsUnsafeUrlChar](#atlisunsafeurlchar)|Détermine si un caractère peut être utilisé en toute sécurité dans une URL.|
|[AtlUnescapeUrl](#atlunescapeurl)|Convertit les caractères d’échappement vers leurs valeurs d’origine.|
|[RGBToHtml](#rgbtohtml)|Convertit une valeur [COLORREF](/windows/win32/gdi/colorref) en texte HTML correspondant à cette valeur de couleur.|
|[SystemTimeToHttpDate](#systemtimetohttpdate)|Appelez cette fonction pour convertir une heure système en une chaîne au format approprié pour être utilisée dans les en-têtes HTTP.|

## <a name="requirements"></a>Configuration requise

**En-tête :** atlutil. h

## <a name="atlcanonicalizeurl"></a><a name="atlcanonicalizeurl"></a> AtlCanonicalizeUrl

Appelez cette fonction pour rendre canonique une URL, notamment afin de convertir les caractères et espaces non sécurisés en séquences d'échappement.

```cpp
inline BOOL AtlCanonicalizeUrl(
   LPCTSTR szUrl,
   LPTSTR szCanonicalized,
   DWORD* pdwMaxLength,
   DWORD dwFlags = 0) throw();
```

### <a name="parameters"></a>Paramètres

*szUrl*<br/>
URL à rendre canonique.

*szCanonicalized*<br/>
Mémoire tampon allouée par l’appelant pour recevoir l’URL canonique.

*pdwMaxLength*<br/>
Pointeur vers une variable qui contient la longueur en caractères de *szCanonicalized*. Si la fonction a abouti, la variable reçoit le nombre de caractères écrits dans la mémoire tampon, y compris le caractère null de fin. Si la fonction échoue, la variable reçoit la longueur requise en octets de la mémoire tampon, y compris l’espace pour le caractère null de fin.

*dwFlags*<br/>
ATL_URL indicateurs contrôlant le comportement de cette fonction.

- ATL_URL_BROWSER_MODE n’encode pas ou ne décode pas les caractères après « # » ou «  ? », et ne supprime pas les espaces blancs de fin après «  ? ». Si cette valeur n’est pas spécifiée, l’URL entière est encodée et l’espace blanc de fin est supprimé.

- ATL_URL_DECODE convertit toutes les séquences% XX en caractères, y compris les séquences d’échappement, avant l’analyse de l’URL.

- ATL_URL_ENCODE_PERCENT encode tous les signes de pourcentage rencontrés. Par défaut, les signes de pourcentage ne sont pas encodés.

- ATL_URL_ENCODE_SPACES_ONLY code les espaces uniquement.

- ATL_URL_ESCAPE convertit toutes les séquences d’échappement (% XX) en leurs caractères correspondants.

- ATL_URL_NO_ENCODE ne convertit pas les caractères non sécurisés en séquences d’échappement.

- ATL_URL_NO_META ne supprime pas les séquences Meta (telles que « . » et « .. ») de l’URL.

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur TRUE en cas de réussite, FALSe en cas d’échec.

### <a name="remarks"></a>Notes

Se comporte comme la version actuelle de [InternetCanonicalizeUrl](/windows/win32/api/wininet/nf-wininet-internetcanonicalizeurlw) , mais ne nécessite pas l’installation de WinInet ou d’Internet Explorer.

## <a name="atlcombineurl"></a><a name="atlcombineurl"></a> AtlCombineUrl

Appelez cette fonction pour associer une URL de base et une URL relative en une URL unique et canonique.

```cpp
inline BOOL AtlCombineUrl(
   LPCTSTR szBaseUrl,
   LPCTSTR szRelativeUrl,
   LPTSTR szBuffer,
   DWORD* pdwMaxLength,
   DWORD dwFlags = 0) throw();
```

### <a name="parameters"></a>Paramètres

*szBaseUrl*<br/>
URL de base.

*szRelativeUrl*<br/>
URL relative à l’URL de base.

*szBuffer*<br/>
Mémoire tampon allouée par l’appelant pour recevoir l’URL canonique.

*pdwMaxLength*<br/>
Pointeur vers une variable qui contient la longueur en caractères de *szBuffer*. Si la fonction a abouti, la variable reçoit le nombre de caractères écrits dans la mémoire tampon, y compris le caractère null de fin. Si la fonction échoue, la variable reçoit la longueur requise en octets de la mémoire tampon, y compris l’espace pour le caractère null de fin.

*dwFlags*<br/>
Indicateurs contrôlant le comportement de cette fonction. Consultez [AtlCanonicalizeUrl](#atlcanonicalizeurl).

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur TRUE en cas de réussite, FALSe en cas d’échec.

### <a name="remarks"></a>Notes

Se comporte comme la version actuelle de [InternetCombineUrl](/windows/win32/api/wininet/nf-wininet-internetcombineurlw) , mais ne nécessite pas l’installation de WinInet ou d’Internet Explorer.

## <a name="atlescapeurl"></a><a name="atlescapeurl"></a> AtlEscapeUrl

Appelez cette fonction pour convertir tous les caractères non sécurisés en séquences d'échappement.

```cpp
inline BOOL AtlEscapeUrl(
   LPCSTR szStringIn,
   LPSTR szStringOut,
   DWORD* pdwStrLen,
   DWORD dwMaxLength,
   DWORD dwFlags = 0) throw();

inline BOOL AtlEscapeUrl(
   LPCWSTR szStringIn,
   LPWSTR szStringOut,
   DWORD* pdwStrLen,
   DWORD dwMaxLength,
   DWORD dwFlags = 0) throw();
```

### <a name="parameters"></a>Paramètres

*lpszStringIn*<br/>
URL à convertir.

*lpszStringOut*<br/>
Mémoire tampon allouée par l’appelant dans laquelle l’URL convertie sera écrite.

*pdwStrLen*<br/>
Pointeur vers une variable DWORD. Si la fonction a abouti, *pdwStrLen* reçoit le nombre de caractères écrits dans la mémoire tampon, y compris le caractère null de fin. Si la fonction échoue, la variable reçoit la longueur requise en octets de la mémoire tampon, y compris l’espace pour le caractère null de fin. Lors de l’utilisation de la version à caractères larges de cette méthode, *pdwStrLen* reçoit le nombre de caractères requis, et non le nombre d’octets.

*dwMaxLength*<br/>
Taille de la mémoire tampon *lpszStringOut*.

*dwFlags*<br/>
ATL_URL indicateurs contrôlant le comportement de cette fonction. Pour connaître les valeurs possibles, consultez [ATLCanonicalizeUrl](#atlcanonicalizeurl) .

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur TRUE en cas de réussite, FALSe en cas d’échec.

## <a name="atlgetdefaulturlport"></a><a name="atlgetdefaulturlport"></a> AtlGetDefaultUrlPort

Appelez cette fonction pour obtenir le numéro de port par défaut associé à un protocole ou un modèle Internet particulier.

```cpp
inline ATL_URL_PORT AtlGetDefaultUrlPort(ATL_URL_SCHEME m_nScheme) throw();
```

### <a name="parameters"></a>Paramètres

*m_nScheme*<br/>
Valeur [ATL_URL_SCHEME](atl-url-scheme-enum.md) identifiant le schéma pour lequel vous souhaitez obtenir le numéro de port.

### <a name="return-value"></a>Valeur renvoyée

[ATL_URL_PORT](atl-typedefs.md#atl_url_port) associé au schéma ou ATL_URL_INVALID_PORT_NUMBER spécifié si le schéma n’est pas reconnu.

## <a name="atlisunsafeurlchar"></a><a name="atlisunsafeurlchar"></a> AtlIsUnsafeUrlChar

Appelez cette fonction pour déterminer si un caractère peut être utilisé de manière sécurisée dans une URL.

```cpp
inline BOOL AtlIsUnsafeUrlChar(char chIn) throw();
```

### <a name="parameters"></a>Paramètres

*Sell*<br/>
Caractère à tester pour des raisons de sécurité.

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur TRUE si le caractère d’entrée est unsafe ; sinon, FALSe.

### <a name="remarks"></a>Notes

Les caractères qui ne doivent pas être utilisés dans les URL peuvent être testés à l’aide de cette fonction et convertis à l’aide de [AtlCanonicalizeUrl](#atlcanonicalizeurl).

## <a name="atlunescapeurl"></a><a name="atlunescapeurl"></a> AtlUnescapeUrl

Appelez cette fonction pour convertir les caractères ayant fait l'objet d'une séquence d'échappement vers leurs valeurs d'origine.

```cpp
inline BOOL AtlUnescapeUrl(
   LPCSTR szStringIn,
   LPSTR szStringOut,
   LPDWORD pdwStrLen,
   DWORD dwMaxLength) throw();

inline BOOL AtlUnescapeUrl(
   LPCWSTR szStringIn,
   LPWSTR szStringOut,
   LPDWORD pdwStrLen,
   DWORD dwMaxLength) throw();
```

### <a name="parameters"></a>Paramètres

*lpszStringIn*<br/>
URL à convertir.

*lpszStringOut*<br/>
Mémoire tampon allouée par l’appelant dans laquelle l’URL convertie sera écrite.

*pdwStrLen*<br/>
Pointeur vers une variable DWORD. Si la fonction a abouti, la variable reçoit le nombre de caractères écrits dans la mémoire tampon, y compris le caractère null de fin. Si la fonction échoue, la variable reçoit la longueur requise en octets de la mémoire tampon, y compris l’espace pour le caractère null de fin.

*dwMaxLength*<br/>
Taille de la mémoire tampon *lpszStringOut*.

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur TRUE en cas de réussite, FALSe en cas d’échec.

### <a name="remarks"></a>Notes

Inverse le processus de conversion appliqué par [AtlEscapeUrl](#atlescapeurl).

## <a name="rgbtohtml"></a><a name="rgbtohtml"></a> RGBToHtml

Convertit une valeur [COLORREF](/windows/win32/gdi/colorref) en texte HTML correspondant à cette valeur de couleur.

```cpp
bool inline RGBToHtml(
   COLORREF color,
   LPTSTR pbOut,
   long nBuffer);
```

### <a name="parameters"></a>Paramètres

*color*<br/>
Valeur de couleur RVB.

*pbOut*<br/>
Mémoire tampon allouée par l’appelant pour recevoir le texte de la valeur de couleur HTML. La mémoire tampon doit avoir un espace pour au moins 8 caractères, y compris l’espace pour la marque de fin null).

*nBuffer*<br/>
Taille en octets de la mémoire tampon (y compris l’espace pour la marque de fin null).

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur TRUE en cas de réussite, FALSe en cas d’échec.

### <a name="remarks"></a>Notes

Une valeur de couleur HTML est un signe dièse suivi d’une valeur hexadécimale à 6 chiffres utilisant 2 chiffres pour chacun des composants rouge, vert et bleu de la couleur (par exemple, #FFFFFF est blanc).

## <a name="systemtimetohttpdate"></a><a name="systemtimetohttpdate"></a> SystemTimeToHttpDate

Appelez cette fonction pour convertir une heure système en une chaîne au format approprié pour être utilisée dans les en-têtes HTTP.

```cpp
inline void SystemTimeToHttpDate(
   const SYSTEMTIME& st,
   CStringA& strTime);
```

### <a name="parameters"></a>Paramètres

*St*<br/>
Heure système à obtenir sous la forme d’une chaîne de format HTTP.

*strTime*<br/>
Référence à une variable de chaîne pour recevoir la date et l’heure HTTP, comme défini dans RFC 2616 ( [https://www.ietf.org/rfc/rfc2616.txt](https://www.ietf.org/rfc/rfc2616.txt) ) et rfc 1123 ( [https://www.ietf.org/rfc/rfc1123.txt](https://www.ietf.org/rfc/rfc1123.txt) ).

## <a name="see-also"></a>Voir aussi

[Concepts](../active-template-library-atl-concepts.md)<br/>
[Composants de bureau COM ATL](../atl-com-desktop-components.md)<br/>
[InternetCanonicalizeUrl](/windows/win32/api/wininet/nf-wininet-internetcanonicalizeurlw)
