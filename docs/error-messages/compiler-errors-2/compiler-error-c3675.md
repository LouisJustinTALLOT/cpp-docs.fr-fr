---
description: 'En savoir plus sur : erreur du compilateur C3675'
title: Erreur du compilateur C3675
ms.date: 11/04/2016
f1_keywords:
- C3675
helpviewer_keywords:
- C3675
ms.assetid: 87461613-6633-430b-b95d-c7cb1bb63776
ms.openlocfilehash: 0e8ea8d3450cd7a145e596f7122a5d2cbb31c5fd
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97228740"
---
# <a name="compiler-error-c3675"></a>Erreur du compilateur C3675

'fonction' : est réservé, car’Property’est défini

Quand vous déclarez une propriété simple, le compilateur génère les méthodes d’accesseur get et Set, et ces noms sont présents dans la portée de votre programme.  Les noms générés par le compilateur sont formés en ajoutant get_ et set_ au nom de la propriété.  Par conséquent, vous ne pouvez pas déclarer des fonctions portant le même nom que les accesseurs générés par le compilateur.

Pour plus d’informations, consultez [property](../../extensions/property-cpp-component-extensions.md) .

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
