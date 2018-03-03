---
title: "Modifications apportées aux opérateurs de Conversion | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- conversion operators
- operators [C++], explicit type conversion
- type conversion, explicit conversions
- conversions, explicit
- explicit keyword [C++]
ms.assetid: 9b83925c-71b7-4bd3-ac2e-843dd7c7f184
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 8f89c49035e2e48dde8d502b1d61fa33d198f69a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="changes-to-conversion-operators"></a>Modifications apportées aux opérateurs de conversion
La syntaxe pour les opérateurs de conversion a changé entre les Extensions managées pour C++ vers Visual C++.  
  
 Un exemple consiste à écrire `op_Implicit` pour spécifier une conversion. Voici une définition de `MyDouble` obtenue à partir de la spécification de langage :  
  
```  
__gc struct MyDouble {  
   static MyDouble* op_Implicit( int i );   
   static int op_Explicit( MyDouble* val );  
   static String* op_Explicit( MyDouble* val );   
};  
```  
  
 Cela indique que, si un entier, l’algorithme pour convertir cet entier en un `MyDouble` est fournie par le `op_Implicit` opérateur. En outre, cette conversion sera effectuée implicitement par le compilateur. De même, étant donné un `MyDouble` (objet), les deux `op_Explicit` opérateurs fournissent les algorithmes respectifs pour convertir cet objet en un entier ou managé `String` entité. Toutefois, le compilateur n’effectuera pas la conversion sauf demande explicite par l’utilisateur.  
  
 En c#, cela se présente comme suit :  
  
```  
class MyDouble {  
   public static implicit operator MyDouble( int i );   
   public static explicit operator int( MyDouble val );  
   public static explicit operator string( MyDouble val );   
};  
```  
  
 Le code c# ressemble plus à C++ que les extensions managées pour C++. Qui n’est pas le cas dans la nouvelle syntaxe.  
  
 Le comité ISO-C++ a introduit un mot clé, `explicit`, pour atténuer des conséquences inattendues - par exemple, un `Array` classe qui prend un argument entier unique comme une dimension convertit implicitement tout entier en un `Array` de l’objet qui n’est pas ce que vous souhaitez. Une façon d’éviter ce problème est un idiome de conception d’un deuxième argument factice d’un constructeur  
  
 En revanche, vous ne devez pas fournir une paire de conversion lors de la conception d’un type de classe dans C++. L’exemple suivant pour qui est la classe de chaîne standard. La conversion implicite est le constructeur à argument unique qui prend une chaîne de style C. Toutefois, il ne fournit pas l’opérateur de conversion implicite correspondant - qui de conversion d’une chaîne de l’objet en une chaîne de style C, mais au lieu de cela, l’utilisateur doit appeler explicitement une fonction nommée - dans ce cas, `c_str()`.  
  
 Par conséquent, association d’un comportement implicite/explicite sur un opérateur de conversion (de même que l’encapsulation du jeu de conversions sous un seul format de déclaration) semble être une amélioration par rapport à la prise en charge C++ d’origine pour les opérateurs de conversion, qui a finalement conduit le `explicit` (mot clé). La prise en charge du langage Visual C++ pour les opérateurs de conversion se présente comme suit, légèrement moins détaillé que celle de c# en raison du comportement par défaut de l’opérateur prenant en charge une application implicite de l’algorithme de conversion :  
  
```  
ref struct MyDouble {  
public:  
   static operator MyDouble^ ( int i );  
   static explicit operator int ( MyDouble^ val );  
   static explicit operator String^ ( MyDouble^ val );  
};  
```  
  
 Une autre modification est qu’un constructeur à argument unique est traité comme s’il est déclaré comme `explicit`. Cela signifie que pour déclencher ses appels, un cast explicite est requis. Toutefois, notez que si un opérateur de conversion explicite est défini, il et pas le constructeur à argument unique, est appelée.  
  
## <a name="see-also"></a>Voir aussi  
 [Déclarations de membre dans une classe ou interface (C++-CLI)](../dotnet/member-declarations-within-a-class-or-interface-cpp-cli.md)