---
title: Instanciation du modèle de fonction | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- templates, instantiation
- function templates, instantiation
- instantiation, function templates
ms.assetid: f22a07c7-3ad1-465a-84f5-8737e274bd47
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e773fd8e2c38311a1c36aff4c97199cbebb503e8
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/01/2018
ms.locfileid: "39406479"
---
# <a name="function-template-instantiation"></a>Instanciation du modèle de fonction
Lorsqu'un modèle de fonction est appelé pour la première fois pour chaque type, le compilateur crée une instanciation. Chaque instanciation est une version de la fonction basée sur un modèle spécialisée pour le type. Cette instanciation est appelée chaque fois que la fonction est utilisée pour le type. Si vous avez plusieurs instanciations identiques, même dans différents modules, une seule copie de l'instanciation finira dans le fichier exécutable.  
  
 La conversion des arguments de fonction est autorisée dans les modèles de fonction pour toute paire argument-paramètre où le paramètre ne dépend pas d’un argument template.  
  
 Les modèles de fonction peuvent être instanciés de manière explicite en déclarant le modèle avec un type particulier comme argument. Par exemple, le code suivant est autorisé :  
  
```cpp
// function_template_instantiation.cpp  
template<class T> void f(T) { }  
  
// Instantiate f with the explicitly specified template.  
// argument 'int'  
//  
template void f<int> (int);  
  
// Instantiate f with the deduced template argument 'char'.  
template void f(char);  
int main()  
{  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Modèles de fonctions](../cpp/function-templates.md)