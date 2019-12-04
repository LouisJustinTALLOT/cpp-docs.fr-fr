---
title: Erreur du compilateur C3533
ms.date: 11/04/2016
f1_keywords:
- C3533
helpviewer_keywords:
- C3533
ms.assetid: a68b1ba5-466e-4190-a1a4-505ccfe548b7
ms.openlocfilehash: ce95bba417e9be3603f15376a0fd65a48f951a2f
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755640"
---
# <a name="compiler-error-c3533"></a>Erreur du compilateur C3533

'type' : un paramètre ne peut pas avoir un type contenant’auto'

Une méthode ou un paramètre de modèle ne peut pas être déclaré avec le mot clé `auto` si l’option de compilateur [/Zc : auto](../../build/reference/zc-auto-deduce-variable-type.md) par défaut est activée.

### <a name="to-correct-this-error"></a>Pour corriger cette erreur

1. Supprimez le mot clé `auto` de la déclaration de paramètre.

## <a name="example"></a>Exemple

L’exemple suivant génère C3533, car il déclare un paramètre de fonction avec le mot clé `auto` et il est compilé avec **/Zc : auto**.

```cpp
// C3533a.cpp
// Compile with /Zc:auto
void f(auto j) {} // C3533
```

## <a name="example"></a>Exemple

L’exemple suivant génère C3533 en mode C++ 14, car il déclare un paramètre de modèle avec le mot clé `auto` et il est compilé avec **/Zc : auto**. (En C++ 17, il s’agit d’une définition valide d’un modèle de classe avec un paramètre de modèle sans type unique dont le type est déduit.)

```cpp
// C3533b.cpp
// Compile with /Zc:auto
template<auto T> class C {}; // C3533
```

## <a name="see-also"></a>Voir aussi

[auto, mot clé](../../cpp/auto-keyword.md)<br/>
[/Zc:auto (Déduire le type de variable)](../../build/reference/zc-auto-deduce-variable-type.md)
