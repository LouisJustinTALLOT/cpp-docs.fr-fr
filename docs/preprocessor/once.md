---
description: 'En savoir plus sur : pragma once'
title: once, pragma
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.once
- once_CPP
helpviewer_keywords:
- once pragma
- pragmas, once
ms.assetid: c7517556-6403-4b16-8898-f2aa0a6f685f
ms.openlocfilehash: 3aa1e50173ef625d13ad9f36684aec3a1c512d2d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97333234"
---
# <a name="once-pragma"></a>once, pragma

Spécifie que le compilateur n’intègre le fichier d’en-tête qu’une seule fois, lors de la compilation d’un fichier de code source.

## <a name="syntax"></a>Syntaxe

> **#pragma une fois**

## <a name="remarks"></a>Notes

L’utilisation de `#pragma once` peut réduire les délais de génération, car le compilateur ne s’ouvre pas et ne lit plus le fichier après le premier `#include` fichier de l’unité de traduction. Il s’agit de l' *optimisation à plusieurs includes*. Elle a un effet similaire à l’idiome *include Guard* , qui utilise des définitions de macros de préprocesseur pour empêcher plusieurs inclusions du contenu du fichier. Il permet également d’éviter les violations de la *règle de définition*, l’exigence selon laquelle tous les modèles, types, fonctions et objets n’ont pas plus d’une définition dans votre code.

Par exemple :

```cpp
// header.h
#pragma once
// Code placed here is included only once per translation unit
```

Nous vous recommandons la directive `#pragma once` pour le nouveau code, car elle ne pollue pas l'espace de noms global avec un symbole de préprocesseur. Elle nécessite moins de frappe, est moins gênante et ne peut pas provoquer de *collisions de symboles*, erreurs provoquées lorsque des fichiers d’en-tête différents utilisent le même symbole de préprocesseur que la valeur de garde. Elle ne fait pas partie de la norme C++, mais elle est implémentée de façon portable par plusieurs compilateurs courants.

Il n’y a aucun avantage à utiliser l’idiome include Guard et `#pragma once` dans le même fichier. Le compilateur reconnaît l’idiome include Guard et implémente l’optimisation à plusieurs includes de la même façon que la `#pragma once` directive si aucun code sans commentaire ni aucune directive de préprocesseur n’est antérieur ou postérieur au formulaire standard de l’idiome :

```cpp
// header.h
// Demonstration of the #include guard idiom.
// Note that the defined symbol can be arbitrary.
#ifndef HEADER_H_     // equivalently, #if !defined HEADER_H_
#define HEADER_H_
// Code placed here is included only once per translation unit
#endif // HEADER_H_
```

Nous recommandons l’idiome include Guard lorsque le code doit être portable pour les compilateurs qui n’implémentent pas la `#pragma once` directive, pour maintenir la cohérence avec le code existant ou lorsque l’optimisation à plusieurs includes est impossible. Elle peut se produire dans des projets complexes lorsque l’alias de système de fichiers ou les chemins d’accès include avec alias empêchent le compilateur d’identifier les fichiers include identiques par un chemin d’accès canonique.

Veillez à ne pas utiliser `#pragma once` ou l’idiome include Guard dans les fichiers d’en-tête conçus pour être inclus plusieurs fois, qui utilisent des symboles de préprocesseur pour contrôler leurs effets. Pour obtenir un exemple de cette conception, consultez le \<assert.h> fichier d’en-tête. Veillez également à gérer vos chemins d’accès include pour éviter de créer plusieurs chemins d’accès aux fichiers inclus, ce qui peut nuire à l’optimisation de plusieurs includes pour les protecteurs include et `#pragma once` .

## <a name="see-also"></a>Voir aussi

[Directives Pragma et mot clé __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
