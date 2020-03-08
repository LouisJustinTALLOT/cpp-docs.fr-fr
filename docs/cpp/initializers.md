---
title: Initialiseurs
ms.date: 07/29/2019
description: Comment initialiser des classes, des structures, des tableaux et des types fondamentaux C++dans.
helpviewer_keywords:
- arrays [C++], array-element initializers
- aggregate initializers [C++]
ms.assetid: ce301ed8-aa1c-47b2-bb39-9f0541b4af85
ms.openlocfilehash: 2cc68f2384402ce1eb3ac06b414f597a6b3951f0
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78865776"
---
# <a name="initializers"></a>Initialiseurs

Un initialiseur spécifie la valeur initiale d'une variable. Vous pouvez initialiser des variables dans les contextes suivants :

- Dans la définition d'une variable :

    ```cpp
    int i = 3;
    Point p1{ 1, 2 };
    ```

- Comme l'un des paramètres d'une fonction :

    ```cpp
    set_point(Point{ 5, 6 });
    ```

- En tant que valeur de retour d'une fonction :

    ```cpp
    Point get_new_point(int x, int y) { return { x, y }; }
    Point get_new_point(int x, int y) { return Point{ x, y }; }
    ```

Les initialiseurs peuvent prendre les formes suivantes :

- Une expression (ou une liste d'expressions séparées par des virgules) entre parenthèses :

    ```cpp
    Point p1(1, 2);
    ```

- Un signe égal suivi d'une expression :

    ```cpp
    string s = "hello";
    ```

- Une liste d'initialiseurs entre accolades. La liste peut être vide ou comprendre un ensemble de listes, comme dans l'exemple suivant :

    ```cpp
    struct Point{
        int x;
        int y;
    };
    class PointConsumer{
    public:
        void set_point(Point p){};
        void set_points(initializer_list<Point> my_list){};
    };
    int main() {
        PointConsumer pc{};
        pc.set_point({});
        pc.set_point({ 3, 4 });
        pc.set_points({ { 3, 4 }, { 5, 6 } });
    }
    ```

## <a name="kinds-of-initialization"></a>Types d'initialisations

Il existe plusieurs types d'initialisations, qui peuvent se produire à différents moments durant l'exécution du programme. Les différents types d'initialisations ne s'excluent pas mutuellement. Par exemple, l'initialisation de listes peut déclencher l'initialisation de valeurs et dans d'autres cas, l'initialisation d'agrégats.

### <a name="zero-initialization"></a>Initialisation à zéro

L'initialisation à zéro attribue à une variable une valeur zéro convertie implicitement en type :

- Les variables numériques sont initialisées à 0 (ou 0,0, ou 0,0000000000, etc.).

- Les variables char sont initialisées avec `'\0'`.

- Les pointeurs sont initialisés sur **nullptr**.

- Les membres des tableaux, des classes [Pod](../standard-library/is-pod-class.md) , des structs et des unions sont initialisés à zéro.

L'initialisation à zéro peut être effectuée à différents moments :

- Au démarrage du programme, pour toutes les variables nommées dont la durée est statique. Ces variables pourront être initialisées à nouveau.

- Pendant l'initialisation de valeurs, pour les types scalaires et ceux de classe POD qui sont initialisés à l'aide d'accolades vides.

- Pour les tableaux dont seul un sous-ensemble de leurs membres est initialisé.

Voici quelques exemples d'initialisation à zéro :

```cpp
struct my_struct{
    int i;
    char c;
};

int i0;              // zero-initialized to 0
int main() {
    static float f1;  // zero-initialized to 0.000000000
    double d{};     // zero-initialized to 0.00000000000000000
    int* ptr{};     // initialized to nullptr
    char s_array[3]{'a', 'b'};  // the third char is initialized to '\0'
    int int_array[5] = { 8, 9, 10 };  // the fourth and fifth ints are initialized to 0
    my_struct a_struct{};   // i = 0, c = '\0'
}
```

### <a name="default_initialization"></a>Initialisation par défaut

L'initialisation par défaut des classes, des structs et des unions utilise un constructeur par défaut. Le constructeur par défaut peut être appelé sans expression d’initialisation ni avec le mot clé **New** :

```cpp
MyClass mc1;
MyClass* mc3 = new MyClass;
```

Si la classe, le struct ou l'union n'a pas de constructeur par défaut, le compilateur renvoie une erreur.

Les variables scalaires sont initialisées par défaut lorsqu'elles sont définies sans expression d'initialisation. Leurs valeurs sont indéterminées.

```cpp
int i1;
float f;
char c;
```

Les tableaux sont initialisés par défaut lorsqu'ils sont définis sans expression d'initialisation. Lorsqu'un tableau est initialisé par défaut, ses membres sont initialisés par défaut et ont des valeurs indéterminées, comme dans l'exemple suivant :

```cpp
int int_arr[3];
```

Si les membres du tableau n'ont pas de constructeur par défaut, le compilateur renvoie une erreur.

#### <a name="default-initialization-of-constant-variables"></a>Initialisation par défaut des variables constantes

Les variables constantes doivent être déclarées en même temps que l'initialiseur. Si elles sont de type scalaire, elles entraîneront une erreur du compilateur. Si elles sont de type de classe avec un constructeur par défaut, elles entraîneront un avertissement :

```cpp
class MyClass{};
int main() {
    //const int i2;   // compiler error C2734: const object must be initialized if not extern
    //const char c2;  // same error
    const MyClass mc1; // compiler error C4269: 'const automatic data initialized with compiler generated default constructor produces unreliable results
}
```

#### <a name="default-initialization-of-static-variables"></a>Initialisation par défaut des variables statiques

Les variables statiques déclarées sans initialiseur sont initialisées à 0 (implicitement converties en type).

```cpp
class MyClass {
private:
    int m_int;
    char m_char;
};

int main() {
    static int int1;       // 0
    static char char1;     // '\0'
    static bool bool1;   // false
    static MyClass mc1;     // {0, '\0'}
}
```

Pour plus d’informations sur l’initialisation des objets statiques globaux, consultez [fonctions principales et arguments de ligne de commande](main-function-command-line-args.md).

### <a name="value-initialization"></a>Initialisation de valeurs

L'initialisation de valeurs se produit dans les cas suivants :

- une valeur nommée est initialisée à l'aide d'accolades vides ;

- un objet temporaire anonyme est initialisé à l'aide de parenthèses ou d'accolades vides ;

- un objet est initialisé avec le mot clé **New** , ainsi que des parenthèses ou des accolades vides

L'initialisation de valeurs entraîne ce qui suit :

- pour les classes qui possèdent au moins un constructeur public, le constructeur par défaut est appelé ;

- pour les classes (autres que les classes d'union) qui n'ont pas déclaré de constructeur, l'objet est initialisé à zéro et le constructeur par défaut est appelé ;

- pour les tableaux, chaque élément est initialisé par une valeur ;

- dans tous les autres cas, la variable est initialisée à zéro.

```cpp
class BaseClass {
private:
    int m_int;
};

int main() {
    BaseClass bc{};     // class is initialized
    BaseClass*  bc2 = new BaseClass();  // class is initialized, m_int value is 0
    int int_arr[3]{};  // value of all members is 0
    int a{};     // value of a is 0
    double b{};  // value of b is 0.00000000000000000
}
```

### <a name="copy-initialization"></a>Initialisation de copie

L'initialisation de copie correspond à l'initialisation d'un objet à l'aide d'un autre objet. Elle se produit dans les cas suivants :

- Une variable est initialisée à l'aide d'un signe égal.

- Un argument est passé à une fonction.

- Un objet est retourné par une fonction.

- Une exception est levée ou interceptée.

- Des données membres non statiques sont initialisées à l'aide d'un signe égal.

- Les membres des classes, des structs et des unions sont initialisés par initialisation de copie pendant l'initialisation des agrégats. Pour obtenir des exemples, consultez [initialisation d’agrégats](#agginit) .

Le code suivant montre plusieurs exemples d'initialisation de copie :

```cpp
#include <iostream>
using namespace std;

class MyClass{
public:
    MyClass(int myInt) {}
    void set_int(int myInt) { m_int = myInt; }
    int get_int() const { return m_int; }
private:
    int m_int = 7; // copy initialization of m_int

};
class MyException : public exception{};
int main() {
    int i = 5;              // copy initialization of i
    MyClass mc1{ i };
    MyClass mc2 = mc1;      // copy initialization of mc2 from mc1
    MyClass mc1.set_int(i);    // copy initialization of parameter from i
    int i2 = mc2.get_int(); // copy initialization of i2 from return value of get_int()

    try{
        throw MyException();
    }
    catch (MyException ex){ // copy initialization of ex
        cout << ex.what();
    }
}
```

L'initialisation de copie ne peut pas appeler de constructeurs explicites :

```cpp
vector<int> v = 10; // the constructor is explicit; compiler error C2440: cannot convert from 'int' to 'std::vector<int,std::allocator<_Ty>>'
regex r = "a.*b"; // the constructor is explicit; same error
shared_ptr<int> sp = new int(1729); // the constructor is explicit; same error
```

Dans certains cas, si le constructeur de copie de la classe est supprimé ou inaccessible, l'initialisation de copie entraîne une erreur du compilateur.

### <a name="direct-initialization"></a>Initialisation directe

L'initialisation directe utilise des accolades ou des parenthèses non vides. Contrairement à l'initialisation de copie, elle peut appeler des constructeurs explicites. Elle se produit dans les cas suivants :

- Une variable est initialisée à l'aide d'accolades ou de parenthèses non vides.

- une variable est initialisée avec le mot clé **New** et des accolades ou des parenthèses non vides

- une variable est initialisée avec **static_cast**

- Dans un constructeur, les classes de base et les membres non statiques sont initialisés à l'aide d'une liste d'initialiseurs.

- Dans la copie d’une variable capturée d’une expression lambda.

Le code suivant montre des exemples d'initialisation directe :

```cpp
class BaseClass{
public:
    BaseClass(int n) :m_int(n){} // m_int is direct initialized
private:
    int m_int;
};

class DerivedClass : public BaseClass{
public:
    // BaseClass and m_char are direct initialized
    DerivedClass(int n, char c) : BaseClass(n), m_char(c) {}
private:
    char m_char;
};
int main(){
    BaseClass bc1(5);
    DerivedClass dc1{ 1, 'c' };
    BaseClass* bc2 = new BaseClass(7);
    BaseClass bc3 = static_cast<BaseClass>(dc1);

    int a = 1;
    function<int()> func = [a](){  return a + 1; }; // a is direct initialized
    int n = func();
}
```

### <a name="list-initialization"></a>Initialisation de liste

L'initialisation de liste se produit lorsqu'une variable est initialisée à l'aide d'une liste d'initialiseurs entre accolades. Les listes d'initialiseurs entre accolades peuvent être utilisées dans les cas suivants :

- Une variable est initialisée.

- une classe est initialisée avec le mot clé **New**

- Un objet est retourné par une fonction.

- Un argument est passé à une fonction.

- L’un des arguments est compris dans une initialisation directe.

- Dans un initialiseur de données membres non statiques.

- Dans une liste d'initialiseurs de constructeur.

Le code suivant montre des exemples d'initialisation de liste :

```cpp
class MyClass {
public:
    MyClass(int myInt, char myChar) {}
private:
    int m_int[]{ 3 };
    char m_char;
};
class MyClassConsumer{
public:
    void set_class(MyClass c) {}
    MyClass get_class() { return MyClass{ 0, '\0' }; }
};
struct MyStruct{
    int my_int;
    char my_char;
    MyClass my_class;
};
int main() {
    MyClass mc1{ 1, 'a' };
    MyClass* mc2 = new MyClass{ 2, 'b' };
    MyClass mc3 = { 3, 'c' };

    MyClassConsumer mcc;
    mcc.set_class(MyClass{ 3, 'c' });
    mcc.set_class({ 4, 'd' });

    MyStruct ms1{ 1, 'a', { 2, 'b' } };
}
```

### <a name="agginit"></a>Initialisation d’agrégats

L'initialisation d'agrégats est un type d'initialisation de liste utilisé pour les tableaux et les types de classes (souvent des structs ou des unions) qui n'ont :

- aucun membre privé ou protégé ;

- aucun constructeur fourni par l'utilisateur, à l'exception des constructeurs supprimés ou utilisés par défaut de manière explicite ;

- aucune classe de base ;

- aucune fonction membre virtuelle ;

> [!NOTE]
> <!--conformance note-->Dans Visual Studio 2015 et les versions antérieures, un agrégat n’est pas autorisé à avoir des initialiseurs d’accolade ou d’égalité pour les membres non statiques. Cette restriction a été supprimée dans la norme C++ 14 et implémentée dans Visual Studio 2017.

Les initialiseurs d'agrégats se composent d'une liste d'initialisation entre accolades, avec ou sans signe égal, comme dans l'exemple suivant :

```cpp
#include <iostream>
using namespace std;

struct MyAggregate{
    int myInt;
    char myChar;
};

struct MyAggregate2{
    int myInt;
    char myChar = 'Z'; // member-initializer OK in C++14
};

int main() {
    MyAggregate agg1{ 1, 'c' };
    MyAggregate2 agg2{2};
    cout << "agg1: " << agg1.myChar << ": " << agg1.myInt << endl;
    cout << "agg2: " << agg2.myChar << ": " << agg2.myInt << endl;

    int myArr1[]{ 1, 2, 3, 4 };
    int myArr2[3] = { 5, 6, 7 };
    int myArr3[5] = { 8, 9, 10 };

    cout << "myArr1: ";
    for (int i : myArr1){
        cout << i << " ";
    }
    cout << endl;

    cout << "myArr3: ";
    for (auto const &i : myArr3) {
        cout << i << " ";
    }
    cout << endl;
}
```

Vous devez normalement voir la sortie suivante.

```Output
agg1: c: 1
agg2: Z: 2
myArr1: 1 2 3 4
myArr3: 8 9 10 0 0
```

> [!IMPORTANT]
> Les membres du tableau qui sont déclarés mais pas explicitement initialisés pendant l’initialisation de l’agrégat sont initialisés à zéro, comme dans `myArr3` ci-dessus.

#### <a name="initializing-unions-and-structs"></a>Initialisation des unions et des structs

Si une union n'a pas de constructeur, vous pouvez l'initialiser à l'aide d'une valeur (ou d'une autre instance d'union). La valeur est utilisée pour initialiser le premier champ non static. C'est donc différent de l'initialisation de struct, durant laquelle la première valeur de l'initialiseur est utilisée pour initialiser le premier champ, la deuxième pour initialiser le deuxième champ, et ainsi de suite. L'exemple suivant vous permet de comparer l'initialisation des unions et des structs :

```cpp
struct MyStruct {
    int myInt;
    char myChar;
};
union MyUnion {
    int my_int;
    char my_char;
    bool my_bool;
    MyStruct my_struct;
};

int main() {
    MyUnion mu1{ 'a' };  // my_int = 97, my_char = 'a', my_bool = true, {myInt = 97, myChar = '\0'}
    MyUnion mu2{ 1 };   // my_int = 1, my_char = 'x1', my_bool = true, {myInt = 1, myChar = '\0'}
    MyUnion mu3{};      // my_int = 0, my_char = '\0', my_bool = false, {myInt = 0, myChar = '\0'}
    MyUnion mu4 = mu3;  // my_int = 0, my_char = '\0', my_bool = false, {myInt = 0, myChar = '\0'}
    //MyUnion mu5{ 1, 'a', true };  // compiler error: C2078: too many initializers
    //MyUnion mu6 = 'a';            // compiler error: C2440: cannot convert from 'char' to 'MyUnion'
    //MyUnion mu7 = 1;              // compiler error: C2440: cannot convert from 'int' to 'MyUnion'

    MyStruct ms1{ 'a' };            // myInt = 97, myChar = '\0'
    MyStruct ms2{ 1 };              // myInt = 1, myChar = '\0'
    MyStruct ms3{};                 // myInt = 0, myChar = '\0'
    MyStruct ms4{1, 'a'};           // myInt = 1, myChar = 'a'
    MyStruct ms5 = { 2, 'b' };      // myInt = 2, myChar = 'b'
}
```

#### <a name="initializing-aggregates-that-contain-aggregates"></a>Initialisation d'agrégats contenant des agrégats

Les types d'agrégats peuvent contenir d'autres types d'agrégats. Par exemple, les tableaux peuvent contenir des tableaux, des structs, etc. Ces types sont initialisés à l'aide de jeux imbriqués d'accolades, par exemple :

```cpp
struct MyStruct {
    int myInt;
    char myChar;
};
int main() {
    int intArr1[2][2]{{ 1, 2 }, { 3, 4 }};
    int intArr3[2][2] = {1, 2, 3, 4};
    MyStruct structArr[]{ { 1, 'a' }, { 2, 'b' }, {3, 'c'} };
}
```

### <a name="reference-initialization"></a>Initialisation de références

Les variables de type référence doivent être initialisées avec un objet du type à partir duquel le type référence est dérivé, ou avec un objet d'un type pouvant être converti en type à partir duquel le type référence est dérivé. Par exemple :

```cpp
// initializing_references.cpp
int iVar;
long lVar;
int main()
{
    long& LongRef1 = lVar;        // No conversion required.
    long& LongRef2 = iVar;        // Error C2440
    const long& LongRef3 = iVar;  // OK
    LongRef1 = 23L;               // Change lVar through a reference.
    LongRef2 = 11L;               // Change iVar through a reference.
    LongRef3 = 11L;               // Error C3892
}
```

La seule façon d'initialiser une référence avec un objet temporaire consiste à initialiser un objet constant temporaire. Une fois initialisée, une variable de type référence pointe toujours vers le même objet ; elle ne peut pas être modifiée pour pointer vers un autre objet.

Bien que la syntaxe puisse être identique, l'initialisation des variables de type référence et l'assignation à des variables de type référence sont sémantiquement différentes. Dans l'exemple précédent, les assignations qui modifient `iVar` et `lVar` ressemblent aux initialisations, mais leurs effets sont différents. L'initialisation spécifie l'objet vers lequel pointe la variable de type référence ; l'assignation assigne à l'objet référencé via la référence.

Étant donné que le passage d'un argument de type référence à une fonction et le retour d'une valeur de type référence à partir d'une fonction sont des initialisations, les arguments formels d'une fonction sont initialisés correctement, de même que les références retournées.

Les variables de type référence peuvent être déclarées sans initialiseurs uniquement dans les éléments suivants :

- Déclarations de fonction (prototypes). Par exemple :

    ```cpp
    int func( int& );
    ```

- Déclarations de type retour de fonction. Par exemple :

    ```cpp
    int& func( int& );
    ```

- Déclaration d'un membre de classe de type référence. Par exemple :

    ```cpp
    class c {public:   int& i;};
    ```

- Déclaration d’une variable explicitement spécifiée comme **extern**. Par exemple :

    ```cpp
    extern int& iVal;
    ```

Lors de l'initialisation d'une variable de type référence, le compilateur utilise le graphique de décision représenté dans l'illustration suivante pour choisir entre la création d'une référence à un objet et la création d'un objet temporaire vers lequel pointe la référence.

![Graphique de décision pour l’initialisation des types référence](../cpp/media/vc38s71.gif "Graphique de décision pour l’initialisation des types référence") <br/>
Graphique de décision pour l’initialisation des types référence

Les références aux types **volatiles** (déclarées en tant qu' *identificateur*<strong>&</strong> *TypeName* **volatile** ) peuvent être initialisées avec des objets **volatiles** du même type ou avec des objets qui n’ont pas été déclarés comme **volatile**. Toutefois, elles ne peuvent pas être initialisées avec des objets **const** de ce type. De même, les références aux types **const** (déclarés comme **const** *TypeName* <strong>&</strong> *identificateur*) peuvent être initialisées avec des objets **const** du même type (ou tout ce qui a une conversion vers ce type ou avec des objets qui n’ont pas été déclarés comme **const**). Toutefois, elles ne peuvent pas être initialisées avec des objets **volatiles** de ce type.

Les références qui ne sont pas qualifiées avec le mot clé **const** ou **volatile** peuvent être initialisées uniquement avec des objets déclarés comme **const** ou **volatile**.

### <a name="initialization-of-external-variables"></a>Initialisation des variables externes

Les déclarations de variables automatiques, statiques et externes peuvent contenir des initialiseurs. Toutefois, les déclarations de variables externes peuvent contenir des initialiseurs uniquement si les variables ne sont pas déclarées comme **extern**.
