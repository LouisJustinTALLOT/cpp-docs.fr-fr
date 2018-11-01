---
title: Erreur du compilateur C3904
ms.date: 11/04/2016
f1_keywords:
- C3904
helpviewer_keywords:
- C3904
ms.assetid: 08297605-e4f2-4c6c-b637-011f1fd40631
ms.openlocfilehash: 8c7f4a2861825a35d676328b5e283a5e4087d85b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50519780"
---
# <a name="compiler-error-c3904"></a>Erreur du compilateur C3904

'accesseur_propriété' : doit spécifier numéro (s)

Vérifiez le nombre de paramètres dans votre `get` et `set` des méthodes sur les dimensions de la propriété.

- Le nombre de paramètres pour le `get` méthode doit être égal au nombre de dimensions de la propriété ou être égal à zéro pour les propriétés non indexées.

- Le nombre de paramètres de la `set` méthode doit être supérieur au nombre de dimensions de la propriété.

Pour plus d'informations, consultez [property](../../windows/property-cpp-component-extensions.md).

## <a name="example"></a>Exemple

L’exemple suivant génère C3904.

```
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

## <a name="example"></a>Exemple

L’exemple suivant génère C3904.

```
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