---
title: Coloradjustment, Structure | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- COLORADJUSTMENT
dev_langs:
- C++
helpviewer_keywords:
- COLORADJUSTMENT structure [MFC]
ms.assetid: 67fc4e63-0e0e-4fcb-8c45-aa5ebfefa013
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 03c5346a59ea52ca6b2428652d5da69aacf6ea5b
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/05/2018
ms.locfileid: "37849087"
---
# <a name="coloradjustment-structure"></a>COLORADJUSTMENT, structure
Le `COLORADJUSTMENT` structure définit les valeurs d’ajustement de couleur utilisés par le Windows `StretchBlt` et `StretchDIBits` fonctions lors de la `StretchBlt` mode est demi-teintes.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef struct  tagCOLORADJUSTMENT {    /* ca */  
    WORD caSize;  
    WORD caFlags;  
    WORD caIlluminantIndex;  
    WORD caRedGamma;  
    WORD caGreenGamma;  
    WORD caBlueGamma;  
    WORD caReferenceBlack;  
    WORD caReferenceWhite;  
    SHORT caContrast;  
    SHORT caBrightness;  
    SHORT caColorfulness;  
    SHORT caRedGreenTint;  
} COLORADJUSTMENT;  
```  
  
#### <a name="parameters"></a>Paramètres  
 *caSize*  
 Spécifie la taille de la structure en octets.  
  
 *caFlags*  
 Spécifie comment l’image de sortie doit être préparé. Ce membre peut être défini sur NULL ou n’importe quelle combinaison des valeurs suivantes :  
  
- CA_NEGATIVE indique que la valeur négative de l’image d’origine doit être affichée.  
  
- CA_LOG_FILTER Spécifie que la fonction logarithmique doit être appliquée à la densité finale des couleurs de sortie. Cela augmentera le contraste des couleurs lorsque la luminance est faible.  
  
 *caIlluminantIndex*  
 Spécifie la luminance de la source de lumière sous lequel l’objet de l’image est affiché. Ce membre peut être défini à une des valeurs suivantes :  
  
- ILLUMINANT_EQUAL_ENERGY  
  
- ILLUMINANT_A  
  
- ILLUMINANT_B  
  
- ILLUMINANT_C  
  
- ILLUMINANT_D50  
  
- ILLUMINANT_D55  
  
- ILLUMINANT_D65  
  
- ILLUMINANT_D75  
  
- ILLUMINANT_F2  
  
- ILLUMINANT_TURNGSTEN  
  
- ILLUMINANT_DAYLIGHT  
  
- ILLUMINANT_FLUORESCENT  
  
- ILLUMINANT_NTSC  
  
 *caRedGamma*  
 Spécifie la valeur de correction gamma de puissance n pour le serveur principal rouge des couleurs source. La valeur doit être dans la plage de 2 500 à 65,000. Une valeur de 10 000 ne signifie aucune correction gamma.  
  
 *caGreenGamma*  
 Spécifie la valeur de correction gamma de puissance n pour le serveur principal vert des couleurs source. La valeur doit être dans la plage de 2 500 à 65,000. Une valeur de 10 000 ne signifie aucune correction gamma.  
  
 *caBlueGamma*  
 Spécifie la valeur de correction gamma de puissance n pour bleu primaire des couleurs source. La valeur doit être dans la plage de 2 500 à 65,000. Une valeur de 10 000 ne signifie aucune correction gamma.  
  
 *caReferenceBlack*  
 Spécifie la référence noir pour les couleurs de la source. Les couleurs qui sont plus foncés que ce sont traités en noir. La valeur doit être dans la plage de 0 à 4 000.  
  
 *caReferenceWhite*  
 Spécifie la référence de blanche pour les couleurs de la source. Les couleurs plus claires que ce sont traités comme blanc. La valeur doit être dans la plage comprise entre 6 000 à 10 000.  
  
 *caContrast*  
 Spécifie la quantité de contraste à appliquer à l’objet source. La valeur doit être dans la plage comprise entre -100 et 100. La valeur 0 ne signifie aucun ajustement de contraste.  
  
 *caBrightness*  
 Spécifie la quantité de luminosité à appliquer à l’objet source. La valeur doit être dans la plage comprise entre -100 et 100. La valeur 0 ne signifie aucun ajustement de la luminosité.  
  
 *caColorfulness*  
 Spécifie la quantité de colorfulness à appliquer à l’objet source. La valeur doit être dans la plage comprise entre -100 et 100. La valeur 0 ne signifie aucun ajustement colorfulness.  
  
 *caRedGreenTint*  
 Spécifie la quantité d’ajustement rouge ou vert teinte à appliquer à l’objet source. La valeur doit être dans la plage comprise entre -100 et 100. Nombres positifs seraient ajustez vers le rouge et celle de nombres négatifs vers le vert. 0 ne signifie aucun ajustement de la teinte.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** wingdi.h  
  
## <a name="see-also"></a>Voir aussi  
 [Structures, Styles, rappels et tables des messages](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDC::GetColorAdjustment](../../mfc/reference/cdc-class.md#getcoloradjustment)


