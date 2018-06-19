---
title: Mettre à jour une colonne quand une autre table contient une référence à la ligne | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- rowsets, column updates
ms.assetid: abb5db69-055d-431f-b12d-ad2940a661ba
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 17d260f522432a78729c9998c518398dfa41275a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33102883"
---
# <a name="updating-a-column-when-another-table-contains-a-reference-to-the-row"></a>Mise à jour d'une colonne quand une autre table contient une référence à la ligne
Certains fournisseurs peuvent détecter les colonnes dans la modification de ligne, mais pas de nombreux fournisseurs. Par conséquent, la mise à jour d’une colonne peut entraîner une erreur lorsqu’il existe une référence à la ligne que vous tentez de mettre à jour. Pour résoudre ce problème, créez un accesseur séparé contenant uniquement les colonnes que vous souhaitez modifier. Transmettre le numéro de cet accesseur à `SetData`.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation des accesseurs](../../data/oledb/using-accessors.md)