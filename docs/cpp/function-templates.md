---
title: "Modèles de fonction | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- function templates
- templates, function
- function templates, about function templates
ms.assetid: 59b56a4b-0689-4161-9c07-25021562e2a7
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 721e466e5d7e77592e66aa3ebacb3ad59eb89bb5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="function-templates"></a>Modèles de fonctions
Les modèles de classe définissent une famille de classes connexes basées sur les arguments de type passés à la classe lors de son instanciation. Les modèles de fonction sont semblables aux modèles de classe mais définissent une famille de fonctions. Avec les modèles de fonction, vous pouvez spécifier un ensemble de fonctions basées sur le même code mais agir sur différents types ou différentes classes. Le modèle de fonction suivant permute deux éléments :  
  
```cpp
// function_templates1.cpp  
template< class T > void MySwap( T& a, T& b ) {  
   T c(a);   
   a = b;   
   b = c;  
}  
int main() {  
}  
```  
  
 Ce code définit une famille de fonctions qui permutent les valeurs des arguments. À partir de ce modèle, vous pouvez générer des fonctions qui permuteront **int** et **long** types et les types définis par l’utilisateur. `MySwap` permutera même une classe si le constructeur de copie et l'opérateur d'assignation de cette classe sont correctement définis.  
  
 En outre, le modèle de fonction vous empêche de permuter des objets de types différents, car le compilateur connaît les types des paramètres `a` et `b` au moment de la compilation.  
  
 Bien que cette fonction puisse être effectuée par une fonction non basée sur un modèle à l'aide de pointeurs void, la version de modèle est de type sécurisé. Prenons les appels suivants :  
  
```cpp
int j = 10;  
int k = 18;  
CString Hello = "Hello, Windows!";  
MySwap( j, k );          //OK  
MySwap( j, Hello );      //error  
```  
  
 Le deuxième appel `MySwap` déclenche une erreur de compilation, car le compilateur ne peut pas générer de fonction `MySwap` avec des paramètres de types différents. Si des pointeurs void étaient utilisés, les deux appels de fonction se compileraient correctement, mais la fonction ne fonctionnerait pas correctement au moment de l'exécution.  
  
 Il est autorisé de spécifier explicitement les arguments template d’un modèle de fonction. Exemple :  
  
```cpp
// function_templates2.cpp  
template<class T> void f(T) {}  
int main(int j) {  
   f<char>(j);   // Generate the specialization f(char).  
   // If not explicitly specified, f(int) would be deduced.  
}  
```  
  
 Lorsque l’argument template est spécifié explicitement, les conversions implicites normales sont effectuées pour convertir l’argument de fonction vers le type des paramètres de modèle de fonction correspondants. Dans l’exemple ci-dessus, le compilateur convertit `char j` au type `int`.  
  
## <a name="see-also"></a>Voir aussi  
 [Modèles](../cpp/templates-cpp.md)   
 [Instanciation du modèle de fonction](../cpp/function-template-instantiation.md)   
 [Instanciation explicite](../cpp/explicit-instantiation.md)   
 [Spécialisation explicite de modèles de fonctions](../cpp/explicit-specialization-of-function-templates.md)
