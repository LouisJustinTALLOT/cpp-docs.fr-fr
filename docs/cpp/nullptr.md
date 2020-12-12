---
description: 'En savoir plus sur les éléments suivants : nullptr'
title: nullptr
ms.date: 07/22/2020
f1_keywords:
- nullptr_cpp
helpviewer_keywords:
- nullptr keyword [C++]
ms.assetid: e9d80ea6-2506-4eb5-b47b-2349df085832
ms.openlocfilehash: 8d7eb3a578addc14b85c53c50ab81c6e5592d541
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97146150"
---
# <a name="nullptr"></a>nullptr

Le **`nullptr`** mot clé spécifie une constante de pointeur null de type `std::nullptr_t` , qui est convertible en n’importe quel type de pointeur brut.  Bien que vous puissiez utiliser le mot clé **`nullptr`** sans inclure d’en-tête, si votre code utilise le type `std::nullptr_t` , vous devez le définir en incluant l’en-tête `<cstddef>` .

> [!NOTE]
> Le **`nullptr`** mot clé est également défini en C++/CLI pour les applications de code managé et n’est pas interchangeable avec le mot clé ISO C++ standard. Si votre code peut être compilé à l’aide de l' [`/clr`](../build/reference/clr-common-language-runtime-compilation.md) option du compilateur, qui cible le code managé, utilisez `__nullptr` dans n’importe quelle ligne de code où vous devez vous assurer que le compilateur utilise l’interprétation C++ native. Pour plus d’informations, consultez [ `nullptr` (c++/CLI et c++/CX)](../extensions/nullptr-cpp-component-extensions.md).

## <a name="remarks"></a>Notes

Évitez d’utiliser `NULL` ou zéro ( `0` ) comme constante de pointeur null ; **`nullptr`** est moins vulnérable à une utilisation incorrecte et fonctionne mieux dans la plupart des situations.  Par exemple, étant donné `func(std::pair<const char *, double>)`, l'appel à `func(std::make_pair(NULL, 3.14))` provoque une erreur du compilateur.  La macro `NULL` se développe en `0` , afin que l’appel `std::make_pair(0, 3.14)` retourne `std::pair<int, double>` , qui n’est pas convertible en `std::pair<const char *, double>` type de paramètre dans `func` .  L'appel à `func(std::make_pair(nullptr, 3.14))` entraîne une compilation correcte, car `std::make_pair(nullptr, 3.14)` retourne `std::pair<std::nullptr_t, double>`, qui peut être convertie en `std::pair<const char *, double>`.

## <a name="see-also"></a>Voir aussi

[Mots clés](../cpp/keywords-cpp.md)<br/>
[`nullptr` (C++/CLI et C++/CX)](../extensions/nullptr-cpp-component-extensions.md)
