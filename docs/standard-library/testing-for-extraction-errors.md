---
title: Tester les erreurs d'extraction
ms.date: 11/04/2016
helpviewer_keywords:
- extraction errors
ms.assetid: 6a681028-adba-4557-8f7b-f137932905f8
ms.openlocfilehash: db551a21fd33665d83b11373f040be158406d492
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68453665"
---
# <a name="testing-for-extraction-errors"></a>Tester les erreurs d'extraction

Les fonctions de traitement des erreurs de sortie, présentées dans [Fonctions de traitement des erreurs](../standard-library/output-file-stream-member-functions.md), s’appliquent aux flux d’entrée. Il est important de tester les erreurs lors de l’extraction. Examinez cette instruction :

```cpp
cin>> n;
```

Si `n` est un entier signé, une valeur supérieure à 32 767 (la valeur maximale autorisée ou MAX_INT) définit le bit `fail` du flux et l’objet `cin` devient inutilisable. Toutes les extractions ultérieures entraînent un retour immédiat sans valeur stockée.

## <a name="see-also"></a>Voir aussi

[Flux d’entrée](../standard-library/input-streams.md)
