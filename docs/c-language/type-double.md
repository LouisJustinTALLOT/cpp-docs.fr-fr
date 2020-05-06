---
title: double, type
ms.date: 11/04/2016
helpviewer_keywords:
- mantissas, floating-point variables
- type double
- portability [C++], type double
- double data type
ms.assetid: 17c85b24-1475-4d41-a03c-ddf2d6561d34
ms.openlocfilehash: 43e6cc444f4d6a973fc58b5ce550e468066aca1b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62290730"
---
# <a name="type-double"></a>double, type

Les valeurs à double précision avec type double possèdent 8 octets. Le format est semblable au format float si ce n'est qu'il a 11 bits d'exposant (excès de 1023) et 52 bits de mantisse, plus le bit 1 d'ordre haut implicite. Ce format fournit une plage d’approximativement 1,7E-308 à 1,7E+308 pour le type double.

**Spécifique à Microsoft**

Le type double contient 64 bits : 1 pour le signe, 11 pour l'exposant et 52 pour la mantisse. Sa plage est +/-1,7E308 avec au moins 15 chiffres de précision.

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Stockage de types de base](../c-language/storage-of-basic-types.md)
