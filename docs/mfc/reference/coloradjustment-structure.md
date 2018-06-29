---
title: Coloradjustment, Structure | Documents Microsoft
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
ms.openlocfilehash: 1bb4cba5ef2eafa27a26c945f8754eb1a0ab0315
ms.sourcegitcommit: be0e3457f2884551f18e183ef0ea65c3ded7f689
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/28/2018
ms.locfileid: "37077953"
---
# <a name="coloradjustment-structure"></a>COLORADJUSTMENT, structure
Le `COLORADJUSTMENT` structure définit les valeurs d’ajustement de couleur utilisés par Windows `StretchBlt` et `StretchDIBits` fonctions lors de la `StretchBlt` mode est **demi-teintes**.  
  
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
 Spécifie comment l’image de sortie doit être préparée. Ce membre peut être défini sur **NULL** ou n’importe quelle combinaison des valeurs suivantes :  
  
- **CA_NEGATIVE** indique que la valeur négative de l’image d’origine doit être affichée.  
  
- **CA_LOG_FILTER** Spécifie qu’une fonction logarithmique doit être appliquée à la densité finale des couleurs de sortie. Cela augmentera le contraste couleur lorsque la luminance est faible.  
  
 *caIlluminantIndex*  
 Spécifie la luminance de la source de lumière sous lequel l’objet d’image est affichée. Ce membre peut être défini à une des valeurs suivantes :  
  
- **ILLUMINANT_EQUAL_ENERGY**  
  
- **ILLUMINANT_A**  
  
- **ILLUMINANT_B**  
  
- **ILLUMINANT_C**  
  
- **ILLUMINANT_D50**  
  
- **ILLUMINANT_D55**  
  
- **ILLUMINANT_D65**  
  
- **ILLUMINANT_D75**  
  
- **ILLUMINANT_F2**  
  
- **ILLUMINANT_TURNGSTEN**  
  
- **ILLUMINANT_DAYLIGHT**  
  
- **ILLUMINANT_FLUORESCENT**  
  
- **ILLUMINANT_NTSC**  
  
 *caRedGamma*  
 Spécifie la valeur de correction gamma puissance n pour le serveur principal rouge de couleurs de la source. La valeur doit être dans la plage de 2 500 à 65,000. Une valeur de 10 000 ne signifie aucune correction gamma.  
  
 *caGreenGamma*  
 Spécifie la valeur de correction gamma puissance n pour principal vert de couleurs de la source. La valeur doit être dans la plage de 2 500 à 65,000. Une valeur de 10 000 ne signifie aucune correction gamma.  
  
 *caBlueGamma*  
 Spécifie la valeur de correction gamma puissance n pour le bleu primaire de couleurs de la source. La valeur doit être dans la plage de 2 500 à 65,000. Une valeur de 10 000 ne signifie aucune correction gamma.  
  
 *caReferenceBlack*  
 Spécifie la référence noire pour les couleurs de la source. Les couleurs qui sont plus foncés que cela sont traités en noir. La valeur doit être dans la plage de 0 à 4 000.  
  
 *caReferenceWhite*  
 Spécifie la référence de blanche pour les couleurs de la source. Les couleurs qui sont plus fine que ce sont traités comme blanc. La valeur doit être comprise entre 6 000 à 10 000.  
  
 *caContrast*  
 Spécifie la quantité de contraste à appliquer à l’objet source. La valeur doit être comprise entre -100 à 100. La valeur 0 ne signifie aucun ajustement de contraste.  
  
 *caBrightness*  
 Spécifie la quantité de luminosité à appliquer à l’objet source. La valeur doit être comprise entre -100 à 100. La valeur 0 ne signifie aucun ajustement de luminosité.  
  
 *caColorfulness*  
 Spécifie la quantité de colorfulness à appliquer à l’objet source. La valeur doit être comprise entre -100 à 100. La valeur 0 ne signifie aucun ajustement colorfulness.  
  
 *caRedGreenTint*  
 Spécifie la quantité d’ajustement rouges ou verts teinte à appliquer à l’objet source. La valeur doit être comprise entre -100 à 100. Les nombres positifs seraient ajustez vers le rouge, et celle de nombres négatifs vers le vert. 0 ne signifie aucun ajustement de la teinte.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** wingdi.h  
  
## <a name="see-also"></a>Voir aussi  
 [Structures, Styles, rappels et tables des messages](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDC::GetColorAdjustment](../../mfc/reference/cdc-class.md#getcoloradjustment)


