---
title: Constructeurs (C++)
ms.date: 10/17/2019
helpviewer_keywords:
- constructors [C++]
- objects [C++], creating
- instance constructors
ms.assetid: 3e9f7211-313a-4a92-9584-337452e061a9
ms.openlocfilehash: 799be6cfd4b14061ba61586f361dd884ad59224c
ms.sourcegitcommit: 8178d22701047d24f69f10d01ba37490e3d67241
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72587940"
---
# <a name="constructors-c"></a>Constructeurs (C++)

Pour personnaliser la façon dont les membres de classe sont initialisés, ou pour appeler des fonctions quand un objet de votre classe est créé, définissez un *constructeur*. Un constructeur porte le même nom que la classe et n'a aucune valeur de retour. Vous pouvez définir autant de constructeurs surchargés que nécessaire pour personnaliser l’initialisation de différentes façons. En règle générale, les constructeurs ont une accessibilité publique afin que le code en dehors de la définition de classe ou de la hiérarchie d’héritage puisse créer des objets de la classe. Toutefois, vous pouvez également déclarer un constructeur comme **protected** ou **Private**.

Les constructeurs peuvent éventuellement prendre une liste init de membre. Il s’agit d’un moyen plus efficace d’initialiser les membres de classe que d’assigner des valeurs dans le corps du constructeur. L’exemple suivant montre une classe `Box` avec trois constructeurs surchargés. Les deux derniers utilisent les listes init des membres :

```cpp
class Box {
public:
    // Default constructor
    Box() {}

    // Initialize a Box with equal dimensions (i.e. a cube)
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

Quand vous déclarez une instance d’une classe, le compilateur choisit le constructeur à appeler en fonction des règles de résolution de surcharge :

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

- Les constructeurs peuvent être déclarés comme **inline**, [Explicit](#explicit_constructors), **Friend** ou [constexpr](#constexpr_constructors).
- Un constructeur peut initialiser un objet qui a été déclaré comme **const**, **volatile** ou **const volatile**. L’objet devient **const** une fois le constructeur terminé.
- Pour définir un constructeur dans un fichier d’implémentation, donnez-lui un nom qualifié comme avec toute autre fonction membre : `Box::Box(){...}`.

## <a name="member_init_list"></a>Listes d’initialiseurs de membres

Un constructeur peut éventuellement avoir une liste d’initialiseurs de membre, qui initialise les membres de classe avant l’exécution du corps du constructeur. (Notez qu’une liste d’initialiseurs de membre n’est pas la même chose qu’une *liste d’initialiseurs* de type [std :: initializer_list \<T >](../standard-library/initializer-list-class.md).)

Il est préférable d’utiliser une liste d’initialiseurs de membre pour assigner des valeurs dans le corps du constructeur, car il initialise directement le membre. Dans l’exemple suivant, la liste d’initialiseurs de membre se compose de toutes les expressions d' **identificateur (argument)** après les deux-points :

```cpp
    Box(int width, int length, int height)
        : m_width(width), m_length(length), m_height(height)
    {}
```

L’identificateur doit faire référence à un membre de classe ; elle est initialisée avec la valeur de l’argument. L’argument peut être l’un des paramètres de constructeur, un appel de fonction ou un [std :: initializer_list \<T >](../standard-library/initializer-list-class.md).

les membres **const** et les membres du type référence doivent être initialisés dans la liste d’initialiseurs de membres.

Les appels aux constructeurs de classes de base paramétrables doivent être effectués dans la liste d’initialiseurs pour garantir que la classe de base est entièrement initialisée avant l’exécution du constructeur dérivé.

## <a name="default_constructors"></a>Constructeurs par défaut

Les *constructeurs par défaut* n’ont généralement pas de paramètres, mais ils peuvent avoir des paramètres avec des valeurs par défaut.

```cpp
class Box {
public:
    Box() { /*perform any required default initialization steps*/}

    // All params have default values
    Box (int w = 1, int l = 1, int h = 1): m_width(w), m_height(h), m_length(l){}
...
}
```

Les constructeurs par défaut sont l’une des [fonctions membres spéciales](special-member-functions.md). Si aucun constructeur n’est déclaré dans une classe, le compilateur fournit un constructeur par défaut **inline** implicite.

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

Si vous vous fiez à un constructeur par défaut implicite, veillez à initialiser les membres dans la définition de classe, comme indiqué dans l’exemple précédent. Sans ces initialiseurs, les membres ne sont pas initialisés et l’appel de volume () produit une valeur de garbage collection. En général, il est conseillé d’initialiser les membres de cette manière, même si vous ne vous fiez pas à un constructeur par défaut implicite.

Vous pouvez empêcher le compilateur de générer un constructeur par défaut implicite en le définissant comme [supprimé](#explicitly_defaulted_and_deleted_constructors):

```cpp
    // Default constructor
    Box() = delete;
```

Un constructeur par défaut généré par le compilateur sera défini comme supprimé si tous les membres de la classe ne sont pas de type constructible par défaut. Par exemple, tous les membres de type classe et leurs membres de type classe doivent avoir un constructeur par défaut et des destructeurs qui sont accessibles. Tous les membres de données de type référence, ainsi que les membres **const** doivent avoir un initialiseur de membre par défaut.

Quand vous appelez un constructeur par défaut généré par le compilateur et que vous essayez d’utiliser des parenthèses, un avertissement est émis :

```cpp
class myclass{};
int main(){
myclass mc();     // warning C4930: prototyped function not called (was a variable definition intended?)
}
```

Voici un exemple de problème de type « Most Vexing Parse ». Puisque l'exemple d'expression peut être interprété comme la déclaration d'une fonction ou comme l'appel d'un constructeur par défaut, et puisque les analyseurs C++ privilégient les déclarations sur d'autres choses, l'expression est traitée comme une déclaration de fonction. Pour plus d’informations, consultez [la plupart des vexing parse](https://en.wikipedia.org/wiki/Most_vexing_parse).

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

Toutefois, vous pouvez utiliser un ensemble de listes d’initialiseurs pour initialiser un tableau d’objets Box :

```cpp
Box boxes[3]{ { 1, 2, 3 }, { 4, 5, 6 }, { 7, 8, 9 } };
```

Pour plus d’informations, consultez [initialiseurs](initializers.md).

## <a name="copy_and_move_constructors"></a>Constructeurs de copie

Un *constructeur de copie* Initialise un objet en copiant les valeurs de membre à partir d’un objet du même type. Si vos membres de classe sont tous des types simples tels que des valeurs scalaires, le constructeur de copie généré par le compilateur est suffisant et vous n’avez pas besoin de définir les vôtres. Si votre classe requiert une initialisation plus complexe, vous devez implémenter un constructeur de copie personnalisé. Par exemple, si un membre de classe est un pointeur, vous devez définir un constructeur de copie pour allouer de la nouvelle mémoire et copier les valeurs de l’objet pointé vers l’autre. Le constructeur de copie généré par le compilateur copie simplement le pointeur, de sorte que le nouveau pointeur pointe toujours vers l’emplacement de mémoire de l’autre.

Un constructeur de copie peut avoir l’une des signatures suivantes :

```cpp
    Box(Box& other); // Avoid if possible--allows modification of other.
    Box(const Box& other);
    Box(volatile Box& other);
    Box(volatile const Box& other);

    // Additional parameters OK if they have default values
    Box(Box& other, int i = 42, string label = "Box");
```

Lorsque vous définissez un constructeur de copie, vous devez également définir un opérateur d’assignation de copie (=). Pour plus d’informations, consultez constructeurs d' [assignation](assignment.md) et de [copie et opérateurs d’assignation de copie](copy-constructors-and-copy-assignment-operators-cpp.md).

Vous pouvez empêcher la copie de votre objet en définissant le constructeur de copie comme supprimé :

```cpp
    Box (const Box& other) = delete;
```

La tentative de copie de l’objet génère *une erreur C2280 : tentative de référencement d’une fonction supprimée*.

## <a name="move_constructors"></a>Constructeurs de déplacement

Un *constructeur de déplacement* est une fonction membre spéciale qui déplace la propriété des données d’un objet existant vers une nouvelle variable sans copier les données d’origine. Elle prend une référence rvalue comme premier paramètre, et tous les paramètres supplémentaires doivent avoir des valeurs par défaut. Les constructeurs de déplacement peuvent augmenter considérablement l’efficacité de votre programme lors du passage autour d’objets volumineux.

```cpp
Box(Box&& other);
```

Le compilateur choisit un constructeur de déplacement dans certaines situations où l’objet est initialisé par un autre objet du même type qui va être détruit et n’a plus besoin de ses ressources. L’exemple suivant illustre un cas où un constructeur de déplacement est sélectionné par la résolution de surcharge. Dans le constructeur qui appelle `get_Box()`, la valeur retournée est un *xValue* (valeur d’expiration). Elle n’est assignée à aucune variable et est donc sur le point de sortir de la portée. Pour fournir de la motivation pour cet exemple, nous allons donner à Box un grand vecteur de chaînes qui représentent son contenu. Au lieu de copier le vecteur et ses chaînes, le constructeur de déplacement le « vole » de la valeur d’expiration « Box » afin que le vecteur appartienne à présent au nouvel objet. L’appel à `std::move` est tout ce qui est nécessaire, car les classes `vector` et `string` implémentent leurs propres constructeurs de déplacement.

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

Si une classe ne définit pas de constructeur de déplacement, le compilateur en génère un implicite s’il n’existe aucun constructeur de copie déclaré par l’utilisateur, opérateur d’assignation de copie, opérateur d’assignation de déplacement ou destructeur. Si aucun constructeur de déplacement explicite ou implicite n’est défini, les opérations qui, autrement, utiliseraient un constructeur de déplacement, utilisent le constructeur de copie à la place. Si une classe déclare un constructeur de déplacement ou un opérateur d’assignation de déplacement, le constructeur de copie implicitement déclaré est défini comme supprimé.

Un constructeur de déplacement déclaré implicitement est défini comme supprimé si tous les membres qui sont des types de classe n’ont pas de destructeur ou si le compilateur ne peut pas déterminer le constructeur à utiliser pour l’opération de déplacement.

Pour plus d’informations sur la façon d’écrire un constructeur de déplacement non trivial, consultez [constructeurs de déplacement et opérateurs d'C++assignation de déplacement ()](../cpp/move-constructors-and-move-assignment-operators-cpp.md).

## <a name="explicitly_defaulted_and_deleted_constructors"></a>Constructeurs explicitement par défaut et supprimés

Vous pouvez explicitement définir *par défaut* des constructeurs de copie, des constructeurs par défaut, des constructeurs de déplacement, des opérateurs d’assignation de copie, des opérateurs d’assignation de déplacement et des destructeurs. Vous pouvez *supprimer* de manière explicite toutes les fonctions membres spéciales.

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

Pour plus d’informations, consultez [fonctions explicitement supprimées et par défaut](../cpp/explicitly-defaulted-and-deleted-functions.md).

## <a name="constexpr_constructors"></a>constructeurs constexpr

Un constructeur peut être déclaré comme [constexpr](constexpr-cpp.md) si

- elle est déclarée comme étant définie par défaut ou elle répond à toutes les conditions pour les [fonctions constexpr](constexpr-cpp.md#constexpr_functions) en général ;
- la classe n’a aucune classe de base virtuelle ;
- chacun des paramètres est un [type littéral](trivial-standard-layout-and-pod-types.md#literal_types);
- le corps n’est pas un bloc try de fonction ;
- tous les membres de données non statiques et les sous-objets de classe de base sont initialisés ;
- Si la classe est (a) une Union ayant des membres variants, ou (b) a des unions anonymes, seul l’un des membres de l’Union est initialisé ;
- chaque membre de données non statique de type classe et tous les sous-objets de la classe de base ont un constructeur constexpr

## <a name="init_list_constructors"></a>Constructeurs de liste d’initialiseurs

Si un constructeur prend un [std :: initializer_list \<T \>](../standard-library/initializer-list-class.md) comme paramètre et que tous les autres paramètres ont des arguments par défaut, ce constructeur est sélectionné dans la résolution de surcharge lorsque la classe est instanciée par le biais de direct d’initialisation. Vous pouvez utiliser initializer_list pour initialiser tout membre qui peut l’accepter. Par exemple, supposons que la classe Box (indiquée précédemment) a un membre `std::vector<string>` `m_contents`. Vous pouvez fournir un constructeur comme suit :

```cpp
    Box(initializer_list<string> list, int w = 0, int h = 0, int l = 0)
        : m_contents(list), m_width(w), m_height(h), m_length(l)
{}
```

Puis créez des objets Box comme suit :

```cpp
    Box b{ "apples", "oranges", "pears" }; // or ...
    Box b2(initializer_list<string> { "bread", "cheese", "wine" }, 2, 4, 6);
```

## <a name="explicit_constructors"></a>Constructeurs explicites

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

Ces conversions peuvent être utiles dans certains cas mais, le plus souvent, elles peuvent entraîner des erreurs subtiles mais graves dans votre code. En règle générale, vous devez utiliser le mot clé **Explicit** sur un constructeur (et les opérateurs définis par l’utilisateur) pour éviter ce type de conversion de type implicite :

```cpp
explicit Box(int size): m_width(size), m_length(size), m_height(size){}
```

Si le constructeur est explicite, cette ligne entraîne une erreur du compilateur : `ShippingOrder so(42, 10.8);`.  Pour plus d’informations, consultez [conversions de types définis par l’utilisateur](../cpp/user-defined-type-conversions-cpp.md).

## <a name="order_of_construction"></a>Ordre de construction

Un constructeur effectue son travail dans l'ordre suivant :

1. Il appelle les constructeurs membres et de classe de base dans l'ordre de déclaration.

1. Si la classe est dérivée de classes de base virtuelles, il initialise les pointeurs de base virtuels de l'objet.

1. Si la classe possède ou hérite des fonctions virtuelles, il initialise les pointeurs de fonction virtuelle de l'objet. Les pointeurs de fonction virtuelle pointent sur la table de fonctions virtuelles de la classe pour permettre la liaison correcte des appels de fonction virtuelle au code.

1. Il exécute le code dans son corps de fonction.

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

Un constructeur de classe dérivée appelle toujours un constructeur de classe de base, afin de pouvoir s'appuyer sur des classes de base complètement construites avant d'effectuer tout travail supplémentaire. Les constructeurs de classe de base sont appelés par ordre de dérivation, par exemple, si `ClassA` est dérivée de `ClassB`, qui est dérivée de `ClassC`, le constructeur `ClassC` est appelé en premier, puis le constructeur `ClassB`, puis le constructeur `ClassA`.

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

1. Les objets de classe de base et membres sont détruits dans l’ordre inverse de déclaration.

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

## <a name="delegating_constructors"></a>Constructeurs de délégation

Un *constructeur de délégation* appelle un constructeur différent dans la même classe pour effectuer une partie du travail d’initialisation. Cela est utile lorsque vous avez plusieurs constructeurs qui doivent tous effectuer un travail similaire. Vous pouvez écrire la logique principale dans un constructeur et l’appeler à partir d’autres. Dans l’exemple trivial suivant, Box (int) délègue son travail à Box (int, int, int) :

```cpp
class Box {
public:
    // Default constructor
    Box() {}

    // Initialize a Box with equal dimensions (i.e. a cube)
    Box(int i) :  Box(i, i, i);  // delegating constructor
    {}

    // Initialize a Box with custom dimensions
    Box(int width, int length, int height)
        : m_width(width), m_length(length), m_height(height)
    {}
    //... rest of class as before
};
```

L'objet créé par les constructeurs est entièrement initialisé dès qu'un constructeur est terminé. Pour plus d’informations, consultez [constructeurs d’initialisation uniforme et de délégation](../cpp/uniform-initialization-and-delegating-constructors.md).

## <a name="inheriting_constructors"></a>Héritage des constructeurs (C++ 11)

Une classe dérivée peut hériter des constructeurs d’une classe de base directe à l’aide d’une déclaration **using** , comme indiqué dans l’exemple suivant :

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

::: moniker range=">=vs-2017"

**Visual Studio 2017 version 15,7 et versions ultérieures**: l’instruction **using** dans **/std : le mode c++ 17** met en portée tous les constructeurs de la classe de base, à l’exception de ceux qui ont une signature identique aux constructeurs de la classe dérivée. En général, il est préférable d'utiliser les constructeurs d'héritage quand la classe dérivée ne déclare aucun nouveau constructeur ni aucune nouvelle donnée membre. Consultez également [améliorations dans Visual Studio 2017 version 15,7](https://docs.microsoft.com/cpp/overview/cpp-conformance-improvements?view=vs-2017#improvements_157).

::: moniker-end

Un modèle de classe peut hériter de tous les constructeurs d'un argument de type si ce type spécifie une classe de base :

```cpp
template< typename T >
class Derived : T {
    using T::T;   // declare the constructors from T
    // ...
};
```

Une classe dérivée ne peut pas hériter de plusieurs classes de base si ces classes de base possèdent des constructeurs qui ont une signature identique.

## <a name="constructors_in_composite_classes"></a>Constructeurs et classes composites

Les classes qui contiennent des membres de type classe sont appelées *classes composites*. Lorsqu'un membre de type classe d'une classe composite est créé, le constructeur est appelé avant le propre constructeur de la classe. Lorsqu'une classe contenue n'a pas de constructeur par défaut, vous devez utiliser une liste d'initialisation dans le constructeur de la classe composite. Dans l'exemple `StorageBox` précédent, si vous remplacez le type de la variable membre `m_label` par une nouvelle classe `Label`, vous devez appeler le constructeur de classe de base et initialiser la variable `m_label` dans le constructeur `StorageBox` :

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
