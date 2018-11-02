---
title: Mettre à jour une colonne quand une autre table contient une référence à la ligne
ms.date: 10/24/2018
helpviewer_keywords:
- rowsets, column updates
ms.assetid: abb5db69-055d-431f-b12d-ad2940a661ba
ms.openlocfilehash: 2adca735558033aa9324f37b5a61385b5f48096c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50519887"
---
# <a name="updating-a-column-when-another-table-contains-a-reference-to-the-row"></a>Mise à jour d'une colonne quand une autre table contient une référence à la ligne

Certains fournisseurs peuvent détecter les colonnes de la modification de ligne, mais pas de nombreux fournisseurs. Par conséquent, la mise à jour une colonne peut entraîner une erreur lorsqu’il existe une référence à la ligne que vous tentez de mettre à jour. Pour résoudre ce problème, créez un accesseur séparé contenant uniquement les colonnes que vous souhaitez modifier. Transmettre le numéro de cet accesseur à `SetData`.

## <a name="see-also"></a>Voir aussi

[Utilisation des accesseurs](../../data/oledb/using-accessors.md)