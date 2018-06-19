---
title: Types (C++ moderne) valeur | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: f63bb62c-60da-40d5-ac14-4366608fe260
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e7e49c97bca86b8d2debde2f5b132f7dde16998e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32423416"
---
# <a name="value-types-modern-c"></a>Types de valeur (Modern C++)
Les classes C++ sont par types de valeur par défaut. Cette rubrique fournit une présentation des types valeur et les problèmes liés à leur utilisation.  
  
## <a name="value-vs-reference-types"></a>Valeur et types référence  
 Comme indiqué plus haut, sont des classes C++ par types de valeur par défaut. Elles peuvent être spécifiées en tant que types de référence, qui permettent à un comportement polymorphe prendre en charge de programmation orientée objet. Types valeur sont parfois affichés du point de vue de contrôle de mémoire et la disposition, alors que les types référence sont sur les classes de base et les fonctions virtuelles à des fins polymorphe. Par défaut, les types valeur sont copiables, ce qui signifie que l’il y a toujours un constructeur de copie et un opérateur d’assignation de copie. Pour les types référence, vous rendez la classe non reproductible (désactiver le constructeur de copie et un opérateur d’assignation de copie) et utiliser un destructeur virtuel, qui prend en charge leur polymorphisme prévu. Types valeur sont également sur le contenu, ce qui, lorsqu’ils sont copiés, toujours deux valeurs distinctes qui peuvent être modifiées séparément. Types référence concernent l’identité - le type d’objet est-il ? Pour cette raison, « types de référence » sont également appelés « types polymorphes ».  
  
 Si vous voulez vraiment d’un type de référence de type (classe de base, les fonctions virtuelles), vous devez désactiver explicitement la copie, comme indiqué dans la `MyRefType` classe dans le code suivant.  
  
```cpp  
// cl /EHsc /nologo /W4  
  
class MyRefType {  
private:  
    MyRefType & operator=(const MyRefType &);  
    MyRefType(const MyRefType &);  
public:  
    MyRefType () {}  
};  
  
int main()  
{  
    MyRefType Data1, Data2;  
    // ...  
    Data1 = Data2;  
}  
```  
  
 Compilation du code ci-dessus génère l’erreur suivante :  
  
```Output  
test.cpp(15) : error C2248: 'MyRefType::operator =' : cannot access private member declared in class 'MyRefType'  
        meow.cpp(5) : see declaration of 'MyRefType::operator ='  
        meow.cpp(3) : see declaration of 'MyRefType'  
  
```  
  
## <a name="value-types-and-move-efficiency"></a>Types valeur et déplacer l’efficacité  
 Surcharge d’allocation de copie est évitée en raison de nouvelles optimisations de copie. Par exemple, lorsque vous insérez une chaîne au milieu d’un vecteur de chaînes, il n’y aura aucune surcharge de réallocation de copie, uniquement un déplacement - même si elle entraîne une augmentation du vecteur lui-même. Cela s’applique également à d’autres opérations, par exemple en effectuant une opération d’ajout sur deux objets très volumineux. Comment faire pour activer ces optimisations d’opération valeur ? Dans certains compilateurs C++, le compilateur s’activer cette option pour vous implicitement, comme les constructeurs de copie peuvent être générés automatiquement par le compilateur. Toutefois, dans Visual C++, votre classe doit « opt-in » pour déplacer l’affectation et les constructeurs en le déclarant dans votre définition de classe. Cela s’effectue à l’aide de la double perluète (& &) référence rvalue dans le membre approprié définition constructeur de déplacement et les déclarations de fonction et les méthodes d’assignation de déplacement.  Vous devez également insérer le code approprié pour « voler l’essentiel », hors de l’objet source.  
  
 Comment savoir si vous avez besoin de déplacer activé ? Si vous connaissez déjà que vous devez copier la construction activée, vous pouvez déplacer activée si elle peut être moins chère qu’une copie complète. Toutefois, si vous savez que vous devez déplacer la prise en charge, il ne signifie pas nécessairement copie activée. Ce dernier cas est appelé un « type move-only ». Est un exemple déjà dans la bibliothèque standard `unique_ptr`. Comme une note rapide, l’ancien `auto_ptr` est déconseillé et a été remplacé par `unique_ptr` exactement en raison de l’absence de prise en charge la sémantique de déplacement dans la version précédente de C++.  
  
 À l’aide d’une sémantique de déplacement, vous pouvez en valeur de retour ou d’insertion de l’intercepteur. Déplacement est une optimisation de la copie. Il est nécessaire pour l’allocation de tas comme solution de contournement. Considérez le pseudocode suivant :  
  
```cpp  
#include <set>  
#include <vector>  
#include <string>  
using namespace std;  
  
//...  
set<widget> LoadHugeData() {  
    set<widget> ret;  
    // ... load data from disk and populate ret  
    return ret;  
}  
//...  
widgets = LoadHugeData();   // efficient, no deep copy  
  
vector<string> v = IfIHadAMillionStrings();  
v.insert( begin(v)+v.size()/2, "scott" );   // efficient, no deep copy-shuffle  
v.insert( begin(v)+v.size()/2, "Andrei" );  // (just 1M ptr/len assignments)  
//...  
HugeMatrix operator+(const HugeMatrix& , const HugeMatrix& );  
HugeMatrix operator+(const HugeMatrix& ,       HugeMatrix&&);  
HugeMatrix operator+(      HugeMatrix&&, const HugeMatrix& );  
HugeMatrix operator+(      HugeMatrix&&,       HugeMatrix&&);  
//...  
hm5 = hm1+hm2+hm3+hm4+hm5;   // efficient, no extra copies  
```  
  
### <a name="enabling-move-for-appropriate-value-types"></a>L’activation de déplacement pour les types de valeur appropriée  
 Pour une classe de type valeur où move peut être moins chère qu’une copie complète, autorisent la construction de déplacement et assignation de l’efficacité de déplacement. Considérez le pseudocode suivant :  
  
```cpp  
#include <memory>  
#include <stdexcept>  
using namespace std;  
// ...  
class my_class {  
    unique_ptr<BigHugeData> data;  
public:  
    my_class( my_class&& other )   // move construction  
        : data( move( other.data ) ) { }  
    my_class& operator=( my_class&& other )   // move assignment  
    { data = move( other.data ); return *this; }  
    // ...  
    void method() {   // check (if appropriate)  
        if( !data )   
            throw std::runtime_error("RUNTIME ERROR: Insufficient resources!");  
    }  
};  
  
```  
  
 Si vous activez la construction/assignation de copie, activez également construction/assignation de déplacement si elle peut être moins chère qu’une copie complète.  
  
 Certains *sans valeur* sont de types move-uniquement, tels que lorsque vous ne peut pas cloner une ressource, uniquement de transférer la propriété. Par exemple : `unique_ptr`  
  
## <a name="section"></a>Section  
 Contenu  
  
## <a name="see-also"></a>Voir aussi  
 [Système de Type C++](../cpp/cpp-type-system-modern-cpp.md)   
 [Bienvenue dans C++](../cpp/welcome-back-to-cpp-modern-cpp.md)   
 [Référence du langage C++](../cpp/cpp-language-reference.md)   
 [Bibliothèque C++ standard](../standard-library/cpp-standard-library-reference.md)