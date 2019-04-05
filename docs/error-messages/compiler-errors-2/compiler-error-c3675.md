---
title: Erreur du compilateur C3675
ms.date: 11/04/2016
f1_keywords:
- C3675
helpviewer_keywords:
- C3675
ms.assetid: 87461613-6633-430b-b95d-c7cb1bb63776
ms.openlocfilehash: e29e536bf89aef887dc043327e4b4596703d0538
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/05/2019
ms.locfileid: "58775190"
---
# <a name="compiler-error-c3675"></a>Erreur du compilateur C3675

'fonction' : est réservé, car 'propriété' est définie.

Lorsque vous déclarez une propriété simple, le compilateur génère get et méthodes d’accesseur set et ces noms sont présents dans la portée de votre programme.  Le nom généré par le compilateur est constitué en ajoutant le préfixe get_ et set_ au nom de propriété.  Par conséquent, vous ne pouvez pas déclarer des fonctions avec le même nom que les accesseurs générés par le compilateur.

Pour plus d'informations, voir [property](../../extensions/property-cpp-component-extensions.md) .

## <a name="example"></a>Exemple

L’exemple suivant génère C3675.

```
// C3675.cpp
// compile with: /clr /c
ref struct C {
public:
   property int Size;
   int get_Size() { return 0; }   // C3675
};
```