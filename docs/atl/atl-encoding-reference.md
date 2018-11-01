---
title: Référence d'encodage ATL
ms.date: 11/04/2016
helpviewer_keywords:
- encoding
- encoding, functions
ms.assetid: 82d4fdf3-3c4a-4fe2-b297-8ffb4714406f
ms.openlocfilehash: f23c6ee3354521d0edbd2772f9a2fdf3ec6a184c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50492714"
---
# <a name="atl-encoding-reference"></a>Référence d'encodage ATL

Encodage dans une plage de normes Internet communes telles qu’uuencode, hexadécimal et UTF-8 est pris en charge par le code figurant dans atlenc.h ainsi que.

### <a name="functions"></a>Fonctions

|||
|-|-|
|[AtlGetHexValue](reference/atl-text-encoding-functions.md#atlgethexvalue)|Appelez cette fonction pour obtenir la valeur numérique d'un chiffre hexadécimal.|
|[AtlHexDecode](reference/atl-text-encoding-functions.md#atlhexdecode)|Décode une chaîne de données qui a été encodées sous forme de texte hexadécimal, notamment par un appel précédent à [AtlHexEncode](reference/atl-text-encoding-functions.md#atlhexencode).|
|[AtlHexDecodeGetRequiredLength](reference/atl-text-encoding-functions.md#atlhexdecodegetrequiredlength)|Appelez cette fonction pour obtenir la taille en octets d'une mémoire tampon qui peut contenir des données décodées à partir d'une chaîne encodée au format hexadécimal de longueur spécifique.|
|[AtlHexEncode](reference/atl-text-encoding-functions.md#atlhexencode)|Appelez cette fonction pour encoder des données sous forme de chaîne hexadécimale.|
|[AtlHexEncodeGetRequiredLength](reference/atl-text-encoding-functions.md#atlhexencodegetrequiredlength)|Appelez cette fonction pour obtenir la taille en caractères d'une mémoire tampon qui peut contenir une chaîne encodée à partir des données de la taille spécifiée.|
|[AtlUnicodeToUTF8](reference/atl-text-encoding-functions.md#atlunicodetoutf8)|Appelez cette fonction pour convertir une chaîne Unicode au format UTF-8.|
|[BEncode](reference/atl-text-encoding-functions.md#bencode)|Appelez cette fonction pour convertir certaines données à l'aide de l'encodage « B ».|
|[BEncodeGetRequiredLength](reference/atl-text-encoding-functions.md#bencodegetrequiredlength)|Appelez cette fonction pour obtenir la taille en caractères d'une mémoire tampon qui peut contenir une chaîne encodée à partir des données de la taille spécifiée.|
|[EscapeXML](reference/atl-text-encoding-functions.md#escapexml)|Appelez cette fonction pour convertir les caractères dont l'utilisation n'est pas sécurisée dans du code XML en leurs équivalents sécurisés.|
|[GetExtendedChars](reference/atl-text-encoding-functions.md#getextendedchars)|Appelez cette fonction pour obtenir le nombre de caractères étendus d'une chaîne.|
|[IsExtendedChar](reference/atl-text-encoding-functions.md#isextendedchar)|Appelez cette fonction pour déterminer si un caractère donné est un caractère étendu (inférieur à 32, supérieur à 126 et qui n'est pas une tabulation, un saut de ligne ou un retour chariot)|
|[QEncode](reference/atl-text-encoding-functions.md#qencode)|Appelez cette fonction pour convertir certaines données à l'aide de l'encodage « Q ».|
|[QEncodeGetRequiredLength](reference/atl-text-encoding-functions.md#qencodegetrequiredlength)|Appelez cette fonction pour obtenir la taille en caractères d'une mémoire tampon qui peut contenir une chaîne encodée à partir des données de la taille spécifiée.|
|[QPDecode](reference/atl-text-encoding-functions.md#qpdecode)|Décode une chaîne de données qui a été encodées au format quoted-printable tels que par un appel précédent à [QPEncode](reference/atl-text-encoding-functions.md#qpencode).|
|[QPDecodeGetRequiredLength](reference/atl-text-encoding-functions.md#qpdecodegetrequiredlength)|Appelez cette fonction pour obtenir la taille en octets d'une mémoire tampon qui peut contenir des données décodées à partir d'une chaîne encodée au format Quoted-Printable (QP) de longueur spécifique.|
|[QPEncode](reference/atl-text-encoding-functions.md#qpencode)|Appelez cette fonction pour encoder des données au format Quoted-Printable (QP).|
|[QPEncodeGetRequiredLength](reference/atl-text-encoding-functions.md#qpencodegetrequiredlength)|Appelez cette fonction pour obtenir la taille en caractères d'une mémoire tampon qui peut contenir une chaîne encodée à partir des données de la taille spécifiée.|
|[UUDecode](reference/atl-text-encoding-functions.md#uudecode)|Décode une chaîne de données qui a été convertie au format UUENCODE tels que par un appel précédent à [UUEncode](reference/atl-text-encoding-functions.md#uuencode).|
|[UUDecodeGetRequiredLength](reference/atl-text-encoding-functions.md#uudecodegetrequiredlength)|Appelez cette fonction pour obtenir la taille en octets d'une mémoire tampon qui peut contenir des données décodées à partir d'une chaîne encodée au format UUEncode de longueur spécifique.|
|[UUEncode](reference/atl-text-encoding-functions.md#uuencode)|Appelez cette fonction pour convertir des données au format UUEncode.|
|[UUEncodeGetRequiredLength](reference/atl-text-encoding-functions.md#uuencodegetrequiredlength)|Appelez cette fonction pour obtenir la taille en caractères d'une mémoire tampon qui peut contenir une chaîne encodée à partir des données de la taille spécifiée.|

## <a name="see-also"></a>Voir aussi

[Concepts](../atl/active-template-library-atl-concepts.md)<br/>
[Composants de bureau COM ATL](../atl/atl-com-desktop-components.md)

