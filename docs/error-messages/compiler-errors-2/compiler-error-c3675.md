---
title: Erreur du compilateur C3675
ms.date: 11/04/2016
f1_keywords:
- C3675
helpviewer_keywords:
- C3675
ms.assetid: 87461613-6633-430b-b95d-c7cb1bb63776
ms.openlocfilehash: c154a0fe1989c92bb5e07c0710d3846883d1a113
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50546312"
---
# <a name="compiler-error-c3675"></a>Erreur du compilateur C3675

'fonction' : est réservé, car 'propriété' est définie.

Lorsque vous déclarez une propriété simple, le compilateur génère get et méthodes d’accesseur set et ces noms sont présents dans la portée de votre programme.  Le nom généré par le compilateur est constitué en ajoutant le préfixe get_ et set_ au nom de propriété.  Par conséquent, vous ne pouvez pas déclarer des fonctions avec le même nom que les accesseurs générés par le compilateur.

Pour plus d'informations, voir [property](../../windows/property-cpp-component-extensions.md) .

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