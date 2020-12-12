---
description: 'En savoir plus sur : préprocesseur'
title: Préprocesseur
ms.date: 08/29/2019
helpviewer_keywords:
- preprocessor
ms.assetid: e120eda3-b413-49f1-a07c-e9fb128cf500
ms.openlocfilehash: dd79766777926871e7bbf849f96420ef37052eba
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97202078"
---
# <a name="preprocessor"></a>Préprocesseur

Le préprocesseur est un processeur de texte qui manipule le texte d'un fichier source dans le cadre de la première phase de traduction. Le préprocesseur n’analyse pas le texte source, mais il le découpe en jetons pour localiser les appels de macro. Bien que le compilateur appelle normalement le préprocesseur lors de sa première passe, le préprocesseur peut également être appelé séparément pour traiter du texte sans compilation.

La documentation de référence sur le préprocesseur comprend les sections suivantes :

- [Directives de préprocesseur](../preprocessor/preprocessor-directives.md)

- [Opérateurs de préprocesseur](../preprocessor/preprocessor-operators.md)

- [Macros prédéfinies](../preprocessor/predefined-macros.md)

- [Pragmas](../preprocessor/pragma-directives-and-the-pragma-keyword.md)

**Spécifique à Microsoft**

Vous pouvez obtenir une liste de votre code source après le prétraitement à l’aide de l’option du compilateur [/e](../build/reference/e-preprocess-to-stdout.md) ou [/EP](../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md) . Les deux options appellent le préprocesseur et envoient le texte résultant au périphérique de sortie standard, qui, dans la plupart des cas, est la console. La différence entre les deux options est que `/E` comprend des `#line` directives et `/EP` supprime ces directives.

**FIN spécifique à Microsoft**

## <a name="special-terminology"></a><a name="_predir_special_terminology"></a> Terminologie spéciale

Dans la documentation du préprocesseur, le terme « argument » fait référence à l'entité passée à une fonction. Dans certains cas, il est modifié par « réel » ou « formel », qui décrit l’expression d’argument spécifiée dans l’appel de fonction, et la déclaration d’argument spécifiée dans la définition de fonction, respectivement.

Le terme « variable » fait référence à un objet de données simple de type C. Le terme « objet » fait référence aux objets et aux variables C++. Il s’agit d’un terme inclusif.

## <a name="see-also"></a>Voir aussi

[Référence du préprocesseur C/C++](../preprocessor/c-cpp-preprocessor-reference.md)\
[Phases de traduction](../preprocessor/phases-of-translation.md)
