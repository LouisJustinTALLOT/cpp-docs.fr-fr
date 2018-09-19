---
title: Fonctions inline | Microsoft Docs
ms.custom: ''
ms.date: 10/16/2017
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- fast code
- inline functions, __inline keyword
- functions [C++], inline functions
ms.assetid: 00f4b2ff-8ad0-4165-9f4c-2ef157d03f31
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 127438da4929e58e07e10701dd64869b084fe4c5
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46078580"
---
# <a name="inline-functions"></a>Fonctions inline

**Section spécifique à Microsoft**

Le mot clé `__inline` indique au compilateur de substituer le code dans la définition de fonction pour chaque instance d'un appel de fonction. Toutefois, la substitution se produit uniquement à la discrétion du compilateur. Par exemple, le compilateur n'incorpore pas une fonction si son adresse est prise ou si elle trop volumineuse pour être incorporée.

Pour qu'une fonction soit considérée comme candidat pour l'incorporation, elle doit utiliser la définition de fonction de style nouveau.

Utilisez la forme suivante pour spécifier une fonction inline :

> **__inline** *type*<sub>opt</sub> *function-definition*

Les fonctions inline permettent de générer un code plus rapide et parfois plus petit que l'appel de fonction équivalent, pour les raisons suivantes :

- Elles permettent d'économiser le temps requis pour exécuter les appels de fonction.

- Les petites fonctions inline, de trois lignes ou moins, créent moins de code que l'appel de fonction équivalent, car le compilateur ne génère pas de code pour gérer les arguments et une valeur de retour.

- Les fonctions générées inline font l'objet d'optimisations de code non disponibles aux fonctions normales, car le compilateur n'exécute pas les optimisations interprocédurales.

Les fonctions utilisant `__inline` ne doivent pas être confondues avec du code assembleur inline. Consultez [Assembleur inline](../c-language/inline-assembler-c.md) pour plus d’informations.

**Fin de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[inline, __inline, \__forceinline](../cpp/inline-functions-cpp.md)

