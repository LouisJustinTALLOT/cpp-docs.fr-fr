---
description: 'En savoir plus sur : mise à jour d’une colonne quand une autre table contient une référence à la ligne'
title: Mettre à jour une colonne lorsqu’une autre table contient une référence à la ligne
ms.date: 10/24/2018
helpviewer_keywords:
- rowsets, column updates
ms.assetid: abb5db69-055d-431f-b12d-ad2940a661ba
ms.openlocfilehash: 5c4562aaaa435c9745bedd146c04c98158d50cc5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97272615"
---
# <a name="updating-a-column-when-another-table-contains-a-reference-to-the-row"></a>Mise à jour d'une colonne quand une autre table contient une référence à la ligne

Certains fournisseurs peuvent détecter les colonnes de la modification de ligne, mais ce n’est pas le nombre des fournisseurs. Par conséquent, la mise à jour d’une colonne peut provoquer une erreur lorsqu’il existe une référence à la ligne que vous essayez de mettre à jour. Pour résoudre ce problème, créez un accesseur distinct contenant uniquement les colonnes que vous souhaitez modifier. Transmettez le numéro de cet accesseur à `SetData` .

## <a name="see-also"></a>Voir aussi

[Utilisation des accesseurs](../../data/oledb/using-accessors.md)
