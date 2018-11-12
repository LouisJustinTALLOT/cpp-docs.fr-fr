---
title: Erreur du compilateur C2558
ms.date: 11/04/2016
f1_keywords:
- C2558
helpviewer_keywords:
- C2558
ms.assetid: 822b701e-dcae-423a-b21f-47f36aff9c90
ms.openlocfilehash: b0dca0b19d427cf83238c824739d288a1cfd54d4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50571728"
---
# <a name="compiler-error-c2558"></a>Erreur du compilateur C2558

'identificateur' : pas de constructeur de copie disponible ou le constructeur de copie est déclaré 'explicit'

Un constructeur de copie initialise un objet d'un autre objet de même type. (Il fait une copie de l'objet.) Le compilateur génère un constructeur de copie par défaut si vous ne définissez pas de constructeur.

### <a name="to-fix-this-error"></a>Pour corriger cette erreur

1. Le problème peut se produire lors d'une tentative de copie d'une classe dont le constructeur de copie est `private`. Le plus souvent, une classe qui a un constructeur de copie `private` ne doit pas être copiée. Une technique de programmation classique déclare un constructeur de copie `private` pour éviter l'utilisation directe d'une classe. La classe peut être inutile en tant que telle ou nécessiter une autre classe afin de fonctionner correctement.

   Si vous pensez que l'utilisation d'une classe qui a un constructeur de copie `private` ne présente aucun risque, dérivez une nouvelle classe à partir de la classe ayant le constructeur `private` et mettez un constructeur de copie `public` ou `protected` à la disposition de la nouvelle classe. Utilisez la classe dérivée à la place de l'original.

1. Le problème peut se produire lors d'une tentative de copie d'une classe dont le constructeur de copie est explicite. La déclaration d'un constructeur de copie comme `explicit` évite le passage ou le retour d'objets d'une classe depuis ou vers les fonctions. Pour plus d’informations sur les constructeurs explicites, consultez [les Conversions de types définis par l’utilisateur](../../cpp/user-defined-type-conversions-cpp.md).

1. Le problème peut se produire lors d'une tentative de copie d'une instance de classe déclarée `const` à l'aide d'un constructeur de copie qui n'accepte pas de paramètre de référence `const`. Déclarez votre constructeur de copie avec une référence de type `const` au lieu d'une référence de type non const.