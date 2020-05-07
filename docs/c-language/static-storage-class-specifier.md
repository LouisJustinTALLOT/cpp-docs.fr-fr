---
title: Spécificateur de classe de stockage static
ms.date: 11/04/2016
helpviewer_keywords:
- static variables, specifier
- storage classes, static
- static storage class specifiers
ms.assetid: 9bce361e-919b-46b9-8148-40d7ab0eb024
ms.openlocfilehash: ef85ee4d757cb9579431427fba7b46a0e5ac905f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62157940"
---
# <a name="static-storage-class-specifier"></a>Spécificateur de classe de stockage static

Une variable déclarée au niveau interne avec le spécificateur de classe de stockage **static** a une durée de vie globale, mais est visible uniquement dans le bloc dans lequel elle est déclarée. Pour les chaînes constantes, l’utilisation de **static** est utile, car elle allège la surcharge liée à l’initialisation fréquente des fonctions souvent appelées.

## <a name="remarks"></a>Notes 

Si vous n’initialisez pas explicitement une variable **static**, elle est initialisée sur 0 par défaut. Dans une fonction, **static** provoque l’allocation du stockage et sert de définition. Les variables statiques internes fournissent du stockage permanent, privé visible uniquement à une fonction unique.

## <a name="see-also"></a>Voir aussi

[Classes de stockage C](c-storage-classes.md)<br/>
[Classes de stockage (C++)](../cpp/storage-classes-cpp.md)
