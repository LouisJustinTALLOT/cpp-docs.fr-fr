---
title: auto, mot clé | Microsoft Docs
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
ms.openlocfilehash: f9b4b9e2526d621e9e9fee1d1f8c05c5a05d3312
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2018
ms.locfileid: "37941676"
---
# <a name="auto-keyword"></a>auto, mot clé
Le **automatique** mot clé est un spécificateur de déclaration. Cependant, le code C++ standard définit une signification originale et modifiée pour ce mot clé . Avant Visual C++ 2010, le **automatique** mot clé déclare une variable dans le *automatique* classe de stockage ; autrement dit, une variable qui a une durée de vie locale. À partir de Visual C++ 2010, le **automatique** mot clé déclare une variable dont le type est déduit à partir de l’expression d’initialisation dans sa déclaration. Le [/Zc : auto&#91;-&#93; ](../build/reference/zc-auto-deduce-variable-type.md) option du compilateur contrôle la signification de la **automatique** mot clé.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
auto declarator ;  
auto declarator initializer;  
```  
  
## <a name="remarks"></a>Notes  
 La définition de la **automatique** les modifications de mot clé dans le langage de programmation C++, mais pas dans le langage de programmation C.  
  
 Les rubriques suivantes décrivent les **automatique** mot clé et l’option du compilateur correspondante :  
  
-   [Auto](../cpp/auto-cpp.md) décrit la nouvelle définition de la **automatique** mot clé.  
  
  
-   [/ Zc : auto (déduire le Type de Variable)](../build/reference/zc-auto-deduce-variable-type.md) décrit l’option du compilateur qui indique au compilateur quelle définition de la **automatique** mot clé à utiliser.  
  
## <a name="see-also"></a>Voir aussi  
 [Mots clés](../cpp/keywords-cpp.md)