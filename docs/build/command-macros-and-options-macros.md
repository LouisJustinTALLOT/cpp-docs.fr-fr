---
title: Macros de commandes et macros d'options
ms.date: 11/04/2016
helpviewer_keywords:
- options macros
- command macros in NMAKE
- macros, options macros
- macros, command macros
ms.assetid: 50dff03c-0dc3-4a8a-9a17-57e0e4ea9bac
ms.openlocfilehash: f18cfd6ada235485a5fe47bdc94b49631b9abbbe
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50601303"
---
# <a name="command-macros-and-options-macros"></a>Macros de commandes et macros d'options

Macros de commandes sont prédéfinies pour les produits Microsoft. Macros d’options représentent des options de ces produits et ne sont pas définies par défaut. Les deux sont utilisés dans les règles d’inférence prédéfinies et peuvent être utilisées dans les blocs de description ou les règles d’inférence définies par l’utilisateur. Macros de commandes peuvent être redéfinies pour représenter tout ou partie d’une ligne de commande, y compris les options. Macros d’options génèrent une chaîne null si non définie de gauche.

|Produit Microsoft|Macros de commande|Défini comme|Macros d’options|
|-----------------------|-------------------|----------------|-------------------|
|Macro Assembler|**EN TANT QUE**|ml|**AFLAGS**|
|Compilateur de base|**BC**|BC|**BFLAGS**|
|Compilateur C|**CC**|CL|**CFLAGS**|
|Compilateur C++|**CPP**|CL|**CPPFLAGS**|
|Compilateur C++|**CXX**|CL|**CXXFLAGS**|
|compilateur de ressources|**RC**|rc|**RFLAGS**|

## <a name="see-also"></a>Voir aussi

[Macros spéciales de NMAKE](../build/special-nmake-macros.md)