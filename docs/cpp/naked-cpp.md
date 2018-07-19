---
title: naked (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- naked_cpp
dev_langs:
- C++
helpviewer_keywords:
- __declspec keyword [C++], naked
- naked __declspec keyword
ms.assetid: 69723241-05e1-439b-868e-20a83a16ab6d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1057754b5c98086de42daedd5e7aab70656eba69
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2018
ms.locfileid: "37942681"
---
# <a name="naked-c"></a>naked (C++)
**Section spécifique à Microsoft**  
  
 Pour les fonctions déclarées avec le **naked** attribut, le compilateur génère du code sans code de prologue et épilogue. Vous pouvez utiliser cette fonctionnalité pour écrire vos propres séquences de code de prologue/épilogue à l'aide de code assembleur inline. Les fonctions naked sont particulièrement utiles pour l'écriture de pilotes de périphériques virtuels.  Notez que le **naked** attribut est uniquement valide sur x86 et ARM et n’est pas disponible sur [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)].  
  
## <a name="syntax"></a>Syntaxe  
  
```  
__declspec(naked) declarator  
```  
  
## <a name="remarks"></a>Notes  
 Étant donné que le **naked** attribut se rapporte uniquement à la définition d’une fonction et n’est pas un modificateur de type, des fonctions naked doivent utiliser la syntaxe à attributs étendus et le [__declspec](../cpp/declspec.md) mot clé.  
  

 Le compilateur ne peut pas générer une fonction inline pour une fonction marquée avec l’attribut naked, même si la fonction est également marquée avec le [__forceinline](inline-functions-cpp.md) mot clé.  

  
 Le compilateur émet une erreur si le **naked** attribut est appliqué à l’autre que la définition d’une méthode non membre.  
  
## <a name="examples"></a>Exemples  
 Ce code définit une fonction avec la **naked** attribut :  
  
```  
__declspec( naked ) int func( formal_parameters ) {}  
```  
  
 Ou, alternativement :  
  
```  
#define Naked __declspec( naked )  
Naked int func( formal_parameters ) {}  
```  
  
 Le **naked** attribut affecte uniquement la nature de la génération de code du compilateur pour les séquences de prologue et épilogue de la fonction. Il n'affecte pas le code généré pour appeler de telles fonctions. Par conséquent, le **naked** attribut n’est pas considéré comme partie du type de la fonction et des pointeurs de fonction ne peut pas avoir le **naked** attribut. En outre, le **naked** attribut ne peut pas être appliqué à une définition de données. Par exemple, cet exemple de code génère une erreur :  
  
```  
__declspec( naked ) int i;  
// Error--naked attribute not permitted on data declarations.  
```  
  
 Le **naked** attribut s’applique uniquement à la définition de la fonction et ne peut pas être spécifié dans le prototype de la fonction. Par exemple, cette déclaration génère une erreur du compilateur :  
  
```  
__declspec( naked ) int func();  // Error--naked attribute not permitted on function declarations  
```  
  
 **FIN de la section spécifique à Microsoft**  
  
## <a name="see-also"></a>Voir aussi  
 [__declspec](../cpp/declspec.md)   
 [Mots clés](../cpp/keywords-cpp.md)   
 [Appels de fonction naked](../cpp/naked-function-calls.md)