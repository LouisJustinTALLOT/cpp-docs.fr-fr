---
description: 'En savoir plus sur : fonctions inline'
title: Fonctions inline
ms.date: 10/16/2017
helpviewer_keywords:
- fast code
- inline functions, __inline keyword
- functions [C++], inline functions
ms.assetid: 00f4b2ff-8ad0-4165-9f4c-2ef157d03f31
ms.openlocfilehash: 616e85f2ac298420b3de174551ea2f6f879f24f1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97137552"
---
# <a name="inline-functions"></a>Fonctions inline

**Spécifique à Microsoft**

Le **`__inline`** mot clé indique au compilateur de substituer le code dans la définition de fonction pour chaque instance d’un appel de fonction. Toutefois, la substitution se produit uniquement à la discrétion du compilateur. Par exemple, le compilateur n'incorpore pas une fonction si son adresse est prise ou si elle trop volumineuse pour être incorporée.

Pour qu'une fonction soit considérée comme candidat pour l'incorporation, elle doit utiliser la définition de fonction de style nouveau.

Utilisez la forme suivante pour spécifier une fonction inline :

> **`__inline`***type* fonction <sub>OPT</sub> *-définition*

Les fonctions inline permettent de générer un code plus rapide et parfois plus petit que l'appel de fonction équivalent, pour les raisons suivantes :

- Elles permettent d'économiser le temps requis pour exécuter les appels de fonction.

- Les petites fonctions inline, de trois lignes ou moins, créent moins de code que l'appel de fonction équivalent, car le compilateur ne génère pas de code pour gérer les arguments et une valeur de retour.

- Les fonctions générées inline font l'objet d'optimisations de code non disponibles aux fonctions normales, car le compilateur n'exécute pas les optimisations interprocédurales.

Les fonctions utilisant ne **`__inline`** doivent pas être confondues avec du code assembleur inline. Consultez [Assembleur inline](../c-language/inline-assembler-c.md) pour plus d’informations.

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Inline, __inline, \_ _forceinline](../cpp/inline-functions-cpp.md)
