---
title: Fonctions Naked | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- naked functions
- functions [C++], naked
- prolog code
- epilog code
ms.assetid: 2543c8af-00d4-4a2a-8a87-e746da1f9929
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5ce7eeaf94bf23bcee67650b3074f2f9b622c0fe
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32390812"
---
# <a name="naked-functions"></a>Naked, fonctions
**Section spécifique à Microsoft**  
  
 L'attribut de classe de stockage `naked` est une extension spécifique à Microsoft pour le langage C. Pour les fonctions déclarées avec l'attribut de classe de stockage `naked`, le compilateur génère un code dépourvu de code de prologue et d'épilogue. Vous pouvez utiliser cette fonctionnalité pour écrire vos propres séquences de code de prologue/épilogue à l'aide de code assembleur inline. Les fonctions naked sont particulièrement utiles pour l'écriture de pilotes de périphériques virtuels.  
  
 Comme l'attribut `naked` se rapporte uniquement à la définition d'une fonction et n'est pas un modificateur de type, les fonctions naked utilisent la syntaxe à attributs étendus, décrite dans l'article [Attributs étendus de classe de stockage](../c-language/c-extended-storage-class-attributes.md).  
  
 L'exemple suivant définit une fonction avec l'attribut `naked` :  
  
```  
__declspec( naked ) int func( formal_parameters )  
{  
   /* Function body */  
}  
```  
  
 Ou encore :  
  
```  
#define Naked   __declspec( naked )  
  
Naked int func( formal_parameters )  
{  
   /* Function body */  
}  
```  
  
 L'attribut `naked` affecte uniquement la nature de la génération de code du compilateur pour les séquences de prologue et d'épilogue de la fonction. Il n'affecte pas le code généré pour appeler de telles fonctions. Ainsi, l'attribut `naked` n'est pas considéré comme faisant partie du type de la fonction, et les pointeurs fonction ne peuvent pas avoir l'attribut `naked`. De plus, l'attribut `naked` ne peut pas être appliqué à une définition de données. Par exemple, le code suivant génère des erreurs :  
  
```  
__declspec( naked ) int i;  /* Error--naked attribute not */  
                            /* permitted on data declarations. */  
```  
  
 L'attribut `naked` se rapporte uniquement à la définition de la fonction et ne peut pas être spécifié dans le prototype de la fonction. La déclaration suivante génère une erreur de compilateur :  
  
```  
__declspec( naked ) int func();   /* Error--naked attribute not */  
                     /* permitted on function declarations.    */   \  
```  
  
 **FIN de la section spécifique à Microsoft**  
  
## <a name="see-also"></a>Voir aussi  
 [Définitions de fonction C](../c-language/c-function-definitions.md)