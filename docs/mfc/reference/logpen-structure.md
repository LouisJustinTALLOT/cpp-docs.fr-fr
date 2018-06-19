---
title: LOGPEN (Structure) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- LOGPEN
dev_langs:
- C++
helpviewer_keywords:
- LOGPEN structure [MFC]
ms.assetid: a89e8690-6b61-4af5-990c-7c82da24f3b0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4c0e07ce3a38eaca54e860ebe821924c0f564c69
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33374148"
---
# <a name="logpen-structure"></a>LOGPEN, structure
Le `LOGPEN` structure définit le style, la largeur et la couleur d’un stylet, un dessin utilisé pour dessiner des lignes et les bordures. Le [CPen::CreatePenIndirect](../../mfc/reference/cpen-class.md#createpenindirect) fonction utilise le `LOGPEN` structure.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef struct tagLOGPEN {  /* lgpn */  
    UINT lopnStyle;  
    POINT lopnWidth;  
    COLORREF lopnColor;  
} LOGPEN;  
```  
  
#### <a name="parameters"></a>Paramètres  
 *lopnStyle*  
 Spécifie le type de stylet. Ce membre peut être une des valeurs suivantes :  
  
- **PS_SOLID** crée un stylet continu.  
  
- **PS_DASH** crée un stylet en pointillés. (Valide uniquement lorsque la largeur du stylet est 1).  
  
- **PS_DOT** crée un stylet en pointillés. (Valide uniquement lorsque la largeur du stylet est 1).  
  
- **PS_DASHDOT** crée un stylet avec des points et des tirets alternés. (Valide uniquement lorsque la largeur du stylet est 1).  
  
- **PS_DASHDOTDOT** crée un stylet avec deux points et des tirets alternés. (Valide uniquement lorsque la largeur du stylet est 1).  
  
- **PS_NULL** crée un stylet null.  
  
- **PS_INSIDEFRAME** crée un stylet qui dessine une ligne dans le cadre des formes fermées produites par des fonctions de sortie GDI qui spécifient un rectangle englobant (par exemple, le **Ellipse**, **Rectangle**, `RoundRect`, `Pie`, et `Chord` fonctions membres). Lorsque ce style est utilisé avec GDI des fonctions qui ne spécifient pas d’un rectangle englobant de sortie (par exemple, le `LineTo` fonction membre), la zone de dessin du stylet n’est pas limitée par un frame.  
  
     Si le stylet a la **PS_INSIDEFRAME** style et une couleur qui ne correspond pas à une couleur de la table logique, le stylet est dessiné avec une couleur dégradée. Le **PS_SOLID** style de stylet ne peut pas être utilisé pour créer un stylet avec une couleur dégradée. Le **PS_INSIDEFRAME** style est identique à **PS_SOLID** si la largeur du stylet est inférieure ou égale à 1.  
  
     Lorsque le **PS_INSIDEFRAME** style est utilisé avec les objets GDI produites par des fonctions autres que **Ellipse**, **Rectangle**, et `RoundRect`, la ligne ne peut-être pas être traitées à l’intérieur du frame spécifié.  
  
 *lopnWidth*  
 Spécifie la largeur du stylet, en unités logiques. Si le **lopnWidth** membre est 0, le stylet est 1 pixel de large sur les appareils raster quel que soit le mode de mappage en cours.  
  
 *lopnColor*  
 Spécifie la couleur du stylet.  
  
## <a name="remarks"></a>Notes  
 Le **y** valeur dans le [POINT](../../mfc/reference/point-structure1.md) la structure de la **lopnWidth** membre n’est pas utilisé.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** wingdi.h  
  
## <a name="see-also"></a>Voir aussi  
 [Structures, Styles, rappels et tables des messages](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CPen::CreatePenIndirect](../../mfc/reference/cpen-class.md#createpenindirect)

