---
title: Considérations supplémentaires sur le démarrage
ms.date: 11/04/2016
helpviewer_keywords:
- program startup [C++]
- startup code
- initializing before main
ms.assetid: 0e942aa6-8342-447c-b068-8980ed7622bd
ms.openlocfilehash: 16e48f2e4f7544d28a1bea00e1fdf2d1cff397b5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62385074"
---
# <a name="additional-startup-considerations"></a>Considérations supplémentaires sur le démarrage

En langage C++, la construction et la destruction d'objets peuvent impliquer l'exécution de code utilisateur. Par conséquent, il est important de comprendre quelles initialisations ont lieu avant l’entrée dans `main` et quels destructeurs sont appelés après la sortie de `main`. (Pour plus d’informations sur la construction et la destruction d’objets, consultez [constructeurs](../cpp/constructors-cpp.md) et [destructeurs](../cpp/destructors-cpp.md).)

Les initialisations suivantes ont lieu avant l’entrée dans `main`:

- Mise à zéro par défaut des données statiques. Toutes les données statiques sans initialiseurs explicites sont mises à zéro avant d'exécuter tout autre code, y compris l'initialisation du runtime. Les données membres statiques doivent encore être définies explicitement.

- Initialisation des objets statiques globaux dans une unité de traduction. Cela peut se produire avant l’entrée dans `main` ou avant la première utilisation d’une fonction ou un objet dans l’unité de traduction de l’objet.

**Section spécifique à Microsoft**

Dans Microsoft C++, les objets statiques globaux sont initialisés avant l’entrée dans `main`.

**FIN de la section spécifique à Microsoft**

Des objets statiques globaux mutuellement interdépendants mais figurant dans des unités de traduction distinctes peuvent provoquer un comportement incorrect.

## <a name="see-also"></a>Voir aussi

[Démarrage et terminaison](../cpp/startup-and-termination-cpp.md)