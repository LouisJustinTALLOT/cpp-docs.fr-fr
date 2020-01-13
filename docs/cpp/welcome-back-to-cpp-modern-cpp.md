---
title: Retour à C++ la page moderneC++
description: Décrit les nouveaux idiomes de programmation dans C++ moderne et leurs raisonnements.
ms.date: 01/10/2020
ms.topic: conceptual
ms.assetid: 1cb1b849-ed9c-4721-a972-fd8f3dab42e2
ms.openlocfilehash: 9630322024e639f9e5db1888dac5a1530befc716
ms.sourcegitcommit: ba129dc55dc3ff638f3af5ac0e87ec2ca1cb2674
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2020
ms.locfileid: "75869719"
---
# <a name="welcome-back-to-c---modern-c"></a>Retour à C++ la page moderneC++

Depuis sa création, C++ est devenu l’un des langages de programmation les plus couramment utilisés au monde. Les programmes C++ bien écrits sont rapides et efficaces. Le langage est plus flexible que d’autres langages : il peut fonctionner aux niveaux d’abstraction les plus élevés et baisser au niveau du silicium. C++fournit des bibliothèques standard hautement optimisées. Il permet d’accéder aux fonctionnalités matérielles de bas niveau, afin d’optimiser la vitesse et de réduire les besoins en mémoire. À C++l’aide de, vous pouvez créer un large éventail d’applications. Jeux, pilotes de périphériques et logiciels scientifiques à hautes performances. Programmes incorporés. Applications clientes Windows. Même les bibliothèques et les compilateurs pour d’autres langages de C++programmation sont écrits dans.

L'une des spécifications d'origine du C++ était la compatibilité descendante avec le langage C. Par conséquent, C++ a toujours autorisé la programmation de style C, avec des pointeurs bruts, des tableaux, des chaînes de caractères se terminant par null et d’autres fonctionnalités. Elles peuvent permettre de meilleures performances, mais elles peuvent également générer des bogues et une complexité. L’évolution de C++ a mis en évidence des fonctionnalités qui réduisent de façon considérable la nécessité d’utiliser des idiomes de style C. Les anciennes fonctionnalités de programmation en C sont là lorsque vous en avez besoin, mais C++ avec du code moderne, vous devez en avoir besoin moins et moins. Le C++ code moderne est plus simple, plus sûr, plus élégant et toujours aussi rapide que jamais.

Les sections suivantes fournissent une vue d’ensemble des principales fonctionnalités d' C++moderne. Sauf indication contraire, les fonctionnalités répertoriées ici sont disponibles dans C++ 11 et versions ultérieures. Dans le compilateur C++ Microsoft, vous pouvez définir l’option du compilateur [/STD](../build/reference/std-specify-language-standard-version.md) pour spécifier la version de la norme à utiliser pour votre projet.

## <a name="resources-and-smart-pointers"></a>Ressources et pointeurs intelligents

La *fuite de mémoire*est l’une des principales classes de bogues dans la programmation de style C. Les fuites sont souvent dues à l’impossibilité d’appeler **Delete** pour la mémoire qui a été allouée avec **New**. Moderne C++ insiste sur le principe de l’initialisation de l' *acquisition des ressources* (RAII). L’idée est simple. Les ressources (mémoire du tas, descripteurs de fichiers, Sockets, etc.) doivent *appartenir* à un objet. Cet objet crée ou reçoit la ressource qui vient d’être allouée dans son constructeur, puis le supprime dans son destructeur. Le principe de l’RAII garantit que toutes les ressources sont correctement retournées au système d’exploitation lorsque l’objet propriétaire sort de l’étendue.

Pour prendre en charge l’adoption facile des principes C++ RAII, la bibliothèque standard fournit trois types pointeur intelligents : [std :: unique_ptr](../standard-library/unique-ptr-class.md), [std :: shared_ptr](../standard-library/shared-ptr-class.md)et [std :: weak_ptr](../standard-library/weak-ptr-class.md). Un pointeur intelligent gère l’allocation et la suppression de la mémoire qu’il détient. L’exemple suivant montre une classe avec un membre de tableau qui est alloué sur le tas dans l’appel à `make_unique()`. Les appels à **New** et **Delete** sont encapsulés par la classe `unique_ptr`. Quand un objet `widget` est hors de portée, le destructeur unique_ptr est appelé et libère la mémoire qui a été allouée pour le tableau.  

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

Les chaînes de style C représentent une autre source importante de bogues. En utilisant [std :: String et std :: wstring](../standard-library/basic-string-class.md), vous pouvez éliminer pratiquement toutes les erreurs associées aux chaînes de style C. Vous bénéficiez également de l’avantage des fonctions membres pour la recherche, l’ajout, le préattente, etc. Les deux sont hautement optimisés pour la vitesse. Lors du passage d’une chaîne à une fonction qui requiert uniquement un accès en lecture seule, en C++ 17, vous pouvez utiliser [std :: string_view](../standard-library/basic-string-view-class.md) pour un gain de performances encore plus important.

## <a name="stdvector-and-other-standard-library-containers"></a>std :: Vector et autres conteneurs de bibliothèque standard

Les conteneurs de la bibliothèque standard suivent tous le principe du RAII. Ils fournissent des itérateurs pour un parcours sécurisé des éléments. De plus, ils sont hautement optimisés pour les performances et ont été soigneusement testés pour l’exactitude. À l’aide de ces conteneurs, vous éliminez les risques de bogues ou d’inefficacités qui peuvent être introduits dans des structures de données personnalisées. Au lieu de tableaux bruts, utilisez [Vector](../standard-library/vector-class.md) comme conteneur séquentiel dans C++.

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

L’itération de style C sur les tableaux et les conteneurs est sujette à l’indexation des erreurs et est également fastidieux à taper. Pour éliminer ces erreurs et rendre votre code plus lisible, utilisez des boucles for basées sur une plage avec des conteneurs de bibliothèque standard et des tableaux bruts. Pour plus d’informations, consultez [instruction for basée sur une plage](../cpp/range-based-for-statement-cpp.md).

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

Dans moderne C++, vous pouvez utiliser l’initialisation des accolades pour n’importe quel type. Cette forme d’initialisation est particulièrement pratique lors de l’initialisation de tableaux, de vecteurs ou d’autres conteneurs. Dans l’exemple suivant, `v2` est initialisée avec trois instances de `S`. `v3` est initialisée avec trois instances de `S` qui sont elles-mêmes initialisées à l’aide d’accolades. Le compilateur déduit le type de chaque élément en fonction du type déclaré de `v3`.

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

Moderne C++ fournit la *sémantique de déplacement*, qui permet d’éliminer les copies de mémoire inutiles. Dans les versions antérieures du langage, les copies étaient inévitables dans certaines situations. Une opération de *déplacement* transfère la propriété d’une ressource d’un objet à l’autre sans effectuer de copie. Lors de l’implémentation d’une classe qui possède une ressource (telle que la mémoire du tas, les handles de fichiers, etc.), vous pouvez définir un *constructeur de déplacement* et un opérateur d' *assignation de déplacement* pour celui-ci. Le compilateur choisira ces membres spéciaux lors de la résolution de la surcharge dans les cas où une copie n’est pas nécessaire. Les types de conteneurs de la bibliothèque standard appellent le constructeur de déplacement sur les objets, s’il est défini. Pour plus d’informations, consultez [constructeurs de déplacement et opérateurs d’assignationC++de déplacement ()](move-constructors-and-move-assignment-operators-cpp.md).

## <a name="lambda-expressions"></a>Expressions lambda

Dans la programmation de style C, une fonction peut être passée à une autre fonction à l’aide d’un *pointeur de fonction*. Les pointeurs de fonction sont peu pratiques à gérer et à comprendre. La fonction à laquelle ils font référence peut être définie ailleurs dans le code source, loin du point auquel elle est appelée. En outre, ils ne sont pas de type sécurisé. Moderne C++ fournit des *objets de fonction*, des classes qui remplacent l’opérateur [()](function-call-operator-parens.md) , ce qui leur permet d’être appelés comme une fonction. La méthode la plus pratique pour créer des objets de fonction consiste à utiliser des [expressions lambda](../cpp/lambda-expressions-in-cpp.md)Inline. L’exemple suivant montre comment utiliser une expression lambda pour passer un objet de fonction, que la fonction `for_each` appellera sur chaque élément du vecteur :

```cpp
    std::vector<int> v {1,2,3,4,5};
    int x = 2;
    int y = 4;
    auto result = find_if(begin(v), end(v), [=](int i) { return i > x && i < y; });
```

L’expression lambda `[=](int i) { return i > x && i < y; }` peut être lue comme « Function qui accepte un argument unique de type `int` et retourne une valeur booléenne qui indique si l’argument est supérieur à `x` et inférieur à `y`». Notez que les variables `x` et `y` à partir du contexte environnant peuvent être utilisées dans l’expression lambda. L' `[=]` spécifie que ces variables sont *capturées* par valeur ; en d’autres termes, l’expression lambda a ses propres copies de ces valeurs.

## <a name="exceptions"></a>Exceptions

Moderne C++ met en évidence les exceptions plutôt que les codes d’erreur comme la meilleure façon de signaler et gérer les conditions d’erreur. Pour plus d’informations, [consultez C++ meilleures pratiques modernes pour les exceptions et la gestion des erreurs](errors-and-exception-handling-modern-cpp.md).

## <a name="stdatomic"></a>std :: Atomic

Utilisez la C++ structure standard de la bibliothèque [std :: Atomic](../standard-library/atomic-structure.md) et les types associés pour les mécanismes de communication entre threads.

## <a name="stdvariant-c17"></a>std :: variant (C++ 17)

Les unions sont couramment utilisées dans la programmation de style C pour économiser la mémoire en permettant aux membres de types différents d’occuper le même emplacement de mémoire. Toutefois, les unions ne sont pas de type sécurisé et sont sujettes à des erreurs de programmation. C++ 17 introduit la classe [std :: variant](../standard-library/variant-class.md) comme une alternative plus robuste et plus sûre aux unions. La fonction [std :: Visit](../standard-library/variant-functions.md#visit) peut être utilisée pour accéder aux membres d’un type de `variant` de manière sécurisée.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur le langage C++](../cpp/cpp-language-reference.md)\
[Expressions lambda](../cpp/lambda-expressions-in-cpp.md)\
[Bibliothèque standard C++](../standard-library/cpp-standard-library-reference.md)\
[Table C++ de conformité linguistique Microsoft](../overview/visual-cpp-language-conformance.md)
