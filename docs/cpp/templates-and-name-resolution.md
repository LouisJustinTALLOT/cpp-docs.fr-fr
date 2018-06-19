---
title: Modèles et résolution de noms | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 519ba7b5-cd25-4549-865a-9a7b9dffdc28
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2b27f6f7f56604976bb1004594fc7c0ac6fdc923
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32422811"
---
# <a name="templates-and-name-resolution"></a>Modèles et résolution de noms

Dans les définitions de modèle, il existe trois types de noms :  
  
-   les noms déclarés localement, notamment le nom du modèle lui-même et tous les noms déclarés dans la définition de modèle ;  
  
-   les noms provenant de la portée englobante située en dehors de la définition de modèle ;  
  
-   les noms qui dépendent d’une certaine façon des arguments template, appelés noms dépendants.  
  
 Alors que les deux premiers noms concernent aussi des portées de classe et de fonction, des règles spécifiques de résolution de noms sont requises dans les définitions de modèle pour gérer la complexité ajouté des noms dépendants. Cela provient du fait que le compilateur connaît peu ces noms avant que le modèle ne soit instancié car il peut s'agir de types complètement différents selon les arguments template utilisés. Les noms non dépendants sont recherchés selon les règles classiques et au point de définition du modèle. Ces noms, qui sont indépendants des arguments template, sont recherchés une fois pour toutes les spécialisations de modèle. Les noms dépendants ne sont pas recherchés tant que le modèle n'est pas instancié et sont recherchés séparément pour chaque spécialisation.  
  
 Un type est dépendant s’il dépend des arguments template. En particulier un type est dépendant s'il s'agit :  
  
-   de l'argument template lui-même ;  
  
    ```cpp
    T  
    ```  
  
-   d'un nom complet avec une qualification comprenant un type dépendant ;  
  
    ```cpp
    T::myType  
    ```  
  
-   d'un nom complet si la partie non qualifiée identifie un type dépendant ;  
  
    ```cpp
    N::T  
    ```  
  
-   d'un type const ou volatile pour lequel le type de base est un type dépendant ;  
  
    ```cpp
    const T  
    ```  
  
-   d'un type pointeur, référence, tableau ou pointeur de fonction basé sur un type dépendant :  
  
    ```cpp
    T *, T &, T [10], T (*)()  
    ```  
  
-   d'un tableau dont la taille est basée sur un paramètre de modèle :  
  
    ```cpp
    template <int arg> class X {  
    int x[arg] ; // dependent type  
    }  
    ```  
  
-   d'un type modèle construit à partir d'un modèle de paramètre :  
  
    ```cpp
    T<int>, MyTemplate<T>  
    ```  
  
## <a name="type-dependence-and-value-dependence"></a>Dépendance de type et dépendance de valeur

 Les noms et les expressions dépendants d’un paramètre de modèle sont classés comme dépendant de type ou dépendant de valeur selon que le paramètre de modèle est un paramètre de type ou un paramètre de valeur. En outre, tous les identificateurs déclarés dans un modèle avec un type dépendant de l'argument template sont considérés comme dépendants de valeur, étant donné qu'un type intégral ou énumération est initialisé avec une expression dépendante de valeur.  
  
 Les expressions dépendantes de type et de valeur sont des expressions qui impliquent des variables qui dépendent de type ou de valeur. Ces expressions peuvent avoir une sémantique qui diffère selon les paramètres utilisés pour le modèle.  
  
## <a name="see-also"></a>Voir aussi

 [Modèles](../cpp/templates-cpp.md)
