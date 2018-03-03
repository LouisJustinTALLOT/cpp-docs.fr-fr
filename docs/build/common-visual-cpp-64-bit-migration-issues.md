---
title: "Les problèmes courants de Migration de 64 bits de Visual C++ | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- 64-bit programming [C++], migration
- 64-bit compiler [C++], migration
- porting 32-bit code to 64-bit code
- upgrading Visual C++ applications, 32-bit code
- migration [C++], 64-bit code issues
- 32-bit code porting [C++]
- 64-bit applications [C++]
- 64-bit compiler [C++], porting 32-bit code
- Win64 [C++]
ms.assetid: d17fb838-7513-4e2d-8b27-a1666f17ad76
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b9ea3690e04106f0836d236eefee4acd9dda3a82
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="common-visual-c-64-bit-migration-issues"></a>Problèmes courants de migration vers Visual C++ 64 bits

Quand vous utilisez Visual C++ pour créer des applications destinées à s'exécuter sur un système d'exploitation Windows 64 bits, tenez compte des points suivants :  
  
-   `int` et `long` sont des valeurs 32 bits sur les systèmes d'exploitation Windows 64 bits. Pour les programmes que vous prévoyez de compiler pour des plateformes 64 bits, veillez à ne pas assigner de pointeurs à des variables 32 bits. Les pointeurs sont des valeurs 64 bits sur les plateformes 64 bits et vous tronquerez la valeur d'un pointeur si vous l'assignez à une variable 32 bits.  
  
-   `size_t`, `time_t`, et `ptrdiff_t` sont des valeurs 64 bits sur les systèmes d’exploitation Windows 64 bits.  
  
-   `time_t` est une valeur 32 bits sur les systèmes d'exploitation Windows 32 bits dans les versions de Visual C++ antérieures à Visual C++ 2005. `time_t` est maintenant un entier 64 bits par défaut. Pour plus d’informations, consultez [gestion du temps](../c-runtime-library/time-management.md).  
  
     Vous devez savoir dans quels cas votre code prend une valeur `int` et la traite comme une valeur `size_t` ou `time_t`. En effet, le nombre peut augmenter au point de dépasser la taille d'un nombre 32 bits. Dans ce cas, les données sont tronquées quand elles sont renvoyées vers le stockage `int`.  
  
Le modificateur %x (format `int` hexadécimal) `printf` ne fonctionne pas comme prévu sur un système d'exploitation Windows 64 bits. Il ne fonctionne que sur les 32 premiers bits de la valeur qui lui est passée.  
  
-   Utilisez %I32x pour afficher un type intégral 32 bits au format hexadécimal.  
  
-   Utilisez %I64x pour afficher un type intégral 64 bits au format hexadécimal.  
  
-   Le %p (format hexadécimal pour un pointeur) fonctionnera comme prévu sur un système d'exploitation Windows 64 bits.  
  
Pour plus d'informations, voir :  
  
-   [Options du compilateur](../build/reference/compiler-options.md)  
  
-   [Conseils de migration](http://msdn.microsoft.com/library/windows/desktop/aa384214)  
  
## <a name="see-also"></a>Voir aussi  

[Configurer Visual C++ pour 64 bits, x64 cibles](../build/configuring-programs-for-64-bit-visual-cpp.md)   
[Guide du portage et de la mise à niveau de Visual C++](../porting/visual-cpp-porting-and-upgrading-guide.md)