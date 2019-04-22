---
title: Erreur du compilateur C3533
ms.date: 11/04/2016
f1_keywords:
- C3533
helpviewer_keywords:
- C3533
ms.assetid: a68b1ba5-466e-4190-a1a4-505ccfe548b7
ms.openlocfilehash: 7a567e4396999f98d9e9740db0acf951c443d525
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59026303"
---
# <a name="compiler-error-c3533"></a>Erreur du compilateur C3533

'type' : un paramètre ne peut pas avoir un type contenant 'auto'

Une méthode ou paramètre de modèle ne peut pas être déclaré avec le `auto` mot clé si la valeur par défaut [/Zc : auto](../../build/reference/zc-auto-deduce-variable-type.md) option du compilateur est en vigueur.

### <a name="to-correct-this-error"></a>Pour corriger cette erreur

1. Supprimer le `auto` mot clé à partir de la déclaration du paramètre.

## <a name="example"></a>Exemple

L’exemple suivant donne C3533, car il déclare un paramètre de fonction avec la `auto` mot clé et il est compilé avec **/Zc : auto**.

```
// C3533a.cpp
// Compile with /Zc:auto
void f(auto j) {} // C3533
```

## <a name="example"></a>Exemple

L’exemple suivant donne C3533 en mode C ++ 14, car il déclare un paramètre de modèle avec le `auto` mot clé et il est compilé avec **/Zc : auto**. (Dans C ++ 17, voici une définition d’un modèle de classe avec un paramètre de modèle sans type unique dont le type est déduit valide.)

```
// C3533b.cpp
// Compile with /Zc:auto
template<auto T> class C {}; // C3533
```

## <a name="see-also"></a>Voir aussi

[auto, mot clé](../../cpp/auto-keyword.md)<br/>
[/Zc:auto (Déduire le type de variable)](../../build/reference/zc-auto-deduce-variable-type.md)
