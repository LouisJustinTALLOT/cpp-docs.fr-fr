---
title: Classes C++ en tant que types de valeurs
ms.date: 11/19/2019
ms.topic: conceptual
ms.assetid: f63bb62c-60da-40d5-ac14-4366608fe260
ms.openlocfilehash: 1aabcad46e848e1a499a142adaba5002a829bbf5
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2019
ms.locfileid: "74246019"
---
# <a name="c-classes-as-value-types"></a>Classes C++ en tant que types de valeurs

C++les classes sont des types valeur par défaut. Ils peuvent être spécifiés en tant que types référence, qui permettent un comportement polymorphe pour prendre en charge la programmation orientée objet. Les types valeur sont parfois affichés du point de vue de la gestion de la mémoire et de la disposition, tandis que les types référence concernent les classes de base et les fonctions virtuelles à des fins polymorphes. Par défaut, les types valeur peuvent être copiés, ce qui signifie qu’il y a toujours un constructeur de copie et un opérateur d’assignation de copie. Pour les types référence, vous rendez la classe non pouvant être copiée (désactivez le constructeur de copie et l’opérateur d’assignation de copie) et utilisez un destructeur virtuel qui prend en charge le polymorphisme prévu. Les types valeur concernent également le contenu, qui, lorsqu’ils sont copiés, vous donne toujours deux valeurs indépendantes qui peuvent être modifiées séparément. Les types référence sont à propos de l’identité-quel type d’objet est-il ? C’est pour cette raison que les « types référence » sont également appelés « types polymorphes ».

Si vous souhaitez vraiment un type de référence (classe de base, fonctions virtuelles), vous devez désactiver explicitement la copie, comme indiqué dans la classe `MyRefType` dans le code suivant.

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

Si vous compilez le code ci-dessus, l’erreur suivante se produit :

```Output
test.cpp(15) : error C2248: 'MyRefType::operator =' : cannot access private member declared in class 'MyRefType'
        meow.cpp(5) : see declaration of 'MyRefType::operator ='
        meow.cpp(3) : see declaration of 'MyRefType'
```

## <a name="value-types-and-move-efficiency"></a>Types valeur et efficacité du déplacement

La surcharge d’allocation de copie est évitée en raison de nouvelles optimisations de copie. Par exemple, lorsque vous insérez une chaîne au milieu d’un vecteur de chaînes, il n’y a aucune surcharge de réallocation de copie, mais uniquement un déplacement, même si elle entraîne une croissance du vecteur lui-même. Cela s’applique également aux autres opérations, par exemple en effectuant une opération d’ajout sur deux objets très volumineux. Comment activer ces optimisations d’opération de valeur ? Dans certains C++ compilateurs, le compilateur l’active pour vous implicitement, de la même façon que les constructeurs de copie peuvent être générés automatiquement par le compilateur. Toutefois, dans C++, votre classe doit « accepter » pour déplacer les assignations et les constructeurs en la déclarant dans votre définition de classe. Pour ce faire, il faut utiliser la référence rvalue double (& &) dans les déclarations de fonction membre appropriées et définir des méthodes d’assignation de déplacement et de constructeur de déplacement.  Vous devez également insérer le code correct pour « voler les boyaux » de l’objet source.

Comment décider si vous devez activer le déplacement ? Si vous savez déjà que vous avez besoin de la construction de copie activée, vous souhaiterez probablement activer le déplacement s’il peut être moins onéreux qu’une copie complète. Toutefois, si vous savez que vous avez besoin de la prise en charge du déplacement, cela ne signifie pas nécessairement que vous souhaitez que la copie soit activée. Ce dernier cas est appelé « type de déplacement uniquement ». `unique_ptr`est déjà présent dans la bibliothèque standard. En guise de note, l’ancien `auto_ptr` est déconseillé et a été remplacé par `unique_ptr` en raison de l’absence de prise en charge de la sémantique de déplacement dans C++la version précédente de.

En utilisant la sémantique de déplacement, vous pouvez retourner par valeur ou insérer-in-Middle. Le déplacement est une optimisation de la copie. Il est nécessaire d’allouer des tas comme solution de contournement. Considérez le pseudocode suivant :

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

### <a name="enabling-move-for-appropriate-value-types"></a>Activation du déplacement pour les types de valeur appropriés

Pour une classe de type valeur où Move peut être moins onéreux qu’une copie complète, activez la construction de déplacement et l’assignation de déplacement pour améliorer l’efficacité. Considérez le pseudocode suivant :

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

Si vous activez la création ou l’affectation de copie, activez également l’attribution ou la construction de déplacement si elle peut être moins coûteuse qu’une copie complète.

Certains types *non-valeur* sont de type déplacement seul, par exemple lorsque vous ne pouvez pas cloner une ressource, transférer uniquement la propriété. Par exemple : `unique_ptr`

## <a name="see-also"></a>Voir aussi

[C++système de type](../cpp/cpp-type-system-modern-cpp.md)<br/>
[Bienvenue dansC++](../cpp/welcome-back-to-cpp-modern-cpp.md)<br/>
[Informations de référence sur le langage C++](../cpp/cpp-language-reference.md)<br/>
[Bibliothèque standard C++](../standard-library/cpp-standard-library-reference.md)
