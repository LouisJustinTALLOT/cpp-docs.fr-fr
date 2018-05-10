---
title: C++, démarrage et arrêt du programme | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- C++ Standard Library, program startup and termination
- terminating execution
- Function Main procedures
- control text streams
- startup code, and C++ program termination
- main function, program startup
ms.assetid: f72c8f76-f507-4ddd-a270-7b60f4fed625
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f781df914384b553c53e5c42fe16d4c74c9ef99d
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
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

[Vue d’ensemble de la bibliothèque standard C++](../standard-library/cpp-standard-library-overview.md)<br/>
[Sécurité des threads dans la bibliothèque standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
