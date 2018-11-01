---
title: Portabilité aux limites ABI (Modern C++)
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: abbd405e-3038-427c-8c24-e00598f0936a
ms.openlocfilehash: 12f60b92e71c15a94546e5b099c3b49e3685b68b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50549953"
---
# <a name="portability-at-abi-boundaries-modern-c"></a>Portabilité aux limites ABI (Modern C++)

Utiliser des conventions et types suffisamment portables aux limites de l’interface binaire. Un « type portable » est un type intégré de C ou un struct qui contient uniquement des types intégrés C. Classe types peuvent uniquement être utilisés lors de l’appelant et l’appelé d’accord sur la mise en page, appelant convention, etc. Cela est possible uniquement lorsque les deux sont compilées avec le même compilateur et les paramètres de compilateur.

## <a name="how-to-flatten-a-class-for-c-portability"></a>Comment aplatir une classe pour la portabilité de C

Lorsque les appelants peut être compilés avec un autre compilateur/langage, les « aplatir » un **extern « C »** API avec une convention d’appel spécifique :

```cpp
// class widget {
//   widget();
//   ~widget();
//   double method( int, gadget& );
// };
extern "C" {        // functions using explicit "this"
   struct widget;   // opaque type (forward declaration only)
   widget* STDCALL widget_create();      // constructor creates new "this"
   void STDCALL widget_destroy(widget*); // destructor consumes "this"
   double STDCALL widget_method(widget*, int, gadget*); // method uses "this"
}
```

## <a name="see-also"></a>Voir aussi

[Bienvenue dans C++](../cpp/welcome-back-to-cpp-modern-cpp.md)<br/>
[Informations de référence sur le langage C++](../cpp/cpp-language-reference.md)<br/>
[Bibliothèque C++ standard](../standard-library/cpp-standard-library-reference.md)