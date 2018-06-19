---
title: Modifications apportées à la sémantique du destructeur | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- finalizers [C++]
- destructors, C++
ms.assetid: f1869944-a407-452f-b99a-04d8c209f0dc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 8a3d078300ca0e51ba8eb035d5428d300b0413a1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33113198"
---
# <a name="changes-in-destructor-semantics"></a>Modifications de la sémantique du destructeur
Sémantique des destructeurs de classe ont considérablement évolué depuis les Extensions managées pour C++ vers Visual C++.  
  
 Dans les Extensions managées, un destructeur de classe a été autorisé dans une classe de référence mais pas dans une classe value. Cela n’a pas changé dans la nouvelle syntaxe. Toutefois, la sémantique du destructeur de classe ont été modifiés. Cette rubrique se concentre sur les raisons de cette modification et explique comment elle affecte la traduction du code CLR existant. Il s’agit probablement de la modification au niveau du programmeur plus importante entre les deux versions du langage.  
  
## <a name="non-deterministic-finalization"></a>Finalisation non déterministe  
 Avant que la mémoire associée à un objet est récupérée par le garbage collector, associé à un `Finalize` méthode, le cas échéant, est appelée. Vous pouvez considérer cette méthode comme un type de destructeur super, car il n’est pas lié à la durée de vie du programme de l’objet. Nous appelons cela finalisation. Le minutage de simplement lorsque ou même si un `Finalize` méthode est appelée n’est pas défini. C’est ce que nous entendons lorsque nous disons que le garbage collection expose une finalisation non déterministe.  
  
 Finalisation non déterministe fonctionne bien avec gestion de la mémoire dynamique. Lorsque la mémoire disponible devient rare, le garbage collector entre en action. Sous un garbage collectées environnement, les destructeurs pour libérer de la mémoire ne sont pas nécessaires. Finalisation non déterministe ne fonctionne pas, toutefois, lorsqu’un objet détient une ressource critique, comme une connexion de base de données ou un verrou quelconque. Dans ce cas, il faut libérer cette ressource, dès que possible. Dans le monde natif, qui est obtenue à l’aide d’une paire constructeur/destructeur. Dès la fin de la durée de vie de l’objet, à la fin de bloc local dans lequel elle est déclarée, ou lors de la pile dénouement en raison de la levée d’une exception, le destructeur s’exécute et la ressource est automatiquement libérée. Cette approche fonctionne très bien, et son absence dans les Extensions managées malheureusement omise.  
  
 La solution fournie par le CLR est pour une classe implémenter le `Dispose` méthode de la `IDisposable` interface. Le problème ici est que `Dispose` requiert un appel explicite par l’utilisateur. Il s’agit d’erreurs. Le langage c# fournit une forme relative d’automatisation sous la forme d’un spécial `using` instruction. La conception des Extensions managées fourni sans prise en charge spéciale.  
  
## <a name="destructors-in-managed-extensions-for-c"></a>Destructeurs dans les Extensions managées pour C++  
 Dans les Extensions managées, le destructeur d’une classe de référence est implémenté à l’aide de le des deux étapes suivantes :  
  
1.  Le destructeur fourni par l’utilisateur est renommé en interne en `Finalize`. Si la classe a une classe de base (pour mémoire, sous le modèle objet CLR, seul l’héritage unique est pris en charge), le compilateur injecte un appel de son finaliseur suite à l’exécution du code fourni par l’utilisateur. Par exemple, considérez la hiérarchie suivante extraite de la spécification du langage des Extensions managées :  
  
```  
__gc class A {  
public:  
   ~A() { Console::WriteLine(S"in ~A"); }  
};  
  
__gc class B : public A {  
public:  
   ~B() { Console::WriteLine(S"in ~B");  }  
};  
```  
  
 Dans cet exemple, les deux destructeurs sont renommés `Finalize`. `B`de `Finalize` a un appel à `A`de `Finalize` méthode ajoutée après l’appel de `WriteLine`. C’est ce que le garbage collector entraîne par défaut lors de la finalisation. Voici à quoi peut ressembler cette transformation interne :  
  
```  
// internal transformation of destructor under Managed Extensions  
__gc class A {  
public:  
   void Finalize() { Console::WriteLine(S"in ~A"); }  
};  
  
__gc class B : public A {  
public:  
   void Finalize() {   
      Console::WriteLine(S"in ~B");  
      A::Finalize();   
   }  
};  
```  
  
1.  Dans la deuxième étape, le compilateur synthétise un destructeur virtuel. Ce destructeur est ce que nos programmes d’utilisateur des Extensions managées appeler directement ou via une application de l’expression de suppression. Il n’est jamais appelé par le garbage collector.  
  
     Deux instructions sont placées dans ce destructeur synthétisé. Un est un appel à `GC::SuppressFinalize` pour vous assurer qu’il n’y a aucune appels de `Finalize`. Le deuxième est l’appel réel de `Finalize`, qui représente le destructeur fourni par l’utilisateur pour cette classe. Voici ce que cela peut se présenter comme :  
  
```  
__gc class A {  
public:  
   virtual ~A() {  
      System::GC::SuppressFinalize(this);  
      A::Finalize();  
   }  
};  
  
__gc class B : public A {  
public:  
   virtual ~B() {  
      System::GC::SuppressFinalize(this);  
      B::Finalize();  
   }  
};  
```  
  
 Alors que cette implémentation permet à l’utilisateur d’appeler explicitement la classe `Finalize` méthode maintenant plutôt qu’à un moment que vous n’avez aucun contrôle, il ne pas vraiment à la `Dispose` solution de la méthode. Elle est modifiée dans Visual C++.  
  
## <a name="destructors-in-new-syntax"></a>Destructeurs dans la nouvelle syntaxe  
 Dans la nouvelle syntaxe, le destructeur est renommé en interne en le `Dispose` (méthode) et la classe de référence est automatiquement étendue pour implémenter le `IDispose` interface. Autrement dit, sous Visual C++, notre paire de classes est transformée comme suit :  
  
```  
// internal transformation of destructor under the new syntax  
__gc class A : IDisposable {  
public:  
   void Dispose() {   
      System::GC::SuppressFinalize(this);  
      Console::WriteLine( "in ~A");  
   }  
};  
  
__gc class B : public A {  
public:  
   void Dispose() {   
      System::GC::SuppressFinalize(this);  
      Console::WriteLine( "in ~B");    
      A::Dispose();   
   }  
};  
```  
  
 Quand un destructeur est appelé explicitement dans la nouvelle syntaxe, ou quand `delete` est appliqué à un handle de suivi, sous-jacent `Dispose` méthode est appelée automatiquement. Si elle est une classe dérivée, un appel de la `Dispose` méthode de la classe de base est inséré à la fin de la méthode synthétisée.  
  
 Mais cela n’obtient pas de nous jusqu'à la finalisation déterministe. Pour y parvenir, nous devons la prise en charge supplémentaire des objets de référence locale. (Cela n’a aucune prise en charge analogue dans les Extensions managées, et par conséquent, il n’est pas un problème de traduction).  
  
## <a name="declaring-a-reference-object"></a>Déclaration d’un objet de référence  
 Visual C++ prend en charge la déclaration d’un objet d’une classe de référence sur la pile locale ou en tant que membre d’une classe comme si elle était directement accessible. Lorsqu’elles sont combinées avec l’association du destructeur avec le `Dispose` , le résultat est un appel automatisé de la sémantique de finalisation sur les types référence.  
  
 Tout d’abord, nous définissons notre classe de référence telles que la création d’objets fonctionne comme l’acquisition d’une ressource via son constructeur de classe. Ensuite, dans le destructeur de classe, nous diffuserons la ressource acquise lorsque l’objet a été créé.  
  
```  
public ref class R {  
public:  
   R() { /* acquire expensive resource */ }  
   ~R() { /* release expensive resource */ }  
  
   // everything else...  
};  
```  
  
 L’objet est déclaré localement en utilisant le nom de type mais sans le chapeau d’accompagnement. Toutes les utilisations de l’objet, comme l’appel d’une méthode, sont effectuées via le point de sélection de membre (`.`) au lieu de flèche (`->`). À la fin du bloc, le destructeur associé, transformé en `Dispose`, est automatiquement appelé, comme indiqué ici :  
  
```  
void f() {  
   R r;   
   r.methodCall();  
  
   // r is automatically destructed here -  
   // that is, r.Dispose() is invoked  
}  
```  
  
 Comme avec la `using` instruction en c#, cela ne Relevez pas la contrainte CLR sous-jacente que tous les types référence doivent être alloués sur le tas CLR. La sémantique sous-jacente reste inchangée. L’utilisateur pourrait aurait écrire les éléments suivants (et c’est probablement la transformation interne effectuée par le compilateur) :  
  
```  
// equivalent implementation  
// except that it should be in a try/finally clause  
void f() {  
   R^ r = gcnew R;   
   r->methodCall();  
  
   delete r;  
}  
```  
  
 En effet, dans la nouvelle syntaxe, les destructeurs sont à nouveau appariés aux constructeurs comme une acquisition/la libération automatique mécanisme liée à la durée de vie d’un objet local.  
  
## <a name="declaring-an-explicit-finalize"></a>Déclaration d’une méthode Finalize explicite  
 Dans la nouvelle syntaxe, comme nous l’avons vu, le destructeur est synthétisé dans le `Dispose` (méthode). Cela signifie que lorsque le destructeur n’est pas appelé explicitement, le garbage collector, lors de la finalisation, pas comme avant recherchera des associé à un `Finalize` méthode pour l’objet. Pour prendre en charge de destruction et la finalisation, nous avons introduit une syntaxe spéciale pour fournir un finaliseur. Par exemple :  
  
```  
public ref class R {  
public:  
   !R() { Console::WriteLine( "I am the R::finalizer()!" ); }  
};  
```  
  
 Le `!` préfixe est analogue à un tilde (`~`) qui présente un destructeur, autrement dit, les deux méthodes de durée de vie après aboutissent un jeton en ajoutant le préfixe le nom de la classe. Si la synthèse `Finalize` méthode se produit dans une classe dérivée, un appel à la classe de base `Finalize` (méthode) est insérée à sa fin. Si le destructeur est appelé explicitement, le finaliseur est supprimé. Voici à quoi peut ressembler la transformation :  
  
```  
// internal transformation under new syntax  
public ref class R {  
public:  
   void Finalize() {  
      Console::WriteLine( "I am the R::finalizer()!" );  
   }  
};   
```  
  
## <a name="moving-from-managed-extensions-for-c-to-visual-c-2010"></a>Transfert des Extensions managées pour C++ vers Visual C++ 2010  
 Le comportement d’exécution d’un programme Extensions managées pour C++ est modifié lorsqu’il est compilé sous Visual C++, chaque fois qu’une classe de référence contient un destructeur non trivial. L’algorithme de traduction requis est similaire à ce qui suit :  
  
1.  Si un destructeur est présent, réécrivez-la pour être le finaliseur de classe.  
  
2.  Si un `Dispose` méthode est présente, réécrivez-la pour en faire le destructeur de classe.  
  
3.  Si un destructeur est présent, mais aucune `Dispose` méthode, conservez le destructeur lors de l’exécution du premier élément.  
  
 Lors du déplacement de votre code à partir des Extensions managées pour la nouvelle syntaxe, vous risquez de manquer exécution de cette transformation. Si l’application dépendait d’une certaine manière de l’exécution des méthodes de finalisation associées, le comportement de l’application sera silencieusement différent de celui prévu.  
  
## <a name="see-also"></a>Voir aussi  
 [Types managés (C + c++ / CL)](../dotnet/managed-types-cpp-cl.md)   
 [Destructeurs et finaliseurs dans Comment : définir et consommer des classes et structs (C + c++ / CLI)](../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers)