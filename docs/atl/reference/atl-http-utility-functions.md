---
title: Fonctions utilitaires ATL HTTP | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 4db57ef2-31fa-4696-bbeb-79a9035033ed
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cdec5fe54a581d2654e2945a0012c5261608d1e4
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43762510"
---
# <a name="atl-http-utility-functions"></a>Fonctions utilitaires ATL HTTP

Ces fonctions prennent en charge la manipulation d’URL.

|||
|-|-|
|[AtlCanonicalizeUrl](#atlcanonicalizeurl)|Canonicalise une URL qui inclut la conversion des caractères non sécurisés et des espaces dans les séquences d’échappement.|
|[AtlCombineUrl](#atlcombineurl)|Combine une URL de base et une URL relative en une URL unique et canonique.|
|[AtlEscapeUrl](#atlescapeurl)|Convertit tous les caractères non sécurisés en séquences d’échappement.|
|[AtlGetDefaultUrlPort](#atlgetdefaulturlport)|Obtient le numéro de port par défaut associé à un protocole Internet particulier ou d’un schéma.|
|[AtlIsUnsafeUrlChar](#atlisunsafeurlchar)|Détermine si un caractère est utilisé dans une URL en toute sécurité.|
|[AtlUnescapeUrl](#atlunescapeurl)|Convertit les caractères d’échappement vers leurs valeurs d’origine.|
|[RGBToHtml](#rgbtohtml)|Convertit un [COLORREF](/windows/desktop/gdi/colorref) le texte HTML correspondant à cette valeur de couleur à la valeur.|
|[SystemTimeToHttpDate](#systemtimetohttpdate)|Appelez cette fonction pour convertir une heure système en une chaîne au format approprié pour être utilisée dans les en-têtes HTTP.|

## <a name="requirements"></a>Configuration requise

**En-tête :** atlutil.h  

## <a name="atlcanonicalizeurl"></a> AtlCanonicalizeUrl

Appelez cette fonction pour rendre canonique une URL, notamment afin de convertir les caractères et espaces non sécurisés en séquences d'échappement.

```    
inline BOOL AtlCanonicalizeUrl(  
   LPCTSTR szUrl,  
   LPTSTR szCanonicalized,  
   DWORD* pdwMaxLength,  
   DWORD dwFlags = 0) throw();  
```

### <a name="parameters"></a>Paramètres

*szUrl*  
URL à mettre en forme canonique.

*szCanonicalized*  
Mémoire tampon allouée par l’appelant de recevoir l’URL au format canonique.

*pdwMaxLength*  
Pointeur vers une variable qui contient la longueur en caractères de *szCanonicalized*. Si la fonction réussit, la variable reçoit le nombre de caractères écrits dans la mémoire tampon, y compris le caractère null de fin. Si la fonction échoue, la variable reçoit la longueur en octets de la mémoire tampon, y compris l’espace pour le caractère null de fin.

*dwFlags*  
Indicateurs ATL_URL contrôlant le comportement de cette fonction. 

- ATL_URL_BROWSER_MODE est pas encoder ou décoder les caractères après « # » ou « ? » et ne supprime pas l’espace blanc de fin après « ? ». Si cette valeur n’est pas spécifiée, l’URL entière est encodée et espace blanc de fin est supprimé.
- ATL_URL_DECODE convertit toutes les séquences XX % en caractères, y compris les séquences d’échappement, avant que l’URL est analysée.
- Les signes de pourcentage ATL_URL_ENCODE_PERCENT encode rencontré. Par défaut, les signes de pourcentage ne sont pas encodés.
- Encode ATL_URL_ENCODE_SPACES_ONLY uniquement des espaces.
- ATL_URL_ESCAPE convertit toutes les séquences d’échappement de (% XX) pour les caractères correspondants.
- ATL_URL_NO_ENCODE ne convertit pas les caractères non sécurisés en séquences d’échappement.
- Ne de ATL_URL_NO_META ne supprime pas les séquences de métadonnées (tel que «. « et ».. ») à partir de l’URL.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE en cas de réussite, FALSE en cas d’échec.

### <a name="remarks"></a>Notes

Se comporte comme la version actuelle de [InternetCanonicalizeUrl](/windows/desktop/api/wininet/nf-wininet-internetcanonicalizeurla) mais ne nécessite ne pas de WinInet ou Internet Explorer soit installé.

### <a name="see-also"></a>Voir aussi

[InternetCanonicalizeUrl](/windows/desktop/api/wininet/nf-wininet-internetcanonicalizeurla)

## <a name="atlcombineurl"></a> AtlCombineUrl

Appelez cette fonction pour associer une URL de base et une URL relative en une URL unique et canonique.

```    
inline BOOL AtlCombineUrl(  
   LPCTSTR szBaseUrl,  
   LPCTSTR szRelativeUrl,  
   LPTSTR szBuffer,  
   DWORD* pdwMaxLength,  
   DWORD dwFlags = 0) throw();  
```

### <a name="parameters"></a>Paramètres

*szBaseUrl*  
L’URL de base.

*szRelativeUrl*  
L’URL par rapport à l’URL de base.

*szBuffer*  
Mémoire tampon allouée par l’appelant de recevoir l’URL au format canonique.

*pdwMaxLength*  
Pointeur vers une variable qui contient la longueur en caractères de *szBuffer*. Si la fonction réussit, la variable reçoit le nombre de caractères écrits dans la mémoire tampon, y compris le caractère null de fin. Si la fonction échoue, la variable reçoit la longueur en octets de la mémoire tampon, y compris l’espace pour le caractère null de fin.

*dwFlags*  
Indicateurs contrôlant le comportement de cette fonction. Consultez [AtlCanonicalizeUrl](#atlcanonicalizeurl).

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE en cas de réussite, FALSE en cas d’échec.

### <a name="remarks"></a>Notes

Se comporte comme la version actuelle de [InternetCombineUrl](/windows/desktop/api/wininet/nf-wininet-internetcombineurla) mais ne nécessite ne pas de WinInet ou Internet Explorer soit installé.

## <a name="atlescapeurl"></a> AtlEscapeUrl

Appelez cette fonction pour convertir tous les caractères non sécurisés en séquences d'échappement.

```    
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

*lpszStringIn*  
L’URL à convertir.

*lpszStringOut*  
Tampon allouée par l’appelant dans lequel l’URL convertie doit être écrite.

*pdwStrLen*  
Pointeur vers une variable DWORD. Si la fonction réussit, *pdwStrLen* reçoit le nombre de caractères écrits dans la mémoire tampon, y compris le caractère null de fin. Si la fonction échoue, la variable reçoit la longueur en octets de la mémoire tampon, y compris l’espace pour le caractère null de fin. Lorsque vous utilisez la version à caractères larges de cette méthode, *pdwStrLen* reçoit le nombre de caractères requis, pas le nombre d’octets.

*dwMaxLength*  
La taille de la mémoire tampon *lpszStringOut*.

*dwFlags*  
Indicateurs ATL_URL contrôlant le comportement de cette fonction. Consultez [ATLCanonicalizeUrl](#atlcanonicalizeurl) pour les valeurs possibles.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE en cas de réussite, FALSE en cas d’échec.

## <a name="atlgetdefaulturlport"></a> AtlGetDefaultUrlPort

Appelez cette fonction pour obtenir le numéro de port par défaut associé à un protocole ou un modèle Internet particulier.

```  
inline ATL_URL_PORT AtlGetDefaultUrlPort(ATL_URL_SCHEME m_nScheme) throw();  
```

### <a name="parameters"></a>Paramètres

*m_nScheme*  
Le [ATL_URL_SCHEME](atl-url-scheme-enum.md) valeur identifiant le schéma pour lequel vous souhaitez obtenir le numéro de port.

### <a name="return-value"></a>Valeur de retour

Le [ATL_URL_PORT](atl-typedefs.md#atl_url_port) associé avec le schéma spécifié ou le ATL_URL_INVALID_PORT_NUMBER si le schéma n’est pas reconnu.  

## <a name="atlisunsafeurlchar"></a> AtlIsUnsafeUrlChar

Appelez cette fonction pour déterminer si un caractère peut être utilisé de manière sécurisée dans une URL.

```  
inline BOOL AtlIsUnsafeUrlChar(char chIn) throw();  
```

### <a name="parameters"></a>Paramètres

*chIn*  
Caractère à tester pour la sécurité.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE si le caractère d’entrée est unsafe, FALSE sinon.

### <a name="remarks"></a>Notes

Les caractères qui ne doivent pas être utilisés dans les URL peuvent être testées à l’aide de cette fonction et convertie à l’aide [AtlCanonicalizeUrl](#atlcanonicalizeurl).

## <a name="atlunescapeurl"></a> AtlUnescapeUrl

Appelez cette fonction pour convertir les caractères ayant fait l'objet d'une séquence d'échappement vers leurs valeurs d'origine.

```    
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

*lpszStringIn*  
L’URL à convertir.

*lpszStringOut*  
Tampon allouée par l’appelant dans lequel l’URL convertie doit être écrite.

*pdwStrLen*  
Pointeur vers une variable DWORD. Si la fonction réussit, la variable reçoit le nombre de caractères écrits dans la mémoire tampon, y compris le caractère null de fin. Si la fonction échoue, la variable reçoit la longueur en octets de la mémoire tampon, y compris l’espace pour le caractère null de fin.

*dwMaxLength*  
La taille de la mémoire tampon *lpszStringOut*.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE en cas de réussite, FALSE en cas d’échec.

### <a name="remarks"></a>Notes

Inverse le processus de conversion appliqué par [AtlEscapeUrl](#atlescapeurl).

## <a name="rgbtohtml"></a> RGBToHtml

Convertit un [COLORREF](/windows/desktop/gdi/colorref) le texte HTML correspondant à cette valeur de couleur à la valeur.

```  
bool inline RGBToHtml(  
   COLORREF color,  
   LPTSTR pbOut,  
   long nBuffer);  
```

### <a name="parameters"></a>Paramètres

*Couleur*  
Une valeur de couleur RVB.

*pbOut*  
Mémoire tampon allouée par l’appelant qui recevra le texte pour la valeur de couleur HTML. La mémoire tampon doit avoir espace pour au moins 8 caractères, y compris un espace pour le terminateur null).

*nBuffer*  
La taille en octets de la mémoire tampon (y compris le terminateur null).

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE en cas de réussite, FALSE en cas d’échec.

### <a name="remarks"></a>Notes

Une valeur de couleur HTML est un signe dièse suivi d’une valeur hexadécimale à 6 chiffres à l’aide de 2 chiffres pour chacun des composants rouges, vert et bleus de la couleur (par exemple, est blanc #FFFFFF).

## <a name="systemtimetohttpdate"></a> SystemTimeToHttpDate

Appelez cette fonction pour convertir une heure système en une chaîne au format approprié pour être utilisée dans les en-têtes HTTP.

```  
inline void SystemTimeToHttpDate( 
   const SYSTEMTIME& st,  
   CStringA& strTime);  
```

### <a name="parameters"></a>Paramètres

*St*  
L’heure système à être obtenus sous forme d’une chaîne de format HTTP.

*strTime*  
Une référence à une variable chaîne à l’heure de réception HTTP date tel que défini dans RFC 2616 ([http://www.ietf.org/rfc/rfc2616.txt](http://www.ietf.org/rfc/rfc2616.txt)) et la norme RFC 1123 ([http://www.ietf.org/rfc/rfc1123.txt](http://www.ietf.org/rfc/rfc1123.txt)).

## <a name="see-also"></a>Voir aussi

[Concepts](../../atl/active-template-library-atl-concepts.md)   
[Composants de bureau COM ATL](../../atl/atl-com-desktop-components.md)   

