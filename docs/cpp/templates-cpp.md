---
title: Modèles (C++)
ms.date: 12/27/2019
f1_keywords:
- template_cpp
helpviewer_keywords:
- templates, C++
- templates [C++]
ms.assetid: 90fcc14a-2092-47af-9d2e-dba26d25b872
ms.openlocfilehash: 996458417b20533db074ce2fa13c06860c54247c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223562"
---
# <a name="templates-c"></a>Modèles (C++)

Les modèles constituent la base de la programmation générique en C++. En tant que langage fortement typé, C++ exige que toutes les variables aient un type spécifique, explicitement déclarées par le programmeur ou déduites par le compilateur. Toutefois, de nombreux algorithmes et structures de données se présentent de la même façon, quel que soit le type sur lequel ils s’exécutent. Les modèles vous permettent de définir les opérations d’une classe ou d’une fonction, et de permettre à l’utilisateur de spécifier les types concrets sur lesquels ces opérations doivent fonctionner.

## <a name="defining-and-using-templates"></a>Définition et utilisation de modèles

Un modèle est une construction qui génère un type ordinaire ou une fonction au moment de la compilation en fonction des arguments fournis par l’utilisateur pour les paramètres du modèle. Par exemple, vous pouvez définir un modèle de fonction comme suit :

```cpp
template <typename T>
T minimum(const T& lhs, const T& rhs)
{
    return lhs < rhs ? lhs : rhs;
}
```

Le code ci-dessus décrit un modèle pour une fonction générique avec un seul paramètre de type *T*, dont la valeur de retour et les paramètres d’appel (LHS et RHS) sont tous de ce type. Vous pouvez nommer un paramètre de type comme vous le souhaitez, mais par Convention les lettres majuscules uniques sont le plus couramment utilisées. *T* est un paramètre de modèle ; le **`typename`** mot clé indique que ce paramètre est un espace réservé pour un type. Lorsque la fonction est appelée, le compilateur remplace chaque instance de `T` par l’argument de type concret qui est spécifié par l’utilisateur ou déduit par le compilateur. Le processus dans lequel le compilateur génère une classe ou une fonction à partir d’un modèle est appelé *instanciation de modèle*; `minimum<int>`est une instanciation du modèle `minimum<T>` .

Ailleurs, un utilisateur peut déclarer une instance du modèle spécialisée pour int. Supposons que get_a () et get_b () sont des fonctions qui retournent un int :

```cpp
int a = get_a();
int b = get_b();
int i = minimum<int>(a, b);
```

Toutefois, étant donné qu’il s’agit d’un modèle de fonction et que le compilateur peut déduire le type de `T` à partir des arguments *a* et *b*, vous pouvez l’appeler comme une fonction ordinaire :

```cpp
int i = minimum(a, b);
```

Quand le compilateur rencontre cette dernière instruction, il génère une nouvelle fonction dans laquelle chaque occurrence de *T* dans le modèle est remplacée par **`int`** :

```cpp
int minimum(const int& lhs, const int& rhs)
{
    return lhs < rhs ? lhs : rhs;
}
```

Les règles relatives à la façon dont le compilateur effectue la déduction de type dans les modèles de fonction sont basées sur les règles des fonctions ordinaires. Pour plus d’informations, consultez [résolution de surcharge des appels de modèle de fonction](../cpp/overload-resolution-of-function-template-calls.md).

## <a name="type-parameters"></a><a id="type_parameters"></a>Paramètres de type

Dans le `minimum` modèle ci-dessus, Notez que le paramètre de type *T* n’est pas qualifié tant qu’il n’est pas utilisé dans les paramètres d’appel de fonction, où les qualificateurs const et de référence sont ajoutés.

Il n’existe aucune limite pratique au nombre de paramètres de type. Séparez plusieurs paramètres par des virgules :

```cpp
template <typename T, typename U, typename V> class Foo{};
```

Le mot clé **`class`** est équivalent à **`typename`** dans ce contexte. Vous pouvez exprimer l’exemple précédent comme suit :

```cpp
template <class T, class U, class V> class Foo{};
```

Vous pouvez utiliser l’opérateur des points de suspension (...) pour définir un modèle qui accepte un nombre arbitraire de zéro, un ou plusieurs paramètres de type :

```cpp
template<typename... Arguments> class vtclass;

vtclass< > vtinstance1;
vtclass<int> vtinstance2;
vtclass<float, bool> vtinstance3;
```

Tout type intégré ou défini par l’utilisateur peut être utilisé comme argument de type. Par exemple, vous pouvez utiliser [std :: Vector](../standard-library/vector-class.md) dans la bibliothèque standard pour stocker les variables de type **`int`** , **`double`** , [std :: String](../standard-library/basic-string-class.md), `MyClass` , **`const`** `MyClass` *, `MyClass&` , etc. La restriction principale lors de l’utilisation de modèles est qu’un argument de type doit prendre en charge toutes les opérations appliquées aux paramètres de type. Par exemple, si vous appelez `minimum` à l’aide `MyClass` de comme dans cet exemple :

```cpp
class MyClass
{
public:
    int num;
    std::wstring description;
};

int main()
{
    MyClass mc1 {1, L"hello"};
    MyClass mc2 {2, L"goodbye"};
    auto result = minimum(mc1, mc2); // Error! C2678
}
```

Une erreur de compilateur est générée, car `MyClass` ne fournit pas de surcharge pour l' **<** opérateur.

Il n’existe aucune exigence inhérente selon laquelle les arguments de type d’un modèle particulier appartiennent tous à la même hiérarchie d’objets, même si vous pouvez définir un modèle qui applique une telle restriction. Vous pouvez combiner des techniques orientées objet et des modèles. par exemple, vous pouvez stocker un * dérivé dans un vecteur \<Base\*> .    Notez que les arguments doivent être des pointeurs

```cpp
vector<MyClass*> vec;
   MyDerived d(3, L"back again", time(0));
   vec.push_back(&d);

   // or more realistically:
   vector<shared_ptr<MyClass>> vec2;
   vec2.push_back(make_shared<MyDerived>());
```

Les exigences de base que `std::vector` et d’autres conteneurs de bibliothèque standard imposent sur les éléments de `T` sont de `T` type copie-assignation et copie-constructible.

## <a name="non-type-parameters"></a>Paramètres sans type

Contrairement aux types génériques dans d’autres langages tels que C# et Java, les modèles C++ prennent en charge les *paramètres sans type*, également appelés paramètres de valeur. Par exemple, vous pouvez fournir une valeur intégrale constante pour spécifier la longueur d’un tableau, comme dans cet exemple qui est semblable à la classe [std :: Array](../standard-library/array-class-stl.md) dans la bibliothèque standard :

```cpp
template<typename T, size_t L>
class MyArray
{
    T arr[L];
public:
    MyArray() { ... }
};
```

Notez la syntaxe de la déclaration de modèle. La `size_t` valeur est passée comme argument de modèle au moment de la compilation et doit être **`const`** ou une **`constexpr`** expression. Vous l’utilisez comme suit :

```cpp
MyArray<MyClass*, 10> arr;
```

D’autres types de valeurs, y compris les pointeurs et les références, peuvent être passés en tant que paramètres sans type. Par exemple, vous pouvez passer un pointeur vers une fonction ou un objet de fonction pour personnaliser une opération à l’intérieur du code du modèle.

### <a name="type-deduction-for-non-type-template-parameters"></a>Déduction de type pour les paramètres de modèle sans type

Dans Visual Studio 2017 et versions ultérieures, en mode **/std : c++ 17** , le compilateur déduit le type d’un argument de modèle sans type déclaré avec **`auto`** :

```cpp
template <auto x> constexpr auto constant = x;

auto v1 = constant<5>;      // v1 == 5, decltype(v1) is int
auto v2 = constant<true>;   // v2 == true, decltype(v2) is bool
auto v3 = constant<'a'>;    // v3 == 'a', decltype(v3) is char
```

## <a name="templates-as-template-parameters"></a><a id="template_parameters"></a>Modèles en tant que paramètres de modèle

Un modèle peut être un paramètre de modèle. Dans cet exemple, MyClass2 a deux paramètres de modèle : un paramètre TypeName *T* et un paramètre de modèle *arr*:

```cpp
template<typename T, template<typename U, int I> class Arr>
class MyClass2
{
    T t; //OK
    Arr<T, 10> a;
    U u; //Error. U not in scope
};
```

Étant donné que le paramètre *arr* lui-même n’a pas de corps, ses noms de paramètres ne sont pas nécessaires. En fait, il est erroné de faire référence aux noms de paramètre TypeName ou de classe d' *arr*à partir du corps de `MyClass2` . Pour cette raison, les noms des paramètres de type d' *arr*peuvent être omis, comme illustré dans cet exemple :

```cpp
template<typename T, template<typename, int> class Arr>
class MyClass2
{
    T t; //OK
    Arr<T, 10> a;
};
```

## <a name="default-template-arguments"></a>Arguments template par défaut

Les modèles de classe et de fonction peuvent avoir des arguments par défaut. Quand un modèle a un argument par défaut, vous pouvez le conserver non spécifié quand vous l’utilisez. Par exemple, le modèle std :: Vector a un argument par défaut pour l’allocateur :

```cpp
template <class T, class Allocator = allocator<T>> class vector;
```

Dans la plupart des cas, la classe std :: Allocator par défaut est acceptable. vous utilisez donc un vecteur comme celui-ci :

```cpp
vector<int> myInts;
```

Toutefois, si nécessaire, vous pouvez spécifier un allocateur personnalisé comme suit :

```cpp
vector<int, MyAllocator> ints;
```

Pour plusieurs arguments template, tous les arguments après le premier argument par défaut doivent avoir des arguments par défaut.

Lorsque vous utilisez un modèle dont les paramètres sont tous par défaut, utilisez des crochets pointus vides :

```cpp
template<typename A = int, typename B = double>
class Bar
{
    //...
};
...
int main()
{
    Bar<> bar; // use all default type arguments
}
```

## <a name="template-specialization"></a>Spécialisation de modèle

Dans certains cas, il n’est pas possible ou souhaitable pour un modèle de définir exactement le même code pour n’importe quel type. Par exemple, vous souhaiterez peut-être définir un chemin d’accès de code à exécuter uniquement si l’argument de type est un pointeur ou un std :: wstring ou un type dérivé d’une classe de base particulière.  Dans ce cas, vous pouvez définir une *spécialisation* du modèle pour ce type particulier. Quand un utilisateur instancie le modèle avec ce type, le compilateur utilise la spécialisation pour générer la classe, et pour tous les autres types, le compilateur choisit le modèle plus général. Les spécialisations dans lesquelles tous les paramètres sont spécialisés sont des *spécialisations complètes*. Si seuls certains paramètres sont spécialisés, il s’agit d’une *spécialisation partielle*.

```cpp
template <typename K, typename V>
class MyMap{/*...*/};

// partial specialization for string keys
template<typename V>
class MyMap<string, V> {/*...*/};
...
MyMap<int, MyClass> classes; // uses original template
MyMap<string, MyClass> classes2; // uses the partial specialization
```

Un modèle peut avoir un nombre quelconque de spécialisations, à condition que chaque paramètre de type spécialisé soit unique. Seuls les modèles de classe peuvent être partiellement spécialisés. Toutes les spécialisations complètes et partielles d’un modèle doivent être déclarées dans le même espace de noms que le modèle d’origine.

Pour plus d’informations, consultez [spécialisation de modèle](../cpp/template-specialization-cpp.md).
