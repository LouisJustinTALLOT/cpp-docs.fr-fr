---
title: une fois | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- vc-pragma.once
- once_CPP
dev_langs:
- C++
helpviewer_keywords:
- once pragma
- pragmas, once
ms.assetid: c7517556-6403-4b16-8898-f2aa0a6f685f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9b0e0b2b3667d4a33709caa643e4d26ed70b2990
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33912925"
---
# <a name="once"></a>once
Spécifie que le fichier sera inclus (ouvert) une seule fois par le compilateur lors de la compilation d'un fichier de code source.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
#pragma once  
  
```  
  
## <a name="remarks"></a>Notes  
 L'utilisation de `#pragma once` peut réduire les durées de génération étant donné que le compilateur n'ouvrira pas le fichier et ne le lira pas après le premier élément #include du fichier dans l'unité de traduction. Cela est appelé *optimisation de plusieurs inclusions*. Il a un effet semblable à la *#include guard* idiome, qui utilise les définitions de macro de préprocesseur pour empêcher plusieurs inclusions du contenu du fichier. Cela permet également d’empêcher les violations de la *règle d’unique définition*, qui exige que tous les modèles, types, fonctions et objets aient pas plus d’une définition dans votre code.  
  
 Par exemple :  
  
```  
// header.h  
#pragma once  
// Code placed here is included only once per translation unit  
  
```  
  
 Nous vous recommandons la directive `#pragma once` pour le nouveau code, car elle ne pollue pas l'espace de noms global avec un symbole de préprocesseur. Elle nécessite moins de saisie de texte, est moins perturbante et ne peut pas provoquer de collisions de symboles (erreurs provoquées par l'utilisation du même symbole de préprocesseur comme valeur de garde par différents fichiers d'en-tête). Elle ne fait pas partie de la norme C++, mais est implémentée de façon portable par plusieurs compilateurs courants.  
  
 L'utilisation à la fois de l'idiome #include guard et de `#pragma once` dans le même fichier ne présente aucun avantage. Le compilateur reconnaît l'idiome #include guard et implémente l'optimisation de plusieurs inclusions de la même façon que la directive `#pragma once` si aucun code sans commentaire ni directive de préprocesseur ne précède ou suit la forme standard de l'idiome :  
  
```  
// header.h  
// Demonstration of the #include guard idiom.  
// Note that the defined symbol can be arbitrary.  
#ifndef HEADER_H_     // equivalently, #if !defined HEADER_H_  
#define HEADER_H_  
// Code placed here is included only once per translation unit  
#endif // HEADER_H_  
  
```  
  
 Nous recommandons l'idiome #include guard quand le code doit être portable sur les compilateurs qui n'implémentent pas la directive `#pragma once`, pour maintenir la cohérence avec le code existant ou quand l'optimisation de plusieurs inclusions est impossible. Cela peut se produire dans des projets complexes quand l'alias de système de fichiers ou des chemins d'accès Include dotés d'un alias empêchent le compilateur d'identifier les fichiers Include identiques par le chemin d'accès canonique.  
  
 Veillez à ne pas utiliser `#pragma once` ni l'idiome #include guard dans les fichiers d'en-tête destinés à être inclus plusieurs fois, avec des symboles de préprocesseur pour contrôler leurs effets. Pour obtenir un exemple de cette conception, consultez le \<assert.h > fichier d’en-tête. Veillez également à gérer les chemins d'accès Include pour éviter de créer plusieurs chemins d'accès aux fichiers inclus, ce qui peut anéantir l'optimisation de plusieurs inclusions à la fois pour l'idiome #include guard et `#pragma once`.  
  
## <a name="see-also"></a>Voir aussi  
 [Directives pragma et mot clé _Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)