---
title: "ATL, référence d’encodage | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- encoding
- encoding, functions
ms.assetid: 82d4fdf3-3c4a-4fe2-b297-8ffb4714406f
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: cd0f4b448de3fcaabe33822c0d8b1ee834260609
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2017
---
# <a name="atl-encoding-reference"></a>Référence d'encodage ATL
Encodage dans une plage de normes Internet communes telles qu’uuencode, hexadécimal et UTF-8 est pris en charge par le code trouvé dans atlenc.h.  
  
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
|[QPDecode](reference/atl-text-encoding-functions.md#qpdecode)|Décode une chaîne de données qui a été encodées au format quoted-printable, notamment par un appel précédent à [QPEncode](reference/atl-text-encoding-functions.md#qpencode).|  
|[QPDecodeGetRequiredLength](reference/atl-text-encoding-functions.md#qpdecodegetrequiredlength)|Appelez cette fonction pour obtenir la taille en octets d'une mémoire tampon qui peut contenir des données décodées à partir d'une chaîne encodée au format Quoted-Printable (QP) de longueur spécifique.|  
|[QPEncode](reference/atl-text-encoding-functions.md#qpencode)|Appelez cette fonction pour encoder des données au format Quoted-Printable (QP).|  
|[QPEncodeGetRequiredLength](reference/atl-text-encoding-functions.md#qpencodegetrequiredlength)|Appelez cette fonction pour obtenir la taille en caractères d'une mémoire tampon qui peut contenir une chaîne encodée à partir des données de la taille spécifiée.|  
|[UUDecode](reference/atl-text-encoding-functions.md#uudecode)|Décode une chaîne de données qui a été convertie au format UUENCODE tels que par un appel précédent à [UUEncode](reference/atl-text-encoding-functions.md#uuencode).|  
|[UUDecodeGetRequiredLength](reference/atl-text-encoding-functions.md#uudecodegetrequiredlength)|Appelez cette fonction pour obtenir la taille en octets d'une mémoire tampon qui peut contenir des données décodées à partir d'une chaîne encodée au format UUEncode de longueur spécifique.|  
|[UUEncode](reference/atl-text-encoding-functions.md#uuencode)|Appelez cette fonction pour convertir des données au format UUEncode.|  
|[UUEncodeGetRequiredLength](reference/atl-text-encoding-functions.md#uuencodegetrequiredlength)|Appelez cette fonction pour obtenir la taille en caractères d'une mémoire tampon qui peut contenir une chaîne encodée à partir des données de la taille spécifiée.|  
  
## <a name="see-also"></a>Voir aussi  
 [Concepts](../atl/active-template-library-atl-concepts.md)   
 [Composants de bureau COM ATL](../atl/atl-com-desktop-components.md)

