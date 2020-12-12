---
description: En savoir plus sur les constantes de type de paramètre variant
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
ms.openlocfilehash: 5bc3dcc8a0a888b21b88700db99b05c0f12a4c5e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97218496"
---
# <a name="variant-parameter-type-constants"></a>Constantes de type paramètre variant

Cette rubrique répertorie les nouvelles constantes qui indiquent les types de paramètres variant conçus pour être utilisés avec les classes de contrôle OLE de l’bibliothèque MFC (Microsoft Foundation Class).

La liste suivante répertorie les constantes de classe :

## <a name="variant-data-constants"></a><a name="_mfc_variant_data_constants"></a> Constantes de données variant

- VTS_COLOR un entier 32 bits utilisé pour représenter une valeur de couleur RVB.

- VTS_FONT un pointeur vers l' `IFontDisp` interface d’un objet OLE font.

- VTS_HANDLE une valeur de handle Windows.

- VTS_PICTURE un pointeur vers l' `IPictureDisp` interface d’un objet image OLE.

- VTS_OPTEXCLUSIVE une valeur de 16 bits utilisée pour un contrôle destiné à être utilisé dans un groupe de contrôles, tels que les cases d’option. Ce type indique au conteneur que si un contrôle dans un groupe a une valeur TRUE, tous les autres doivent avoir la valeur FALSe.

- VTS_TRISTATE un entier 16 bits signé utilisé pour les propriétés qui peuvent avoir l’une des trois valeurs possibles (sélectionnée, désactivée, non disponible), par exemple, une case à cocher.

- VTS_XPOS_HIMETRIC un entier non signé 32 bits utilisé pour représenter une position le long de l’axe x en unités HIMETRIC.

- VTS_YPOS_HIMETRIC un entier non signé 32 bits utilisé pour représenter une position le long de l’axe y en unités HIMETRIC.

- VTS_XPOS_PIXELS un entier non signé 32 bits utilisé pour représenter une position le long de l’axe x en pixels.

- VTS_YPOS_PIXELS un entier non signé 32 bits utilisé pour représenter une position le long de l’axe y en pixels.

- VTS_XSIZE_PIXELS un entier non signé 32 bits utilisé pour représenter la largeur d’un objet Screen en pixels.

- VTS_YSIZE_PIXELS un entier non signé 32 bits utilisé pour représenter la hauteur d’un objet Screen en pixels.

- VTS_XSIZE_HIMETRIC un entier non signé 32 bits utilisé pour représenter la largeur d’un objet Screen en unités HIMETRIC.

- VTS_YSIZE_HIMETRIC un entier non signé 32 bits utilisé pour représenter la hauteur d’un objet Screen en unités HIMETRIC.

    > [!NOTE]
    >  Des constantes variant supplémentaires ont été définies pour tous les types variant, à l’exception de VTS_FONT et VTS_PICTURE, qui fournissent un pointeur vers la constante de données Variant. Ces constantes sont nommées à l’aide de la Convention de VTS_P `constantname` . Par exemple, VTS_PCOLOR est un pointeur vers une constante VTS_COLOR.

## <a name="requirements"></a>Spécifications

**En-tête :** afxdisp.h

## <a name="see-also"></a>Voir aussi

[Macros et objet Globals](../../mfc/reference/mfc-macros-and-globals.md)
