---
description: 'En savoir plus sur : définitions et conventions'
title: Définitions et conventions
ms.date: 11/04/2016
helpviewer_keywords:
- nonterminals definition
ms.assetid: f9b3cf5f-6a7c-4a10-9b18-9d4a43efdaeb
ms.openlocfilehash: 892f14bfc3059406bbc192640e04c0181d06eee2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97186868"
---
# <a name="definitions-and-conventions"></a>Définitions et conventions

Les terminaux sont des points de terminaison dans une définition de syntaxe. Aucune autre résolution n'est possible. Les terminaux incluent l'ensemble des mots réservés et des identificateurs définis par l'utilisateur.

Les non terminaux sont des espaces réservés dans la syntaxe qui sont définis ailleurs dans ce résumé de syntaxe. Les définitions peuvent être récursives.

Un composant facultatif est indiqué par le script <sub>OPT</sub>. Par exemple :

> **{** *expression*<sub>OPT</sub> **}**

indique une expression facultative entre accolades.

Les conventions syntaxiques utilisent différents attributs de police pour différents composants de la syntaxe. Les symboles et les polices sont comme suit :

|Attribut|Description|
|---------------|-----------------|
|*élément non terminal*|Le type italique indique des symboles non terminaux.|
|**`const`**|Les symboles terminaux en gras sont des mots réservés littéraux et des symboles littéraux qui doivent être écrits comme indiqué. Les caractères situés dans ce contexte respectent toujours la casse.|
|<sub>option</sub>|Les non terminaux suivis de <sub>OPT</sub> sont toujours facultatifs.|
|police par défaut|Les caractères dans le jeu décrit ou répertorié dans cette police peuvent être utilisés comme terminaux dans les instructions C.|

Un signe deux-points (**:**) qui suit un symbole non terminal introduit sa définition. Les définitions alternatives figurent sur des lignes distinctes, sauf lorsqu'elles sont précédées des mots « one of ».

## <a name="see-also"></a>Voir aussi

[Résumé de la syntaxe du langage C](../c-language/c-language-syntax-summary.md)
