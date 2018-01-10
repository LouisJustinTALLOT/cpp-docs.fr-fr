---
title: "Un Handle de suivi d’une valeur Boxed | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: boxed value types, tracking handle to
ms.assetid: 16c92048-5b74-47d5-8eca-dfea3d38879a
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: baae8c5317f1e5c9c5acf5bef26a4b79de281a3e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="a-tracking-handle-to-a-boxed-value"></a>Handle de suivi d'une valeur boxed
L’utilisation d’un handle de suivi pour référencer un type valeur a changé entre les Extensions managées pour C++ vers Visual C++.  
  
 La conversion boxing est une particularité du système de type CLR unifiée. Types valeur contiennent directement leur état, tandis que les types référence sont une paire implicite : l’entité nommée est un handle vers un objet sans nom alloué sur le tas managé. Toute initialisation ou assignation d’une valeur de type pour un `Object`, par exemple, requiert que le type de valeur soit placé dans le tas CLR - il s’agit où l’image d’une conversion boxing intervient - tout d’abord en allouant la mémoire associée, puis en copiant état la valeur du type et puis de retourner l’adresse de cet hybride valeur/référence anonyme. Par conséquent, lorsqu’on écrit en c#  
  
```  
object o = 1024; // C# implicit boxing  
```  
  
 Il est beaucoup plus passer d’est rendu visible par la simplicité du code. La conception de c# masque la complexité non seulement de quelles opérations ont lieu dans les coulisses, mais également de l’abstraction de la conversion boxing elle-même. Extensions managées pour C++, en revanche, concerné que cela entraînerait un sentiment d’efficacité, il place en face de l’utilisateur en requérant une instruction explicite :  
  
```  
Object *o = __box( 1024 ); // Managed Extensions explicit boxing  
```  
  
 Conversion boxing est implicite dans Visual C++ :  
  
```  
Object ^o = 1024; // new syntax implicit boxing  
```  
  
 Le `__box` mot clé rend un service vital au sein des Extensions managées, absent volontairement de langages tels que c# et Visual Basic : il fournit un vocabulaire et le suivi handle pour manipuler directement une instance boxed sur le tas managé. Par exemple, considérez le petit programme suivant :  
  
```  
int main() {  
   double result = 3.14159;  
   __box double * br = __box( result );  
  
   result = 2.7;   
   *br = 2.17;     
   Object * o = br;  
  
   Console::WriteLine( S"result :: {0}", result.ToString() ) ;  
   Console::WriteLine( S"result :: {0}", __box(result) ) ;  
   Console::WriteLine( S"result :: {0}", br );  
}  
```  
  
 Le code sous-jacent généré pour les trois appels de `WriteLine` afficher les différents coûts d’accès à la valeur d’une valeur boxed de type (grâce aux Yves Dolce pour ces différences), où les lignes indiquées affichent la surcharge associée à chaque appel.  
  
```  
// Console::WriteLine( S"result :: {0}", result.ToString() ) ;  
ldstr      "result :: {0}"  
ldloca.s   result  // ToString overhead  
call       instance string  [mscorlib]System.Double::ToString()  // ToString overhead  
call       void [mscorlib]System.Console::WriteLine(string, object)  
  
// Console::WriteLine( S"result :: {0}", __box(result) ) ;  
Ldstr    " result :: {0}"  
ldloc.0  
box    [mscorlib]System.Double // box overhead  
call    void [mscorlib]System.Console::WriteLine(string, object)  
  
// Console::WriteLine( S"result :: {0}", br );  
ldstr    "result :: {0}"  
ldloc.0  
call     void [mscorlib]System.Console::WriteLine(string, object)  
```  
  
 En passant le type valeur boxed directement à `Console::WriteLine` élimine la conversion boxing et la nécessité d’appeler `ToString()`. (Bien entendu, il est la boxing antérieure à initialiser `br`, donc nous n’obtenir quoi que ce soit, à moins que nous avons vraiment mis `br` fonctionne.  
  
 Dans la nouvelle syntaxe, la prise en charge pour les types valeur boxed est considérablement plus élégante et intégré dans le système de type tout en conservant sa puissance. Par exemple, voici la traduction de petit programme précédent :  
  
```  
int main()  
{  
   double result = 3.14159;  
   double^ br = result;  
   result = 2.7;  
   *br = 2.17;  
   Object^ o = br;  
   Console::WriteLine( "result :: {0}", result.ToString() );  
   Console::WriteLine( "result :: {0}", result );  
   Console::WriteLine( "result :: {0}", br );  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Types valeur et leurs comportements (C + c++ / CLI)](../dotnet/value-types-and-their-behaviors-cpp-cli.md)   
 [Guide pratique pour demander explicitement le boxing](../dotnet/how-to-explicitly-request-boxing.md)