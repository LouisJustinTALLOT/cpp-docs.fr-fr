---
title: "Spécificateur de classe de stockage static │ Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- static variables, specifier
- storage classes, static
- static storage class specifiers
ms.assetid: 9bce361e-919b-46b9-8148-40d7ab0eb024
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c957b78eeb506e9f1f91a670cf5cc4d52ad72878
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="static-storage-class-specifier"></a>Spécificateur de classe de stockage static
Une variable déclarée au niveau interne avec le spécificateur de classe de stockage **static** a une durée de vie globale, mais est visible uniquement dans le bloc dans lequel elle est déclarée. Pour les chaînes constantes, l’utilisation de **static** est utile, car elle allège la surcharge liée à l’initialisation fréquente des fonctions souvent appelées.  
  
## <a name="remarks"></a>Notes  
Si vous n’initialisez pas explicitement une variable **static**, elle est initialisée sur 0 par défaut. Dans une fonction, **static** provoque l’allocation du stockage et sert de définition. Les variables statiques internes fournissent du stockage permanent, privé visible uniquement à une fonction unique.  
  
## <a name="see-also"></a>Voir aussi  
[Classes de stockage C](c-storage-classes.md)  
[Classes de stockage (C++)](../cpp/storage-classes-cpp.md)  