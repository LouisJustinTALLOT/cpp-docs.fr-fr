---
title: Types de valeur (Modern C++)
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: f63bb62c-60da-40d5-ac14-4366608fe260
ms.openlocfilehash: 32cdb29ec1c59081ad7e0493888f290f21561d2b
ms.sourcegitcommit: a1fad0a266b20b313364a74b16c9ac45d089b1e9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/11/2019
ms.locfileid: "54220346"
---
# <a name="value-types-modern-c"></a>Types de valeur (Modern C++)

Les classes C++ sont par types de valeur par défaut. Cette rubrique fournit une présentation des types valeur et des problèmes liés à leur utilisation.

## <a name="value-vs-reference-types"></a>Valeur et types référence

Comme indiqué précédemment, les classes C++ sont en types de valeur par défaut. Elles peuvent être spécifiées en tant que types de référence, qui permettent à un comportement polymorphe prendre en charge de programmation orientée objet. Les types valeur sont parfois considérés du point de vue du contrôle de mémoire et de mise en page, alors que les types référence sont des classes de base et de fonctions virtuelles polymorphe à des fins. Par défaut, les types valeur sont copiables, ce qui signifie qu’il y a toujours un constructeur de copie et un opérateur d’assignation de copie. Pour les types référence, vous rendez la classe non COPIABLE (désactiver le constructeur de copie et l’opérateur d’assignation de copie) et utiliser un destructeur virtuel, qui prend en charge leur polymorphisme prévu. Types valeur sont également sur le contenu, ce qui, lorsqu’ils sont copiés, toujours vous donne deux valeurs distinctes qui peuvent être modifiées séparément. Types référence concernent l’identité - le type d’objet s’agit-il ? Pour cette raison, « types référence » sont également appelés « types polymorphes ».

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

Compilation du code ci-dessus entraîne l’erreur suivante :

```Output
test.cpp(15) : error C2248: 'MyRefType::operator =' : cannot access private member declared in class 'MyRefType'
        meow.cpp(5) : see declaration of 'MyRefType::operator ='
        meow.cpp(3) : see declaration of 'MyRefType'
```

## <a name="value-types-and-move-efficiency"></a>Types valeur et déplacer l’efficacité

Surcharge d’allocation de copie est évitée en raison de nouvelles optimisations de copie. Par exemple, lorsque vous insérez une chaîne au milieu d’un vecteur de chaînes, il n’y aura aucune surcharge de réallocation de copie, uniquement un déplacement - même s’il en résulte une augmentation du vecteur proprement dit. Cela s’applique également à d’autres opérations, par exemple effectuer une opération d’ajout sur deux objets très volumineux. Comment faire pour activer ces optimisations d’opération de valeur ? Dans certains compilateurs C++, le compilateur active cette option pour vous implicitement, de la même manière que les constructeurs de copie peuvent être générées automatiquement par le compilateur. Toutefois, dans Visual C++, votre classe devra « opt-in » pour déplacer des constructeurs et affectation en le déclarant dans votre définition de classe. Cela est accompli en utilisant la double perluète (& &) référence rvalue dans le membre approprié définition de constructeur de déplacement et les déclarations de fonctions et méthodes d’affectation de déplacement.  Vous devez également insérer le code correct pour « subtiliser finalement voir le fonctionnement « hors de l’objet source.

Comment décider si vous devez déplacer activé ? Si vous connaissez déjà que vous devez copier la construction activée, vous souhaitez probablement déplacer est activée si elle peut être moins cher que d’une copie complète. Toutefois, si vous savez que vous avez besoin de déplacer la prise en charge, n’implique pas forcément copie activée. Ce dernier cas est appelé un « type move-only ». Un exemple déjà dans la bibliothèque standard est `unique_ptr`. Note à part, l’ancien `auto_ptr` est déconseillé et a été remplacé par `unique_ptr` exactement en raison de l’absence de prise en charge la sémantique de déplacement dans la version précédente de C++.

En utilisant la sémantique de déplacement, vous pouvez en valeur de retour ou insertion dans intermédiaire. Déplacement est une optimisation de la copie. Il est nécessaire pour l’allocation de tas pour résoudre ce problème. Considérez le pseudocode suivant :

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

### <a name="enabling-move-for-appropriate-value-types"></a>L’activation de déplacement pour les types valeur appropriée

Pour une classe de type valeur où le déplacement peut être moins cher que d’une copie complète, permettent la construction de déplacement et déplacer affectation par souci d’efficacité. Considérez le pseudocode suivant :

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

Si vous activez l’assignation de la construction de copie, activer également la construction/assignation de déplacement si elle peut être moins cher que d’une copie complète.

Certains *non-valeur* types sont move-uniquement, tels que lorsque vous ne pouvez pas cloner une ressource, uniquement à transférer la propriété. Par exemple : `unique_ptr`

## <a name="section"></a>Section

Contenu

## <a name="see-also"></a>Voir aussi

[Système de type C++ (C++ moderne)](../cpp/cpp-type-system-modern-cpp.md)<br/>
[Bienvenue dans C++ (C++ moderne)](../cpp/welcome-back-to-cpp-modern-cpp.md)<br/>
[Informations de référence sur le langage C++](../cpp/cpp-language-reference.md)<br/>
[Bibliothèque C++ standard](../standard-library/cpp-standard-library-reference.md)
