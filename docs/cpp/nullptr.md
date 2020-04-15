---
title: nullptr
ms.date: 11/04/2016
f1_keywords:
- nullptr_cpp
helpviewer_keywords:
- nullptr keyword [C++]
ms.assetid: e9d80ea6-2506-4eb5-b47b-2349df085832
ms.openlocfilehash: 51df20ea00e5dd77ab1fc1a2a01253b8f788ad0a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81358856"
---
# <a name="nullptr"></a>nullptr

Désigne une constante de pointeur null du type `std::nullptr_t`, qui peut être convertie en tout type pointeur brut.  Bien que vous puissiez utiliser le mot clé **nullptr** sans `std::nullptr_t`inclure d’en-têtes, `<cstddef>`si votre code utilise le type , alors vous devez le définir en incluant l’en-tête .

> [!NOTE]
> Le mot clé **nullptr** est également défini dans le CMD/CLI pour les applications de code gérée et n’est pas interchangeable avec le mot clé ISO Standard CMD. Si votre code peut être compilé en utilisant l’option [compilateur /clr,](../build/reference/clr-common-language-runtime-compilation.md) qui cible le code géré, puis utiliser `__nullptr` dans n’importe quelle ligne de code où vous devez garantir que le compilateur utilise l’interprétation native C . Pour plus d’informations, voir [nullptr](../extensions/nullptr-cpp-component-extensions.md).

## <a name="remarks"></a>Notes

Évitez d’utiliser`0`NULL ou zéro ( ) comme une constante pointeur nul; **nullptr** est moins vulnérable à l’utilisation abusive et fonctionne mieux dans la plupart des situations.  Par exemple, étant donné `func(std::pair<const char *, double>)`, l'appel à `func(std::make_pair(NULL, 3.14))` provoque une erreur du compilateur.  Étant donné que la macro NULL se développe en `0`, l’appel `std::make_pair(0, 3.14)` retourne `std::pair<int, double>`, qui n’est pas convertible au type de paramètre `std::pair<const char *, double>` de func().  L'appel à `func(std::make_pair(nullptr, 3.14))` entraîne une compilation correcte, car `std::make_pair(nullptr, 3.14)` retourne `std::pair<std::nullptr_t, double>`, qui peut être convertie en `std::pair<const char *, double>`.

## <a name="see-also"></a>Voir aussi

[Mots clés](../cpp/keywords-cpp.md)<br/>
[nullptr](../extensions/nullptr-cpp-component-extensions.md)(C/CLI)
