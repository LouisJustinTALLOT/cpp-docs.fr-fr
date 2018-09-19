---
title: Erreur du compilateur C3675 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3675
dev_langs:
- C++
helpviewer_keywords:
- C3675
ms.assetid: 87461613-6633-430b-b95d-c7cb1bb63776
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c4b6656753ab4a611dcb80d1473e0b44bf47a270
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46094778"
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