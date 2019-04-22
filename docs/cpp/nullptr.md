---
title: nullptr
ms.date: 11/04/2016
f1_keywords:
- nullptr_cpp
helpviewer_keywords:
- nullptr keyword [C++]
ms.assetid: e9d80ea6-2506-4eb5-b47b-2349df085832
ms.openlocfilehash: 57be8d71f1dac4f347ea6567c02a385719bb7306
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58781079"
---
# <a name="nullptr"></a>nullptr

Désigne une constante de pointeur null du type `std::nullptr_t`, qui peut être convertie en tout type pointeur brut.  Bien que vous pouvez utiliser le mot clé **nullptr** sans inclure aucun en-tête, si votre code utilise le type `std::nullptr_t`, ensuite, vous devez la définir en incluant l’en-tête `<cstddef>`.

> [!NOTE]
>  Le **nullptr** mot clé est également défini en C / c++ / CLI pour les applications en code managé et n’est pas interchangeable avec le mot clé C++ de norme ISO. Si votre code peut être compilé à l’aide de la [/CLR](../build/reference/clr-common-language-runtime-compilation.md) option du compilateur qui cible le code managé, puis utilisez `__nullptr` dans n’importe quelle ligne de code où vous devez vous assurer que le compilateur utilise l’interprétation C++ native. Pour plus d’informations, consultez [nullptr](../extensions/nullptr-cpp-component-extensions.md).

## <a name="remarks"></a>Notes

Évitez d’utiliser la valeur NULL ou zéro (`0`) comme une constante pointeur null ; **nullptr** est moins vulnérable à une utilisation malveillante et fonctionne mieux dans la plupart des situations.  Par exemple, étant donné `func(std::pair<const char *, double>)`, l'appel à `func(std::make_pair(NULL, 3.14))` provoque une erreur du compilateur.  Étant donné que la macro NULL se développe en `0`, l’appel `std::make_pair(0, 3.14)` retourne `std::pair<int, double>`, qui n’est pas convertible au type de paramètre `std::pair<const char *, double>` de func().  L'appel à `func(std::make_pair(nullptr, 3.14))` entraîne une compilation correcte, car `std::make_pair(nullptr, 3.14)` retourne `std::pair<std::nullptr_t, double>`, qui peut être convertie en `std::pair<const char *, double>`.

## <a name="see-also"></a>Voir aussi

[Mots clés](../cpp/keywords-cpp.md)<br/>
[nullptr](../extensions/nullptr-cpp-component-extensions.md)(C++/CLI)