---
title: Logpen, Structure | Microsoft Docs
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
ms.openlocfilehash: c677f86a44d24e0d0d2742d47ee1534532001528
ms.sourcegitcommit: 6408139d5f5ff8928f056bde93d20eecb3520361
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37338530"
---
# <a name="logpen-structure"></a>LOGPEN, structure
Le `LOGPEN` structure définit le style, la largeur et la couleur d’un stylet, un objet de dessin utilisé pour dessiner des lignes et les bordures. Le [CPen::CreatePenIndirect](../../mfc/reference/cpen-class.md#createpenindirect) fonction utilise le `LOGPEN` structure.  
  
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
  
- PS_SOLID crée un stylet solid.  
  
- PS_DASH crée un stylet en pointillés. (Valide uniquement lorsque la largeur du stylet est 1).  
  
- PS_DOT crée un stylet en pointillés. (Valide uniquement lorsque la largeur du stylet est 1).  
  
- PS_DASHDOT crée un stylet avec des ALTERNANCES de tirets et points. (Valide uniquement lorsque la largeur du stylet est 1).  
  
- PS_DASHDOTDOT crée un stylet avec double points et des tirets alternés. (Valide uniquement lorsque la largeur du stylet est 1).  
  
- PS_NULL crée un stylet null.  
  
- Les fonctions qui spécifient un rectangle englobant de la sortie des PS_INSIDEFRAME crée un stylet qui dessine une ligne dans le cadre des formes fermées produit par GDI (par exemple, le `Ellipse`, `Rectangle`, `RoundRect`, `Pie`, et `Chord` membre fonctions). Quand ce style est utilisé avec GDI des fonctions qui ne spécifient pas d’un rectangle englobant de sortie (par exemple, le `LineTo` fonction membre), la zone de dessin du stylet n’est pas limitée par un frame.  
  
     Si un stylet a le style PS_INSIDEFRAME et une couleur qui ne correspond pas à une couleur de la table logique, le stylet est dessiné avec une couleur dégradée. Le style de stylet PS_SOLID ne peut pas être utilisé pour créer un stylet avec une couleur dégradée. Le style PS_INSIDEFRAME est identique à PS_SOLID si la largeur du stylet est inférieure ou égale à 1.  
  
     Lorsque le style PS_INSIDEFRAME est utilisé avec les objets GDI générées par des fonctions autres que `Ellipse`, `Rectangle`, et `RoundRect`, la ligne est peut-être pas complètement à l’intérieur du cadre spécifié.  
  
 *lopnWidth*  
 Spécifie la largeur du stylet, en unités logiques. Si le `lopnWidth` membre est 0, le stylet est 1 pixel de large sur les appareils raster, quel que soit le mode de mappage en cours.  
  
 *lopnColor*  
 Spécifie la couleur du stylet.  
  
## <a name="remarks"></a>Notes  
 Le `y` valeur dans le [POINT](../../mfc/reference/point-structure1.md) de structure pour le `lopnWidth` membre n’est pas utilisé.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** wingdi.h  
  
## <a name="see-also"></a>Voir aussi  
 [Structures, Styles, rappels et tables des messages](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CPen::CreatePenIndirect](../../mfc/reference/cpen-class.md#createpenindirect)

