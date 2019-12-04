---
title: Erreur du compilateur C3706
ms.date: 11/04/2016
f1_keywords:
- C3706
helpviewer_keywords:
- C3706
ms.assetid: d20a33eb-d625-46c5-ac87-32075a590d07
ms.openlocfilehash: 810ec59a814b04349913648fb49a03eb63912cd9
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757980"
---
# <a name="compiler-error-c3706"></a>Erreur du compilateur C3706

'fonction' : doit être une interface COM pour déclencher des événements COM

L’interface d’événement que vous utilisez pour déclencher des événements COM doit être une interface COM. Dans ce cas, l’interface doit être définie à l’aide d' C++ un attribut visuel ou importée à l’aide d' [#import](../../preprocessor/hash-import-directive-cpp.md) d’une bibliothèque de types avec l’attribut embedded_idl de #import.

Notez que les `#include` lignes des fichiers d’en-tête ATL indiqués dans l’exemple ci-dessous sont requises pour l’utilisation d’événements COM. Pour remédier à cette erreur, faites `IEvents` (l’interface d’événement) une interface COM en appliquant l’un des attributs suivants à la définition de l’interface : [Object](../../windows/object-cpp.md), [Dual](../../windows/dual.md)ou [dispinterface](../../windows/dispinterface.md).

Si une interface provient d’un fichier d’en-tête généré par MIDL, le compilateur ne la reconnaît pas comme une interface COM.

L’exemple suivant génère l’C3706 :

```cpp
// C3706.cpp
// compile with: /c
// C3706 expected
#define _ATL_ATTRIBUTES 1
#include <atlbase.h>
#include <atlcom.h>
#include <atlctl.h>

[module(dll, name="idid", uuid="12341234-1234-1234-1234-123412341234")];

// Uncomment the following line to resolve.
// [object, uuid="12341234-1234-1234-1234-123412341237"]
__interface IEvents : IUnknown {
   HRESULT event1(/*[in]*/ int i);   // uncomment [in]
};

[dual, uuid="12341234-1234-1234-1234-123412341235"]
__interface IBase {
   HRESULT fireEvents();
};

[coclass, event_source(com), uuid="12341234-1234-1234-1234-123412341236"]
class CEventSrc : public IBase {
   public:
   __event __interface IEvents;

   HRESULT fireEvents() {
      HRESULT hr = IEvents_event1(123);
      return hr;
   }
};
```
