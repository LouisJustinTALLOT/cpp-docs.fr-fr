---
title: être conforme | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- conform_CPP
- vc-pragma.conform
dev_langs:
- C++
helpviewer_keywords:
- conform pragma
- forScope conform pragma
- pragmas, conform
ms.assetid: 71b3e174-c53c-4bfc-adf3-af39b1554191
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b145225cfed3131b406d15827b589aed718d16bb
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33843741"
---
# <a name="conform"></a>conform
**Spécifique à C++**  
  
 Spécifie le comportement au moment de l’exécution de la [/Zc : forScope](../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md) option du compilateur.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
#pragma conform(name [, show ] [, on | off ] [ [, push | pop ] [, identifier ] ] )  
```  
  
#### <a name="parameters"></a>Paramètres  
 *name*  
 Spécifie le nom de l'option du compilateur à modifier. Valide uniquement *nom* est `forScope`.  
  
 **afficher** (facultatif)  
 Provoque le paramètre actuel de *nom* (true ou false) à afficher au moyen d’un message d’avertissement lors de la compilation. Par exemple, `#pragma conform(forScope, show)`.  
  
 **activer, désactiver**(facultatif)  
 Paramètre *nom* à **sur** permet la [/Zc : forScope](../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md) option du compilateur. La valeur par défaut est **hors**.  
  
 **Push** (facultatif)  
 Exécute un push de la valeur actuelle de *nom* sur la pile interne du compilateur. Si vous spécifiez *identificateur*, vous pouvez spécifier le **sur** ou **hors** valeur *nom* à être placé sur la pile. Par exemple, `#pragma conform(forScope, push, myname, on)`.  
  
 **POP** (facultatif)  
 Définit la valeur de *nom* à la valeur en haut de la pile interne du compilateur, puis dépile la pile. Si l’identificateur est spécifié avec **pop**, la pile est alors dépilée jusqu'à ce qu’il trouve l’enregistrement avec *identificateur*, qui sera également dépilé ; la valeur actuelle pour *nom* dans l’enregistrement suivant dans la pile devient la nouvelle valeur pour *nom*. Si vous spécifiez pop avec un *identificateur* qui n’est pas dans un enregistrement dans la pile, le **pop** est ignoré.  
  
 *identificateur*(facultatif)  
 Peut être inclus dans un **push** ou **pop** commande. Si *identificateur* est utilisé, alors un **sur** ou **hors** spécificateur peut également être utilisé.  
  
## <a name="example"></a>Exemple  
  
```  
// pragma_directive_conform.cpp  
// compile with: /W1  
// C4811 expected  
#pragma conform(forScope, show)  
#pragma conform(forScope, push, x, on)  
#pragma conform(forScope, push, x1, off)  
#pragma conform(forScope, push, x2, off)  
#pragma conform(forScope, push, x3, off)  
#pragma conform(forScope, show)  
#pragma conform(forScope, pop, x1)  
#pragma conform(forScope, show)  
  
int main() {}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Directives pragma et mot clé _Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)