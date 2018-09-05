---
title: Fonctions de codage de texte ATL | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- atlbase/ATL::AtlGetHexValue
- atlbase/ATL::AtlGetVersion
- atlenc/ATL::AtlHexDecode
- atlenc/ATL::AtlHexDecodeGetRequiredLength
- atlenc/ATL::AtlHexEncode
- atlenc/ATL::AtlHexEncodeGetRequiredLength
- atlenc/ATL::AtlHexValue
- atlenc/ATL::BEncode
- atlenc/ATL::BEncodeGetRequiredLength
- atlenc/ATL::EscapeXML
- atlenc/ATL::GetExtendedChars
- atlenc/ATL::IsExtendedChar
- atlenc/ATL::QEncode
- atlenc/ATL::QEncodeGetRequiredLength
- atlenc/ATL::QPDecode
- atlenc/ATL::QPDecodeGetRequiredLength
- atlenc/ATL::QPEncode
- atlenc/ATL::QPEncodeGetRequiredLength
- atlenc/ATL::UUDecode
- atlenc/ATL::UUDecodeGetRequiredLength
- atlenc/ATL::UUEncode
- atlenc/ATL::UUEncodeGetRequiredLength
ms.assetid: 2ae1648b-2b87-4112-92aa-0069fcfd23da
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a63caaa23fa59356a5904740cf03b8c36a909930
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43688570"
---
# <a name="atl-text-encoding-functions"></a>Fonctions de codage de texte ATL
Ces fonctions prennent en charge l’encodage et décodage de texte.

|||  
|-|-|  
|[AtlGetHexValue](#atlgethexvalue)|Appelez cette fonction pour obtenir la valeur numérique d'un chiffre hexadécimal.|   
|[AtlGetVersion](#atlgetversion)|Appelez cette fonction pour obtenir la version de la bibliothèque ATL que vous utilisez.  |  
|[AtlHexDecode](#atlhexdecode)|Décode une chaîne de données qui a été encodées sous forme de texte hexadécimal, notamment par un appel précédent à [AtlHexEncode](#atlhexencode).|
|[AtlHexDecodeGetRequiredLength](#atlhexdecodegetrequiredlength)|Appelez cette fonction pour obtenir la taille en octets d'une mémoire tampon qui peut contenir des données décodées à partir d'une chaîne encodée au format hexadécimal de longueur spécifique.|
|[AtlHexEncode](#atlhexencode)|Appelez cette fonction pour encoder des données sous forme de chaîne hexadécimale.|
|[AtlHexEncodeGetRequiredLength](#atlhexencodegetrequiredlength)|Appelez cette fonction pour obtenir la taille en caractères d'une mémoire tampon qui peut contenir une chaîne encodée à partir des données de la taille spécifiée.|
|[AtlHexValue](#atlhexvalue)|Appelez cette fonction pour obtenir la valeur numérique d'un chiffre hexadécimal. |
|[AtlUnicodeToUTF8](#atlunicodetoutf8)|Appelez cette fonction pour convertir une chaîne Unicode au format UTF-8. |
|[BEncode](#bencode)|Appelez cette fonction pour convertir certaines données à l'aide de l'encodage « B ».|
|[BEncodeGetRequiredLength](#bencodegetrequiredlength)|Appelez cette fonction pour obtenir la taille en caractères d'une mémoire tampon qui peut contenir une chaîne encodée à partir des données de la taille spécifiée.|
|[EscapeXML](#escapexml)|Appelez cette fonction pour convertir les caractères dont l'utilisation n'est pas sécurisée dans du code XML en leurs équivalents sécurisés.|
|[GetExtendedChars](#getextendedchars)|Appelez cette fonction pour obtenir le nombre de caractères étendus d'une chaîne.|
|[IsExtendedChar](#isextendedchar)|Appelez cette fonction pour déterminer si un caractère donné est un caractère étendu (inférieur à 32, supérieur à 126 et qui n'est pas une tabulation, un saut de ligne ou un retour chariot)|
|[QEncode](#qencode)|Appelez cette fonction pour convertir certaines données à l'aide de l'encodage « Q ».  |
|[QEncodeGetRequiredLength](#qencodegetrequiredlength)|Appelez cette fonction pour obtenir la taille en caractères d'une mémoire tampon qui peut contenir une chaîne encodée à partir des données de la taille spécifiée.|
|[QPDecode](#qpdecode)|Décode une chaîne de données qui a été encodées au format quoted-printable tels que par un appel précédent à [QPEncode](#qpencode).|
|[QPDecodeGetRequiredLength](#qpdecodegetrequiredlength)|Appelez cette fonction pour obtenir la taille en octets d'une mémoire tampon qui peut contenir des données décodées à partir d'une chaîne encodée au format Quoted-Printable (QP) de longueur spécifique.|
|[QPEncode](#qpencode)|Appelez cette fonction pour encoder des données au format Quoted-Printable (QP).|
|[QPEncodeGetRequiredLength](#qpencodegetrequiredlength)|Appelez cette fonction pour obtenir la taille en caractères d'une mémoire tampon qui peut contenir une chaîne encodée à partir des données de la taille spécifiée.|
|[UUDecode](#uudecode)|Décode une chaîne de données qui a été convertie au format UUENCODE tels que par un appel précédent à [UUEncode](#uuencode).|
|[UUDecodeGetRequiredLength](#uudecodegetrequiredlength)|Appelez cette fonction pour obtenir la taille en octets d'une mémoire tampon qui peut contenir des données décodées à partir d'une chaîne encodée au format UUEncode de longueur spécifique.|
|[UUEncode](#uuencode)|Appelez cette fonction pour convertir des données au format UUEncode. |
|[UUEncodeGetRequiredLength](#uuencodegetrequiredlength)|Appelez cette fonction pour obtenir la taille en caractères d'une mémoire tampon qui peut contenir une chaîne encodée à partir des données de la taille spécifiée.|

## <a name="requirements"></a>Configuration requise  
 **En-tête :** atlenc.h ainsi que  
 
## <a name="atlgethexvalue"></a> AtlGetHexValue
Appelez cette fonction pour obtenir la valeur numérique d'un chiffre hexadécimal.  
  
```    
inline char AtlGetHexValue(char chIn) throw();  
```  
  
### <a name="parameters"></a>Paramètres  
 *chIn*  
 Le caractère hexadécimal '0'-'9', 'A'-'F', ou 'a'-'f'.  
  
### <a name="return-value"></a>Valeur de retour  
 La valeur numérique du caractère d’entrée est interprétée comme un chiffre hexadécimal. Par exemple, une entrée de '0' Retourne une valeur égale à 0 et une entrée de 'A' Retourne une valeur de 10. Si le caractère d’entrée n’est pas un chiffre hexadécimal, cette fonction retourne -1.  
  
## <a name="atlgetversion"></a> AtlGetVersion
Appelez cette fonction pour obtenir la version de la bibliothèque ATL que vous utilisez.  
  
```  
ATLAPI_(DWORD) AtlGetVersion(void* pReserved);  
```  
  
### <a name="parameters"></a>Paramètres  
 *Conservés*  
 Un pointeur réservé.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne une valeur entière DWORD de la version de la bibliothèque ATL qui sont de compilation ou d’exécution.  
  
## <a name="example"></a>Exemple  
 La fonction doit être appelée comme suit.  
  
 [!code-cpp[NVC_ATL_Utilities#95](../../atl/codesnippet/cpp/atl-text-encoding-functions_1.cpp)]  
  
### <a name="requirements"></a>Configuration requise  
 **En-tête :** atlbase.h  

## <a name="atlhexdecode"></a> AtlHexDecode
Décode une chaîne de données qui a été encodées sous forme de texte hexadécimal, notamment par un appel précédent à [AtlHexEncode](#atlhexencode).  
  
```    
inline BOOL AtlHexDecode(  
   LPCSTR pSrcData,  
   int nSrcLen,  
   LPBYTE pbDest,  
   int* pnDestLen) throw();  
```  
  
### <a name="parameters"></a>Paramètres  
 *pSrcData*  
 Chaîne contenant les données à décoder.  
  
 *nSrcLen*  
 La longueur en caractères de *pSrcData*.  
  
 *pbDest*  
 Mémoire tampon allouée par l’appelant pour recevoir les données décodées.  
  
 *pnDestLen*  
 Pointeur vers une variable qui contient la longueur en octets de *pbDest*. Si la fonction réussit, la variable reçoit le nombre d’octets écrits dans la mémoire tampon. Si la fonction échoue, la variable reçoit la longueur en octets de la mémoire tampon.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la valeur TRUE en cas de réussite, FALSE en cas d’échec.  
  
## <a name="atlhexdecodegetrequiredlength"></a> AtlHexDecodeGetRequiredLength
Appelez cette fonction pour obtenir la taille en octets d'une mémoire tampon qui peut contenir des données décodées à partir d'une chaîne encodée au format hexadécimal de longueur spécifique.  
  
```  
inline int AtlHexDecodeGetRequiredLength(int nSrcLen) throw();  
```  
  
### <a name="parameters"></a>Paramètres  
 *nSrcLen*  
 Le nombre de caractères dans la chaîne encodée.  
  
### <a name="return-value"></a>Valeur de retour  
 Le nombre d’octets requis pour une mémoire tampon qui peut contenir une chaîne décodée de *nSrcLen* caractères.  
  
## <a name="atlhexencode"></a> AtlHexEncode
Appelez cette fonction pour encoder des données sous forme de chaîne hexadécimale.  
  
```  
inline BOOL AtlHexEncode(  
   const BYTE * pbSrcData,  
   int nSrcLen,  
   LPSTR szDest,  
int * pnDestLen) throw();  
```  
  
### <a name="parameters"></a>Paramètres  
 *pbSrcData*  
 La mémoire tampon contenant les données à encoder.  
  
 *nSrcLen*  
 La longueur en octets des données à encoder.  
  
 *szDest*  
 Mémoire tampon allouée par l’appelant pour recevoir les données encodées.  
  
 *pnDestLen*  
 Pointeur vers une variable qui contient la longueur en caractères de *szDest*. Si la fonction réussit, la variable reçoit le nombre de caractères écrits dans la mémoire tampon. Si la fonction échoue, la variable reçoit la longueur requise en caractères de la mémoire tampon.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la valeur TRUE en cas de réussite, FALSE en cas d’échec.  
  
### <a name="remarks"></a>Notes  
 Chaque octet des données sources est encodé comme 2 caractères hexadécimaux.  
  
## <a name="atlhexencodegetrequiredlength"></a> AtlHexEncodeGetRequiredLength
Appelez cette fonction pour obtenir la taille en caractères d'une mémoire tampon qui peut contenir une chaîne encodée à partir des données de la taille spécifiée.  
  
```  
inline int AtlHexEncodeGetRequiredLength(int nSrcLen) throw();  
```  
  
### <a name="parameters"></a>Paramètres  
 *nSrcLen*  
 Le nombre d’octets de données à encoder.  
  
### <a name="return-value"></a>Valeur de retour  
 Le nombre de caractères requis pour une mémoire tampon qui peut contenir des données encodées de *nSrcLen* octets.  
  
## <a name="atlhexvalue"></a> AtlHexValue
Appelez cette fonction pour obtenir la valeur numérique d'un chiffre hexadécimal.  
  
```  
inline short AtlHexValue(char chIn) throw();  
```  
  
### <a name="parameters"></a>Paramètres  
 *chIn*  
 Le caractère hexadécimal '0'-'9', 'A'-'F', ou 'a'-'f'.  
  
### <a name="return-value"></a>Valeur de retour  
 La valeur numérique du caractère d’entrée est interprétée comme un chiffre hexadécimal. Par exemple, une entrée de '0' Retourne une valeur égale à 0 et une entrée de 'A' Retourne une valeur de 10. Si le caractère d’entrée n’est pas un chiffre hexadécimal, cette fonction retourne -1.  
  
## <a name="atlunicodetoutf8"></a> AtlUnicodeToUTF8
Appelez cette fonction pour convertir une chaîne Unicode au format UTF-8.  
  
```  
ATL_NOINLINE inline int AtlUnicodeToUTF8(  
   LPCWSTR wszSrc,  
   int nSrc,  
   LPSTR szDest,  
   int nDest) throw();  
```  
  
### <a name="parameters"></a>Paramètres  
 *wszSrc*  
 La chaîne Unicode à convertir  
  
 *nSrc*  
 La longueur en caractères de la chaîne Unicode.  
  
 *szDest*  
 Mémoire tampon allouée par l’appelant pour recevoir la chaîne convertie.  
  
 *nDest*  
 La longueur en octets de la mémoire tampon.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne le nombre de caractères pour la chaîne convertie.  
  
### <a name="remarks"></a>Notes  
 Pour déterminer la taille de la mémoire tampon requise pour la chaîne convertie, appelez cette fonction en passant de 0 pour *szDest* et *nDest*.  
  
## <a name="bencode"></a> BEncode  
Appelez cette fonction pour convertir certaines données à l'aide de l'encodage « B ».  
  
```  
inline BOOL BEncode(  
   BYTE* pbSrcData,  
   int nSrcLen,  
   LPSTR szDest,  
   int* pnDestLen,  
   LPCSTR pszCharSet) throw();  
```  
  
### <a name="parameters"></a>Paramètres  
 *pbSrcData*  
 La mémoire tampon contenant les données à encoder.  
  
 *nSrcLen*  
 La longueur en octets des données à encoder.  
  
 *szDest*  
 Mémoire tampon allouée par l’appelant pour recevoir les données encodées.  
  
 *pnDestLen*  
 Pointeur vers une variable qui contient la longueur en caractères de *szDest*. Si la fonction réussit, la variable reçoit le nombre de caractères écrits dans la mémoire tampon. Si la fonction échoue, la variable reçoit la longueur requise en caractères de la mémoire tampon.  
  
 *pszCharSet*  
 Le jeu de caractères à utiliser pour la conversion.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la valeur TRUE en cas de réussite, FALSE en cas d’échec.  
  
### <a name="remarks"></a>Notes  
 Le schéma d’encodage « B » est décrite dans RFC 2047 ([http://www.ietf.org/rfc/rfc2047.txt](http://www.ietf.org/rfc/rfc2047.txt)).  
  
## <a name="bencodegetrequiredlength"></a> BEncodeGetRequiredLength 
Appelez cette fonction pour obtenir la taille en caractères d'une mémoire tampon qui peut contenir une chaîne encodée à partir des données de la taille spécifiée.  
  
```  
inline int BEncodeGetRequiredLength(int nSrcLen, int nCharsetLen) throw();  
```  
  
### <a name="parameters"></a>Paramètres  
 *nSrcLen*  
 Le nombre d’octets de données à encoder.  
  
 *nCharsetLen*  
 La longueur en caractères du jeu de caractères à utiliser pour la conversion.  
  
### <a name="return-value"></a>Valeur de retour  
 Le nombre de caractères requis pour une mémoire tampon qui peut contenir des données encodées de *nSrcLen* octets.  
  
### <a name="remarks"></a>Notes  
 Le schéma d’encodage « B » est décrite dans RFC 2047 ([http://www.ietf.org/rfc/rfc2047.txt](http://www.ietf.org/rfc/rfc2047.txt)).  
  
## <a name="escapexml"></a> EscapeXML
Appelez cette fonction pour convertir les caractères dont l'utilisation n'est pas sécurisée dans du code XML en leurs équivalents sécurisés.  
  
```  
inline int EscapeXML(  
   const wchar_t * szIn,  
   int nSrcLen,  
   wchar_t * szEsc,  
   int nDestLen,  
   DWORD dwFlags = ATL_ESC_FLAG_NONE) throw();  
```  
  
### <a name="parameters"></a>Paramètres  
 *szIn*  
 Chaîne à convertir.  
  
 *nSrclen*  
 La longueur en caractères de la chaîne à convertir.  
  
 *szEsc*  
 Mémoire tampon allouée par l’appelant pour recevoir la chaîne convertie.  
  
 *nDestLen*  
 La longueur en caractères de la mémoire tampon allouée par l’appelant.  
  
 *dwFlags*  
 Indicateurs de ATL_ESC décrivant comment la conversion doit être effectuée. 

- Comportement par défaut ATL_ESC_FLAG_NONE. Guillemet les marques et les apostrophes ne sont pas converties.
- Marques ATL_ESC_FLAG_ATTR mettre entre guillemets et les apostrophes sont convertis en `&quot;` et `&apos;` respectivement.


  
### <a name="return-value"></a>Valeur de retour  
 La longueur en caractères de la chaîne convertie.  
  
### <a name="remarks"></a>Notes  
 Conversions possibles effectuées par cette fonction sont affichées dans la table :  
  
|Source|Destination|  
|------------|-----------------|  
|\<|&lt;|  
|>|&gt;|  
|&|&amp;|  
|'|&apos;|  
|"|&quot;|  
  
## <a name="getextendedchars"></a> GetExtendedChars
Appelez cette fonction pour obtenir le nombre de caractères étendus d'une chaîne.  
  
```  
inline int GetExtendedChars(LPCSTR szSrc, int nSrcLen) throw();  
```  
  
### <a name="parameters"></a>Paramètres  
 *szSrc*  
 La chaîne à analyser.  
  
 *nSrcLen*  
 La longueur de la chaîne en caractères.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne le nombre de caractères étendus trouvé dans la chaîne, comme déterminé par [IsExtendedChar](#isextendedchar).  
  
## <a name="isextendedchar"></a> IsExtendedChar
Appelez cette fonction pour déterminer si un caractère donné est un caractère étendu (inférieur à 32, supérieur à 126 et qui n'est pas une tabulation, un saut de ligne ou un retour chariot)  
  
```  
inline int IsExtendedChar(char ch) throw();  
```  
  
### <a name="parameters"></a>Paramètres  
 *ch*  
 Le caractère à tester  
  
### <a name="return-value"></a>Valeur de retour  
 TRUE si le caractère est étendu.  
  
## <a name="qencode"></a> QEncode
Appelez cette fonction pour convertir certaines données à l'aide de l'encodage « Q ».  
  
```  
inline BOOL QEncode(  
   BYTE* pbSrcData,  
   int nSrcLen,  
   LPSTR szDest,  
   int* pnDestLen,  
   LPCSTR pszCharSet,  
   int* pnNumEncoded = NULL) throw();  
```  
  
### <a name="parameters"></a>Paramètres  
 *pbSrcData*  
 La mémoire tampon contenant les données à encoder.  
  
 *nSrcLen*  
 La longueur en octets des données à encoder.  
  
 *szDest*  
 Mémoire tampon allouée par l’appelant pour recevoir les données encodées.  
  
 *pnDestLen*  
 Pointeur vers une variable qui contient la longueur en caractères de *szDest*. Si la fonction réussit, la variable reçoit le nombre de caractères écrits dans la mémoire tampon. Si la fonction échoue, la variable reçoit la longueur requise en caractères de la mémoire tampon.  
  
 *pszCharSet*  
 Le jeu de caractères à utiliser pour la conversion.  
  
 *pnNumEncoded*  
 Pointeur vers une variable qui, en retour, contient le nombre de caractères potentiellement dangereux qui devait être converti.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la valeur TRUE en cas de réussite, FALSE en cas d’échec.  
  
### <a name="remarks"></a>Notes  
 Le schéma d’encodage « Q » est décrite dans RFC 2047 ([http://www.ietf.org/rfc/rfc2047.txt](http://www.ietf.org/rfc/rfc2047.txt)).  
  
## <a name="qencodegetrequiredlength"></a> QEncodeGetRequiredLength 
Appelez cette fonction pour obtenir la taille en caractères d'une mémoire tampon qui peut contenir une chaîne encodée à partir des données de la taille spécifiée.  
  
```  
inline int QEncodeGetRequiredLength(int nSrcLen, int nCharsetLen) throw();  
```  
  
### <a name="parameters"></a>Paramètres  
 *nSrcLen*  
 Le nombre d’octets de données à encoder.  
  
 *nCharsetLen*  
 La longueur en caractères du jeu de caractères à utiliser pour la conversion.  
  
### <a name="return-value"></a>Valeur de retour  
 Le nombre de caractères requis pour une mémoire tampon qui peut contenir des données encodées de *nSrcLen* octets.  
  
### <a name="remarks"></a>Notes  
 Le schéma d’encodage « Q » est décrite dans RFC 2047 ([http://www.ietf.org/rfc/rfc2047.txt](http://www.ietf.org/rfc/rfc2047.txt)).  
  
## <a name="qpdecode"></a> QPDecode
Décode une chaîne de données qui a été encodées au format quoted-printable tels que par un appel précédent à [QPEncode](#qpencode).  
  
```  
inline BOOL QPDecode(  
   BYTE* pbSrcData,  
   int nSrcLen,  
   LPSTR szDest,  
   int* pnDestLen,  
   DWORD dwFlags = 0) throw();  
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *pbSrcData*  
 La mémoire tampon contenant les données à décoder.  
  
 [in] *nSrcLen*  
 La longueur en octets de *pbSrcData*.  
  
 [out] *szDest*  
 Mémoire tampon allouée par l’appelant pour recevoir les données décodées.  
  
 [out] *pnDestLen*  
 Pointeur vers une variable qui contient la longueur en octets de *szDest*. Si la fonction réussit, la variable reçoit le nombre d’octets écrits dans la mémoire tampon. Si la fonction échoue, la variable reçoit la longueur en octets de la mémoire tampon.  
  
 [in] *dwFlags*  
 Indicateurs ATLSMTP_QPENCODE décrivant comment la conversion doit être effectuée.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la valeur TRUE en cas de réussite, FALSE en cas d’échec.  
  
### <a name="remarks"></a>Notes  
 Le schéma d’encodage quoted-printable est décrit dans RFC 2045 ([http://www.ietf.org/rfc/rfc2045.txt](http://www.ietf.org/rfc/rfc2045.txt)).  
  
## <a name="qpdecodegetrequiredlength"></a> QPDecodeGetRequiredLength
Appelez cette fonction pour obtenir la taille en octets d'une mémoire tampon qui peut contenir des données décodées à partir d'une chaîne encodée au format Quoted-Printable (QP) de longueur spécifique.  
  
```  
inline int QPDecodeGetRequiredLength(int nSrcLen) throw();  
```  
  
### <a name="parameters"></a>Paramètres  
 *nSrcLen*  
 Le nombre de caractères dans la chaîne encodée.  
  
### <a name="return-value"></a>Valeur de retour  
 Le nombre d’octets requis pour une mémoire tampon qui peut contenir une chaîne décodée de *nSrcLen* caractères.  
  
### <a name="remarks"></a>Notes  
 Le schéma d’encodage quoted-printable est décrit dans RFC 2045 ([http://www.ietf.org/rfc/rfc2045.txt](http://www.ietf.org/rfc/rfc2045.txt)).  
  
## <a name="qpencode"></a> QPEncode
Appelez cette fonction pour encoder des données au format Quoted-Printable (QP).  
  
```  
inline BOOL QPEncode(  
   BYTE* pbSrcData,  
   int nSrcLen,  
   LPSTR szDest,  
   int* pnDestLen,  
   DWORD dwFlags = 0) throw ();  
```  
  
### <a name="parameters"></a>Paramètres  
 *pbSrcData*  
 La mémoire tampon contenant les données à encoder.  
  
 *nSrcLen*  
 La longueur en octets des données à encoder.  
  
 *szDest*  
 Mémoire tampon allouée par l’appelant pour recevoir les données encodées.  
  
 *pnDestLen*  
 Pointeur vers une variable qui contient la longueur en caractères de *szDest*. Si la fonction réussit, la variable reçoit le nombre de caractères écrits dans la mémoire tampon. Si la fonction échoue, la variable reçoit la longueur requise en caractères de la mémoire tampon.  
  
 *dwFlags*  
 Indicateurs ATLSMTP_QPENCODE décrivant comment la conversion doit être effectuée. 
- ATLSMTP_QPENCODE_DOT si une période apparaît au début d’une ligne, elle est ajoutée à la sortie ainsi qu’encodé.
- ATLSMTP_QPENCODE_TRAILING_SOFT ajoute `=\r\n` à la chaîne encodée.

Le schéma d’encodage quoted-printable est décrite dans [RFC 2045](http://www.ietf.org/rfc/rfc2045.txt).
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la valeur TRUE en cas de réussite, FALSE en cas d’échec.  
  
### <a name="remarks"></a>Notes  
 Le schéma d’encodage quoted-printable est décrit dans RFC 2045 ([http://www.ietf.org/rfc/rfc2045.txt](http://www.ietf.org/rfc/rfc2045.txt)).  
  
## <a name="qpencodegetrequiredlength"></a> QPEncodeGetRequiredLength
Appelez cette fonction pour obtenir la taille en caractères d'une mémoire tampon qui peut contenir une chaîne encodée à partir des données de la taille spécifiée.  
  
```  
inline int QPEncodeGetRequiredLength(int nSrcLen) throw ();  
```  
  
### <a name="parameters"></a>Paramètres  
 *nSrcLen*  
 Le nombre d’octets de données à encoder.  
  
### <a name="return-value"></a>Valeur de retour  
 Le nombre de caractères requis pour une mémoire tampon qui peut contenir des données encodées de *nSrcLen* octets.  
  
### <a name="remarks"></a>Notes  
 Le schéma d’encodage quoted-printable est décrit dans RFC 2045 ([http://www.ietf.org/rfc/rfc2045.txt](http://www.ietf.org/rfc/rfc2045.txt)).  
  
## <a name="uudecode"></a> UUDecode
Décode une chaîne de données qui a été convertie au format UUENCODE tels que par un appel précédent à [UUEncode](#uuencode).  
  
```  
inline BOOL UUDecode(  
   BYTE* pbSrcData,  
   int nSrcLen,  
   BYTE* pbDest,  
   int* pnDestLen) throw ();  
```  
  
### <a name="parameters"></a>Paramètres  
 *pbSrcData*  
 Chaîne contenant les données à décoder.  
  
 *nSrcLen*  
 La longueur en octets de *pbSrcData*.  
  
 *pbDest*  
 Mémoire tampon allouée par l’appelant pour recevoir les données décodées.  
  
 *pnDestLen*  
 Pointeur vers une variable qui contient la longueur en octets de *pbDest*. Si la fonction réussit, la variable reçoit le nombre d’octets écrits dans la mémoire tampon. Si la fonction échoue, la variable reçoit la longueur en octets de la mémoire tampon.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la valeur TRUE en cas de réussite, FALSE en cas d’échec.  
  
### <a name="remarks"></a>Notes  
 Cette implémentation uuencoding suit la spécification de POSIX P1003.2b/D11.  
  
## <a name="uudecodegetrequiredlength"></a> UUDecodeGetRequiredLength
Appelez cette fonction pour obtenir la taille en octets d'une mémoire tampon qui peut contenir des données décodées à partir d'une chaîne encodée au format UUEncode de longueur spécifique.  
  
```  
inline int UUDecodeGetRequiredLength(int nSrcLen) throw ();  
```  
  
### <a name="parameters"></a>Paramètres  
 *nSrcLen*  
 Le nombre de caractères dans la chaîne encodée.  
  
### <a name="return-value"></a>Valeur de retour  
 Le nombre d’octets requis pour une mémoire tampon qui peut contenir une chaîne décodée de *nSrcLen* caractères.  
  
### <a name="remarks"></a>Notes  
 Cette implémentation uuencoding suit la spécification de POSIX P1003.2b/D11.  
  
## <a name="uuencode"></a> UUEncode
Appelez cette fonction pour convertir des données au format UUEncode.  
  
```  
inline BOOL UUEncode(  
   const BYTE* pbSrcData,  
   int nSrcLen,  
   LPSTR szDest,  
   int* pnDestLen,  
   LPCTSTR lpszFile = _T("file"),  
   DWORD dwFlags = 0) throw ();  
```  
  
### <a name="parameters"></a>Paramètres  
 *pbSrcData*  
 La mémoire tampon contenant les données à encoder.  
  
 *nSrcLen*  
 La longueur en octets des données à encoder.  
  
 *szDest*  
 Mémoire tampon allouée par l’appelant pour recevoir les données encodées.  
  
 *pnDestLen*  
 Pointeur vers une variable qui contient la longueur en caractères de *szDest*. Si la fonction réussit, la variable reçoit le nombre de caractères écrits dans la mémoire tampon. Si la fonction échoue, la variable reçoit la longueur requise en caractères de la mémoire tampon.  
  
 *lpszFile*  
 Le fichier à ajouter à l’en-tête lorsque ATLSMTP_UUENCODE_HEADER est spécifié dans *dwFlags*.  
  
 *dwFlags*  
 Indicateurs contrôlant le comportement de cette fonction. 
- ATLSMTP_UUENCODE_HEADE l’en-tête doit être encodé.
- ATLSMTP_UUENCODE_END la fin doit être encodé.
- Pliaient des données de ATLSMTP_UUENCODE_DOT sera effectuée.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la valeur TRUE en cas de réussite, FALSE en cas d’échec.  
  
### <a name="remarks"></a>Notes  
 Cette implémentation uuencoding suit la spécification de POSIX P1003.2b/D11.  
  
## <a name="uuencodegetrequiredlength"></a> UUEncodeGetRequiredLength
Appelez cette fonction pour obtenir la taille en caractères d'une mémoire tampon qui peut contenir une chaîne encodée à partir des données de la taille spécifiée.  
  
```  
inline int UUEncodeGetRequiredLength(int nSrcLen) throw ();  
```  
  
### <a name="parameters"></a>Paramètres  
 *nSrcLen*  
 Le nombre d’octets de données à encoder.  
  
### <a name="return-value"></a>Valeur de retour  
 Le nombre de caractères requis pour une mémoire tampon qui peut contenir des données encodées de *nSrcLen* octets.  
  
### <a name="remarks"></a>Notes  
 Cette implémentation uuencoding suit la spécification de POSIX P1003.2b/D11.  
  
### <a name="see-also"></a>Voir aussi  
 [Concepts](../../atl/active-template-library-atl-concepts.md)   
 [Composants de bureau COM ATL](../../atl/atl-com-desktop-components.md)   