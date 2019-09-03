---
title: Conventions de document
ms.date: 08/29/2019
helpviewer_keywords:
- preprocessor
- preprocessor, conventions
ms.assetid: 469ce448-dc6c-4d0e-ba2b-e2e7a10155e1
ms.openlocfilehash: bb826b879b71edd3631c11a717320cee51c87175
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220376"
---
# <a name="document-conventions"></a>Conventions de document

Les conventions utilisent différents attributs de police pour différents composants de la syntaxe. Les symboles et les polices sont comme suit :

| Attribut | Description |
|---------------|-----------------|
| *nonterminal* | Le type italique indique des symboles non terminaux. |
| **#include** | Les symboles terminaux en gras sont des mots réservés littéraux et des symboles littéraux qui doivent être écrits comme indiqué. Les caractères situés dans ce contexte respectent toujours la casse. |
| <sub>opt</sub> | Les symboles non terminaux suivis d’<sub>opt</sub> sont toujours facultatifs.|
| police par défaut | Les caractères du jeu décrit ou répertorié dans cette police peuvent être utilisés comme symboles terminaux dans les instructions C. |

Un signe deux-points ( **:** ) qui suit un symbole non terminal introduit sa définition. D'autres définitions apparaissent sur des lignes distinctes.

Dans les blocs de syntaxe de code, ces symboles dans la police par défaut ont une signification particulière:

| Symbole | Description |
|---|---|
| \[ ] | Les crochets entourent un élément facultatif. |
| { \| } | Les accolades entourent les autres éléments, séparés par des barres verticales. |
| ... | Indique que le modèle d’élément précédent peut être répété. |

Dans les blocs de syntaxe de code,`,`les virgules (`.`), les points (),`;`les points-virgules`:`(), les signes`( )`deux-points (),`"`les parenthèses (), les`'`guillemets doubles () et les guillemets simples () sont des littéraux.

## <a name="see-also"></a>Voir aussi

[Résumé de la grammaire (C++C/)](../preprocessor/grammar-summary-c-cpp.md)
