---
title: Boxing (C++ / c++ / CX) | Microsoft Docs
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: language-reference
ms.assetid: edfb12fa-2a9b-42f6-bdac-d4d76cb8274e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7e9ab84bf840f01fbb22ef3b2510056338d10c74
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44108375"
---
# <a name="boxing-ccx"></a>Boxing (C++/CX)

*Boxing* est l’encapsulation d’une variable de type valeur tel que [Windows::Foundation :: DateTime](https://msdn.microsoft.com/library/windows/apps/windows.foundation.datetime.aspx), ou un type scalaire fondamental tel que `int`— dans une classe ref quand la variable est passée à une méthode qui accepte [ Platform::Object ^](../cppcx/platform-object-class.md) en tant que son type d’entrée.

## <a name="passing-a-value-type-to-an-object-parameter"></a>Passer un type valeur à un paramètre Object^

Bien que vous ne deviez pas convertir par boxing une variable explicitement pour la passer à un paramètre de méthode de type [Platform::Object^](../cppcx/platform-object-class.md), vous devez caster explicitement vers le type d'origine lorsque vous récupérez des valeurs qui ont été précédemment converties par boxing.

[!code-cpp[cx_boxing#01](../cppcx/codesnippet/CPP/cx_boxing/class1.cpp#01)]

### <a name="using-platformiboxt-to-support-nullable-value-types"></a>Utilisation de Platform::IBox\<T > pour prendre en charge des types valeur nullable

C# et Visual Basic prennent en charge le concept des types valeur autorisant la valeur Null. En C / c++ / CX, vous pouvez utiliser la `Platform::IBox<T>` type pour exposer des méthodes publiques qui prennent en charge les paramètres de type valeur nullable. L’exemple suivant montre un C + c++ / CX public méthode renvoyant null quand un appelant c# passe la valeur null pour un des arguments.

[!code-cpp[cx_boxing#02](../cppcx/codesnippet/CPP/cx_boxing/class1.h#02)]

Dans un client C# XAML, vous pouvez l'utiliser comme suit :

```

// C# client code
    BoxingDemo.Class1 obj = new BoxingDemo.Class1();
    int? a = null;
    int? b = 5;
    var result = obj.Multiply(a,b); //result = null

```

## <a name="see-also"></a>Voir aussi

[Système de type (C++/CX)](../cppcx/type-system-c-cx.md)<br/>
[Cast (C++/CX)](../cppcx/casting-c-cx.md)<br/>
[Référence du langage Visual C++](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[Référence des espaces de noms](../cppcx/namespaces-reference-c-cx.md)