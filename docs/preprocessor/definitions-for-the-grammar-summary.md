---
title: Résumé des définitions de grammaire
ms.date: 11/04/2016
helpviewer_keywords:
- preprocessor, definitions
- preprocessor
ms.assetid: cc752dc8-6f4e-4347-a556-e0d9ef4c46bd
ms.openlocfilehash: 133000c0cc8ef636a3f9752d2f6fc7f1934bd831
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50521123"
---
# <a name="definitions-for-the-grammar-summary"></a>Résumé des définitions de grammaire

Les terminaux sont des points de terminaison dans une définition de syntaxe. Aucune autre résolution n'est possible. Les terminaux incluent l'ensemble des mots réservés et des identificateurs définis par l'utilisateur.

Les éléments non terminaux sont des espaces réservés dans la syntaxe. La plupart de ces éléments sont définis ailleurs dans ce résumé de syntaxe. Les définitions peuvent être récursives. Les éléments non terminaux suivants sont définis dans le [Conventions lexicales](../cpp/lexical-conventions.md) section de la *référence du langage C++*:

`constant`, *constant-expression*, *identifier*, *keyword*, `operator`, `punctuator`

Un composant facultatif est indiqué par l'élément <sub>opt</sub> indicé. Par exemple, le code suivant indique une expression facultative entre accolades :

**{** *expression*<sub>opt</sub> **}**

## <a name="see-also"></a>Voir aussi

[Résumé de la grammaire (C/C++)](../preprocessor/grammar-summary-c-cpp.md)