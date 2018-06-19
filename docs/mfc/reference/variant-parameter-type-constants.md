---
title: Constantes de Type paramètre Variant | Documents Microsoft
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
ms.openlocfilehash: 13820ff4fb07c3743f36ba3ebe33ee56a3a79c7d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33379858"
---
# <a name="variant-parameter-type-constants"></a>Constantes de type paramètre variant
Cette rubrique répertorie les nouvelles constantes qui indiquent les types de paramètre variant conçus pour une utilisation avec les classes de contrôle OLE de la bibliothèque Microsoft Foundation Class.  
  
 Voici une liste de constantes de la classe :  
  
##  <a name="_mfc_variant_data_constants"></a> Constantes de données Variant  
  
-   **VTS_COLOR** entier de 32 bits permet de représenter une valeur de couleur RVB.  
  
-   **VTS_FONT** un pointeur vers le **IFontDisp** interface d’un objet de police OLE.  
  
-   **VTS_HANDLE** Windows d’un descripteur de valeur.  
  
-   **VTS_PICTURE** un pointeur vers le `IPictureDisp` interface d’un objet d’image OLE.  
  
-   **VTS_OPTEXCLUSIVE** valeur de 16 bits utilisé pour un contrôle qui est destiné à être utilisée dans un groupe de contrôles, tels que des cases d’option. Ce type indique au conteneur que si un contrôle dans un groupe a un **TRUE** valeur, tous les autres doivent être **FALSE**.  
  
-   **VTS_TRISTATE** les entier signé de 16 bits utilisé pour les propriétés qui peuvent avoir l’une des trois valeurs possibles (sélectionnés, désactivées, non disponibles), par exemple, une case à cocher.  
  
-   **VTS_XPOS_HIMETRIC** entier non signé de 32 bits permet de représenter une position le long de l’axe des abscisses dans **HIMETRIC** unités.  
  
-   **VTS_YPOS_HIMETRIC** entier non signé de 32 bits permet de représenter une position le long de l’axe des ordonnées dans **HIMETRIC** unités.  
  
-   **VTS_XPOS_PIXELS** entier non signé de 32 bits permet de représenter une position sur l’axe x en pixels.  
  
-   **VTS_YPOS_PIXELS** entier non signé de 32 bits permet de représenter une position le long de l’axe des y, en pixels.  
  
-   **VTS_XSIZE_PIXELS** entier non signé de 32 bits permet de représenter la largeur d’un objet de l’écran en pixels.  
  
-   **VTS_YSIZE_PIXELS** entier non signé de 32 bits permet de représenter la hauteur d’un objet de l’écran en pixels.  
  
-   **VTS_XSIZE_HIMETRIC** entier non signé de 32 bits permet de représenter la largeur d’un objet d’écran dans **HIMETRIC** unités.  
  
-   **VTS_YSIZE_HIMETRIC** entier non signé de 32 bits permet de représenter la hauteur d’un objet d’écran dans **HIMETRIC** unités.  
  
    > [!NOTE]
    >  Les constantes de type variant supplémentaires ont été définis pour tous les types variants, à l’exception de **VTS_FONT** et **VTS_PICTURE**, qui fournissent un pointeur vers la quantité de données variant co nstante. Ces constantes sont nommées à l’aide de la **VTS_P** `constantname` convention. Par exemple, **VTS_PCOLOR** est un pointeur vers un **VTS_COLOR** constante.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** afxdisp.h  
  
## <a name="see-also"></a>Voir aussi  
 [Macros et objet Globals](../../mfc/reference/mfc-macros-and-globals.md)
