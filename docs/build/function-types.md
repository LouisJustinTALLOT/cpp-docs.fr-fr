---
title: Types de fonctions
ms.date: 11/04/2016
ms.assetid: 7e33d5f4-dabb-406d-afb3-13777b995028
ms.openlocfilehash: 22778f3eaefa6dbcf5f85e54c0940867ef52ab72
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50526375"
---
# <a name="function-types"></a>Types de fonctions

Il existe essentiellement deux types de fonctions. Une fonction qui nécessite un frame de pile est appelée une fonction de frame. Une fonction qui ne nécessite pas d’un frame de pile est appelée une fonction de la feuille.

Une fonction de frame est une fonction qui alloue de l’espace de pile, appelle d’autres fonctions, enregistre les registres non volatils ou utilise la gestion des exceptions. Elle requiert également une entrée de table de fonction. Une fonction de frame exige un prologue et un épilogue. Une fonction de frame peut allouer dynamiquement de l’espace de pile et pouvez employer un pointeur de frame. Une fonction de frame a toutes les fonctionnalités de cet appel standard à sa disposition.

Si une fonction de frame n’appelle pas une autre fonction, il n’est pas nécessaire d’aligner la pile (référencé dans la Section [Allocation de piles](../build/stack-allocation.md)).

Une feuille est une fonction qui ne nécessite pas une entrée de table de fonction. Il ne peut pas apporter des modifications pour les registres non volatils, y compris RSP, ce qui signifie qu’il ne peut pas appeler des fonctions ou allouer de l’espace de pile. Il est autorisé à laisser la pile non alignés lors de son exécution.

## <a name="see-also"></a>Voir aussi

[Utilisation de la pile](../build/stack-usage.md)
