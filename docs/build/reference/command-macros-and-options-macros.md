---
title: Macros de commandes et macros d’options
description: Décrit les macros prédéfinies NMAKE pour les outils de génération et leurs options.
ms.date: 11/20/2019
helpviewer_keywords:
- options macros
- command macros in NMAKE
- macros, options macros
- macros, command macros
ms.assetid: 50dff03c-0dc3-4a8a-9a17-57e0e4ea9bac
no-loc:
- AS
- AFLAGS
- CC
- CFLAGS
- CPP
- CPPFLAGS
- CXX
- CXXFLAGS
- RC
- RFLAGS
- ias
- ml
- ml64
- cl
- rc
ms.openlocfilehash: d5c4477fd97e2a6c48dbac4d0ce83f7fd5f12ad6
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74303177"
---
# <a name="command-macros-and-options-macros"></a>Macros de commandes et macros d’options

Les macros de commande sont prédéfinies pour les produits Microsoft. Les macros d’options représentent des options pour ces produits et ne sont pas définies par défaut. Les deux sont utilisés dans les règles d’inférence prédéfinies et peuvent être utilisés dans des blocs de description ou des règles d’inférence définies par l’utilisateur. Les macros de commandes peuvent être redéfinies pour représenter tout ou partie d’une ligne de commande, y compris les options. Les macros d’options génèrent une chaîne NULL si elles ne sont pas définies.

|Produit Microsoft|Macro de commande|Défini comme|Options, macro|
|-----------------------|-------------------|----------------|-------------------|
|Assembleur de macros|**AS**|ml, ias ou ml64|**AFLAGS**|
|Compilateur C|**CC**|cl|**CFLAGS**|
|Compilateur C++|**CPP**|cl|**CPPFLAGS**|
|Compilateur C++|**CXX**|cl|**CXXFLAGS**|
|compilateur de ressources|**RC**|Release|**RFLAGS**|

## <a name="see-also"></a>Voir aussi

[Macros spéciales de NMAKE](special-nmake-macros.md)
