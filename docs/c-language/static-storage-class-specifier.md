---
title: Spécificateur de classe de stockage static │ Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- static variables, specifier
- storage classes, static
- static storage class specifiers
ms.assetid: 9bce361e-919b-46b9-8148-40d7ab0eb024
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8a7d61e39eb706721ddf936f88f5df02a6eddf96
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32386314"
---
# <a name="static-storage-class-specifier"></a>Spécificateur de classe de stockage static
Une variable déclarée au niveau interne avec le spécificateur de classe de stockage **static** a une durée de vie globale, mais est visible uniquement dans le bloc dans lequel elle est déclarée. Pour les chaînes constantes, l’utilisation de **static** est utile, car elle allège la surcharge liée à l’initialisation fréquente des fonctions souvent appelées.  
  
## <a name="remarks"></a>Notes  
Si vous n’initialisez pas explicitement une variable **static**, elle est initialisée sur 0 par défaut. Dans une fonction, **static** provoque l’allocation du stockage et sert de définition. Les variables statiques internes fournissent du stockage permanent, privé visible uniquement à une fonction unique.  
  
## <a name="see-also"></a>Voir aussi  
[Classes de stockage C](c-storage-classes.md)  
[Classes de stockage (C++)](../cpp/storage-classes-cpp.md)  