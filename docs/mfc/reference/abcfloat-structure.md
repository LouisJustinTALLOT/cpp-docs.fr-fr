---
title: Abcfloat, Structure | Microsoft Docs
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
ms.openlocfilehash: 5a9bbece0773c14a4a8b545bc56209bf682e22c0
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46375409"
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

*abcfA*<br/>
Spécifie l’espacement A du caractère. L’espacement A est la distance à ajouter à la position actuelle avant de dessiner le glyphe de caractères.

*abcfB*<br/>
Spécifie l’espacement B du caractère. L’espacement de B est la largeur de la partie dessinée du glyphe de caractères.

*abcfC*<br/>
Spécifie l’espacement C du caractère. L’espacement C est la distance à ajouter à la position actuelle pour fournir des espaces blancs à droite du glyphe de caractères.

## <a name="remarks"></a>Notes

Les largeurs de A, B et C sont mesurées le long de la ligne de base de la police. L’incrément de caractère (largeur totale) d’un caractère est la somme des espaces A, B et C. L’un ou l’espace C peut être négatif pour indiquer underhangs ou des interférences.

## <a name="requirements"></a>Configuration requise

**En-tête :** wingdi.h

## <a name="see-also"></a>Voir aussi

[Structures, styles, rappels et tables de messages](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CDC::GetCharABCWidths](../../mfc/reference/cdc-class.md#getcharabcwidths)

