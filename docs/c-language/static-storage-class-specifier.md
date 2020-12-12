---
description: 'En savoir plus sur : spécificateur de Storage-Class statique'
title: Spécificateur de classe de stockage static
ms.date: 11/04/2016
helpviewer_keywords:
- static variables, specifier
- storage classes, static
- static storage class specifiers
ms.assetid: 9bce361e-919b-46b9-8148-40d7ab0eb024
ms.openlocfilehash: da7ca4ea71b3e450da986ec175adcaf08852d81b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97168746"
---
# <a name="static-storage-class-specifier"></a>Spécificateur de classe de stockage static

Une variable déclarée au niveau interne avec le **`static`** spécificateur de classe de stockage a une durée de vie globale, mais elle est visible uniquement dans le bloc dans lequel elle est déclarée. Pour les chaînes constantes, l’utilisation de **`static`** est utile, car elle allège la surcharge liée à l’initialisation fréquente dans les fonctions souvent appelées.

## <a name="remarks"></a>Notes

Si vous n’initialisez pas explicitement une **`static`** variable, elle est initialisée à 0 par défaut. Dans une fonction, le **`static`** stockage est alloué et sert de définition. Les variables statiques internes fournissent du stockage permanent, privé visible uniquement à une fonction unique.

## <a name="see-also"></a>Voir aussi

[Classes de stockage C](c-storage-classes.md)<br/>
[Classes de stockage (C++)](../cpp/storage-classes-cpp.md)
