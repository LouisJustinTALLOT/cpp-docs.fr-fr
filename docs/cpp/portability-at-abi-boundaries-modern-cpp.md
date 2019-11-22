---
title: Portabilité aux limites ABI
description: Aplatir C++ les interfaces avec les conventions d’appel C aux limites de l’interface binaire.
ms.date: 11/19/2019
ms.topic: conceptual
ms.assetid: abbd405e-3038-427c-8c24-e00598f0936a
ms.openlocfilehash: b3b2b217739ff5900c8ef0329ff3e8909a3fe036
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74303314"
---
# <a name="portability-at-abi-boundaries"></a>Portabilité aux limites ABI

Utilisez des conventions et des types portables suffisamment aux limites de l’interface binaire. Un « type portable » est un type intégré C ou un struct qui contient uniquement des types intégrés C. Les types de classes ne peuvent être utilisés que lorsque l’appelant et l’appelé conviennent de la disposition, de la Convention d’appel, etc. Cela n’est possible que lorsque les deux sont compilés avec les mêmes paramètres de compilateur et de compilateur.

## <a name="how-to-flatten-a-class-for-c-portability"></a>Comment aplatir une classe pour la portabilité C

Lorsque les appelants peuvent être compilés avec un autre compilateur/langage, puis « aplatir » sur une API **« C » extern** avec une convention d’appel spécifique :

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

[Bienvenue dansC++](../cpp/welcome-back-to-cpp-modern-cpp.md)<br/>
[Référence du langage C++](../cpp/cpp-language-reference.md)<br/>
[Bibliothèque standard C++](../standard-library/cpp-standard-library-reference.md)
