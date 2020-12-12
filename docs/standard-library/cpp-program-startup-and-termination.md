---
description: 'En savoir plus sur : démarrage et arrêt d’un programme C++'
title: C++, démarrage et terminaison de programme
ms.date: 11/04/2016
helpviewer_keywords:
- C++ Standard Library, program startup and termination
- terminating execution
- Function Main procedures
- control text streams
- startup code, and C++ program termination
- main function, program startup
ms.assetid: f72c8f76-f507-4ddd-a270-7b60f4fed625
ms.openlocfilehash: 644be6d4392f8e41b1d1cf7d45b484ed9903d463
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97324785"
---
# <a name="c-program-startup-and-termination"></a>C++, démarrage et terminaison de programme

Un programme C++ exécute les mêmes opérations qu’un programme C au démarrage et à l’arrêt du programme, plus quelques autres décrites ici.

Avant que l’environnement cible n’appelle la fonction `main` et une fois qu’il a stocké toutes les valeurs initiales constante spécifiées dans tous les objets qui ont une durée statique, le programme exécute tous les constructeurs restants pour ces objets statiques. L’ordre d’exécution n’est pas spécifié entre les unités de traduction, mais vous pouvez néanmoins supposer que certains objets [iostreams](../standard-library/iostreams-conventions.md) sont initialisés correctement pour être utilisés par ces constructeurs statiques. Ces flux de texte de contrôle sont :

- [cin](../standard-library/iostream.md#cin), pour une entrée standard.

- [cout](../standard-library/iostream.md#cout), pour une sortie standard.

- [cerr](../standard-library/iostream.md#cerr), pour une sortie d’erreur standard sans mémoire tampon.

- [clog](../standard-library/iostream.md#clog), pour une sortie d’erreur standard avec mémoire tampon.

Vous pouvez également utiliser ces objets dans les destructeurs appelés pour les objets statiques pendant l’arrêt du programme.

Comme avec C, le retour de `main` ou l’appel de `exit` appelle toutes les fonctions enregistrées avec `atexit` dans l’ordre inverse du Registre. Une exception levée par une de ces fonctions enregistrées appelle `terminate`.

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de la bibliothèque standard C++](../standard-library/cpp-standard-library-overview.md)\
[Sécurité des threads dans la bibliothèque C++ standard](../standard-library/thread-safety-in-the-cpp-standard-library.md)
