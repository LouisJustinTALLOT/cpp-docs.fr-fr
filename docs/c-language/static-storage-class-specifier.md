---
title: Spécificateur de classe de stockage static
ms.date: 11/04/2016
helpviewer_keywords:
- static variables, specifier
- storage classes, static
- static storage class specifiers
ms.assetid: 9bce361e-919b-46b9-8148-40d7ab0eb024
ms.openlocfilehash: e84e2745c6077f038f47295119936a1ad6431bdd
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87229491"
---
# <a name="static-storage-class-specifier"></a>Spécificateur de classe de stockage static

Une variable déclarée au niveau interne avec le **`static`** spécificateur de classe de stockage a une durée de vie globale, mais elle est visible uniquement dans le bloc dans lequel elle est déclarée. Pour les chaînes constantes, l’utilisation de **`static`** est utile, car elle allège la surcharge liée à l’initialisation fréquente dans les fonctions souvent appelées.

## <a name="remarks"></a>Notes

Si vous n’initialisez pas explicitement une **`static`** variable, elle est initialisée à 0 par défaut. Dans une fonction, le **`static`** stockage est alloué et sert de définition. Les variables statiques internes fournissent du stockage permanent, privé visible uniquement à une fonction unique.

## <a name="see-also"></a>Voir aussi

[Classes de stockage C](c-storage-classes.md)<br/>
[Classes de stockage (C++)](../cpp/storage-classes-cpp.md)
