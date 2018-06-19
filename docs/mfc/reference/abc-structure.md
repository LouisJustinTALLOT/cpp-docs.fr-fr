---
title: ABC, Structure | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- ABC
dev_langs:
- C++
helpviewer_keywords:
- ABC structure [MFC]
ms.assetid: 32663839-c3b7-4f47-896c-b15329c96bc8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 61b5f67247b556b37cdf934f94c30947675533e7
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33346488"
---
# <a name="abc-structure"></a>ABC, structure
Le **ABC** structure contient la largeur d’un caractère dans une police TrueType.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef struct _ABC { /* abc */  
    int abcA;  
    UINT abcB;  
    int abcC;  
} ABC;  
```  
  
#### <a name="parameters"></a>Paramètres  
 *abcA*  
 Spécifie l’espacement A du caractère. L’espacement A est la distance à ajouter à la position actuelle avant de dessiner le glyphe de caractère.  
  
 *abcB*  
 Spécifie l’espacement B du caractère. L’espacement B est la largeur de la partie dessinée du glyphe de caractère.  
  
 *abcC*  
 Spécifie l’espacement C du caractère. L’espacement C est la distance à ajouter à la position actuelle pour fournir des espaces blancs à droite du glyphe de caractère.  
  
## <a name="remarks"></a>Notes  
 La largeur totale d’un caractère est la somme des espaces A, B et C. L’un ou l’espace de C peut être négatif pour indiquer underhangs ou dépassements.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** wingdi.h  
  
## <a name="see-also"></a>Voir aussi  
 [Structures, Styles, rappels et tables des messages](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDC::GetCharABCWidths](../../mfc/reference/cdc-class.md#getcharabcwidths)


