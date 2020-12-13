---
description: 'En savoir plus sur : erreur du compilateur C3904'
title: Erreur du compilateur C3904
ms.date: 11/04/2016
f1_keywords:
- C3904
helpviewer_keywords:
- C3904
ms.assetid: 08297605-e4f2-4c6c-b637-011f1fd40631
ms.openlocfilehash: 0b1564e609586318d23b4204242f0cb39034c4fd
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97144181"
---
# <a name="compiler-error-c3904"></a>Erreur du compilateur C3904

'property_accessor' : vous devez spécifier un ou plusieurs paramètres de nombre

Vérifiez le nombre de paramètres dans vos `get` `set` méthodes et par rapport aux dimensions des propriétés.

- Le nombre de paramètres de la `get` méthode doit être égal au nombre de dimensions de la propriété ou être égal à zéro pour les propriétés non indexées.

- Le nombre de paramètres de la `set` méthode doit être supérieur au nombre de dimensions de la propriété.

Pour plus d'informations, consultez [property](../../extensions/property-cpp-component-extensions.md).

## <a name="examples"></a>Exemples

L’exemple suivant génère l’C3904.

```cpp
// C3904.cpp
// compile with: /clr /c
ref class X {
   property int P {
      // set
      void set();   // C3904
      // try the following line instead
      // void set(int);

      // get
      int get(int, int);   // C3904
      // try the following line instead
      // int get();
   };
};
```

L’exemple suivant génère l’C3904.

```cpp
// C3904b.cpp
// compile with: /clr /c
ref struct X {
   property int Q[double, double, float, float, void*, int] {
      // set
      void set(double, void*);   // C3904
      // try the following line instead
      // void set(double, double, float, float, void*, int, int);

      // get
      int get();   // C3904
      // try the following line instead
      // int get(double, double, float, float, void*, int);
   }
};
```
