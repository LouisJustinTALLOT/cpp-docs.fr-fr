---
description: 'En savoir plus sur : test des erreurs d’extraction'
title: Tester les erreurs d'extraction
ms.date: 11/04/2016
helpviewer_keywords:
- extraction errors
ms.assetid: 6a681028-adba-4557-8f7b-f137932905f8
ms.openlocfilehash: c4a9b5c1ffe4f78718563b33e39012272cfb8042
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97259355"
---
# <a name="testing-for-extraction-errors"></a>Tester les erreurs d'extraction

Les fonctions de traitement des erreurs de sortie, présentées dans [Fonctions de traitement des erreurs](../standard-library/output-file-stream-member-functions.md), s’appliquent aux flux d’entrée. Il est important de tester les erreurs lors de l’extraction. Imaginons l'instruction suivante :

```cpp
cin>> n;
```

Si `n` est un entier signé, une valeur supérieure à 32 767 (la valeur maximale autorisée ou MAX_INT) définit le bit `fail` du flux et l’objet `cin` devient inutilisable. Toutes les extractions ultérieures entraînent un retour immédiat sans valeur stockée.

## <a name="see-also"></a>Voir aussi

[Flux d’entrée](../standard-library/input-streams.md)
