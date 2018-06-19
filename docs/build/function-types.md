---
title: Types de fonction | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 7e33d5f4-dabb-406d-afb3-13777b995028
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 322bd45abbfe217671fd39f0617987fde21445db
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32367649"
---
# <a name="function-types"></a>Types de fonctions
Il existe deux types de fonctions. Une fonction qui nécessite un frame de pile est appelée une fonction de frame. Une fonction qui ne nécessite pas un frame de pile est appelée une fonction de la feuille.  
  
 Une fonction de frame est une fonction qui alloue de l’espace de pile, appelle d’autres fonctions, enregistre les registres non volatils ou utilise la gestion des exceptions. Elle requiert également une entrée de la fonction table. Une fonction de frame exige un prologue et un épilogue. Une fonction de frame peut allouer dynamiquement de l’espace de pile et peut utiliser un pointeur de frame. Une fonction de frame a toutes les fonctionnalités de cette norme d’appel à sa disposition.  
  
 Si une fonction de frame n’appelle pas une autre fonction, il n’est pas nécessaire d’aligner la pile (référencé dans la Section [Allocation de piles](../build/stack-allocation.md)).  
  
 Une feuille est une fonction qui ne requiert pas une entrée de la fonction table. Il ne peut pas modifier les registres non volatils, y compris RSP, ce qui signifie qu’il ne peut pas appeler des fonctions ou allouer de l’espace de pile. Il est autorisé à laisser la pile non alignée lors de son exécution.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de la pile](../build/stack-usage.md)
