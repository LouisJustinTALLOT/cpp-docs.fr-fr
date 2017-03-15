---
title: "Comment&#160;: conception pour la s&#233;curit&#233; des exceptions | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: 19ecc5d4-297d-4c4e-b4f3-4fccab890b3d
caps.latest.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 20
---
# Comment&#160;: conception pour la s&#233;curit&#233; des exceptions
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Un des avantages du mécanisme d'exception est qu'avec des données sur l'exception, l'exécution passe directement de l'instruction qui lève l'exception à la première instruction catch qui la gère.  Le gestionnaire peut être n'importe quel nombre de level\-up dans la pile des appels.  Les fonctions qui sont appelées entre l'instruction try et l'instruction throw n'ont pas besoin de connaître quoi que ce soit concernant l'exception levée.  Toutefois, elles doivent être conçues afin qu'elles puissent être inopinément mise hors de portée lorsqu'une exception peut se propager en remontant, et veillez donc à ne pas laisser des objets, de la mémoire perdue, ou des structures de données partiellement créés qui seraient inutilisables.  
  
## Techniques de base  
 Une stratégie fiable de gestion des exceptions requiert une pensée attentionnée et doit faire partie du processus de création.  En général, la plupart des exceptions sont détectées et levées dans les couches inférieures d'un module de logiciel, mais généralement ces couches ne disposent pas d'un contexte suffisant pour gérer l'erreur ou pour transmettre un message aux utilisateurs finaux.  Dans les couches intermédiaires, les fonctions peuvent intercepter et lever à nouveau une exception lorsqu'elles sont chargées d'inspecter l'objet exception, ou elles peuvent avoir des informations supplémentaires utiles à fournir au niveau supérieur qui interceptera finalement l'exception.  Une fonction doit intercepter et « avaler » une exception uniquement si elle peut être récupérée entièrement.  Dans de nombreux cas, le comportement correct dans les couches itermédiaires est de laisser une exception se propager vers le haut de la pile des appels.  Même dans la couche la plus haute, il peut s'avérer nécessaire de laisser une exception non gérée terminer un programme si l'exception laisse le programme dans un état dans lequel son exactitude ne peut pas être garantie.  
  
 Peu importe comment une fonction gère une exception, afin de garantir qu'elle soit protégée contre les exceptions, elle doit être conçue selon les principes de base suivants.  
  
### Conservez les classes de ressources simples  
 Lorsque vous encapsulez la gestion manuelle des ressources dans des classes, utilisez une classe qui ne fait rien d'autre que gérer chaque ressource ; sinon, vous pouvez créer des fuites.  Utilisez des [pointeurs intelligents](../cpp/smart-pointers-modern-cpp.md) si possible, comme indiqué dans l'exemple suivant.  Cet exemple est intentionnellement artificiel et simpliste afin de mettre en évidence les différences lorsque `shared_ptr` est utilisé.  
  
```cpp  
// old-style new/delete version  
class NDResourceClass {  
private:  
    int*   m_p;  
    float* m_q;  
public:  
    NDResourceClass() : m_p(0), m_q(0) {  
        m_p = new int;  
        m_q = new float;  
    }  
  
    ~NDResourceClass() {  
        delete m_p;  
        delete m_q;  
    }  
    // Potential leak! When a constructor emits an exception,   
    // the destructor will not be invoked.     
};  
  
// shared_ptr version  
#include <memory>  
  
using namespace std;  
  
class SPResourceClass {  
private:  
    shared_ptr<int> m_p;  
    shared_ptr<float> m_q;  
public:  
    SPResourceClass() : m_p(new int), m_q(new float) { }  
    // Implicitly defined dtor is OK for these members,   
    // shared_ptr will clean up and avoid leaks regardless.  
};  
  
// A more powerful case for shared_ptr  
  
class Shape {  
    // ...  
};  
  
class Circle : public Shape {  
    // ...  
};  
  
class Triangle : public Shape {  
    // ...  
};  
  
class SPShapeResourceClass {  
private:  
    shared_ptr<Shape> m_p;  
    shared_ptr<Shape> m_q;  
public:  
    SPShapeResourceClass() : m_p(new Circle), m_q(new Triangle) { }  
};  
  
```  
  
### Utilisez l'idiome RAII pour gérer des ressources  
 Pour être protégée contre les exceptions, une fonction doit garantir que les objets qu'elle a alloué à l'aide de `malloc` ou de `new` soient détruits, et que toutes les ressources telles que les handles de fichiers soient fermés ou libérés et cela même si une exception est levée.  L'idiome *RAII \(Resource Acquisition Is Initialization\)* lie la gestion de telles ressources à l'espérance de vie de variables automatiques.  Lorsqu'une fonction est hors de portée, soit en retournant normalement ou alors suite à une exception, les destructeurs pour toutes les variables automatiques entièrement construites sont appelés.  Un objet wrapper RAII tel qu'un pointeur intelligent appelle la fonction appropriée, de suppression ou de fermeture, dans son destructeur.  Dans un code protégée contre les exceptions, il est extrêmement important de passer la propriété de chaque ressource immédiatement à un certain type d'objet RAII.  Notez que `vector`, `string`, `make_shared`, `fstream`, et les classes similaires gèrent la saisie de la ressource pour vous.  Toutefois, `unique_ptr` et les constructions traditionnelles `shared_ptr` sont spécifiques car la saisie de ressource est exécutée par l'utilisateur au lieu de l'objet ; Par conséquent, elles comptent comme *RRID \(Resource Release Is Destruction\)* mais sont incertains comme RAII.  
  
## Les trois garanties d'exception  
 En général, la protection contre les exceptions est décrite en termes de trois garanties d'exception qu'une fonction peut proposer : la *garantie sans échec*, la *garantie forte*, et la *garantie de base*.  
  
### Garantie sans échec  
 La garantie sans échec est la garantie la plus puissante qu'une fonction puisse fournir.  Elle indique que la fonction ne lèvera pas d'exception ou ne permettra pas à une de se propager.  Toutefois, vous ne pouvez pas de manière fiable fournir une telle garantie sauf si \(a\) vous savez que toutes les fonctions que cette fonction appelle sont également sans échec, ou \(b\) vous savez que toutes les exceptions levées seront interceptées avant qu'elles n'atteignent cette fonction, ou \(c\) vous savez comment intercepter et gérer correctement toutes les exceptions pouvant atteindre cette fonction.  
  
 La garantie forte et la garantie de base reposent sur l'hypothèse que les destructeurs sont sans échec.  Tous les conteneurs et types de la bibliothèque standard garantissent que leurs destructeurs ne lèvent pas.  Il existe également une spécification inverse : La bibliothèque standard requiert que les types définis par l'utilisateur qui lui sont fournis, par exemple, les arguments de modèle, aient des non\-throwing destructeurs.  
  
### Garantie forte  
 La garantie forte déclare que si une fonction est hors de portée suite à une exception, il n'y aura pas de fuite de mémoire et l'état du programme ne sera pas modifié.  Une fonction qui fournit une garantie forte est essentiellement une transaction qui comporte une sémantique de validation ou de restauration : soit il réussit complètement, soit il n'a aucun effet.  
  
### Garantie de base  
 La garantie de base est la plus faible des trois.  Toutefois, elle peut être le meilleur choix lorsqu'une garantie forte est trop coûteuse en termes de consommation de mémoire ou de performances.  La garantie de base indique que si une exception se produit, aucune fuite de mémoire n'a lieu et l'objet est toujours dans un état utilisable bien que les données peuvent avoir été modifiées.  
  
## Classes protégées contre les exceptions  
 Une classe peut garantir sa propre protection contre les exception, même lorsqu'elle est consommée par des fonctions potentiellement dangereuses, en évitant d'elle\-même d'être partiellement construite ou partiellement détruite.  Si un constructeur de classe s'arrête avant la fin, l'objet n'est pas créé et son destructeur ne sera jamais appelé.  Bien que les variables automatiques qui sont initialisées avant l'exception auront leurs destructeurs appelés, la mémoire ou les ressources allouées dynamiquement qui ne sont pas gérées par un pointeur intelligent ou une variable automatique similaire seront inutilisables.  
  
 Les types intégrés sont tous sans échec, et les types de la bibliothèque standard prennent en charge la garantie de base au minimum.  Suivez ces indications pour tout type défini par l'utilisateur qui doit être protégé contre les exceptions :  
  
-   Utilisez des pointeurs intelligents ou d'autres wrappers de type RAII pour gérer toutes les ressources.  Éviter la fonctionnalité de gestion des ressources dans votre destructeur de classe, car le destructeur ne sera pas appelé si le constructeur lève une exception.  Toutefois, si la classe est un gestionnaire de ressources dédié qui contrôle une seule ressource, il est acceptable d'utiliser le destructeur pour gérer des ressources.  
  
-   Comprennez qu'une exception levée dans un constructeur de classe de base ne peut pas être avalée dans un constructeur de classe dérivé.  Si vous souhaitez traduire et lever à nouveau l'exception de classe de base dans un constructeur dérivé, utilisez une fonction try block.  Pour plus d'informations, consultez [\(NOTINBUILD\)How to: Handle Exceptions in Base Class Constructors \(C\+\+\)](http://msdn.microsoft.com/fr-fr/53bb822e-785b-4581-9517-210dd05060a3).  
  
-   Il est conseillé de stocker tout l'état de classe dans des données membres qui sont encapsulées dans un pointeur intelligent, surtout si une classe a un concept d' « initialisation qui est autorisée à échouer. » Bien que C\+\+ autorise des données membres non initialisées, il ne prend pas en charge les instances de classe non initialisées ou partiellement initialisées.  Un constructeur doit soit réussir, soit échouer ; aucun objet n'est créé si le constructeur ne s'exécute pas jusqu'à la fin.  
  
-   Ne permettez à aucune exception d'échapper à un destructeur.  Un axiome de base C\+\+ est que les destructeurs ne doivent jamais permettre à une exception pour propager vers le haut de la pile des appels.  Si un destructeur doit effectuer une opération qui pourrait être un levage d'exception, il doit le faire dans un bloc Try Catch et avaler l'exception.  La bibliothèque standard fournit cette garantie pour tous les destructeurs qu'elle définit.  
  
## Voir aussi  
 [Gestion des erreurs et des exceptions](../cpp/errors-and-exception-handling-modern-cpp.md)   
 [Comment : établir une interface entre le code exceptionnel et le code non exceptionnel](../cpp/how-to-interface-between-exceptional-and-non-exceptional-code.md)