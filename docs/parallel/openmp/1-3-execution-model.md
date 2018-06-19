---
title: 1.3 modèle d’exécution | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 85ae8bc4-5bf0-45e0-a45f-02de9adaf716
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0acdd7a5d9f2dcb58850254281b5c18fd0d1123c
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33687892"
---
# <a name="13-execution-model"></a>1.3 Modèle d'exécution
OpenMP utilise le modèle de bifurcation-jointure de l’exécution en parallèle. Bien que ce modèle de bifurcation-jointure puisse être utile pour résoudre de nombreux problèmes, il est quelque peu conçu pour les grandes applications basées sur tableau. OpenMP est conçue pour la prise en charge des programmes qui seront exécute correctement à la fois comme parallèle programmes (plusieurs threads d’exécution et une bibliothèque de prise en charge OpenMP complète) et en tant que programmes séquentiels (directives ignorées et une bibliothèque de stubs OpenMP simple). Toutefois, il est possible et autorisé à développer un programme qui ne se comporte pas correctement lors de l’exécution de manière séquentielle. En outre, différents degrés de parallélisme peuvent entraîner des résultats numériques différents en raison de modifications dans l’association d’opérations numériques. Par exemple, une réduction de la série d’addition peut avoir un modèle différent des associations d’ajout à une réduction en parallèle. Ces différentes associations peuvent modifier les résultats de l’addition à virgule flottante.  
  
 Un programme écrit avec l’API de C/C++ OpenMP commence à s’exécuter comme un seul thread d’exécution appelé le *maître thread*. Le thread principal s’exécute dans une région de série jusqu'à ce que la première construction parallèle est rencontrée. Dans l’API C/C++ OpenMP, le **parallèles** directive constitue une construction parallèle. Lorsqu’une construction parallèle est trouvée, le thread principal crée une équipe de threads et le principal devient le maître de l’équipe. Chaque thread dans l’équipe exécute les instructions de l’extension dynamique d’une région parallèle, sauf pour les constructions de partage de travail. Constructions de partage de travail doivent être produites par tous les threads dans l’équipe dans le même ordre, et les instructions dans le bloc structuré associé sont exécutées par un ou plusieurs threads. Le cloisonnement impliqué à la fin d’une construction de partage de travail sans un `nowait` clause est exécutée par tous les threads dans l’équipe.  
  
 Si un thread modifie un objet partagé, elle affecte non seulement son propre environnement d’exécution, mais aussi celles des autres threads dans le programme. La modification est garantie être terminée, à partir du point de vue de l’un des autres threads, au point de séquence suivant (comme défini dans la langue de base) uniquement si l’objet est déclaré comme étant volatile. Dans le cas contraire, la modification est garantie être terminée après tout d’abord la modification de thread, et puis (ou simultanément) rencontrer d’autres threads, un **vider** directive qui spécifie l’objet (implicitement ou explicitement). Notez que lorsque la **vider** directives sont implicites par d’autres directives OpenMP ne sont pas suffisantes pour garantir l’ordre souhaité des effets secondaires, il est la responsabilité du programmeur pour fournir supplémentaires, explicite  **vider** directives.  
  
 À la fin de la construction parallèle, les threads de l’équipe de se synchronisent à une barrière implicite, et uniquement sur le thread principal continue l’exécution. N’importe quel nombre de constructions parallèle peut être spécifié dans un seul programme. Par conséquent, un programme peut effectuer un branchement et joindre autant de fois pendant l’exécution.  
  
 L’API de C/C++ OpenMP permet aux programmeurs d’utiliser les directives dans les fonctions appelées depuis parallèles. Les directives qui n’apparaissent pas dans l’étendue lexicale d’une construction parallèle, mais peuvent se trouver dans l’étendue dynamique sont appelés *orphelins* directives. Directives orphelins permettent aux programmeurs pour exécuter les principales parties de leur programme en parallèle avec des modifications minimes uniquement au programme séquentiel. Avec cette fonctionnalité, les utilisateurs peuvent parallèles sur les niveaux supérieurs de l’arborescence des appels de programme de code et utiliser des directives pour contrôler l’exécution dans les fonctions appelées.  
  
 Fonctions qui écrivent dans le même fichier de sortie dans lequel les données écrites par différents threads apparaissent dans un ordre non déterministe peuvent entraîner de sortie des appels non synchronisés pour C et C++. De même, les appels non synchronisées à l’entrée des fonctions qui lisent à partir du même fichier peuvent lire des données dans un ordre non déterministe. Utilisation non synchronisée d’e/s, telle que chaque thread accède à un autre fichier, produit les mêmes résultats que l’exécution séquentielle de fonctions d’e/s.