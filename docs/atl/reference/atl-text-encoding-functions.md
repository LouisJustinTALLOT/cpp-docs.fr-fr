---
title: Fonctions d’encodage de texte ATL
ms.date: 11/04/2016
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
ms.openlocfilehash: 330a73e0d41bf384a799635d5f2e6f09f7e3dd03
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88833853"
---
# <a name="atl-text-encoding-functions"></a>Fonctions d’encodage de texte ATL

Ces fonctions prennent en charge l’encodage et le décodage de texte.

|Fonction|Description|
|-|-|
|[AtlGetHexValue](#atlgethexvalue)|Appelez cette fonction pour obtenir la valeur numérique d'un chiffre hexadécimal.|
|[AtlGetVersion](#atlgetversion)|Appelez cette fonction pour récupérer la version de la bibliothèque ATL que vous utilisez.  |
|[AtlHexDecode](#atlhexdecode)|Décode une chaîne de données qui a été encodée sous forme de texte hexadécimal, par exemple par un appel précédent à [AtlHexEncode](#atlhexencode).|
|[AtlHexDecodeGetRequiredLength](#atlhexdecodegetrequiredlength)|Appelez cette fonction pour obtenir la taille en octets d'une mémoire tampon qui peut contenir des données décodées à partir d'une chaîne encodée au format hexadécimal de longueur spécifique.|
|[AtlHexEncode](#atlhexencode)|Appelez cette fonction pour encoder des données sous forme de chaîne hexadécimale.|
|[AtlHexEncodeGetRequiredLength](#atlhexencodegetrequiredlength)|Appelez cette fonction pour obtenir la taille en caractères d'une mémoire tampon qui peut contenir une chaîne encodée à partir des données de la taille spécifiée.|
|[AtlHexValue](#atlhexvalue)|Appelez cette fonction pour obtenir la valeur numérique d'un chiffre hexadécimal. |
|[AtlUnicodeToUTF8](#atlunicodetoutf8)|Appelez cette fonction pour convertir une chaîne Unicode au format UTF-8. |
|[BEncode](#bencode)|Appelez cette fonction pour convertir certaines données à l'aide de l'encodage « B ».|
|[BEncodeGetRequiredLength](#bencodegetrequiredlength)|Appelez cette fonction pour obtenir la taille en caractères d'une mémoire tampon qui peut contenir une chaîne encodée à partir des données de la taille spécifiée.|
|[EscapeXML](#escapexml)|Appelez cette fonction pour convertir les caractères dont l'utilisation n'est pas sécurisée dans du code XML en leurs équivalents sécurisés.|
|[GetExtendedChars](#getextendedchars)|Appelez cette fonction pour obtenir le nombre de caractères étendus d'une chaîne.|
|[IsExtendedChar](#isextendedchar)|Appelez cette fonction pour déterminer si un caractère donné est un caractère étendu (inférieur à 32, supérieur à 126, et non un onglet, un saut de ligne ou un retour chariot)|
|[QEncode](#qencode)|Appelez cette fonction pour convertir certaines données à l'aide de l'encodage « Q ».  |
|[QEncodeGetRequiredLength](#qencodegetrequiredlength)|Appelez cette fonction pour obtenir la taille en caractères d'une mémoire tampon qui peut contenir une chaîne encodée à partir des données de la taille spécifiée.|
|[QPDecode](#qpdecode)|Décode une chaîne de données qui a été encodée au format Quoted-Printable, par exemple par un appel précédent à [QPEncode](#qpencode).|
|[QPDecodeGetRequiredLength](#qpdecodegetrequiredlength)|Appelez cette fonction pour obtenir la taille en octets d'une mémoire tampon qui peut contenir des données décodées à partir d'une chaîne encodée au format Quoted-Printable (QP) de longueur spécifique.|
|[QPEncode](#qpencode)|Appelez cette fonction pour encoder des données au format Quoted-Printable (QP).|
|[QPEncodeGetRequiredLength](#qpencodegetrequiredlength)|Appelez cette fonction pour obtenir la taille en caractères d'une mémoire tampon qui peut contenir une chaîne encodée à partir des données de la taille spécifiée.|
|[UUDecode](#uudecode)|Décode une chaîne de données qui a été UUEncoded, par exemple, par un appel précédent à [uuencode](#uuencode).|
|[UUDecodeGetRequiredLength](#uudecodegetrequiredlength)|Appelez cette fonction pour obtenir la taille en octets d'une mémoire tampon qui peut contenir des données décodées à partir d'une chaîne encodée au format UUEncode de longueur spécifique.|
|[UUEncode](#uuencode)|Appelez cette fonction pour convertir des données au format UUEncode. |
|[UUEncodeGetRequiredLength](#uuencodegetrequiredlength)|Appelez cette fonction pour obtenir la taille en caractères d'une mémoire tampon qui peut contenir une chaîne encodée à partir des données de la taille spécifiée.|

## <a name="requirements"></a>Configuration requise

**En-tête :** atlenc. h

## <a name="atlgethexvalue"></a><a name="atlgethexvalue"></a> AtlGetHexValue

Appelez cette fonction pour obtenir la valeur numérique d'un chiffre hexadécimal.

```cpp
inline char AtlGetHexValue(char chIn) throw();
```

### <a name="parameters"></a>Paramètres

*Sell*<br/>
Caractère hexadécimal « 0 »-« 9 », « A'-'z-'F » ou « A'-'z-'F ».

### <a name="return-value"></a>Valeur renvoyée

Valeur numérique du caractère d’entrée interprétée comme un chiffre hexadécimal. Par exemple, une entrée de « 0 » retourne la valeur 0 et une entrée de « A » retourne la valeur 10. Si le caractère d’entrée n’est pas un chiffre hexadécimal, cette fonction retourne-1.

## <a name="atlgetversion"></a><a name="atlgetversion"></a> AtlGetVersion

Appelez cette fonction pour récupérer la version de la bibliothèque ATL que vous utilisez.

```cpp
ATLAPI_(DWORD) AtlGetVersion(void* pReserved);
```

### <a name="parameters"></a>Paramètres

*Respecté*<br/>
Pointeur réservé.

### <a name="return-value"></a>Valeur renvoyée

Retourne une valeur entière DWORD de la version de la bibliothèque ATL que vous êtes en cours de compilation ou d’exécution.

## <a name="example"></a>Exemple

La fonction doit être appelée comme suit.

[!code-cpp[NVC_ATL_Utilities#95](../../atl/codesnippet/cpp/atl-text-encoding-functions_1.cpp)]

### <a name="requirements"></a>Configuration requise

**En-tête :** atlbase. h

## <a name="atlhexdecode"></a><a name="atlhexdecode"></a> AtlHexDecode

Décode une chaîne de données qui a été encodée sous forme de texte hexadécimal, par exemple par un appel précédent à [AtlHexEncode](#atlhexencode).

```cpp
inline BOOL AtlHexDecode(
   LPCSTR pSrcData,
   int nSrcLen,
   LPBYTE pbDest,
   int* pnDestLen) throw();
```

### <a name="parameters"></a>Paramètres

*pSrcData*<br/>
Chaîne contenant les données à décoder.

*nSrcLen*<br/>
Longueur en caractères de *pSrcData*.

*pbDest*<br/>
Mémoire tampon allouée par l’appelant pour recevoir les données décodées.

*pnDestLen*<br/>
Pointeur vers une variable qui contient la longueur en octets de *pbDest*. Si la fonction a abouti, la variable reçoit le nombre d’octets écrits dans la mémoire tampon. Si la fonction échoue, la variable reçoit la longueur requise en octets de la mémoire tampon.

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur TRUE en cas de réussite, FALSe en cas d’échec.

## <a name="atlhexdecodegetrequiredlength"></a><a name="atlhexdecodegetrequiredlength"></a> AtlHexDecodeGetRequiredLength

Appelez cette fonction pour obtenir la taille en octets d'une mémoire tampon qui peut contenir des données décodées à partir d'une chaîne encodée au format hexadécimal de longueur spécifique.

```cpp
inline int AtlHexDecodeGetRequiredLength(int nSrcLen) throw();
```

### <a name="parameters"></a>Paramètres

*nSrcLen*<br/>
Nombre de caractères dans la chaîne encodée.

### <a name="return-value"></a>Valeur renvoyée

Nombre d’octets requis pour une mémoire tampon qui peut contenir une chaîne décodée de caractères *nSrcLen* .

## <a name="atlhexencode"></a><a name="atlhexencode"></a> AtlHexEncode

Appelez cette fonction pour encoder des données sous forme de chaîne hexadécimale.

```cpp
inline BOOL AtlHexEncode(
   const BYTE * pbSrcData,
   int nSrcLen,
   LPSTR szDest,
int * pnDestLen) throw();
```

### <a name="parameters"></a>Paramètres

*pbSrcData*<br/>
Mémoire tampon qui contient les données à encoder.

*nSrcLen*<br/>
Longueur, en octets, des données à encoder.

*szDest*<br/>
Mémoire tampon allouée par l’appelant pour recevoir les données encodées.

*pnDestLen*<br/>
Pointeur vers une variable qui contient la longueur en caractères de *szDest*. Si la fonction a abouti, la variable reçoit le nombre de caractères écrits dans la mémoire tampon. Si la fonction échoue, la variable reçoit la longueur requise en caractères de la mémoire tampon.

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur TRUE en cas de réussite, FALSe en cas d’échec.

### <a name="remarks"></a>Notes

Chaque octet de données sources est encodé sous la forme de 2 caractères hexadécimaux.

## <a name="atlhexencodegetrequiredlength"></a><a name="atlhexencodegetrequiredlength"></a> AtlHexEncodeGetRequiredLength

Appelez cette fonction pour obtenir la taille en caractères d'une mémoire tampon qui peut contenir une chaîne encodée à partir des données de la taille spécifiée.

```cpp
inline int AtlHexEncodeGetRequiredLength(int nSrcLen) throw();
```

### <a name="parameters"></a>Paramètres

*nSrcLen*<br/>
Nombre d’octets de données à encoder.

### <a name="return-value"></a>Valeur renvoyée

Nombre de caractères requis pour une mémoire tampon qui peut contenir des données encodées de *nSrcLen* octets.

## <a name="atlhexvalue"></a><a name="atlhexvalue"></a> AtlHexValue

Appelez cette fonction pour obtenir la valeur numérique d'un chiffre hexadécimal.

```cpp
inline short AtlHexValue(char chIn) throw();
```

### <a name="parameters"></a>Paramètres

*Sell*<br/>
Caractère hexadécimal « 0 »-« 9 », « A'-'z-'F » ou « A'-'z-'F ».

### <a name="return-value"></a>Valeur renvoyée

Valeur numérique du caractère d’entrée interprétée comme un chiffre hexadécimal. Par exemple, une entrée de « 0 » retourne la valeur 0 et une entrée de « A » retourne la valeur 10. Si le caractère d’entrée n’est pas un chiffre hexadécimal, cette fonction retourne-1.

## <a name="atlunicodetoutf8"></a><a name="atlunicodetoutf8"></a> AtlUnicodeToUTF8

Appelez cette fonction pour convertir une chaîne Unicode au format UTF-8.

```cpp
ATL_NOINLINE inline int AtlUnicodeToUTF8(
   LPCWSTR wszSrc,
   int nSrc,
   LPSTR szDest,
   int nDest) throw();
```

### <a name="parameters"></a>Paramètres

*wszSrc*<br/>
Chaîne Unicode à convertir

*nSrc*<br/>
Longueur en caractères de la chaîne Unicode.

*szDest*<br/>
Mémoire tampon allouée par l’appelant pour recevoir la chaîne convertie.

*nDest*<br/>
Longueur en octets de la mémoire tampon.

### <a name="return-value"></a>Valeur renvoyée

Retourne le nombre de caractères de la chaîne convertie.

### <a name="remarks"></a>Notes

Pour déterminer la taille de la mémoire tampon requise pour la chaîne convertie, appelez cette fonction en passant 0 pour *szDest* et *nDest*.

## <a name="bencode"></a><a name="bencode"></a> BEncode

Appelez cette fonction pour convertir certaines données à l'aide de l'encodage « B ».

```cpp
inline BOOL BEncode(
   BYTE* pbSrcData,
   int nSrcLen,
   LPSTR szDest,
   int* pnDestLen,
   LPCSTR pszCharSet) throw();
```

### <a name="parameters"></a>Paramètres

*pbSrcData*<br/>
Mémoire tampon qui contient les données à encoder.

*nSrcLen*<br/>
Longueur, en octets, des données à encoder.

*szDest*<br/>
Mémoire tampon allouée par l’appelant pour recevoir les données encodées.

*pnDestLen*<br/>
Pointeur vers une variable qui contient la longueur en caractères de *szDest*. Si la fonction a abouti, la variable reçoit le nombre de caractères écrits dans la mémoire tampon. Si la fonction échoue, la variable reçoit la longueur requise en caractères de la mémoire tampon.

*pszCharSet*<br/>
Jeu de caractères à utiliser pour la conversion.

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur TRUE en cas de réussite, FALSe en cas d’échec.

### <a name="remarks"></a>Notes

Le schéma d’encodage « B » est décrit dans le document RFC 2047 ( [https://www.ietf.org/rfc/rfc2047.txt](https://www.ietf.org/rfc/rfc2047.txt) ).

## <a name="bencodegetrequiredlength"></a><a name="bencodegetrequiredlength"></a> BEncodeGetRequiredLength

Appelez cette fonction pour obtenir la taille en caractères d'une mémoire tampon qui peut contenir une chaîne encodée à partir des données de la taille spécifiée.

```cpp
inline int BEncodeGetRequiredLength(int nSrcLen, int nCharsetLen) throw();
```

### <a name="parameters"></a>Paramètres

*nSrcLen*<br/>
Nombre d’octets de données à encoder.

*nCharsetLen*<br/>
Longueur en caractères du jeu de caractères à utiliser pour la conversion.

### <a name="return-value"></a>Valeur renvoyée

Nombre de caractères requis pour une mémoire tampon qui peut contenir des données encodées de *nSrcLen* octets.

### <a name="remarks"></a>Notes

Le schéma d’encodage « B » est décrit dans le document RFC 2047 ( [https://www.ietf.org/rfc/rfc2047.txt](https://www.ietf.org/rfc/rfc2047.txt) ).

## <a name="escapexml"></a><a name="escapexml"></a> EscapeXML

Appelez cette fonction pour convertir les caractères dont l'utilisation n'est pas sécurisée dans du code XML en leurs équivalents sécurisés.

```cpp
inline int EscapeXML(
   const wchar_t * szIn,
   int nSrcLen,
   wchar_t * szEsc,
   int nDestLen,
   DWORD dwFlags = ATL_ESC_FLAG_NONE) throw();
```

### <a name="parameters"></a>Paramètres

*szIn*<br/>
Chaîne à convertir.

*nSrclen*<br/>
Longueur en caractères de la chaîne à convertir.

*szEsc*<br/>
Mémoire tampon allouée par l’appelant pour recevoir la chaîne convertie.

*nDestLen*<br/>
Longueur en caractères de la mémoire tampon allouée par l’appelant.

*dwFlags*<br/>
ATL_ESC indicateurs décrivant la manière dont la conversion doit être effectuée.

- ATL_ESC_FLAG_NONE comportement par défaut. Les guillemets et les apostrophes ne sont pas convertis.
- ATL_ESC_FLAG_ATTR guillemets et les apostrophes sont convertis en `&quot;` et `&apos;` respectivement.

### <a name="return-value"></a>Valeur renvoyée

Longueur en caractères de la chaîne convertie.

### <a name="remarks"></a>Notes

Les conversions possibles effectuées par cette fonction sont indiquées dans le tableau :

|Source|Destination|
|------------|-----------------|
|\<|&lt;|
|>|&gt;|
|&|&amp;|
|'|&apos;|
|"|&quot;|

## <a name="getextendedchars"></a><a name="getextendedchars"></a> GetExtendedChars

Appelez cette fonction pour obtenir le nombre de caractères étendus d'une chaîne.

```cpp
inline int GetExtendedChars(LPCSTR szSrc, int nSrcLen) throw();
```

### <a name="parameters"></a>Paramètres

*szSrc*<br/>
Chaîne à analyser.

*nSrcLen*<br/>
Longueur de la chaîne en caractères.

### <a name="return-value"></a>Valeur renvoyée

Retourne le nombre de caractères étendus trouvés dans la chaîne comme déterminé par [IsExtendedChar](#isextendedchar).

## <a name="isextendedchar"></a><a name="isextendedchar"></a> IsExtendedChar

Appelez cette fonction pour déterminer si un caractère donné est un caractère étendu (inférieur à 32, supérieur à 126, et non un onglet, un saut de ligne ou un retour chariot)

```cpp
inline int IsExtendedChar(char ch) throw();
```

### <a name="parameters"></a>Paramètres

*cascade*<br/>
Caractère à tester

### <a name="return-value"></a>Valeur renvoyée

TRUE si le caractère est étendu ; sinon, FALSe.

## <a name="qencode"></a><a name="qencode"></a> QEncode

Appelez cette fonction pour convertir certaines données à l'aide de l'encodage « Q ».

```cpp
inline BOOL QEncode(
   BYTE* pbSrcData,
   int nSrcLen,
   LPSTR szDest,
   int* pnDestLen,
   LPCSTR pszCharSet,
   int* pnNumEncoded = NULL) throw();
```

### <a name="parameters"></a>Paramètres

*pbSrcData*<br/>
Mémoire tampon qui contient les données à encoder.

*nSrcLen*<br/>
Longueur, en octets, des données à encoder.

*szDest*<br/>
Mémoire tampon allouée par l’appelant pour recevoir les données encodées.

*pnDestLen*<br/>
Pointeur vers une variable qui contient la longueur en caractères de *szDest*. Si la fonction a abouti, la variable reçoit le nombre de caractères écrits dans la mémoire tampon. Si la fonction échoue, la variable reçoit la longueur requise en caractères de la mémoire tampon.

*pszCharSet*<br/>
Jeu de caractères à utiliser pour la conversion.

*pnNumEncoded*<br/>
Pointeur vers une variable qui, en retour, contient le nombre de caractères non sécurisés qui devaient être convertis.

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur TRUE en cas de réussite, FALSe en cas d’échec.

### <a name="remarks"></a>Notes

Le schéma d’encodage « Q » est décrit dans le document RFC 2047 ( [https://www.ietf.org/rfc/rfc2047.txt](https://www.ietf.org/rfc/rfc2047.txt) ).

## <a name="qencodegetrequiredlength"></a><a name="qencodegetrequiredlength"></a> QEncodeGetRequiredLength

Appelez cette fonction pour obtenir la taille en caractères d'une mémoire tampon qui peut contenir une chaîne encodée à partir des données de la taille spécifiée.

```cpp
inline int QEncodeGetRequiredLength(int nSrcLen, int nCharsetLen) throw();
```

### <a name="parameters"></a>Paramètres

*nSrcLen*<br/>
Nombre d’octets de données à encoder.

*nCharsetLen*<br/>
Longueur en caractères du jeu de caractères à utiliser pour la conversion.

### <a name="return-value"></a>Valeur renvoyée

Nombre de caractères requis pour une mémoire tampon qui peut contenir des données encodées de *nSrcLen* octets.

### <a name="remarks"></a>Notes

Le schéma d’encodage « Q » est décrit dans le document RFC 2047 ( [https://www.ietf.org/rfc/rfc2047.txt](https://www.ietf.org/rfc/rfc2047.txt) ).

## <a name="qpdecode"></a><a name="qpdecode"></a> QPDecode

Décode une chaîne de données qui a été encodée au format Quoted-Printable, par exemple par un appel précédent à [QPEncode](#qpencode).

```cpp
inline BOOL QPDecode(
   BYTE* pbSrcData,
   int nSrcLen,
   LPSTR szDest,
   int* pnDestLen,
   DWORD dwFlags = 0) throw();
```

### <a name="parameters"></a>Paramètres

*pbSrcData*<br/>
dans Mémoire tampon qui contient les données à décoder.

*nSrcLen*<br/>
dans Longueur en octets de *pbSrcData*.

*szDest*<br/>
à Mémoire tampon allouée par l’appelant pour recevoir les données décodées.

*pnDestLen*<br/>
à Pointeur vers une variable qui contient la longueur en octets de *szDest*. Si la fonction a abouti, la variable reçoit le nombre d’octets écrits dans la mémoire tampon. Si la fonction échoue, la variable reçoit la longueur requise en octets de la mémoire tampon.

*dwFlags*<br/>
dans ATLSMTP_QPENCODE indicateurs décrivant la manière dont la conversion doit être effectuée.

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur TRUE en cas de réussite, FALSe en cas d’échec.

### <a name="remarks"></a>Notes

Le schéma d’encodage entre guillemets est décrit dans le document RFC 2045 ( [https://www.ietf.org/rfc/rfc2045.txt](https://www.ietf.org/rfc/rfc2045.txt) ).

## <a name="qpdecodegetrequiredlength"></a><a name="qpdecodegetrequiredlength"></a> QPDecodeGetRequiredLength

Appelez cette fonction pour obtenir la taille en octets d'une mémoire tampon qui peut contenir des données décodées à partir d'une chaîne encodée au format Quoted-Printable (QP) de longueur spécifique.

```cpp
inline int QPDecodeGetRequiredLength(int nSrcLen) throw();
```

### <a name="parameters"></a>Paramètres

*nSrcLen*<br/>
Nombre de caractères dans la chaîne encodée.

### <a name="return-value"></a>Valeur renvoyée

Nombre d’octets requis pour une mémoire tampon qui peut contenir une chaîne décodée de caractères *nSrcLen* .

### <a name="remarks"></a>Notes

Le schéma d’encodage entre guillemets est décrit dans le document RFC 2045 ( [https://www.ietf.org/rfc/rfc2045.txt](https://www.ietf.org/rfc/rfc2045.txt) ).

## <a name="qpencode"></a><a name="qpencode"></a> QPEncode

Appelez cette fonction pour encoder des données au format Quoted-Printable (QP).

```cpp
inline BOOL QPEncode(
   BYTE* pbSrcData,
   int nSrcLen,
   LPSTR szDest,
   int* pnDestLen,
   DWORD dwFlags = 0) throw ();
```

### <a name="parameters"></a>Paramètres

*pbSrcData*<br/>
Mémoire tampon qui contient les données à encoder.

*nSrcLen*<br/>
Longueur, en octets, des données à encoder.

*szDest*<br/>
Mémoire tampon allouée par l’appelant pour recevoir les données encodées.

*pnDestLen*<br/>
Pointeur vers une variable qui contient la longueur en caractères de *szDest*. Si la fonction a abouti, la variable reçoit le nombre de caractères écrits dans la mémoire tampon. Si la fonction échoue, la variable reçoit la longueur requise en caractères de la mémoire tampon.

*dwFlags*<br/>
ATLSMTP_QPENCODE indicateurs décrivant la manière dont la conversion doit être effectuée.

- ATLSMTP_QPENCODE_DOT si un point apparaît au début d’une ligne, il est ajouté à la sortie et encodé.

- ATLSMTP_QPENCODE_TRAILING_SOFT ajoute `=\r\n` à la chaîne encodée.

Le schéma d’encodage entre guillemets est décrit dans le [document RFC 2045](https://www.ietf.org/rfc/rfc2045.txt).

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur TRUE en cas de réussite, FALSe en cas d’échec.

### <a name="remarks"></a>Notes

Le schéma d’encodage entre guillemets est décrit dans le document RFC 2045 ( [https://www.ietf.org/rfc/rfc2045.txt](https://www.ietf.org/rfc/rfc2045.txt) ).

## <a name="qpencodegetrequiredlength"></a><a name="qpencodegetrequiredlength"></a> QPEncodeGetRequiredLength

Appelez cette fonction pour obtenir la taille en caractères d'une mémoire tampon qui peut contenir une chaîne encodée à partir des données de la taille spécifiée.

```cpp
inline int QPEncodeGetRequiredLength(int nSrcLen) throw ();
```

### <a name="parameters"></a>Paramètres

*nSrcLen*<br/>
Nombre d’octets de données à encoder.

### <a name="return-value"></a>Valeur renvoyée

Nombre de caractères requis pour une mémoire tampon qui peut contenir des données encodées de *nSrcLen* octets.

### <a name="remarks"></a>Notes

Le schéma d’encodage entre guillemets est décrit dans le document RFC 2045 ( [https://www.ietf.org/rfc/rfc2045.txt](https://www.ietf.org/rfc/rfc2045.txt) ).

## <a name="uudecode"></a><a name="uudecode"></a> UUDecode

Décode une chaîne de données qui a été UUEncoded, par exemple, par un appel précédent à [uuencode](#uuencode).

```cpp
inline BOOL UUDecode(
   BYTE* pbSrcData,
   int nSrcLen,
   BYTE* pbDest,
   int* pnDestLen) throw ();
```

### <a name="parameters"></a>Paramètres

*pbSrcData*<br/>
Chaîne contenant les données à décoder.

*nSrcLen*<br/>
Longueur en octets de *pbSrcData*.

*pbDest*<br/>
Mémoire tampon allouée par l’appelant pour recevoir les données décodées.

*pnDestLen*<br/>
Pointeur vers une variable qui contient la longueur en octets de *pbDest*. Si la fonction a abouti, la variable reçoit le nombre d’octets écrits dans la mémoire tampon. Si la fonction échoue, la variable reçoit la longueur requise en octets de la mémoire tampon.

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur TRUE en cas de réussite, FALSe en cas d’échec.

### <a name="remarks"></a>Notes

Cette implémentation de UUEncoding suit la spécification POSIX P version 1003.2 b/D11.

## <a name="uudecodegetrequiredlength"></a><a name="uudecodegetrequiredlength"></a> UUDecodeGetRequiredLength

Appelez cette fonction pour obtenir la taille en octets d'une mémoire tampon qui peut contenir des données décodées à partir d'une chaîne encodée au format UUEncode de longueur spécifique.

```cpp
inline int UUDecodeGetRequiredLength(int nSrcLen) throw ();
```

### <a name="parameters"></a>Paramètres

*nSrcLen*<br/>
Nombre de caractères dans la chaîne encodée.

### <a name="return-value"></a>Valeur renvoyée

Nombre d’octets requis pour une mémoire tampon qui peut contenir une chaîne décodée de caractères *nSrcLen* .

### <a name="remarks"></a>Notes

Cette implémentation de UUEncoding suit la spécification POSIX P version 1003.2 b/D11.

## <a name="uuencode"></a><a name="uuencode"></a> UUEncode

Appelez cette fonction pour convertir des données au format UUEncode.

```cpp
inline BOOL UUEncode(
   const BYTE* pbSrcData,
   int nSrcLen,
   LPSTR szDest,
   int* pnDestLen,
   LPCTSTR lpszFile = _T("file"),
   DWORD dwFlags = 0) throw ();
```

### <a name="parameters"></a>Paramètres

*pbSrcData*<br/>
Mémoire tampon qui contient les données à encoder.

*nSrcLen*<br/>
Longueur, en octets, des données à encoder.

*szDest*<br/>
Mémoire tampon allouée par l’appelant pour recevoir les données encodées.

*pnDestLen*<br/>
Pointeur vers une variable qui contient la longueur en caractères de *szDest*. Si la fonction a abouti, la variable reçoit le nombre de caractères écrits dans la mémoire tampon. Si la fonction échoue, la variable reçoit la longueur requise en caractères de la mémoire tampon.

*lpszFile*<br/>
Fichier à ajouter à l’en-tête lorsque ATLSMTP_UUENCODE_HEADER est spécifié dans *dwFlags*.

*dwFlags*<br/>
Indicateurs contrôlant le comportement de cette fonction.

- ATLSMTP_UUENCODE_HEADE l’en-tête sera encodé.

- ATLSMTP_UUENCODE_END la fin sera encodée.

- ATLSMTP_UUENCODE_DOT les données sont effectuées.

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur TRUE en cas de réussite, FALSe en cas d’échec.

### <a name="remarks"></a>Notes

Cette implémentation de UUEncoding suit la spécification POSIX P version 1003.2 b/D11.

## <a name="uuencodegetrequiredlength"></a><a name="uuencodegetrequiredlength"></a> UUEncodeGetRequiredLength

Appelez cette fonction pour obtenir la taille en caractères d'une mémoire tampon qui peut contenir une chaîne encodée à partir des données de la taille spécifiée.

```cpp
inline int UUEncodeGetRequiredLength(int nSrcLen) throw ();
```

### <a name="parameters"></a>Paramètres

*nSrcLen*<br/>
Nombre d’octets de données à encoder.

### <a name="return-value"></a>Valeur renvoyée

Nombre de caractères requis pour une mémoire tampon qui peut contenir des données encodées de *nSrcLen* octets.

### <a name="remarks"></a>Notes

Cette implémentation de UUEncoding suit la spécification POSIX P version 1003.2 b/D11.

## <a name="see-also"></a>Voir aussi

[Concepts](../active-template-library-atl-concepts.md)<br/>
[Composants de bureau COM ATL](../atl-com-desktop-components.md)
