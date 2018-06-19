---
title: Erreur du compilateur C3533 | Documents Microsoft
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
ms.openlocfilehash: faaf53d08512559b86c95148bc93e7b3367d2b01
ms.sourcegitcommit: 3bb7c1c0ceeb8012418e2fff9ae5a7db0fff3877
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2018
ms.locfileid: "34458912"
---
# <a name="compiler-error-c3533"></a>Erreur du compilateur C3533
'type' : un paramètre ne peut pas avoir un type contenant 'auto'  
  
 Une méthode ou paramètre de modèle ne peut pas être déclaré avec le `auto` mot clé si la valeur par défaut [/Zc : auto](../../build/reference/zc-auto-deduce-variable-type.md) option du compilateur est en vigueur.  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
1.  Supprimer le `auto` (mot clé) à partir de la déclaration de paramètre.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant donne C3533, car il déclare un paramètre de fonction avec la `auto` (mot clé) et il est compilé avec **/Zc : auto**.  
  
```  
// C3533a.cpp  
// Compile with /Zc:auto  
void f(auto j) {} // C3533  
```  
  
## <a name="example"></a>Exemple  
 L’exemple suivant donne C3533 mode C ++ 14, car il déclare un paramètre de modèle avec le `auto` (mot clé) et il est compilé avec **/Zc : auto**. (Dans C ++ 17, ceci est une définition valide d’un modèle de classe avec un paramètre de modèle sans type unique dont le type est déduit).
  
```  
// C3533b.cpp  
// Compile with /Zc:auto  
template<auto T> class C {}; // C3533  
```  
  
## <a name="see-also"></a>Voir aussi  
 [auto, mot clé](../../cpp/auto-keyword.md)   
 [/Zc:auto (Déduire le type de variable)](../../build/reference/zc-auto-deduce-variable-type.md)
