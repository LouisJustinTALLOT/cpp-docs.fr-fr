---
title: Erreur du compilateur C3345
ms.date: 11/04/2016
f1_keywords:
- C3345
helpviewer_keywords:
- C3345
ms.assetid: 1dda4c79-73bb-441b-b939-746154c3afba
ms.openlocfilehash: 196928d7a171aa7ffe2d6b8f38b529d3d3588bc4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50624781"
---
# <a name="compiler-error-c3345"></a>Erreur du compilateur C3345

'identifier' : identificateur non valide pour le nom de module

L’ *identificateur* d’un module contient un ou plusieurs caractères inacceptables. Un identificateur est valide si le premier caractère est un caractère alphabétique, un caractère de soulignement ou un caractère ANSI élevé (0x80-FF), et que tout caractère suivant est un caractère alphanumérique, un caractère de soulignement ou un caractère ANSI élevé.

### <a name="to-correct-this-error"></a>Pour corriger cette erreur

1. Vérifiez que l’ *identificateur* ne contient pas d’espaces ni d’autres caractères inacceptables.

## <a name="example"></a>Exemple

L’exemple de code suivant provoque le message d’erreur C3345, car le paramètre `name` de l’attribut `module` contient un espace.

```
// cpp_attr_name_module.cpp
// compile with: /LD /link /OPT:NOREF
#include <atlbase.h>
#include <atlcom.h>
#include <atlwin.h>
#include <atltypes.h>
#include <atlctl.h>
#include <atlhost.h>
#include <atlplus.h>

// C3345 expected
[module(dll, name="My Library", version="1.2", helpfile="MyHelpFile")]
// Try the following line instead
//[module(dll, name="MyLibrary", version="1.2", helpfile="MyHelpFile")]
// Module attribute now applies to this class
class CMyClass {
public:
BOOL WINAPI DllMain(DWORD dwReason, LPVOID lpReserved) {
   // add your own code here
   return __super::DllMain(dwReason, lpReserved);
   }
};
```

## <a name="see-also"></a>Voir aussi

[__iscsym](../../c-runtime-library/reference/iscsym-functions.md)<br/>
[Classifications des caractères](../../c-runtime-library/character-classification.md)<br/>
[module](../../windows/module-cpp.md)