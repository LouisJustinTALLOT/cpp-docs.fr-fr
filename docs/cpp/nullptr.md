---
title: nullptr
ms.date: 11/04/2016
f1_keywords:
- nullptr_cpp
helpviewer_keywords:
- nullptr keyword [C++]
ms.assetid: e9d80ea6-2506-4eb5-b47b-2349df085832
ms.openlocfilehash: 223f4c3e8c838698f9716e241543db405c9394af
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80177766"
---
# <a name="nullptr"></a>nullptr

Désigne une constante de pointeur null du type `std::nullptr_t`, qui peut être convertie en tout type pointeur brut.  Bien que vous puissiez utiliser le mot clé **nullptr** sans inclure d’en-tête, si votre code utilise le type `std::nullptr_t`, vous devez le définir en incluant l’en-tête `<cstddef>`.

> [!NOTE]
>  Le mot clé **nullptr** est également défini C++dans/CLI pour les applications de code managé et n’est pas interchangeable C++ avec le mot clé ISO standard. Si votre code peut être compilé à l’aide de l’option du compilateur [/CLR](../build/reference/clr-common-language-runtime-compilation.md) , qui cible le code managé, utilisez `__nullptr` dans n’importe quelle ligne de code où vous devez vous assurer C++ que le compilateur utilise l’interprétation native. Pour plus d’informations, consultez [nullptr](../extensions/nullptr-cpp-component-extensions.md).

## <a name="remarks"></a>Notes

Évitez d’utiliser NULL ou zéro (`0`) comme constante de pointeur null ; **nullptr** est moins vulnérable aux utilisations abusives et fonctionne mieux dans la plupart des situations.  Par exemple, étant donné `func(std::pair<const char *, double>)`, l'appel à `func(std::make_pair(NULL, 3.14))` provoque une erreur du compilateur.  Étant donné que la macro NULL se développe en `0`, l’appel `std::make_pair(0, 3.14)` retourne `std::pair<int, double>`, qui n’est pas convertible au type de paramètre `std::pair<const char *, double>` de func().  L'appel à `func(std::make_pair(nullptr, 3.14))` entraîne une compilation correcte, car `std::make_pair(nullptr, 3.14)` retourne `std::pair<std::nullptr_t, double>`, qui peut être convertie en `std::pair<const char *, double>`.

## <a name="see-also"></a>Voir aussi

[Mots clés](../cpp/keywords-cpp.md)<br/>
[nullptr](../extensions/nullptr-cpp-component-extensions.md)(C++/CLI)
