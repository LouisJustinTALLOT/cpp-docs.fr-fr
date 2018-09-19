---
title: Erreur du compilateur C3533 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3533
dev_langs:
- C++
helpviewer_keywords:
- C3533
ms.assetid: a68b1ba5-466e-4190-a1a4-505ccfe548b7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6201f59e3ccefaa920f79f9b9889bd187fb2e0b0
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46042557"
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
