---
title: alloca | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 2b209335-e3a0-4934-93f0-3b5925d22918
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: a2bca8290e080c06e6cf6ec81a82a1ab9a7cb2d1
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2017
---
# <a name="alloca"></a>alloca
[_alloca](../c-runtime-library/reference/alloca.md) doit être de 16 octets alignée et utiliser un pointeur de frame.  
  
 La pile est allouée doit inclure l’espace en dessous pour les paramètres des fonctions appelées par la suite, comme indiqué dans [Allocation de piles](../build/stack-allocation.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de la pile](../build/stack-usage.md)