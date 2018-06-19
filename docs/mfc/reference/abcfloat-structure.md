---
title: Abcfloat, Structure | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- ABCFLOAT
dev_langs:
- C++
helpviewer_keywords:
- ABCFLOAT structure [MFC]
ms.assetid: 338e7e15-9d2c-42d0-aa80-273acfde5cc5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5be39336f3da839dc9b1c7be6a64db54b59f99bd
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33351613"
---
# <a name="abcfloat-structure"></a>ABCFLOAT, structure
Le `ABCFLOAT` structure contient les largeurs de A, B et C d’un caractère de la police.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef struct _ABCFLOAT { /* abcf */  
    FLOAT abcfA;  
    FLOAT abcfB;  
    FLOAT abcfC;  
} ABCFLOAT;  
```  
  
#### <a name="parameters"></a>Paramètres  
 *abcfA*  
 Spécifie l’espacement A du caractère. L’espacement A est la distance à ajouter à la position actuelle avant de dessiner le glyphe de caractère.  
  
 *abcfB*  
 Spécifie l’espacement B du caractère. L’espacement B est la largeur de la partie dessinée du glyphe de caractère.  
  
 *abcfC*  
 Spécifie l’espacement C du caractère. L’espacement C est la distance à ajouter à la position actuelle pour fournir des espaces blancs à droite du glyphe de caractère.  
  
## <a name="remarks"></a>Notes  
 Les largeurs de A, B et C sont mesurées le long de la ligne de base de la police. L’incrément de caractère (largeur totale) d’un caractère est la somme des espaces A, B et C. L’un ou l’espace de C peut être négatif pour indiquer underhangs ou dépassements.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** wingdi.h  
  
## <a name="see-also"></a>Voir aussi  
 [Structures, Styles, rappels et tables des messages](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDC::GetCharABCWidths](../../mfc/reference/cdc-class.md#getcharabcwidths)

