---
title: "Contr&#244;le d&#39;acc&#232;s aux membres (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "contrôle d'accès (C++)"
  - "accès aux membres (C++)"
  - "contrôle d'accès aux membres (C++)"
ms.assetid: 2d596bca-56ad-4277-94e1-ce3db45fa14a
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Contr&#244;le d&#39;acc&#232;s aux membres (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Les contrôles d'accès permettent de séparer l'interface [publique](../cpp/public-cpp.md) d'une classe des détails de l'implémentation [privée](../cpp/private-cpp.md) et des membres [protégés](../cpp/protected-cpp.md) qui doivent uniquement être utilisés par les classes dérivées.  Le spécificateur d'accès s'applique à tous les membres déclarés après lui jusqu'à ce que le spécificateur d'accès suivant soit rencontré.  
  
```  
class Point  
{  
public:                   
    Point( int, int ) // Declare public constructor.;  
    Point();// Declare public default constructor.  
    int &x( int ); // Declare public accessor.  
    int &y( int ); // Declare public accessor.  
  
private:                 // Declare private state variables.  
    int _x;  
    int _y;  
  
protected:      // Declare protected function for derived classes only.  
    Point ToWindowCoords();  
};  
  
```  
  
 L'accès par défaut est `private` dans une classe et `public` dans un struct ou une union.  Les spécificateurs d'accès dans une classe peuvent être utilisés autant de fois que nécessaire dans n'importe quel ordre.  L'allocation du stockage des objets des types de classe est dépendante de l'implémentation, mais les membres ont la garantie d'être assignés successivement aux adresses mémoire supérieures entre les spécificateurs d'accès.  
  
### Contrôle d'accès aux membres  
  
|Type d'accès|Signification|  
|------------------|-------------------|  
|[private](../cpp/private-cpp.md)|Les membres de classe déclarés comme `private` peuvent être utilisés uniquement par les fonctions membres et les composants friend \(classes ou fonctions\) de la classe.|  
|[protected](../cpp/protected-cpp.md)|Les membres de classe déclarés comme `protected` peuvent être utilisés par les fonctions membres et les composants friend \(classes ou fonctions\) de la classe.  En outre, ils peuvent être utilisés par des classes dérivées de la classe.|  
|[public](../cpp/public-cpp.md)|Les membres de classe déclarés comme **public** peuvent être utilisés par n'importe quelle fonction.|  
  
 Le contrôle d'accès vous empêche d'utiliser des objets à d'autres fins que leur usage prévu.  Cette protection est perdue lorsque les conversions de type explicite \(casts\) sont exécutées.  
  
> [!NOTE]
>  Le contrôle d'accès s'applique également à tous les noms : fonctions membres, données membres, classes imbriquées et énumérateurs.  
  
## Contrôle d'accès dans les classes dérivées  
 Deux facteurs contrôlent les membres d'une classe de base qui sont accessibles dans une classe dérivée. Ces mêmes facteurs contrôlent l'accès aux membres hérités dans la classe dérivée :  
  
-   Si la classe dérivée doit déclarer la classe de base à l'aide du spécificateur d'accès **public** dans *class\-head* \(*class\-head* est décrit dans la section Grammaire de la rubrique [Définition des types de classes](http://msdn.microsoft.com/fr-fr/e8c65425-0f3a-4dca-afc2-418c3b1e57da)\).  
  
-   Quel est l'accès au membre de la classe de base.  
  
 Le tableau suivant montre l'interaction entre ces facteurs et la procédure de détermination de l'accès au membre de la classe de base.  
  
### Accès au membre de la classe de base  
  
|private|protected|Public|  
|-------------|---------------|------------|  
|Toujours inaccessible quel que soit l'accès de dérivation|Privé dans la classe dérivée si vous utilisez la dérivation privée|Privé dans la classe dérivée si vous utilisez la dérivation privée|  
||Protégé dans la classe dérivée si vous utilisez la dérivation protégée|Protégé dans la classe dérivée si vous utilisez la dérivation protégée|  
||Protégé dans la classe dérivée si vous utilisez la dérivation publique|Public dans la classe dérivée si vous utilisez la dérivation publique|  
  
 L'exemple suivant illustre ce comportement :  
  
```  
// access_specifiers_for_base_classes.cpp  
class BaseClass  
{  
public:  
    int PublicFunc();    // Declare a public member.  
protected:  
    int ProtectedFunc(); // Declare a protected member.  
private:  
    int PrivateFunc();   // Declare a private member.  
};  
  
// Declare two classes derived from BaseClass.  
class DerivedClass1 : public BaseClass  
{  
};  
  
class DerivedClass2 : private BaseClass  
{  
};  
  
int main()  
{  
}  
```  
  
 Dans `DerivedClass1`, la fonction membre `PublicFunc` est un membre public et `ProtectedFunc` est un membre protégé car `BaseClass` est une classe de base publique.  `PrivateFunc` est privé pour `BaseClass` et inaccessible à toutes les classes dérivées.  
  
 Dans `DerivedClass2`, les fonctions `PublicFunc` et `ProtectedFunc` sont considérées comme des membres privés car `BaseClass` est une classe de base privée.  À nouveau, `PrivateFunc` est privé pour `BaseClass` et inaccessible à toutes les classes dérivées.  
  
 Vous pouvez déclarer une classe dérivée sans spécificateur d'accès de classe de base.  Dans ce cas, la dérivation est considérée comme privée si la déclaration de classe dérivée utilise le mot clé **class**.  La dérivation est considérée comme publique si la déclaration de classe dérivée utilise le mot clé `struct`.  Par exemple, le code suivant :  
  
```  
class Derived : Base  
...  
```  
  
 équivaut à :  
  
```  
class Derived : private Base  
...  
```  
  
 De même, le code suivant :  
  
```  
struct Derived : Base  
...  
```  
  
 équivaut à :  
  
```  
struct Derived : public Base  
...  
```  
  
 Notez que les membres déclarés comme ayant un accès privé ne sont pas accessibles aux fonctions ou aux classes dérivées si ces fonctions ou classes ne sont pas déclarées à l'aide de la déclaration `friend` dans la classe de base.  
  
 Un type **union** ne peut pas avoir de classe de base.  
  
> [!NOTE]
>  Pour spécifier une classe de base privée, il est recommandé d'utiliser explicitement le mot clé `private` afin que les utilisateurs de la classe dérivée comprennent l'accès au membre.  
  
## Contrôle d'accès et membres statiques  
 Lorsque vous spécifiez une classe de base comme `private`, elle affecte uniquement les membres non statiques.  Les membres publics static sont toujours accessibles dans les classes dérivées.  Toutefois, l'accès aux membres de la classe de base à l'aide de pointeurs, de références ou d'objets peut nécessiter une conversion, à laquelle le contrôle d'accès est encore appliqué.  Prenons l'exemple suivant :  
  
```  
// access_control.cpp  
class Base  
{  
public:  
    int Print();             // Nonstatic member.  
    static int CountOf();    // Static member.  
};  
  
// Derived1 declares Base as a private base class.  
class Derived1 : private Base  
{  
};  
// Derived2 declares Derived1 as a public base class.  
class Derived2 : public Derived1  
{  
    int ShowCount();    // Nonstatic member.  
};  
// Define ShowCount function for Derived2.  
int Derived2::ShowCount()  
{  
   // Call static member function CountOf explicitly.  
    int cCount = Base::CountOf();     // OK.  
  
   // Call static member function CountOf using pointer.  
    cCount = this->CountOf();  // C2247. Conversion of  
                               //  Derived2 * to Base * not  
                               //  permitted.  
    return cCount;  
}  
```  
  
 Dans le code précédent, le contrôle d'accès interdit la conversion d'un pointeur vers `Derived2` en un pointeur vers `Base`.  Le pointeur **this** est implicitement de type `Derived2 *`.  Pour sélectionner la fonction `CountOf`, **this** doit être converti en type `Base *`.  Cette conversion n'est pas autorisée car `Base` est une classe de base indirecte privée à `Derived2`.  La conversion en type de classe de base privée est acceptable uniquement pour les pointeurs vers des classes dérivées immédiates.  Par conséquent, les pointeurs de type `Derived1 *` peuvent être convertis en type `Base *`.  
  
 Notez que lorsque vous appelez la fonction `CountOf` explicitement, sans utiliser de pointeur, de référence ou d'objet pour la sélectionner, cela n'implique aucune conversion.  Par conséquent, l'appel est autorisé.  
  
 Les membres et les amis d'une classe dérivée, `T`, peuvent convertir un pointeur vers `T` en pointeur vers une classe de base directe privée de `T`.  
  
## Accès aux fonctions virtuelles  
 Le contrôle d'accès appliqué aux fonctions [virtuelles](../cpp/virtual-cpp.md) est déterminé par le type utilisé pour effectuer l'appel de fonction.  La substitution des déclarations de fonction n'affectent pas le contrôle d'accès pour un type donné.  Exemple :  
  
```  
// access_to_virtual_functions.cpp  
class VFuncBase  
{  
public:  
    virtual int GetState() { return _state; }  
protected:  
    int _state;  
};  
  
class VFuncDerived : public VFuncBase  
{  
private:  
    int GetState() { return _state; }  
};  
  
int main()  
{  
   VFuncDerived vfd;             // Object of derived type.  
   VFuncBase *pvfb = &vfd;       // Pointer to base type.  
   VFuncDerived *pvfd = &vfd;    // Pointer to derived type.  
   int State;  
  
   State = pvfb->GetState();     // GetState is public.  
   State = pvfd->GetState();     // C2248 error expected; GetState is private;  
}  
```  
  
 Dans l'exemple précédent, l'appel de la fonction virtuelle `GetState` à l'aide d'un pointeur vers le type `VFuncBase` appelle `VFuncDerived::GetState` et `GetState` est traité comme public.  Toutefois, l'appel de `GetState` à l'aide d'un pointeur vers le type `VFuncDerived` est une violation de contrôle d'accès car `GetState` est déclaré privé dans la classe `VFuncDerived`.  
  
> [!CAUTION]
>  La fonction virtuelle `GetState` peut être appelée en utilisant un pointeur vers la classe de base `VFuncBase`.  Cela ne signifie pas que la fonction appelée est la version de classe de base de cette fonction.  
  
## Contrôle d'accès avec héritage multiple  
 Dans les treillis à héritage multiple impliquant des classes de base virtuelles, un nom donné est accessible via plusieurs chemins.  Comme un contrôle d'accès différent peut être appliqué le long de ces différents chemins, le compilateur choisit le chemin qui fournit le plus souvent l'accès.  Voir l'illustration suivante.  
  
 ![Chemins d'accès d'un graphique d'héritage](../cpp/media/vc38v91.png "vc38V91")  
Graphique d'accès le long des chemins d'un héritage  
  
 Dans cette figure, un nom déclaré dans la classe `VBase` est toujours accessible via la classe `RightPath`.  Le chemin d'accès correct est plus accessible car `RightPath` déclare `VBase` en tant que classe de base publique, tandis que `LeftPath` déclare `VBase` comme classe privée.  
  
## Voir aussi  
 [Référence du langage C\+\+](../cpp/cpp-language-reference.md)