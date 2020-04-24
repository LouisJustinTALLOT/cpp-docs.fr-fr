---
title: Modèles (C++)
ms.date: 12/27/2019
f1_keywords:
- template_cpp
helpviewer_keywords:
- templates, C++
- templates [C++]
ms.assetid: 90fcc14a-2092-47af-9d2e-dba26d25b872
ms.openlocfilehash: e47f00c7e387974c7d1756cf3ee3865f892e6951
ms.sourcegitcommit: 89d9e1cb08fa872483d1cde98bc2a7c870e505e9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "82032341"
---
# <a name="templates-c"></a>Modèles (C++)

Les modèles sont la base de la programmation générique dans le C. En tant que langue fortement typée, le CMD exige que toutes les variables aient un type spécifique, soit explicitement déclarée par le programmeur, soit déduite par le compilateur. Cependant, de nombreuses structures et algorithmes de données se ressemblent quel que soit le type sur laquelle ils fonctionnent. Les modèles vous permettent de définir les opérations d’une classe ou d’une fonction, et permettent à l’utilisateur de spécifier les types concrets sur qui ces opérations doivent fonctionner.

## <a name="defining-and-using-templates"></a>Définir et utiliser des modèles

Un modèle est une construction qui génère un type ou une fonction ordinaire au moment de compilation basé sur des arguments que l’utilisateur fournit pour les paramètres du modèle. Par exemple, vous pouvez définir un modèle de fonction comme celui-ci :

```cpp
template <typename T>
T minimum(const T& lhs, const T& rhs)
{
    return lhs < rhs ? lhs : rhs;
}
```

Le code ci-dessus décrit un modèle pour une fonction générique avec un paramètre de type *unique T*, dont la valeur de retour et les paramètres d’appel (lhs et rhs) sont tous de ce type. Vous pouvez nommer un paramètre de type tout ce que vous voulez, mais par convention les lettres de cas supérieurs simples sont les plus couramment utilisés. *T* est un paramètre de modèle ; le mot clé **de type** indique que ce paramètre est un espace réservé pour un type. Lorsque la fonction est appelée, le compilateur remplacera chaque instance de l’argument de `T` type concret qui est soit spécifié par l’utilisateur ou déduit par le compilateur. Le processus dans lequel le compilateur génère une classe ou une fonction à partir d’un modèle est appelé *instantané de modèle*; `minimum<int>` est une instantanéisation du `minimum<T>`modèle .

Ailleurs, un utilisateur peut déclarer un exemple du modèle qui est spécialisé pour int. Supposons que get_a() et get_b() sont des fonctions qui renvoient un int:

```cpp
int a = get_a();
int b = get_b();
int i = minimum<int>(a, b);
```

Cependant, parce qu’il s’agit d’un modèle de `T` fonction et le compilateur peut déduire le type de des arguments *a* et *b*, vous pouvez l’appeler comme une fonction ordinaire:

```cpp
int i = minimum(a, b);
```

Lorsque le compilateur rencontre cette dernière déclaration, il génère une nouvelle fonction dans laquelle chaque occurrence de *T* dans le modèle est remplacé par **int:**

```cpp
int minimum(const int& lhs, const int& rhs)
{
    return lhs < rhs ? lhs : rhs;
}
```

Les règles pour la façon dont le compilateur effectue la déduction de type dans les modèles de fonction sont basées sur les règles pour les fonctions ordinaires. Pour plus d’informations, voir [Surcharge résolution des appels de modèle de fonction](../cpp/overload-resolution-of-function-template-calls.md).

## <a name="type-parameters"></a><a id="type_parameters"></a>Paramètres de type

Dans `minimum` le modèle ci-dessus, notez que le paramètre de type *T* n’est pas qualifié de quelque façon que ce soit jusqu’à ce qu’il soit utilisé dans les paramètres d’appel de fonction, où les const et les qualificatifs de référence sont ajoutés.

Il n’y a pas de limite pratique au nombre de paramètres de type. Séparer plusieurs paramètres par virgules :

```cpp
template <typename T, typename U, typename V> class Foo{};
```

La **classe** de mots clés est **équivalente** à un nom de type dans ce contexte. Vous pouvez exprimer l’exemple précédent comme :

```cpp
template <class T, class U, class V> class Foo{};
```

Vous pouvez utiliser l’opérateur ellipsis (...) pour définir un modèle qui prend un nombre arbitraire de paramètres de type zéro ou plus :

```cpp
template<typename... Arguments> class vtclass;

vtclass< > vtinstance1;
vtclass<int> vtinstance2;
vtclass<float, bool> vtinstance3;
```

Tout type intégré ou défini par l’utilisateur peut être utilisé comme argument type. Par exemple, vous pouvez utiliser [std::vector](../standard-library/vector-class.md) dans la bibliothèque standard pour stocker des `MyClass`variables de type **int**, **double**, [std::string](../standard-library/basic-string-class.md), **, const** `MyClass`, `MyClass&`, et ainsi de suite. La principale restriction lors de l’utilisation de modèles est qu’un argument type doit soutenir toutes les opérations qui sont appliquées aux paramètres de type. Par exemple, si `minimum` `MyClass` nous appelons l’utilisation comme dans cet exemple:

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

Une erreur de compilateur `MyClass` sera générée parce qu’elle ne fournit pas de surcharge pour l’opérateur. **<**

Il n’y a aucune exigence inhérente que les arguments de type pour un modèle particulier appartiennent tous à la même hiérarchie d’objet, bien que vous puissiez définir un modèle qui applique une telle restriction. Vous pouvez combiner des techniques orientées objet avec des modèles; par exemple, vous pouvez stocker un\<\* DerivedMD dans une base de vecteur>.    Notez que les arguments doivent être des pointeurs

```cpp
vector<MyClass*> vec;
   MyDerived d(3, L"back again", time(0));
   vec.push_back(&d);

   // or more realistically:
   vector<shared_ptr<MyClass>> vec2;
   vec2.push_back(make_shared<MyDerived>());
```

Les exigences `std::vector` de base que les conteneurs de bibliothèque standard imposent aux éléments `T` sont qui `T` sont copiables et copier-constructibles.

## <a name="non-type-parameters"></a>Paramètres non types

Contrairement aux types génériques dans d’autres langues telles que C et Java, les modèles CMD prennent en charge les *paramètres non types,* également appelés paramètres de valeur. Par exemple, vous pouvez fournir une valeur intégrale constante pour spécifier la longueur d’un tableau, comme avec cet exemple qui est similaire à la [std::classe de tableau](../standard-library/array-class-stl.md) dans la bibliothèque standard:

```cpp
template<typename T, size_t L>
class MyArray
{
    T arr[L];
public:
    MyArray() { ... }
};
```

Notez la syntaxe dans la déclaration de modèle. La `size_t` valeur est transmise comme un argument de modèle au moment de compilation et doit être **const** ou une expression **constexpr.** Vous l’utilisez comme ceci:

```cpp
MyArray<MyClass*, 10> arr;
```

D’autres types de valeurs, y compris les pointeurs et les références peuvent être passés en tant que paramètres non types. Par exemple, vous pouvez passer dans un pointeur à un objet de fonction ou de fonction pour personnaliser une opération à l’intérieur du code de modèle.

### <a name="type-deduction-for-non-type-template-parameters"></a>Déduction de type pour les paramètres de modèle non-type

Dans Visual Studio 2017 et plus tard, en **/std:c '17** mode le compilateur déduit le type d’un argument de modèle non-type qui est déclaré avec **l’auto:**

```cpp
template <auto x> constexpr auto constant = x;

auto v1 = constant<5>;      // v1 == 5, decltype(v1) is int
auto v2 = constant<true>;   // v2 == true, decltype(v2) is bool
auto v3 = constant<'a'>;    // v3 == 'a', decltype(v3) is char
```

## <a name="templates-as-template-parameters"></a><a id="template_parameters"></a>Modèles comme paramètres de modèle

Un modèle peut être un paramètre de modèle. Dans cet exemple, MyClass2 a deux paramètres de modèle : un paramètre de type *T* et un paramètre de modèle *Arr*:

```cpp
template<typename T, template<typename U, int I> class Arr>
class MyClass2
{
    T t; //OK
    Arr<T, 10> a;
    U u; //Error. U not in scope
};
```

Parce que le *paramètre Arr* lui-même n’a pas de corps, ses noms de paramètres ne sont pas nécessaires. En fait, c’est une erreur de se référer à *Arr*'s `MyClass2`typename ou noms de paramètres de classe de l’intérieur du corps de . Pour cette raison, les noms de paramètres de type *Arr*peuvent être omis, comme le montre cet exemple :

```cpp
template<typename T, template<typename, int> class Arr>
class MyClass2
{
    T t; //OK
    Arr<T, 10> a;
};
```

## <a name="default-template-arguments"></a>Arguments de modèle par défaut

Les modèles de classe et de fonction peuvent avoir des arguments par défaut. Lorsqu’un modèle a un argument par défaut, vous pouvez le laisser non spécifié lorsque vous l’utilisez. Par exemple, le std::vector template a un argument par défaut pour l’allocateur:

```cpp
template <class T, class Allocator = allocator<T>> class vector;
```

Dans la plupart des cas, le std par défaut: :la classe d’alloueur est acceptable, de sorte que vous utilisez un vecteur comme celui-ci:

```cpp
vector<int> myInts;
```

Mais si nécessaire, vous pouvez spécifier un allocateur personnalisé comme celui-ci:

```cpp
vector<int, MyAllocator> ints;
```

Pour plusieurs arguments template, tous les arguments après le premier argument par défaut doivent avoir des arguments par défaut.

Lorsque vous utilisez un modèle dont les paramètres sont tous par défaut, utilisez des supports d’angle vides :

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

Dans certains cas, il n’est ni possible ni souhaitable qu’un modèle définisse exactement le même code pour n’importe quel type. Par exemple, vous pouvez définir un chemin de code à exécuter uniquement si l’argument type est un pointeur, ou un std:wstring, ou un type dérivé d’une classe de base particulière.  Dans de tels cas, vous pouvez définir une *spécialisation* du modèle pour ce type particulier. Lorsqu’un utilisateur instantané le modèle avec ce type, le compilateur utilise la spécialisation pour générer la classe, et pour tous les autres types, le compilateur choisit le modèle plus général. Les spécialisations dans lesquelles tous les paramètres sont spécialisés sont *des spécialisations complètes.* Si seulement certains des paramètres sont spécialisés, il est appelé une *spécialisation partielle*.

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

Un modèle peut avoir n’importe quel nombre de spécialisations tant que chaque paramètre de type spécialisé est unique. Seuls les modèles de classe peuvent être partiellement spécialisés. Toutes les spécialisations complètes et partielles d’un modèle doivent être déclarées dans le même espace de nom que le modèle original.

Pour plus d’informations, voir [Template Specialization](../cpp/template-specialization-cpp.md).
