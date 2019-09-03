---
title: Préprocesseur
ms.date: 08/29/2019
helpviewer_keywords:
- preprocessor
ms.assetid: e120eda3-b413-49f1-a07c-e9fb128cf500
ms.openlocfilehash: 883504810f1b659e28764a75ebc7cfda325920a5
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70222235"
---
# <a name="preprocessor"></a>Préprocesseur

Le préprocesseur est un processeur de texte qui manipule le texte d'un fichier source dans le cadre de la première phase de traduction. Le préprocesseur n’analyse pas le texte source, mais il le découpe en jetons pour localiser les appels de macro. Bien que le compilateur appelle normalement le préprocesseur lors de sa première passe, le préprocesseur peut également être appelé séparément pour traiter du texte sans compilation.

La documentation de référence sur le préprocesseur comprend les sections suivantes :

- [Directives de préprocesseur](../preprocessor/preprocessor-directives.md)

- [Opérateurs de préprocesseur](../preprocessor/preprocessor-operators.md)

- [Macros prédéfinies](../preprocessor/predefined-macros.md)

- [Pragmas](../preprocessor/pragma-directives-and-the-pragma-keyword.md)

**Section spécifique à Microsoft**

Vous pouvez obtenir une liste de votre code source après le prétraitement à l’aide de l’option du compilateur [/e](../build/reference/e-preprocess-to-stdout.md) ou [/EP](../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md) . Les deux options appellent le préprocesseur et envoient le texte résultant au périphérique de sortie standard, qui, dans la plupart des cas, est la console. La différence entre les deux options est que `/E` comprend `#line` des directives et `/EP` supprime ces directives.

**FIN de la section spécifique à Microsoft**

##  <a name="_predir_special_terminology"></a>Terminologie spéciale

Dans la documentation du préprocesseur, le terme « argument » fait référence à l'entité passée à une fonction. Dans certains cas, il est modifié par «réel» ou «formel», qui décrit l’expression d’argument spécifiée dans l’appel de fonction, et la déclaration d’argument spécifiée dans la définition de fonction, respectivement.

Le terme « variable » fait référence à un objet de données simple de type C. Le terme «objet» fait référence aux C++ objets et aux variables; Il s’agit d’un terme inclusif.

## <a name="see-also"></a>Voir aussi

[Référence duC++ préprocesseur C/](../preprocessor/c-cpp-preprocessor-reference.md)\
[Phases de traduction](../preprocessor/phases-of-translation.md)
