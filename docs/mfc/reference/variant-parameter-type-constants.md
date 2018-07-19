---
title: Constantes de Type paramètre Variant | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d61930bda4560baaf628ce018cc0161527d9d07e
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2018
ms.locfileid: "37885947"
---
# <a name="variant-parameter-type-constants"></a>Constantes de type paramètre variant
Cette rubrique répertorie les nouvelles constantes qui indiquent les types de paramètre variant conçus pour une utilisation avec les classes de contrôle OLE de la bibliothèque Microsoft Foundation Class.  
  
 Voici une liste de constantes de la classe :  
  
##  <a name="_mfc_variant_data_constants"></a> Constantes de données Variant  
  
-   Entier de 32 bits VTS_COLOR utilisé pour représenter une valeur de couleur RVB.  
  
-   Pointeur d’un VTS_FONT vers le `IFontDisp` interface d’un objet de police OLE.  
  
-   Valeur du handle Windows d’un VTS_HANDLE.  
  
-   Pointeur d’un VTS_PICTURE vers le `IPictureDisp` interface d’un objet d’image OLE.  
  
-   Valeur de 16 bits VTS_OPTEXCLUSIVE utilisée pour un contrôle qui est destiné à être utilisée dans un groupe de contrôles, tels que les cases. Ce type indique au conteneur que si un contrôle dans un groupe a la valeur TRUE, tous les autres doivent être FALSE.  
  
-   VTS_TRISTATE 16 bits signé entier utilisé pour les propriétés qui peuvent avoir une des trois valeurs possibles (sélectionnés, effacés, indisponibles), par exemple, une case à cocher.  
  
-   VTS_XPOS_HIMETRIC un entier 32 bits non signé utilisé pour représenter une position le long de l’axe des x en unités HIMETRIC.  
  
-   VTS_YPOS_HIMETRIC un entier 32 bits non signé utilisé pour représenter une position le long de l’axe des ordonnées en unités HIMETRIC.  
  
-   VTS_XPOS_PIXELS un entier 32 bits non signé utilisé pour représenter une position le long de l’axe des x en pixels.  
  
-   VTS_YPOS_PIXELS un entier 32 bits non signé utilisé pour représenter une position le long de l’axe des y en pixels.  
  
-   VTS_XSIZE_PIXELS un entier 32 bits non signé utilisé pour représenter la largeur d’un objet de l’écran en pixels.  
  
-   VTS_YSIZE_PIXELS un entier 32 bits non signé utilisé pour représenter la hauteur d’un objet de l’écran en pixels.  
  
-   VTS_XSIZE_HIMETRIC un entier 32 bits non signé utilisé pour représenter la largeur d’un objet de l’écran en unités HIMETRIC.  
  
-   VTS_YSIZE_HIMETRIC un entier 32 bits non signé utilisé pour représenter la hauteur d’un objet de l’écran en unités HIMETRIC.  
  
    > [!NOTE]
    >  Les constantes de type variants supplémentaires ont été définis pour tous les types variants, à l’exception VTS_FONT et VTS_PICTURE, qui fournissent un pointeur vers la constante de données variant. Ces constantes sont nommés à l’aide de la VTS_P`constantname` convention. Par exemple, VTS_PCOLOR est un pointeur vers un VTS_COLOR (constante).  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** afxdisp.h  
  
## <a name="see-also"></a>Voir aussi  
 [Macros et objet Globals](../../mfc/reference/mfc-macros-and-globals.md)
