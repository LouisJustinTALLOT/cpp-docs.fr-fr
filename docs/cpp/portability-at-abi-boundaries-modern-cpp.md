---
title: Portabilité aux limites ABI (Modern C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: abbd405e-3038-427c-8c24-e00598f0936a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 891f56d763fc86efd62fb5bae3b21498336a8ccc
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46058406"
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