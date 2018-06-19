---
title: Fonctions utilitaires de ATL HTTP | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 4db57ef2-31fa-4696-bbeb-79a9035033ed
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 476ca29de5a44e8ebb20d53ec0b88834c7b03eea
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32363782"
---
# <a name="atl-http-utility-functions"></a>Fonctions utilitaires de HTTP ATL

Ces fonctions prennent en charge la manipulation d’URL.

|||  
|-|-|  
|[AtlCanonicalizeUrl](#atlcanonicalizeurl)|Canonicalise une URL qui inclut la conversion de caractères non sécurisés et les espaces en séquences d’échappement.|  
|[AtlCombineUrl](#atlcombineurl)|Combine une URL de base et une URL relative en une URL unique et canonique.|  
|[AtlEscapeUrl](#atlescapeurl)|Convertit tous les caractères non sécurisés en séquences d’échappement.|  
|[AtlGetDefaultUrlPort](#atlgetdefaulturlport)|Obtient le numéro de port par défaut associé à un protocole Internet particulier ou le schéma.|  
|[AtlIsUnsafeUrlChar](#atlisunsafeurlchar)|Détermine si un caractère est utilisé dans une URL.|  
|[AtlUnescapeUrl](#atlunescapeurl)|Convertit les caractères d’échappement vers leurs valeurs d’origine.|  
|[RGBToHtml](#rgbtohtml)|Convertit un [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) valeur en texte HTML correspondant à cette valeur de couleur.|
|[SystemTimeToHttpDate](#systemtimetohttpdate)|Appelez cette fonction pour convertir une heure système en une chaîne au format approprié pour être utilisée dans les en-têtes HTTP.|

## <a name="requirements"></a>Spécifications  
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
 `szUrl`  
 URL à mettre en forme canonique.  
  
 `szCanonicalized`  
 Mémoire tampon allouée par l’appelant pour recevoir l’URL au format canonique.  
  
 `pdwMaxLength`  
 Pointeur vers une variable qui contient la longueur en caractères de `szCanonicalized`. Si la fonction réussit, la variable reçoit le nombre de caractères écrits dans la mémoire tampon, y compris le caractère null de fin. Si la fonction échoue, la variable reçoit la longueur en octets de la mémoire tampon y compris un espace pour le caractère null de fin.  
  
 `dwFlags`  
 Indicateurs ATL_URL contrôler le comportement de cette fonction. 

- `ATL_URL_BROWSER_MODE` Ne pas encoder ou décoder les caractères après « # » ou « ? » et ne supprime pas l’espace blanc de fin après « ? ». Si cette valeur n’est pas spécifiée, l’URL entière est encodée et espace blanc de fin est supprimé.
- `ATL_URL_DECODE` Convertit toutes les séquences de XX % en caractères, y compris les séquences d’échappement, avant que l’URL est analysée.
- `ATL_URL_ENCODE_PERCENT` Encode les signes de pourcentage rencontrés. Par défaut, les signes de pourcentage ne sont pas encodés.
- `ATL_URL_ENCODE_SPACES_ONLY` Encode des espaces uniquement.
- `ATL_URL_ESCAPE` Toutes les séquences d’échappement (% XX) convertit les caractères correspondants.
- `ATL_URL_NO_ENCODE` Ne convertit pas les caractères non sécurisés en séquences d’échappement.
- `ATL_URL_NO_META` Ne supprime pas les séquences de métadonnées (tel que «. « et ».. ») à partir de l’URL. 
  
### <a name="return-value"></a>Valeur de retour  
 Retourne **TRUE** en cas de réussite, **FALSE** en cas d’échec.  
  
### <a name="remarks"></a>Notes  
 Se comporte comme la version actuelle de [InternetCanonicalizeUrl](http://msdn.microsoft.com/library/windows/desktop/aa384342) mais ne nécessite ne pas de WinInet ou Internet Explorer soit installé.  
  
### <a name="see-also"></a>Voir aussi  
 [InternetCanonicalizeUrl](http://msdn.microsoft.com/library/windows/desktop/aa384342)

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
  
 `szBuffer`  
 Mémoire tampon allouée par l’appelant pour recevoir l’URL au format canonique.  
  
 `pdwMaxLength`  
 Pointeur vers une variable qui contient la longueur en caractères de `szBuffer`. Si la fonction réussit, la variable reçoit le nombre de caractères écrits dans la mémoire tampon, y compris le caractère null de fin. Si la fonction échoue, la variable reçoit la longueur en octets de la mémoire tampon y compris un espace pour le caractère null de fin.  
  
 `dwFlags`  
 Indicateurs de contrôler le comportement de cette fonction. Consultez [AtlCanonicalizeUrl](#atlcanonicalizeurl).  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne **TRUE** en cas de réussite, **FALSE** en cas d’échec.  
  
### <a name="remarks"></a>Notes  
 Se comporte comme la version actuelle de [InternetCombineUrl](http://msdn.microsoft.com/library/windows/desktop/aa384355) mais ne nécessite ne pas de WinInet ou Internet Explorer soit installé.  
  
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
 `lpszStringIn`  
 L’URL à convertir.  
  
 `lpszStringOut`  
 Tampon allouée par l’appelant dans lequel les URL convertie doit être écrite.  
  
 `pdwStrLen`  
 Pointeur vers une variable DWORD. Si la fonction réussit, `pdwStrLen` reçoit le nombre de caractères écrits dans la mémoire tampon, y compris le caractère null de fin. Si la fonction échoue, la variable reçoit la longueur en octets de la mémoire tampon y compris un espace pour le caractère null de fin. Lors de l’utilisation de cette méthode, la version à caractères larges `pdwStrLen` reçoit le nombre de caractères requis, pas le nombre d’octets.  
  
 `dwMaxLength`  
 La taille de la mémoire tampon `lpszStringOut`.  
  
 `dwFlags`  
 Indicateurs ATL_URL contrôler le comportement de cette fonction. Consultez [ATLCanonicalizeUrl](#atlcanonicalizeurl) pour les valeurs possibles.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne **TRUE** en cas de réussite, **FALSE** en cas d’échec.  
  
## <a name="atlgetdefaulturlport"></a> 
 Appelez cette fonction pour obtenir le numéro de port par défaut associé à un protocole ou un modèle Internet particulier.  
  
```  
inline ATL_URL_PORT AtlGetDefaultUrlPort(ATL_URL_SCHEME m_nScheme) throw();  
```  
  
### <a name="parameters"></a>Paramètres  
 *m_nScheme*  
 Le [ATL_URL_SCHEME](atl-url-scheme-enum.md) valeur permettant d’identifier le schéma pour lequel vous souhaitez obtenir le numéro de port.  
  
### <a name="return-value"></a>Valeur de retour  
 Le [ATL_URL_PORT](atl-typedefs.md#atl_url_port) associé au schéma spécifié ou ATL_URL_INVALID_PORT_NUMBER si le schéma n’est pas reconnu.  

## <a name="atlisunsafeurlchar"></a> AtlIsUnsafeUrlChar
 Appelez cette fonction pour déterminer si un caractère peut être utilisé de manière sécurisée dans une URL.  
  
```  
inline BOOL AtlIsUnsafeUrlChar(char chIn) throw();  
```  
  
### <a name="parameters"></a>Paramètres  
 `chIn`  
 Caractère à tester pour la sécurité.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne **TRUE** si le caractère d’entrée est unsafe, **FALSE** dans le cas contraire.  
  
### <a name="remarks"></a>Notes  
 Les caractères qui ne doivent pas être utilisées dans les URL peut être testés à l’aide de cette fonction et converti à l’aide [AtlCanonicalizeUrl](#atlcanonicalizeurl).  
  
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
 `lpszStringIn`  
 L’URL à convertir.  
  
 `lpszStringOut`  
 Tampon allouée par l’appelant dans lequel les URL convertie doit être écrite.  
  
 `pdwStrLen`  
 Pointeur vers une variable DWORD. Si la fonction réussit, la variable reçoit le nombre de caractères écrits dans la mémoire tampon, y compris le caractère null de fin. Si la fonction échoue, la variable reçoit la longueur en octets de la mémoire tampon y compris un espace pour le caractère null de fin.  
  
 `dwMaxLength`  
 La taille de la mémoire tampon `lpszStringOut`.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne **TRUE** en cas de réussite, **FALSE** en cas d’échec.  
  
### <a name="remarks"></a>Notes  
 Inverse le processus de conversion appliqué par [AtlEscapeUrl](#atlescapeurl).  
  
## <a name="rgbtohtml"></a> RGBToHtml
Convertit un [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) valeur en texte HTML correspondant à cette valeur de couleur.  
  
```  
bool inline RGBToHtml(  
   COLORREF color,  
   LPTSTR pbOut,  
   long nBuffer);  
```  
  
### <a name="parameters"></a>Paramètres  
 `color`  
 Une valeur de couleur RVB.  
  
 `pbOut`  
 Mémoire tampon allouée par l’appelant pour recevoir le texte de la valeur de couleur HTML. La mémoire tampon d’espace doit être d’au moins 8 caractères, y compris un espace pour le terminateur null).  
  
 *nBuffer*  
 La taille en octets de la mémoire tampon (y compris l’espace pour le terminateur null).  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne **TRUE** en cas de réussite, **FALSE** en cas d’échec.  
  
### <a name="remarks"></a>Notes  
 Une valeur de couleur HTML est un signe dièse suivi d’une valeur hexadécimale à 6 chiffres pour chacun des composants rouges, verts et bleus de la couleur à l’aide de 2 chiffres (par exemple, est blanc #FFFFFF).  
  
## <a name="systemtimetohttpdate"></a> SystemTimeToHttpDate
Appelez cette fonction pour convertir une heure système en une chaîne au format approprié pour être utilisée dans les en-têtes HTTP.  
  
```  
inline void SystemTimeToHttpDate( 
   const SYSTEMTIME& st,  
   CStringA& strTime);  
```  
  
### <a name="parameters"></a>Paramètres  
 `st`  
 L’heure système doit être obtenu comme une chaîne de format HTTP.  
  
 *strTime*  
 Une référence à une variable de chaîne pour recevoir le HTTP date heure définis dans RFC 2616 ([http://www.ietf.org/rfc/rfc2616.txt](http://www.ietf.org/rfc/rfc2616.txt)) et la norme RFC 1123 ([http://www.ietf.org/rfc/rfc1123.txt](http://www.ietf.org/rfc/rfc1123.txt)).  
  
## <a name="see-also"></a>Voir aussi  
 [Concepts](../../atl/active-template-library-atl-concepts.md)   
 [Composants de bureau COM ATL](../../atl/atl-com-desktop-components.md)   

