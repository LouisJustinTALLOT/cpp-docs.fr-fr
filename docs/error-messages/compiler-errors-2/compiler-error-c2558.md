---
title: Erreur du compilateur C2558
ms.date: 11/04/2016
f1_keywords:
- C2558
helpviewer_keywords:
- C2558
ms.assetid: 822b701e-dcae-423a-b21f-47f36aff9c90
ms.openlocfilehash: 2504b42f49ccb040f676f0aead8f243d33c7dd1a
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87207743"
---
# <a name="compiler-error-c2558"></a>Erreur du compilateur C2558

'identificateur' : pas de constructeur de copie disponible ou le constructeur de copie est déclaré 'explicit'

Un constructeur de copie initialise un objet d'un autre objet de même type. (Il effectue une copie de l’objet.) Le compilateur génère un constructeur de copie par défaut si vous ne définissez pas de constructeurs.

### <a name="to-fix-this-error"></a>Pour corriger cette erreur

1. Le problème peut se produire lors d’une tentative de copie d’une classe dont le constructeur de copie est **`private`** . Dans la plupart des cas, une classe qui a un **`private`** constructeur de copie ne doit pas être copiée. Une technique de programmation courante déclare un **`private`** constructeur de copie pour empêcher l’utilisation directe d’une classe. La classe peut être inutile en tant que telle ou nécessiter une autre classe afin de fonctionner correctement.

   Si vous déterminez qu’il est possible d’utiliser une classe qui a un constructeur de copie en toute sécurité **`private`** , dérivez une nouvelle classe de la classe qui a le **`private`** constructeur et rendez un **`public`** constructeur de **`protected`** copie ou disponible dans la nouvelle classe. Utilisez la classe dérivée à la place de l'original.

1. Le problème peut se produire lors d'une tentative de copie d'une classe dont le constructeur de copie est explicite. La déclaration d’un constructeur de copie comme **`explicit`** empêche le passage ou le retour d’objets d’une classe vers/à partir de fonctions. Pour plus d’informations sur les constructeurs explicites, consultez [conversions de types définis par l’utilisateur](../../cpp/user-defined-type-conversions-cpp.md).

1. Le problème peut se produire lorsqu’une tentative est faite pour copier une instance de classe déclarée à **`const`** l’aide d’un constructeur de copie qui ne prend pas de **`const`** paramètre de référence. Déclarez votre constructeur de copie avec une **`const`** référence de type au lieu d’une référence de type non const.
