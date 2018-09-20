---
title: 1.3 modèle d’exécution | Microsoft Docs
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
ms.openlocfilehash: c284563a47d21abc9a1dacf045238449d64205d5
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46394008"
---
# <a name="13-execution-model"></a>1.3 Modèle d'exécution

OpenMP utilise le modèle de bifurcation-jointure de l’exécution en parallèle. Bien que ce modèle de bifurcation-jointure peut être utile pour résoudre de nombreux problèmes, il est quelque peu adaptée pour les grandes applications basée sur le tableau. OpenMP est destinée aux programmes de prise en charge qui seront exécutera correctement à la fois comme parallèle de programmes (plusieurs threads d’exécution et une bibliothèque de prise en charge OpenMP complète) et en tant que programmes séquentiels (directives ignorées et une bibliothèque de stubs OpenMP simple). Toutefois, il est possible et autorisés à développer un programme qui ne se comporte pas correctement lors de l’exécution de manière séquentielle. En outre, différents degrés de parallélisme peuvent entraîner des résultats numériques différents en raison de modifications dans l’association d’opérations numériques. Par exemple, une réduction de la série d’addition peut avoir un modèle différent d’associations d’ajout à une réduction en parallèle. Ces différentes associations peuvent changer les résultats de l’addition à virgule flottante.

Un programme écrit avec l’API C/C++ OpenMP commence à s’exécuter en tant qu’un seul thread d’exécution appelé le *maître thread*. Le thread principal s’exécute dans une région série jusqu'à ce que la première construction parallèle est rencontrée. Dans l’API OpenMP C/C++, le **parallèles** directive constitue une construction parallèle. Lorsqu’une construction parallèle est rencontrée, le thread principal crée une équipe de threads et le maître devient le maître de l’équipe. Chaque thread dans l’équipe exécute les instructions de l’extension dynamique d’une région parallèle, sauf pour les constructions de partage de travail. Constructions de partage de travail doivent être rencontrées par tous les threads dans l’équipe dans le même ordre, et les instructions dans le bloc structuré associé sont exécutées par un ou plusieurs threads. Le cloisonnement impliqué à la fin d’une construction de partage de travail sans un `nowait` clause est exécutée par tous les threads dans l’équipe.

Si un thread modifie un objet partagé, elle affecte non seulement son propre environnement d’exécution, mais aussi celles des autres threads dans le programme. La modification est garantie être complète, à partir du point de vue d’un des autres threads, au point de séquence suivant (comme défini dans la langue de base) uniquement si l’objet est déclaré comme étant volatile. Sinon, la modification est garantie comme étant terminée une fois que tout d’abord la modification des threads, et puis (ou simultanément) rencontrez d’autres threads, un **vider** directive qui spécifie l’objet (implicitement ou explicitement). Notez que lorsque le **vider** directives sont implicites par d’autres directives OpenMP ne sont pas suffisantes pour garantir l’ordre souhaité des effets secondaires, il est la responsabilité du programmeur pour fournir supplémentaires, explicite  **vider** directives.

À l’achèvement de la construction parallèle, les threads dans l’équipe synchroniser à une barrière implicite, et seul le thread principal continue l’exécution. N’importe quel nombre de constructions parallèle peut être spécifié dans un seul programme. Par conséquent, un programme peut répliquer et joindre autant de fois pendant l’exécution.

L’API C/C++ OpenMP permet aux programmeurs d’utiliser des directives dans les fonctions appelées à partir de constructions parallèles. Les directives qui n’apparaissent pas dans l’étendue lexicale d’une construction parallèle, mais peuvent se trouver dans l’étendue dynamique sont appelés *orphelins* directives. Directives orphelins permettent aux programmeurs de la capacité d’exécuter des parties principales de leur programme en parallèle avec des modifications minimes uniquement pour le programme séquentiel. Avec cette fonctionnalité, les utilisateurs peuvent les constructions parallèles à des niveaux supérieurs de l’arborescence des appels programme de code et utiliser des directives pour contrôler l’exécution dans les fonctions appelées.

Fonctions qui écrivent dans le même fichier de sortie dans lequel les données écrites par différents threads s’affiche dans un ordre non déterministe peuvent entraîner de sortie des appels non synchronisés à C et C++. De même, les appels non synchronisés à entrer des fonctions qui lisent à partir du même fichier peuvent lire les données dans un ordre non déterministe. Utilisation non synchronisée d’e/s, telle que chaque thread accède à un autre fichier, produit les mêmes résultats que l’exécution en série des fonctions d’e/s.