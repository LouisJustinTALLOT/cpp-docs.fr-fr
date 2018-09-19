---
title: Constructeurs (C++) | Microsoft Docs
ms.custom: ''
ms.date: 04/06/2018
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- constructors [C++]
- objects [C++], creating
- instance constructors
ms.assetid: 3e9f7211-313a-4a92-9584-337452e061a9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 08200320e30816ac45e6c91a14dc41508430cfae
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46069116"
---
# <a name="constructors-c"></a>Constructeurs (C++)

Pour personnaliser la façon dont les membres de classe sont initialisés ou d’appeler des fonctions lors de la création d’un objet de votre classe, définissez un *constructeur*. Un constructeur porte le même nom que la classe et n'a aucune valeur de retour. Vous pouvez définir des constructeurs surchargés autant que nécessaire pour personnaliser l’initialisation de différentes manières. En règle générale, les constructeurs avoir une accessibilité publique afin que le code en dehors de la hiérarchie de définition ou de l’héritage de classes peut créer des objets de la classe. Mais vous pouvez également déclarer un constructeur en tant que **protégé** ou **privé**.

Constructeurs peuvent éventuellement prendre un membre de liste d’init. Il s’agit d’un moyen plus efficace pour initialiser les membres de classe que l’affectation de valeurs dans le corps du constructeur. L’exemple suivant montre une classe `Box` avec trois constructeurs surchargés. Les deux dernières utilisent des listes de membres init :

```cpp
class Box {
public:
    // Default constructor
    Box() {}

    // Initalize a Box with equal dimensions (i.e. a cube)
    explicit Box(int i) : m_width(i), m_length(i), m_height(i) // member init list
    {}

    // Initialize a Box with custom dimensions
    Box(int width, int length, int height)
        : m_width(width), m_length(length), m_height(height)
    {}

    int Volume() { return m_width * m_length * m_height; }

private:
    // Will have value of 0 when default constructor is called.
    // If we didn't zero-init here, default constructor would
    // leave them uninitialized with garbage values.
    int m_width{ 0 };
    int m_length{ 0 };
    int m_height{ 0 };
};
```

Lorsque vous déclarez une instance d’une classe, le compilateur choisit le constructeur à appeler en fonction des règles de résolution de surcharge :

```cpp
int main()
{
    Box b; // Calls Box()

    // Using uniform initialization (preferred):
    Box b2 {5}; // Calls Box(int)
    Box b3 {5, 8, 12}; // Calls Box(int, int, int)

    // Using function-style notation:
    Box b4(2, 4, 6); // Calls Box(int, int, int)
}
```

- Les constructeurs peuvent être déclarées comme **inline**, [explicite](#explicit_constructors), **friend** ou [constexpr](#constexpr_constructors).
- Un constructeur peut initialiser un objet qui a été déclaré en tant que **const**, **volatile** ou **volatile const**. L’objet devient **const** après le constructeur.
- Pour définir un constructeur dans un fichier d’implémentation, attribuez-lui un nom qualifié à l’instar de toute autre fonction membre : `Box::Box(){...}`.

## <a name="member_init_list"></a> Listes d’initialiseurs de membres

Un constructeur peut avoir éventuellement une liste d’initialiseur de membre, qui initialise les membres de classe avant l’exécution du corps du constructeur. (Notez qu’une liste d’initialiseur de membre n’est pas la même chose qu’un *liste d’initialiseurs* de type [std::initializer_list\<T >](../standard-library/initializer-list-class.md).)

Une liste d’initialiseurs de membres est préférable d’utiliser assignation des valeurs dans le corps du constructeur, car elle initialise directement le membre. Dans l’exemple suivant montre l’initialiseur de membre de liste se compose de tous les **identifier(argument)** expressions après le signe deux-points :

```cpp
    Box(int width, int length, int height)
        : m_width(width), m_length(length), m_height(height)
    {}
```

L’identificateur doit faire référence à un membre de classe ; Il est initialisé avec la valeur de l’argument. L’argument peut être un des paramètres de constructeur, un appel de fonction ou un [std::initializer_list\<T >](../standard-library/initializer-list-class.md).

**const** membres et les membres de type référence doivent être initialisés dans la liste d’initialiseurs de membres.

Appels aux constructeurs de classe de base paramétrable doivent être créées à la liste d’initialiseurs pour vous assurer de que la classe de base est entièrement initialisée avant l’exécution du constructeur dérivé.

## <a name="default_constructors"></a> Constructeurs par défaut

*Constructeurs par défaut* ont généralement pas de paramètres, mais ils peuvent avoir des paramètres avec valeurs par défaut.

```cpp
class Box {
public:
    Box() { /*perform any required default initialization steps*/}

    // All params have default values
    Box (int w = 1, int l = 1, int h = 1): m_width(w), m_height(h), m_length(l){}
...
}
```

Les constructeurs par défaut sont un de la [fonctions membres spéciales](special-member-functions.md). Si aucun constructeur n’est déclaré dans une classe, le compilateur fournit implicite **inline** constructeur par défaut.

```cpp
#include <iostream>
using namespace std;

class Box {
public:
    int Volume() {return m_width * m_height * m_length;}
private:
    int m_width { 0 };
    int m_height { 0 };
    int m_length { 0 };
};

int main() {
    Box box1; // Invoke compiler-generated constructor
    cout << "box1.Volume: " << box1.Volume() << endl; // Outputs 0
}
```

Si vous comptez sur un constructeur implicite par défaut, veillez à initialiser les membres dans la définition de classe, comme indiqué dans l’exemple précédent. Sans ces initialiseurs, les membres serait non initialisées et l’appel Volume() produirait une valeur de la mémoire. En règle générale, il est conseillé pour initialiser les membres de cette façon même lorsque vous basez ne pas sur un constructeur par défaut implicite.

Vous pouvez empêcher le compilateur de générer un constructeur implicite par défaut en la définissant en tant que [supprimé](#explicitly_defaulted_and_deleted_constructors):

```cpp
    // Default constructor
    Box() = delete;

```

Un constructeur par défaut du compilateur générée sera soient marquée comme supprimées si aucun membre de classe n’est pas constructible à par défaut. Par exemple, tous les membres du type de classe et leurs membres de type de classe, doivent avoir un constructeur par défaut et les destructeurs sont accessibles. Tapez tous les membres de données de référence, ainsi que **const** membres doivent avoir un initialiseur de membre par défaut.

Lorsque vous appelez un constructeur par défaut du compilateur générée et que vous essayez d’utiliser des parenthèses, un avertissement est émis :

```cpp
class myclass{};
int main(){
myclass mc();     // warning C4930: prototyped function not called (was a variable definition intended?)
}
```

Voici un exemple de problème de type « Most Vexing Parse ». Puisque l'exemple d'expression peut être interprété comme la déclaration d'une fonction ou comme l'appel d'un constructeur par défaut, et puisque les analyseurs C++ privilégient les déclarations sur d'autres choses, l'expression est traitée comme une déclaration de fonction. Pour plus d’informations, consultez [Most Vexing Parse](http://en.wikipedia.org/wiki/Most_vexing_parse).

Si des constructeurs autres que ceux par défaut sont déclarés, le compilateur ne fournit pas de constructeur par défaut :

```cpp
class Box {
public:
    Box(int width, int length, int height)
        : m_width(width), m_length(length), m_height(height){}
private:
    int m_width;
    int m_length;
    int m_height;

};

int main(){

    Box box1(1, 2, 3);
    Box box2{ 2, 3, 4 };
    Box box3; // C2512: no appropriate default constructor available
}
```

Si une classe n'a aucun constructeur par défaut, un tableau d'objets de cette classe ne peut pas être construit seulement à l'aide de la syntaxe avec crochets. Par exemple, dans le bloc de code précédent, un tableau de Boxes ne peut pas être déclaré comme suit :

```cpp
Box boxes[3]; // C2512: no appropriate default constructor available
```

Toutefois, vous pouvez utiliser un ensemble de listes d’initialiseurs pour initialiser un tableau d’objets de la zone :

```cpp
Box boxes[3]{ { 1, 2, 3 }, { 4, 5, 6 }, { 7, 8, 9 } };
```

Pour plus d’informations, consultez [initialiseurs](initializers.md).

## <a name="copy_and_move_constructors"></a> Constructeurs de copie

Un *constructeur de copie* Initialise un objet en copiant les valeurs de membre d’un objet du même type. Si vos membres de classe sont tous les types simples tels que des valeurs scalaires, le constructeur de copie généré par le compilateur est suffisant et il est inutile de définir votre propre. Si votre classe requiert une initialisation plus complexe, vous devez implémenter un constructeur de copie personnalisé. Par exemple, si un membre de classe est un pointeur puis vous devez définir un constructeur de copie pour allouer la nouvelle mémoire et copiez les valeurs à partir de l’autre pointe à objet. Le constructeur de copie généré par le compilateur copie simplement le pointeur, afin que le nouveau pointeur toujours pointe vers l’autre emplacement de mémoire.

Un constructeur de copie peut avoir une de ces signatures :

```cpp
    Box(Box& other); // Avoid if possible--allows modification of other.
    Box(const Box& other);
    Box(volatile Box& other);
    Box(volatile const Box& other);

    // Additional parameters OK if they have default values
    Box(Box& other, int i = 42, string label = "Box");
```

Lorsque vous définissez un constructeur de copie, vous devez également définir un opérateur d’assignation de copie (=). Pour plus d’informations, consultez [attribution](assignment.md) et [constructeurs de copie et opérateurs d’assignation de copie](copy-constructors-and-copy-assignment-operators-cpp.md).

Vous pouvez empêcher votre objet d’être copiés en définissant le constructeur de copie comme étant supprimé :

```cpp
    Box (const Box& other) = delete;
```

Essayez de copier l’objet génère l’erreur *C2280 : tentative de référencement d’une fonction supprimée*.

## <a name="move_constructors"></a> Constructeurs de déplacement

Un *constructeur de déplacement* est une fonction membre spéciale qui déplace la propriété des données d’un objet existant à une nouvelle variable sans copier les données d’origine. Il prend une référence rvalue comme son premier paramètre, et tous les paramètres supplémentaires doivent avoir des valeurs par défaut. Constructeurs de déplacement peuvent augmenter considérablement l’efficacité de votre programme lors de la transmission autour des objets volumineux. Un constructeur de déplacement accepte une référence rvalue en tant que son premier paramètre. Tous les autres paramètres doivent avoir des valeurs par défaut.

```cpp
Box(Box&& other);
```

Le compilateur choisit un constructeur de déplacement dans certaines situations où l’objet est initialisé par un autre objet du même type qui est sur le point d’être détruit et n’a plus besoin il ressources. L’exemple suivant montre un cas lorsqu’un constructeur de déplacement est sélectionné par la résolution de surcharge. La variable *boîte* retourné par get_Box() est un *xvalue* (valeur arrivant à expiration) qui est sur le point de sortir de portée. Pour fournir la motivation pour cet exemple, faisons boîte un grand vecteur de chaînes qui représentent son contenu. Au lieu de copier le vecteur et ses chaînes, le constructeur de déplacement « vole » il à partir de la valeur d’expiration « boîte » afin que le vecteur appartient désormais au nouvel objet. L’appel à `std::move` est tout ce qui est nécessaire, car les deux `vector` et `string` classes implémentent leurs propres constructeurs de déplacement.

```cpp
#include <iostream>
#include <vector>
#include <string>
#include <algorithm>
using namespace std;

class Box {
public:
    Box() { std::cout << "default" << std::endl; }
    Box(int width, int height, int length)
       : m_width(width), m_height(height), m_length(length)
    {
        std::cout << "int,int,int" << std::endl;
    }
    Box(Box& other)
       : m_width(other.m_width), m_height(other.m_height), m_length(other.m_length)
    {
        std::cout << "copy" << std::endl;
    }
    Box(Box&& other) : m_width(other.m_width), m_height(other.m_height), m_length(other.m_length)
    {
        m_contents = std::move(other.m_contents);
        std::cout << "move" << std::endl;
    }
    int Volume() { return m_width * m_height * m_length; }
    void Add_Item(string item) { m_contents.push_back(item); }
    void Get_Contents()
    {
        for (const auto& item : m_contents)
        {
            cout << item << " ";
        }
    }
private:
    int m_width{ 0 };
    int m_height{ 0 };
    int m_length{ 0 };
    vector<string> m_contents;
};

Box get_Box()
{
    Box b(5, 10, 18); // "int,int,int"
    b.Add_Item("Toupee");
    b.Add_Item("Megaphone");
    b.Add_Item("Suit");

    return b;
}

int main()
{
    Box b; // "default"
    Box b1(b); // "copy"
    Box b2(get_Box()); // "move"
    cout << "b2 contents: ";
    b2.Get_Contents(); // Prove that we have all the values

    char ch;
    cin >> ch; // keep window open
    return 0;
}
```

Si une classe ne définit pas un constructeur de déplacement, le compilateur génère un implicit s’il n’existe aucun constructeur de copie déclaré par l’utilisateur, opérateur d’assignation de copie, opérateur d’assignation de déplacement ou un destructeur. Si aucun constructeur de déplacement explicite ou implicite n’est définie, les opérations qui seraient sinon utiliser un constructeur de déplacement utilisent le constructeur de copie à la place. Si une classe déclare un constructeur de déplacement ou un opérateur d’assignation de déplacement, le constructeur de copie déclarée implicitement est défini comme étant supprimé.

Un constructeur de déplacement déclarée implicitement est défini comme étant supprimé si tous les membres qui sont des types de classe ne disposent pas de destructeur ou que le compilateur ne peut pas déterminer le constructeur à utiliser pour l’opération de déplacement.

Pour plus d’informations sur la façon d’écrire un constructeur de déplacement non triviale, consultez [constructeurs de déplacement et opérateurs d’assignation déplacer (C++)](../cpp/move-constructors-and-move-assignment-operators-cpp.md).

## <a name="explicitly_defaulted_and_deleted_constructors"></a> Constructeurs par défaut et supprimées explicitement

Vous pouvez explicitement *par défaut* constructeurs de copie, constructeurs par défaut, des constructeurs de déplacement, opérateurs d’assignation de copier, déplacer des opérateurs d’assignation et les destructeurs. Vous pouvez explicitement *supprimer* toutes les fonctions membres spéciales.

```cpp
class Box
{
public:
    Box2() = delete;
    Box2(const Box2& other) = default;
    Box2& operator=(const Box2& other) = default;
    Box2(Box2&& other) = default;
    Box2& operator=(Box2&& other) = default;
    //...
};
```

Pour plus d’informations, consultez [explicitement une valeur par défaut et les fonctions supprimées](../cpp/explicitly-defaulted-and-deleted-functions.md).

## <a name="constexpr_constructors"></a> constructeurs constexpr

Un constructeur peut être déclaré comme [constexpr](constexpr-cpp.md) si

- Il est soit déclarée comme une valeur par défaut, sans quoi il satisfait à toutes les conditions pour [fonctions constexpr](constexpr-cpp.md#constexpr_functions) en général ;
- la classe n’a aucune classe de base virtuelle ;
- chacun des paramètres est un [type littéral](trivial-standard-layout-and-pod-types.md#literal_types);
- le corps n’est pas une fonction try-block ;
- tous les membres de données non statiques et les sous-objets de classe de base sont initialisés ;
- Si la classe est (a) une union des membres de type variant ou (b) a des unions anonymes, uniquement un membre de l’union est initialisé ;
- chaque membre de données non statiques de type de classe et tous les sous-objets classe de base ont un constructeur constexpr

## <a name="init_list_constructors"></a> Constructeurs de liste d’initialiseur

Si un constructeur accepte un [std::initializer_list\<T\> ](../standard-library/initializer-list-class.md) comme son paramètre et tous les autres paramètres ont des arguments par défaut, ce constructeur est sélectionné dans la résolution de surcharge lorsque la classe est instancié via une initialisation directe. Vous pouvez utiliser initializer_list pour initialiser un membre qui peut l’accepter. Par exemple, supposons que la classe de boîte (expliquée précédemment) a un `std::vector<string>` membre `m_contents`. Vous pouvez fournir un constructeur comme suit :

```cpp
    Box(initializer_list<string> list, int w = 0, int h = 0, int l = 0)
        : m_contents(list), m_width(w), m_height(h), m_length(l)
{}
```

Puis créez des objets de zone comme suit :

```cpp
    Box b{ "apples", "oranges", "pears" }; // or ...
    Box b2(initializer_list<string> { "bread", "cheese", "wine" }, 2, 4, 6);
```

## <a name="explicit_constructors"></a> Constructeurs explicites

Si une classe a un constructeur avec un paramètre unique, ou si tous les paramètres sauf un ont une valeur par défaut, le type de paramètre peut être implicitement converti en type de classe. Par exemple, si la classe `Box` a un constructeur semblable au suivant :

```cpp
Box(int size): m_width(size), m_length(size), m_height(size){}
```

Il est possible d'initialiser un objet Box comme suit :

```cpp
Box b = 42;
```

Ou de passer une valeur int à une fonction qui accepte un objet Box :

```cpp
class ShippingOrder
{
public:
    ShippingOrder(Box b, double postage) : m_box(b), m_postage(postage){}

private:
    Box m_box;
    double m_postage;
}
//elsewhere...
    ShippingOrder so(42, 10.8);
```

Ces conversions peuvent être utiles dans certains cas mais, le plus souvent, elles peuvent entraîner des erreurs subtiles mais graves dans votre code. En règle générale, vous devez utiliser le **explicite** mot clé sur un constructeur (et des opérateurs définis par l’utilisateur) pour éviter ce genre de conversion de type implicite :

```cpp
explicit Box(int size): m_width(size), m_length(size), m_height(size){}
```

Si le constructeur est explicite, cette ligne entraîne une erreur du compilateur : `ShippingOrder so(42, 10.8);`.  Pour plus d’informations, consultez [les Conversions de types définis par l’utilisateur](../cpp/user-defined-type-conversions-cpp.md).

## <a name="order_of_construction"></a> Ordre de construction

Un constructeur effectue son travail dans l'ordre suivant :

1. Il appelle les constructeurs membres et de classe de base dans l'ordre de déclaration.

2. Si la classe est dérivée de classes de base virtuelles, il initialise les pointeurs de base virtuels de l'objet.

3. Si la classe possède ou hérite des fonctions virtuelles, il initialise les pointeurs de fonction virtuelle de l'objet. Les pointeurs de fonction virtuelle pointent sur la table de fonctions virtuelles de la classe pour permettre la liaison correcte des appels de fonction virtuelle au code.

4. Il exécute le code dans son corps de fonction.

L'exemple suivant montre l'ordre dans lequel les constructeurs de classe de base et membres sont appelés dans le constructeur pour une classe dérivée. D'abord, le constructeur de base est appelé, puis les membres de classe de base sont initialisés dans l'ordre dans lequel ils apparaissent dans la déclaration de classe, puis le constructeur dérivé est appelé.

```cpp
#include <iostream>

using namespace std;

class Contained1 {
public:
    Contained1() { cout << "Contained1 ctor\n"; }
};

class Contained2 {
public:
    Contained2() { cout << "Contained2 ctor\n"; }
};

class Contained3 {
public:
    Contained3() { cout << "Contained3 ctor\n"; }
};

class BaseContainer {
public:
    BaseContainer() { cout << "BaseContainer ctor\n"; }
private:
    Contained1 c1;
    Contained2 c2;
};

class DerivedContainer : public BaseContainer {
public:
    DerivedContainer() : BaseContainer() { cout << "DerivedContainer ctor\n"; }
private:
    Contained3 c3;
};

int main() {
    DerivedContainer dc;
}
```

Voici la sortie :

```Output
Contained1 ctor
Contained2 ctor
BaseContainer ctor
Contained3 ctor
DerivedContainer ctor
```

Un constructeur de classe dérivée appelle toujours un constructeur de classe de base, afin de pouvoir s'appuyer sur des classes de base complètement construites avant d'effectuer tout travail supplémentaire. Les constructeurs de classe de base sont appelés dans l’ordre de dérivation — par exemple, si `ClassA` est dérivée de `ClassB`, qui est dérivée de `ClassC`, le `ClassC` constructeur est appelé en premier, puis le `ClassB` constructeur, le `ClassA` constructeur.

Si une classe de base n'a pas de constructeur par défaut, vous devez fournir les paramètres du constructeur de classe de base dans le constructeur de classe dérivée :

```cpp
class Box {
public:
    Box(int width, int length, int height){
       m_width = width;
       m_length = length;
       m_height = height;
    }

private:
    int m_width;
    int m_length;
    int m_height;
};

class StorageBox : public Box {
public:
    StorageBox(int width, int length, int height, const string label&) : Box(width, length, height){
        m_label = label;
    }
private:
    string m_label;
};

int main(){

    const string aLabel = "aLabel";
    StorageBox sb(1, 2, 3, aLabel);
}
```

Si un constructeur lève une exception, l'ordre de destruction est l'inverse de l'ordre de construction :

1. Le code dans le corps de la fonction constructeur est déroulé.

1. Les objets de classe de base et membres sont détruits dans l'ordre inverse de déclaration.

1. Si le constructeur ne délègue pas, tous les membres et objets de classe de base entièrement construits sont détruits. Toutefois, l'objet lui-même n'étant pas complètement construit, le destructeur n'est pas exécuté.

### <a name="constructors-for-classes-that-have-multiple-inheritance"></a>Constructeurs pour les classes ayant un héritage multiple

Si une classe est dérivée de plusieurs classes de base, les constructeurs de classe de base sont appelés dans l'ordre dans lequel ils sont répertoriés dans la déclaration de la classe dérivée :

```cpp
#include <iostream>
using namespace std;

class BaseClass1 {
public:
    BaseClass1() { cout << "BaseClass1 ctor\n"; }
};
class BaseClass2 {
public:
    BaseClass2() { cout << "BaseClass2 ctor\n"; }
};
class BaseClass3 {
public:
    BaseClass3() { cout << "BaseClass3 ctor\n"; }
};
class DerivedClass : public BaseClass1,
                     public BaseClass2,
                     public BaseClass3
                     {
public:
    DerivedClass() { cout << "DerivedClass ctor\n"; }
};

int main() {
    DerivedClass dc;
}
```

Vous devez obtenir la sortie suivante :

```Output
BaseClass1 ctor
BaseClass2 ctor
BaseClass3 ctor
DerivedClass ctor
```

## <a name="virtual_functions_in_constructors"></a> Fonctions virtuelles dans les constructeurs

Nous vous recommandons d'être prudent lorsque vous appelez des fonctions virtuelles dans des constructeurs. Le constructeur de classe de base étant toujours appelé avant le constructeur de classe dérivée, la fonction qui est appelée dans le constructeur de base est la version de classe de base, et non la version de classe dérivée. Dans l'exemple suivant, la construction d'un objet `DerivedClass` provoque l'exécution de l'implémentation `BaseClass` de `print_it()` avant que le constructeur `DerivedClass` provoque l'exécution de l'implémentation `DerivedClass` de `print_it()` :

```cpp
#include <iostream>
using namespace std;

class BaseClass{
public:
    BaseClass(){
        print_it();
    }
    virtual void print_it() {
        cout << "BaseClass print_it" << endl;
    }
};

class DerivedClass : public BaseClass {
public:
    DerivedClass() {
        print_it();
    }
    virtual void print_it(){
        cout << "Derived Class print_it" << endl;
    }
};

int main() {

    DerivedClass dc;
}
```

Voici la sortie :

```Output
BaseClass print_it
Derived Class print_it
```

## <a name="delegating_constructors"></a> Constructeurs de délégation

Un *délégation constructeur* appelle un autre constructeur dans la même classe pour effectuer une partie du travail de l’initialisation. Cela est utile lorsque vous avez plusieurs constructeurs ayant effectuer un travail similaire. Vous pouvez écrire la logique principale dans un constructeur et l’appeler à partir d’autres. Dans l’exemple simple suivant, Box(int) délègue son travail à Box(int,int,int) :

```cpp
class Box {
public:
    // Default constructor
    Box() {}

    // Initalize a Box with equal dimensions (i.e. a cube)
    Box(int i) :  Box(i, i, i);  // delegating constructor
    {}

    // Initialize a Box with custom dimensions
    Box(int width, int length, int height)
        : m_width(width), m_length(length), m_height(height)
    {}
    //... rest of class as before
};
```


L'objet créé par les constructeurs est entièrement initialisé dès qu'un constructeur est terminé. Pour plus d’informations, consultez [d’initialisation uniforme et constructeurs de délégation](../cpp/uniform-initialization-and-delegating-constructors.md).

## <a name="inheriting_constructors"></a> Constructeurs d’héritage (C ++ 11)

Une classe dérivée peut hériter les constructeurs d’une classe de base directe en utilisant un **à l’aide de** déclaration, comme indiqué dans l’exemple suivant :

```cpp
#include <iostream>
using namespace std;

class Base
{
public:
    Base() { cout << "Base()" << endl; }
    Base(const Base& other) { cout << "Base(Base&)" << endl; }
    explicit Base(int i) : num(i) { cout << "Base(int)" << endl; }
    explicit Base(char c) : letter(c) { cout << "Base(char)" << endl; }

private:
    int num;
    char letter;
};

class Derived : Base
{
public:
    // Inherit all constructors from Base
    using Base::Base;

private:
    // Can't initialize newMember from Base constructors.
    int newMember{ 0 };
};

int main()
{
    cout << "Derived d1(5) calls: ";
    Derived d1(5);
    cout << "Derived d1('c') calls: ";
    Derived d2('c');
    cout << "Derived d3 = d2 calls: " ;
    Derived d3 = d2;
    cout << "Derived d4 calls: ";
    Derived d4;
}

/* Output:
Derived d1(5) calls: Base(int)
Derived d1('c') calls: Base(char)
Derived d3 = d2 calls: Base(Base&)
Derived d4 calls: Base()*/
```

**Visual Studio 2017 version 15.7 et ultérieure**: le **à l’aide de** instruction dans **/std : c ++ 17** mode place dans la portée de tous les constructeurs de la classe de base, sauf ceux qui ont une signature identique aux constructeurs dans la classe dérivée. En général, il est préférable d'utiliser les constructeurs d'héritage quand la classe dérivée ne déclare aucun nouveau constructeur ni aucune nouvelle donnée membre. Voir aussi [améliorations dans Visual Studio 2017 version 15.7](../cpp-conformance-improvements-2017.md#improvements_157).

Un modèle de classe peut hériter de tous les constructeurs d’un argument de type si ce type spécifie une classe de base :

```cpp
template< typename T >
class Derived : T {
    using T::T;   // declare the constructors from T
    // ...
};
```

Une classe dérivée ne peut pas hériter de plusieurs classes de base si ces classes de base possèdent des constructeurs qui ont une signature identique.

## <a name="constructors_in_composite_classes"></a> Constructeurs et classes composites

Les classes qui contiennent des membres de type de classe sont appelés *classes composites*. Lorsqu'un membre de type classe d'une classe composite est créé, le constructeur est appelé avant le propre constructeur de la classe. Lorsqu'une classe contenue n'a pas de constructeur par défaut, vous devez utiliser une liste d'initialisation dans le constructeur de la classe composite. Dans l'exemple `StorageBox` précédent, si vous remplacez le type de la variable membre `m_label` par une nouvelle classe `Label`, vous devez appeler le constructeur de classe de base et initialiser la variable `m_label` dans le constructeur `StorageBox` :

```cpp
class Label {
public:
    Label(const string& name, const string& address) { m_name = name; m_address = address; }
    string m_name;
    string m_address;
};

class StorageBox : public Box {
public:
    StorageBox(int width, int length, int height, Label label)
        : Box(width, length, height), m_label(label){}
private:
    Label m_label;
};

int main(){
// passing a named Label
    Label label1{ "some_name", "some_address" };
    StorageBox sb1(1, 2, 3, label1);

    // passing a temporary label
    StorageBox sb2(3, 4, 5, Label{ "another name", "another address" });

    // passing a temporary label as an initializer list
    StorageBox sb3(1, 2, 3, {"myname", "myaddress"});
}
```
