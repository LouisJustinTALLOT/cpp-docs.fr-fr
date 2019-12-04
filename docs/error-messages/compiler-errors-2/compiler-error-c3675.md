---
title: Erreur du compilateur C3675
ms.date: 11/04/2016
f1_keywords:
- C3675
helpviewer_keywords:
- C3675
ms.assetid: 87461613-6633-430b-b95d-c7cb1bb63776
ms.openlocfilehash: 6772572d29765370d6cdbf52ed8470ff2f3f054e
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758071"
---
# <a name="compiler-error-c3675"></a>Erreur du compilateur C3675

'fonction' : est réservé, car’Property’est défini

Quand vous déclarez une propriété simple, le compilateur génère les méthodes d’accesseur get et Set, et ces noms sont présents dans la portée de votre programme.  Les noms générés par le compilateur sont formés en ajoutant get_ et set_ au nom de la propriété.  Par conséquent, vous ne pouvez pas déclarer des fonctions portant le même nom que les accesseurs générés par le compilateur.

Pour plus d'informations, voir [property](../../extensions/property-cpp-component-extensions.md) .

## <a name="example"></a>Exemple

L’exemple suivant génère l’C3675.

```cpp
// C3675.cpp
// compile with: /clr /c
ref struct C {
public:
   property int Size;
   int get_Size() { return 0; }   // C3675
};
```
