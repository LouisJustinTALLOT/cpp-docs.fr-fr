---
description: 'En savoir plus sur : type double'
title: double, type
ms.date: 11/04/2016
helpviewer_keywords:
- mantissas, floating-point variables
- type double
- portability [C++], type double
- double data type
ms.assetid: 17c85b24-1475-4d41-a03c-ddf2d6561d34
ms.openlocfilehash: c30af4ef432251ddf38be2172102ff7a63254940
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97242845"
---
# <a name="type-double"></a>double, type

Les valeurs à double précision avec type double possèdent 8 octets. Le format est semblable au format float si ce n'est qu'il a 11 bits d'exposant (excès de 1023) et 52 bits de mantisse, plus le bit 1 d'ordre haut implicite. Ce format fournit une plage d’approximativement 1,7E-308 à 1,7E+308 pour le type double.

**Spécifique à Microsoft**

Le type double contient 64 bits : 1 pour le signe, 11 pour l'exposant et 52 pour la mantisse. Sa plage est +/-1,7E308 avec au moins 15 chiffres de précision.

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Stockage des types de base](../c-language/storage-of-basic-types.md)
