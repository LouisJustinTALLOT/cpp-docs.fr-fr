---
title: Constantes de type paramètre variant
ms.date: 11/04/2016
f1_keywords:
- VTS_YPOS_HIMETRIC
- VTS_PICTURE
- VTS_FONT
- VTS_XPOS_HIMETRIC
- VTS_XPOS_PIXELS
- VTS_XSIZE_HIMETRIC
- VTS_YPOS_PIXELS
- VTS_TRISTATE
- VTS_HANDLE
- VTS_YSIZE_HIMETRIC
- VTS_COLOR
- VTS_OPTEXCLUSIVE
- VTS_YSIZE_PIXELS
- VTS_XSIZE_PIXELS
helpviewer_keywords:
- VTS_XPOS_HIMETRIC constant [MFC]
- VTS_FONT constant [MFC]
- VTS_XPOS_PIXELS constant [MFC]
- VTS_COLOR constant [MFC]
- Variants [MFC]
- VTS_YPOS_PIXELS constant [MFC]
- VTS_YSIZE_HIMETRIC constant [MFC]
- VTS_YPOS_HIMETRIC constant [MFC]
- Variants, parameter type constants
- Variant data constants [MFC]
- VTS_PICTURE constant [MFC]
- VTS_TRISTATE constant [MFC]
- VTS_XSIZE_HIMETRIC constant [MFC]
- VTS_HANDLE constant [MFC]
- VTS_XSIZE_PIXELS constant [MFC]
- VTS_OPTEXCLUSIVE constant [MFC]
- VTS_YSIZE_PIXELS constant [MFC]
ms.assetid: de99c7a9-7aae-4dc4-b723-40c6380543ab
ms.openlocfilehash: f73c72830216679f8a91d0037d48c1e1b8e400c3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372867"
---
# <a name="variant-parameter-type-constants"></a>Constantes de type paramètre variant

Ce sujet répertorie les nouvelles constantes qui indiquent les types de paramètres variantes conçus pour une utilisation avec les classes de contrôle OLE de la Bibliothèque de classe Microsoft Foundation.

Voici une liste de constantes de classe :

## <a name="variant-data-constants"></a><a name="_mfc_variant_data_constants"></a>Variant Data Constants

- VTS_COLOR un intégrier 32 bits représentait une valeur de couleur RGB.

- VTS_FONT Un pointeur `IFontDisp` à l’interface d’un objet de police OLE.

- VTS_HANDLE une valeur de poignée Windows.

- VTS_PICTURE Un pointeur à `IPictureDisp` l’interface d’un objet d’image OLE.

- VTS_OPTEXCLUSIVE Une valeur 16 bits utilisée pour un contrôle qui est destiné à être utilisé dans un groupe de contrôles, tels que les boutons radio. Ce type indique au conteneur que si un contrôle d’un groupe a une valeur TRUE, tous les autres doivent être FALSE.

- VTS_TRISTATE Un intégré signé 16 bits utilisé pour les propriétés qui peuvent avoir l’une des trois valeurs possibles (sélectionné, effacé, indisponible), par exemple, une case à cocher.

- VTS_XPOS_HIMETRIC Un integer non signé 32 bits représentait autrefois une position le long de l’axe x dans les unités HIMETRIC.

- VTS_YPOS_HIMETRIC Un integer non signé 32 bits représentait autrefois une position le long de l’axe y dans les unités HIMETRIC.

- VTS_XPOS_PIXELS Un integer non signé 32 bits représentait autrefois une position le long de l’axe x en pixels.

- VTS_YPOS_PIXELS Un integer non signé 32 bits représentait autrefois une position le long de l’axe y en pixels.

- VTS_XSIZE_PIXELS Un integer non signé 32 bits représentait la largeur d’un objet d’écran en pixels.

- VTS_YSIZE_PIXELS Un integer non signé 32 bits représentait la hauteur d’un objet d’écran en pixels.

- VTS_XSIZE_HIMETRIC Un integer non signé 32 bits représentait la largeur d’un objet d’écran dans les unités HIMETRIC.

- VTS_YSIZE_HIMETRIC Un integer non signé 32 bits représentait la hauteur d’un objet d’écran dans les unités HIMETRIC.

    > [!NOTE]
    >  D’autres constantes de variantes ont été définies pour tous les types de variantes, à l’exception de VTS_FONT et VTS_PICTURE, qui fournissent un pointeur à la constante de données de variante. Ces constantes sont nommées à`constantname` l’aide de la convention VTS_P. Par exemple, VTS_PCOLOR est un pointeur à une constante VTS_COLOR.

## <a name="requirements"></a>Spécifications

**En-tête :** afxdisp.h

## <a name="see-also"></a>Voir aussi

[Macros et objet Globals](../../mfc/reference/mfc-macros-and-globals.md)
