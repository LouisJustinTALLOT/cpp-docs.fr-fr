---
description: 'En savoir plus sur : boxing (C++/CX)'
title: Boxing (C++/CX)
ms.date: 12/30/2016
ms.assetid: edfb12fa-2a9b-42f6-bdac-d4d76cb8274e
ms.openlocfilehash: 50b7f3f071fcd0109a85fb24985024666bd8fad3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97302736"
---
# <a name="boxing-ccx"></a>Boxing (C++/CX)

Le *boxing* consiste à encapsuler une variable de type valeur telle que [Windows :: Foundation ::D atetime](/uwp/api/windows.foundation.datetime), ou un type scalaire fondamental tel que **`int`** , dans une classe ref lorsque la variable est passée à une méthode qui accepte [Platform :: Object ^](../cppcx/platform-object-class.md) comme son type d’entrée.

## <a name="passing-a-value-type-to-an-object-parameter"></a>Passer un type valeur à un paramètre Object^

Bien que vous ne deviez pas convertir par boxing une variable explicitement pour la passer à un paramètre de méthode de type [Platform::Object^](../cppcx/platform-object-class.md), vous devez caster explicitement vers le type d'origine lorsque vous récupérez des valeurs qui ont été précédemment converties par boxing.

[!code-cpp[cx_boxing#01](../cppcx/codesnippet/CPP/cx_boxing/class1.cpp#01)]

### <a name="using-platformiboxt-to-support-nullable-value-types"></a>Utilisation de Platform :: IBox \<T> pour prendre en charge les types valeur Nullable

C# et Visual Basic prennent en charge le concept des types valeur autorisant la valeur Null. En C++/CX, vous pouvez utiliser le `Platform::IBox<T>` type pour exposer des méthodes publiques qui prennent en charge les paramètres de type valeur Nullable. L’exemple suivant montre une méthode publique C++/CX qui retourne la valeur null lorsqu’un appelant C# passe la valeur null pour l’un des arguments.

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
[Effectuer un cast (C++/CX)](../cppcx/casting-c-cx.md)<br/>
[Informations de référence sur le langage C++/CX](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[Référence des espaces de noms](../cppcx/namespaces-reference-c-cx.md)
