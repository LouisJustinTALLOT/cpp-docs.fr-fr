---
title: Boxing (C++/CX)
ms.date: 12/30/2016
ms.assetid: edfb12fa-2a9b-42f6-bdac-d4d76cb8274e
ms.openlocfilehash: 90c5af31efc6523683227dbf54c85390bc98510a
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70740663"
---
# <a name="boxing-ccx"></a>Boxing (C++/CX)

Le*boxing* est l’encapsulation d’une variable de type valeur, telle que [Windows::Foundation::DateTime](/uwp/api/windows.foundation.datetime)ou de type scalaire fondamental tel que `int`dans une classe ref quand la variable est passée à une méthode qui accepte [Platform::Object^](../cppcx/platform-object-class.md) comme son type d’entrée.

## <a name="passing-a-value-type-to-an-object-parameter"></a>Passer un type valeur à un paramètre Object^

Bien que vous ne deviez pas convertir par boxing une variable explicitement pour la passer à un paramètre de méthode de type [Platform::Object^](../cppcx/platform-object-class.md), vous devez caster explicitement vers le type d'origine lorsque vous récupérez des valeurs qui ont été précédemment converties par boxing.

[!code-cpp[cx_boxing#01](../cppcx/codesnippet/CPP/cx_boxing/class1.cpp#01)]

### <a name="using-platformiboxt-to-support-nullable-value-types"></a>Utilisation de Platform ::\<iBox T > pour prendre en charge les types valeur Nullable

C# et Visual Basic prennent en charge le concept des types valeur autorisant la valeur Null. Dans C++/CX, vous pouvez utiliser le `Platform::IBox<T>` type pour exposer des méthodes publiques qui prennent en charge les paramètres de type valeur Nullable. L’exemple suivant montre une C++méthode publique/CX qui retourne la valeur null C# lorsqu’un appelant passe la valeur null pour l’un des arguments.

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
[Informations de référence sur le langage C++/CX](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[Référence aux espaces de noms](../cppcx/namespaces-reference-c-cx.md)
