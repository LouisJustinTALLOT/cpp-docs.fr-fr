---
title: ABC, structure
ms.date: 11/04/2016
f1_keywords:
- ABC
helpviewer_keywords:
- ABC structure [MFC]
ms.assetid: 32663839-c3b7-4f47-896c-b15329c96bc8
ms.openlocfilehash: f899a84ddbe5ca3ec3abd4dff135a585aa61eaa9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50549563"
---
# <a name="abc-structure"></a>ABC, structure

Le `ABC` structure contient la largeur d’un caractère dans une police TrueType.

## <a name="syntax"></a>Syntaxe

```
typedef struct _ABC { /* abc */
    int abcA;
    UINT abcB;
    int abcC;
} ABC;
```

#### <a name="parameters"></a>Paramètres

*abcA*<br/>
Spécifie l’espacement A du caractère. L’espacement A est la distance à ajouter à la position actuelle avant de dessiner le glyphe de caractères.

*abcB*<br/>
Spécifie l’espacement B du caractère. L’espacement de B est la largeur de la partie dessinée du glyphe de caractères.

*abcC*<br/>
Spécifie l’espacement C du caractère. L’espacement C est la distance à ajouter à la position actuelle pour fournir des espaces blancs à droite du glyphe de caractères.

## <a name="remarks"></a>Notes

La largeur totale d’un caractère est la somme des espaces A, B et C. L’un ou l’espace C peut être négatif pour indiquer underhangs ou des interférences.

## <a name="requirements"></a>Configuration requise

**En-tête :** wingdi.h

## <a name="see-also"></a>Voir aussi

[Structures, styles, rappels et tables de messages](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CDC::GetCharABCWidths](../../mfc/reference/cdc-class.md#getcharabcwidths)

