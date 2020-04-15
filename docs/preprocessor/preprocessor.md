---
title: Préprocesseur
ms.date: 08/29/2019
helpviewer_keywords:
- preprocessor
ms.assetid: e120eda3-b413-49f1-a07c-e9fb128cf500
ms.openlocfilehash: 7188d7a6803c9eec109a59906cf0c016a460819d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81337506"
---
# <a name="preprocessor"></a>Préprocesseur

Le préprocesseur est un processeur de texte qui manipule le texte d'un fichier source dans le cadre de la première phase de traduction. Le préprocesseur n’analyse pas le texte source, mais il ne le décomposer en jetons pour localiser les appels macro. Bien que le compilateur appelle normalement le préprocesseur lors de sa première passe, le préprocesseur peut également être appelé séparément pour traiter du texte sans compilation.

La documentation de référence sur le préprocesseur comprend les sections suivantes :

- [Directives de préprocesseur](../preprocessor/preprocessor-directives.md)

- [Opérateurs de préprocesseurs](../preprocessor/preprocessor-operators.md)

- [Macros prédéfinis](../preprocessor/predefined-macros.md)

- [Pragmas](../preprocessor/pragma-directives-and-the-pragma-keyword.md)

**Microsoft Spécifique**

Vous pouvez obtenir une liste de votre code source après le prétraitement en utilisant l’option de compilateur [/E](../build/reference/e-preprocess-to-stdout.md) [ou/EP.](../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md) Les deux options invoquent le préprocesseur et envoient le texte résultant au périphérique de sortie standard, qui, dans la plupart des cas, est la console. La différence entre les `/E` deux `#line` options `/EP` est qui comprend des directives, et dépouille ces directives.

**END Microsoft Spécifique**

## <a name="special-terminology"></a><a name="_predir_special_terminology"></a>Terminologie spéciale

Dans la documentation du préprocesseur, le terme « argument » fait référence à l'entité passée à une fonction. Dans certains cas, il est modifié par "réel" ou "formel", qui décrit l’expression de l’argument spécifié dans l’appel de fonction, et la déclaration d’argument spécifiée dans la définition de fonction, respectivement.

Le terme « variable » fait référence à un objet de données simple de type C. Le terme « objet » désigne à la fois les objets et les variables de CMD ; c’est un terme inclusif.

## <a name="see-also"></a>Voir aussi

[Référence de préprocesseur C/CMD](../preprocessor/c-cpp-preprocessor-reference.md)\
[Phases de traduction](../preprocessor/phases-of-translation.md)
