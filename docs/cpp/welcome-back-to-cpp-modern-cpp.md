---
title: Bienvenue dans C++ (C++ moderne)
ms.date: 11/19/2019
ms.topic: conceptual
ms.assetid: 1cb1b849-ed9c-4721-a972-fd8f3dab42e2
ms.openlocfilehash: 2739da77fbfa973ca716abc6d8fa4920b81095d9
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74303330"
---
# <a name="welcome-back-to-c-modern-c"></a>Bienvenue dans C++ (C++ moderne)

Au cours des 25 dernières années C++ , a été l’un des langages de programmation les plus couramment utilisés au monde. Les programmes C++ bien écrits sont rapides et efficaces. Le langage est plus flexible que d’autres langages, car il vous permet d’accéder à des fonctionnalités matérielles de bas niveau pour optimiser la vitesse et réduire les besoins en mémoire. Vous pouvez l’utiliser pour créer un large éventail d’applications, des jeux à des logiciels scientifiques à hautes performances, des pilotes de périphériques, des programmes intégrés, des bibliothèques et des compilateurs pour d’autres langages de programmation, des applications clientes Windows, et bien plus encore.

L'une des spécifications d'origine du C++ était la compatibilité descendante avec le langage C. Par conséquent C++ , il a toujours permis la programmation de style C avec des pointeurs bruts, des tableaux, des chaînes de caractères se terminant par null, des structures de données personnalisées et d’autres fonctionnalités qui peuvent permettre de meilleures performances, mais peuvent également générer des bogues et une complexité. L’évolution de C++ a mis en évidence des fonctionnalités qui réduisent de façon considérable la nécessité d’utiliser des idiomes de style C. Les anciennes fonctionnalités de programmation en C sont là lorsque vous en avez besoin, mais C++ avec du code moderne, vous devez en avoir besoin moins et moins. Le C++ code moderne est plus simple, plus sûr, plus élégant et toujours aussi rapide que jamais.

Les sections suivantes fournissent une vue d’ensemble des principales fonctionnalités d' C++moderne. Sauf indication contraire, les fonctionnalités répertoriées ici sont disponibles dans C++ 11 et versions ultérieures. Dans le compilateur C++ Microsoft, vous pouvez définir l’option du compilateur [/STD](../build/reference/std-specify-language-standard-version.md) pour spécifier la version de la norme à utiliser pour votre projet.

## <a name="raii-and-smart-pointers"></a>Pointeurs RAII et intelligent

L’une des principales classes de bogues dans la programmation de style C est la *fuite de mémoire* en raison de l’échec de l’appel de **Delete** pour la mémoire qui a été allouée avec **New**. Moderne C++ insiste sur le principe de l' *acquisition des ressources* , qui stipule que toutes les ressources (mémoire du tas, descripteurs de fichiers, Sockets, etc.) doivent *appartenir* à un objet qui crée ou reçoit la ressource nouvellement allouée dans son constructeur et le supprime dans son destructeur. En adhérant au principe de RAII, vous garantissez que toutes les ressources seront correctement retournées au système d’exploitation lorsque l’objet propriétaire sera hors de portée. Pour prendre en charge l’adoption facile des principes C++ RAII, la bibliothèque standard fournit trois types pointeur intelligents : [std :: unique_ptr](../standard-library/unique-ptr-class.md), [std :: shared_ptr](../standard-library/shared-ptr-class.md)et [std :: weak_ptr](../standard-library/weak-ptr-class.md). Un pointeur intelligent gère l’allocation et la suppression de la mémoire qu’il détient. L’exemple suivant montre une classe avec un membre de tableau qui est alloué sur le tas dans l’appel à `make_unique()`. Les appels à **New** et **Delete** sont encapsulés par la classe `unique_ptr`. Quand un objet `widget` est hors de portée, le destructeur unique_ptr est appelé et libère la mémoire qui a été allouée pour le tableau.  

```cpp
#include <memory>
class widget
{
private:
    std::unique_ptr<int> data;
public:
    widget(const int size) { data = std::make_unique<int>(size); }
    void do_something() {}
};

void functionUsingWidget() {
    widget w(1000000);   // lifetime automatically tied to enclosing scope
                // constructs w, including the w.data gadget member
    // ...
    w.do_something();
    // ...
} // automatic destruction and deallocation for w and w.data

```

Dans la mesure du possible, utilisez un pointeur intelligent lors de l’allocation de la mémoire du tas. Si vous devez utiliser les opérateurs New et Delete explicitement, suivez le principe du RAII. Pour plus d’informations, consultez Gestion de la [durée de vie des objets et de la gestion des ressources (RAII)](object-lifetime-and-resource-management-modern-cpp.md).

## <a name="stdstring-and-stdstring_view"></a>std :: String et std :: string_view

Les chaînes de style C représentent une autre source importante de bogues. En utilisant [std :: String et std :: wstring](../standard-library/basic-string-class.md) , vous pouvez éliminer pratiquement toutes les erreurs associées aux chaînes de style C et tirer parti des fonctions membres pour la recherche, l’ajout, la préattente, etc. Les deux sont hautement optimisés pour la vitesse. Lors du passage d’une chaîne à une fonction qui requiert uniquement un accès en lecture seule, dans (C++ 17), vous pouvez utiliser [std :: string_view](../standard-library/basic-string-view-class.md) pour un gain de performances encore plus important.

## <a name="stdvector-and-other-standard-library-containers"></a>std :: Vector et autres conteneurs de bibliothèque standard

Les conteneurs de la bibliothèque standard suivent tous le principe de l’RAII, fournissent des itérateurs pour un parcours sécurisé des éléments, sont hautement optimisés pour les performances et ont été soigneusement testés pour l’exactitude. En utilisant ces conteneurs chaque fois que cela est possible, vous éliminez le risque de bogues ou d’inefficacités qui peuvent être introduits dans des structures de données personnalisées. Par défaut, utilisez [Vector](../standard-library/vector-class.md) comme conteneur séquentiel par défaut dans C++. Cela équivaut à `List<T>` dans les langages .NET.

```cpp
vector<string> apples;
apples.push_back("Granny Smith");
```

Utilisez [Map](../standard-library/map-class.md) (non `unordered_map`) comme conteneur associatif par défaut. Utilisez [Set](../standard-library/set-class.md), [Multimap](../standard-library/multimap-class.md)et [multijeu](../standard-library/multiset-class.md) pour la dégénération et plusieurs cas.

```cpp
map<string, string> apple_color;
// ...
apple_color["Granny Smith"] = "Green";
```

Lorsque vous avez besoin de l’optimisation des performances, envisagez d’utiliser :

- Le type de [tableau](../standard-library/array-class-stl.md) lorsque l’incorporation est important, par exemple, en tant que membre de classe.

- Conteneurs associatifs non ordonnés, tels que [unordered_map](../standard-library/unordered-map-class.md). Celles-ci ont une surcharge par élément réduite et une recherche à temps constant, mais elles peuvent être plus difficiles à utiliser correctement et efficacement.

- `vector`triée. Pour plus d’informations, consultez [Algorithmes](../cpp/algorithms-modern-cpp.md).

N’utilisez pas de tableaux de style C. Pour les API plus anciennes qui nécessitent un accès direct aux données, utilisez des méthodes d’accesseur telles que `f(vec.data(), vec.size());` à la place. Pour plus d’informations sur les conteneurs, consultez [ C++ conteneurs de bibliothèque standard](../standard-library/stl-containers.md).

## <a name="standard-library-algorithms"></a>Algorithmes de bibliothèque standard

Avant de supposer que vous devez écrire un algorithme personnalisé pour votre programme, commencez par examiner C++ les [algorithmes](../standard-library/algorithm.md)de la bibliothèque standard. La bibliothèque standard contient un assortiment sans cesse croissant d’algorithmes pour de nombreuses opérations courantes, telles que la recherche, le tri, le filtrage et la randomisation. La bibliothèque mathématique est complète. À partir de C++ 17, des versions parallèles de nombreux algorithmes sont fournies.

Voici quelques exemples importants :

- **for_each**, l’algorithme de parcours par défaut (avec les boucles for basées sur une plage). 

- **transformation**, pour la modification sur place des éléments de conteneur

- **find_if**, l’algorithme de recherche par défaut.

- **triez**, **lower_bound**et les autres algorithmes de tri et de recherche par défaut.

Pour écrire un comparateur, utilisez strict **<** et utilisez des *expressions lambda nommées* lorsque vous le pouvez.

```cpp
auto comp = [](const widget& w1, const widget& w2)
     { return w1.weight() < w2.weight(); }

sort( v.begin(), v.end(), comp );

auto i = lower_bound( v.begin(), v.end(), comp );
```

## <a name="auto-instead-of-explicit-type-names"></a>automatique au lieu de noms de types explicites

C++ 11 a introduit le mot clé [auto](auto-cpp.md) à utiliser dans les déclarations de variable, de fonction et de modèle. **auto** indique au compilateur de déduire le type de l’objet afin que vous n’ayez pas à le taper explicitement. **auto** est particulièrement utile lorsque le type déduit est un modèle imbriqué :

```cpp
map<int,list<string>>::iterator i = m.begin(); // C-style
auto i = m.begin(); // modern C++
```

## <a name="range-based-for-loops"></a>Boucles for basées sur une plage

L’itération de style C sur les tableaux et les conteneurs est sujette à l’indexation des erreurs et est également fastidieux à taper. Pour éliminer ces erreurs et rendre votre code plus lisible, utilisez des boucles for basées sur des plages avec des conteneurs de bibliothèque standard ainsi que des tableaux bruts. Pour plus d’informations, consultez [instruction for basée sur une plage](../cpp/range-based-for-statement-cpp.md).

```cpp
#include <iostream>
#include <vector>

int main()
{
    std::vector<int> v {1,2,3};

    // C-style
    for(int i = 0; i < v.size(); ++i)
    {
        std::cout << v[i];
    }

    // Modern C++:
    for(auto& num : v)
    {
        std::cout << num;
    }
}
```

## <a name="constexpr-expressions-instead-of-macros"></a>expressions constexpr au lieu de macros

Les macros en C C++ et sont des jetons traités par le préprocesseur avant la compilation. Chaque instance d’un jeton de macro est remplacée par la valeur ou l’expression définie avant la compilation du fichier. Les macros sont couramment utilisées dans la programmation de style C pour définir des valeurs constantes au moment de la compilation. Toutefois, les macros sont sujettes aux erreurs et difficiles à déboguer. Dans moderne C++, vous devez préférer les variables [constexpr](constexpr-cpp.md) pour les constantes au moment de la compilation :

```cpp
#define SIZE 10 / C-style
constexpr int size = 10; // modern C++
```

### <a name="uniform-initialization"></a>Initialisation uniforme

Dans moderne C++, vous pouvez utiliser l’initialisation des accolades pour n’importe quel type. Cette forme d’initialisation est particulièrement pratique lors de l’initialisation de tableaux, de vecteurs ou d’autres conteneurs. Dans l’exemple suivant, `v2` est initialisé avec 3 instances de `S`. `v3` est initialisé avec 3 instances de `S` qui sont elles-mêmes initialisées avec des accolades. Le compilateur déduit le type de chaque élément en fonction du type déclaré de `v3`.

```cpp
#include <vector>

struct S
{
    std::string name;
    float num;
    S(std::string s, float f) : name(s), num(f) {}
};

int main()
{
    // C-style initialization
    std::vector<S> v;
    S s1("Norah", 2.7);
    S s2("Frank", 3.5);
    S s3("Jeri", 85.9);

    v.push_back(s1);
    v.push_back(s2);
    v.push_back(s3);

    // Modern C++:
    std::vector<S> v2 {s1, s2, s3};

    // or...
    std::vector<S> v3{ {"Norah", 2.7}, {"Frank", 3.5}, {"Jeri", 85.9} };

}
```

Pour plus d’informations, consultez [initialisation des accolades](initializing-classes-and-structs-without-constructors-cpp.md).

## <a name="move-semantics"></a>Sémantique de déplacement

Moderne C++ fournit la *sémantique de déplacement* qui permet d’éliminer les copies de mémoire inutiles qui, dans les versions antérieures du langage, étaient inévitables dans certaines situations. Une opération de *déplacement* transfère la propriété d’une ressource d’un objet à l’autre sans effectuer de copie. Lors de l’implémentation d’une classe qui possède une ressource telle que la mémoire du tas, les handles de fichiers, etc., vous pouvez définir un *constructeur de déplacement* et un opérateur d' *assignation de déplacement* pour celui-ci. Le compilateur choisira ces membres spéciaux lors de la résolution de la surcharge dans les cas où une copie n’est pas nécessaire. Les types de conteneurs de la bibliothèque standard appellent le constructeur de déplacement sur les objets, s’il est défini. Pour plus d’informations, consultez [constructeurs de déplacement et opérateurs d’assignationC++de déplacement ()](move-constructors-and-move-assignment-operators-cpp.md).

## <a name="lambda-expressions"></a>Expressions lambda

Dans la programmation de style C, une fonction peut être passée à une autre fonction au moyen d’un *pointeur de fonction*. Les pointeurs fonction sont peu pratiques à gérer et à comprendre, car la fonction à laquelle ils font référence peut être définie ailleurs dans le code source, loin du point auquel elle est appelée. En outre, ils ne sont pas de type sécurisé. Moderne C++ fournit des objets de fonction, des classes qui remplacent l’opérateur [()](function-call-operator-parens.md) , ce qui leur permet d’être appelés comme une fonction. La méthode la plus pratique pour créer des objets de fonction consiste à utiliser des [expressions lambda](../cpp/lambda-expressions-in-cpp.md)Inline. L’exemple suivant montre comment utiliser une expression lambda pour passer un objet de fonction, que la fonction `for_each` appellera sur chaque élément du vecteur :

```cpp
    std::vector<int> v {1,2,3,4,5};
    int x = 2;
    int y = 4;
    auto result = find_if(begin(v), end(v), [=](int i) { return i > x && i < y; });
```

L’expression lambda `[=](int i) { return i > x && i < y; }` peut être lue en tant que fonction qui accepte un argument unique de type `int` et retourne une valeur booléenne qui indique si l’expression a la valeur true. Notez que les variables `x` et `y` à partir du contexte environnant peuvent être utilisées dans l’expression lambda. L' `[=]` spécifie que ces variables sont *capturées* par valeur ; en d’autres termes, l’expression lambda a ses propres copies de ces valeurs.

## <a name="exceptions"></a>Exceptions

En règle générale, moderne C++ met l’accent sur les exceptions plutôt que sur les codes d’erreur comme la meilleure façon de signaler et gérer les conditions d’erreur. Pour plus d’informations, [consultez C++ meilleures pratiques modernes pour les exceptions et la gestion des erreurs](errors-and-exception-handling-modern-cpp.md).

## <a name="stdatomic"></a>std :: Atomic

Utilisez la C++ structure standard de la bibliothèque [std :: Atomic](../standard-library/atomic-structure.md) et les types associés pour les mécanismes de communication entre threads.

## <a name="stdvariant-c17"></a>std :: variant (C++ 17)

Les unions sont couramment utilisées dans la programmation de style C pour économiser la mémoire en permettant aux membres de types différents d’occuper le même emplacement de mémoire. Toutefois, les unions ne sont pas de type sécurisé et sont sujettes à des erreurs de programmation. C++ 17 introduit la classe [std :: variant](../standard-library/variant-class.md) comme une alternative plus robuste et plus sûre aux unions. La fonction [std :: Visit](../standard-library/variant-functions.md#visit) peut être utilisée pour accéder aux membres d’un type de `variant` de manière sécurisée.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur le langage C++](../cpp/cpp-language-reference.md)<br/>
[Expressions lambda](../cpp/lambda-expressions-in-cpp.md)<br/>
[Bibliothèque C++ standard](../standard-library/cpp-standard-library-reference.md)<br/>
[Table C++ de conformité linguistique Microsoft](../overview/visual-cpp-language-conformance.md)