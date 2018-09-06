---
title: Le résumé de syntaxe des définitions de | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- preprocessor, definitions
- preprocessor
ms.assetid: cc752dc8-6f4e-4347-a556-e0d9ef4c46bd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3c11f2f839ef806d74eae65c9fc8fe3a71cd2e9c
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43760810"
---
# <a name="definitions-for-the-grammar-summary"></a>Résumé des définitions de grammaire

Les terminaux sont des points de terminaison dans une définition de syntaxe. Aucune autre résolution n'est possible. Les terminaux incluent l'ensemble des mots réservés et des identificateurs définis par l'utilisateur.

Les éléments non terminaux sont des espaces réservés dans la syntaxe. La plupart de ces éléments sont définis ailleurs dans ce résumé de syntaxe. Les définitions peuvent être récursives. Les éléments non terminaux suivants sont définis dans le [Conventions lexicales](../cpp/lexical-conventions.md) section de la *référence du langage C++*:

`constant`, *constant-expression*, *identifier*, *keyword*, `operator`, `punctuator`

Un composant facultatif est indiqué par l’indice <sub>opt</sub>. Par exemple, le code suivant indique une expression facultative entre accolades :

**{** *expression*<sub>opt</sub> **}**

## <a name="see-also"></a>Voir aussi

[Résumé de la grammaire (C/C++)](../preprocessor/grammar-summary-c-cpp.md)