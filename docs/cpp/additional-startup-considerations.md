---
title: Considérations sur le démarrage supplémentaires | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- program startup [C++]
- startup code
- initializing before main
ms.assetid: 0e942aa6-8342-447c-b068-8980ed7622bd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c23f18a04010ba62d3651344464ff1668b2127d9
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/01/2018
ms.locfileid: "39405069"
---
# <a name="additional-startup-considerations"></a>Considérations supplémentaires sur le démarrage
En langage C++, la construction et la destruction d'objets peuvent impliquer l'exécution de code utilisateur. Par conséquent, il est important de comprendre quelles initialisations ont lieu avant l’entrée dans `main` et quels destructeurs sont appelés après la sortie de `main`. (Pour plus d’informations sur la construction et la destruction d’objets, consultez [constructeurs](../cpp/constructors-cpp.md) et [destructeurs](../cpp/destructors-cpp.md).)  
  
 Les initialisations suivantes ont lieu avant l’entrée dans `main`:  
  
-   Mise à zéro par défaut des données statiques. Toutes les données statiques sans initialiseurs explicites sont mises à zéro avant d'exécuter tout autre code, y compris l'initialisation du runtime. Les données membres statiques doivent encore être définies explicitement.  
  
-   Initialisation des objets statiques globaux dans une unité de traduction. Cela peut se produire avant l’entrée dans `main` ou avant la première utilisation d’une fonction ou un objet dans l’unité de traduction de l’objet.  
  
 **Section spécifique à Microsoft**  
  
 Dans Microsoft C++, les objets statiques globaux sont initialisés avant l’entrée dans `main`.  
  
 **FIN de la section spécifique à Microsoft**  
  
 Des objets statiques globaux mutuellement interdépendants mais figurant dans des unités de traduction distinctes peuvent provoquer un comportement incorrect.  
  
## <a name="see-also"></a>Voir aussi  
 [Démarrage et terminaison](../cpp/startup-and-termination-cpp.md)