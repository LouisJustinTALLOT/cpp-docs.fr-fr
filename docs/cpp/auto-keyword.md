---
title: auto, mot clé | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 744a41c0-2510-4140-a1be-96257e722908
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 93b2f5e28dc0306a996b4c8bdb799122fe4646ab
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32409997"
---
# <a name="auto-keyword"></a>auto, mot clé
Le mot clé `auto` est un spécificateur de déclaration. Cependant, le code C++ standard définit une signification originale et modifiée pour ce mot clé . Avant Visual C++ 2010, le `auto` mot clé déclare une variable dans le *automatique* classe de stockage ; autrement dit, une variable qui a une durée de vie locale. Depuis Visual C++ 2010, le `auto` mot clé déclare une variable dont le type est déduit à partir de l’expression d’initialisation dans sa déclaration. Le [/Zc : auto&#91;-&#93; ](../build/reference/zc-auto-deduce-variable-type.md) option du compilateur contrôle la signification de la `auto` (mot clé).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
auto declarator ;  
auto declarator initializer;  
```  
  
## <a name="remarks"></a>Notes  
 La définition du mot clé `auto` change dans le langage de programmation C++, mais pas dans le langage de programmation C.  
  
 Les rubriques suivantes décrivent le mot clé `auto` et l'option du compilateur correspondante :  
  
-   [Auto](../cpp/auto-cpp.md) décrit la nouvelle définition de la `auto` (mot clé).  
  
  
-   [/ Zc : auto (déduire le Type de Variable)](../build/reference/zc-auto-deduce-variable-type.md) décrit l’option du compilateur qui indique au compilateur de la définition du `auto` mot clé à utiliser.  
  
## <a name="see-also"></a>Voir aussi  
 [Mots clés](../cpp/keywords-cpp.md)