---
title: Macros de commandes et macros d'options
ms.date: 11/04/2016
helpviewer_keywords:
- options macros
- command macros in NMAKE
- macros, options macros
- macros, command macros
ms.assetid: 50dff03c-0dc3-4a8a-9a17-57e0e4ea9bac
ms.openlocfilehash: daf8c243f95f7cc12a3d3b1c5cf16f5a384c9671
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57418296"
---
# <a name="command-macros-and-options-macros"></a>Macros de commandes et macros d'options

Macros de commandes sont prédéfinies pour les produits Microsoft. Macros d’options représentent des options de ces produits et ne sont pas définies par défaut. Les deux sont utilisés dans les règles d’inférence prédéfinies et peuvent être utilisées dans les blocs de description ou les règles d’inférence définies par l’utilisateur. Macros de commandes peuvent être redéfinies pour représenter tout ou partie d’une ligne de commande, y compris les options. Macros d’options génèrent une chaîne null si non définie de gauche.

|Produit Microsoft|Macros de commande|Défini comme|Macros d’options|
|-----------------------|-------------------|----------------|-------------------|
|Macro Assembler|**AS**|ml|**AFLAGS**|
|Compilateur de base|**BC**|bc|**BFLAGS**|
|Compilateur C|**CC**|cl|**CFLAGS**|
|Compilateur C++|**CPP**|cl|**CPPFLAGS**|
|Compilateur C++|**CXX**|cl|**CXXFLAGS**|
|compilateur de ressources|**RC**|rc|**RFLAGS**|

## <a name="see-also"></a>Voir aussi

[Macros spéciales de NMAKE](../build/special-nmake-macros.md)
