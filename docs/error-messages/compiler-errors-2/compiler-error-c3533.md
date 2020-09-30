---
title: Erreur du compilateur C3533
ms.date: 11/04/2016
f1_keywords:
- C3533
helpviewer_keywords:
- C3533
ms.assetid: a68b1ba5-466e-4190-a1a4-505ccfe548b7
ms.openlocfilehash: c77c5c0fff8f8d9c1c64ba11773503b197006b67
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91510109"
---
# <a name="compiler-error-c3533"></a>Erreur du compilateur C3533

'type' : un paramètre ne peut pas avoir un type contenant’auto'

Une méthode ou un paramètre de modèle ne peut pas être déclaré avec le **`auto`** mot clé si l’option de compilateur [/Zc : auto](../../build/reference/zc-auto-deduce-variable-type.md) par défaut est activée.

### <a name="to-correct-this-error"></a>Pour corriger cette erreur

1. Supprimez le **`auto`** mot clé de la déclaration de paramètre.

## <a name="examples"></a>Exemples

L’exemple suivant génère C3533, car il déclare un paramètre de fonction avec le **`auto`** mot clé et il est compilé avec **/Zc : auto**.

```cpp
// C3533a.cpp
// Compile with /Zc:auto
void f(auto j) {} // C3533
```

L’exemple suivant génère C3533 en mode C++ 14, car il déclare un paramètre de modèle avec le **`auto`** mot clé et il est compilé avec **/Zc : auto**. (En C++ 17, il s’agit d’une définition valide d’un modèle de classe avec un paramètre de modèle sans type unique dont le type est déduit.)

```cpp
// C3533b.cpp
// Compile with /Zc:auto
template<auto T> class C {}; // C3533
```

## <a name="see-also"></a>Voir aussi

[Auto, mot clé](../../cpp/auto-cpp.md)<br/>
[/Zc : auto (déduire le type de variable)](../../build/reference/zc-auto-deduce-variable-type.md)
