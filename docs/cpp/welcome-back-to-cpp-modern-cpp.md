---
title: Bienvenue à CMD - Modern C
description: Décrit les nouveaux idiomes de programmation dans Modern C et leur justification.
ms.date: 01/10/2020
ms.topic: conceptual
ms.assetid: 1cb1b849-ed9c-4721-a972-fd8f3dab42e2
ms.openlocfilehash: 7d0fcb623162713b845107bbf00669af7ae5ca98
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369491"
---
# <a name="welcome-back-to-c---modern-c"></a>Bienvenue à CMD - Modern C

Depuis sa création, le C est devenu l’un des langages de programmation les plus utilisés au monde. Les programmes C++ bien écrits sont rapides et efficaces. La langue est plus souple que les autres langues : elle peut fonctionner aux plus hauts niveaux d’abstraction, et au niveau du silicium. CMD fournit des bibliothèques standard hautement optimisées. Il permet d’accéder à des fonctionnalités matérielles de bas niveau, de maximiser la vitesse et de minimiser les besoins de mémoire. À l’aide de C, vous pouvez créer un large éventail d’applications. Jeux, pilotes d’appareils et logiciels scientifiques de haute performance. Programmes intégrés. Applications client Windows. Même les bibliothèques et les compilateurs pour d’autres langages de programmation sont écrits en C.

L'une des spécifications d'origine du C++ était la compatibilité descendante avec le langage C. Par conséquent, le CMD a toujours permis une programmation de style C, avec des pointeurs bruts, des tableaux, des chaînes de caractères à durée nulle et d’autres fonctionnalités. Ils peuvent permettre de grandes performances, mais peuvent également engendrer des bogues et de la complexité. L’évolution de la C a mis l’accent sur les caractéristiques qui réduisent considérablement le besoin d’utiliser des idiomes de style C. Les anciennes installations de programmation C sont là quand vous en avez besoin, mais avec le code C', vous devriez en avoir besoin de moins en moins. Le code moderne de C EST plus simple, plus sûr, plus élégant et toujours aussi rapide.

Les sections suivantes donnent un aperçu des principales caractéristiques du C moderne. Sauf indication contraire, les fonctionnalités énumérées ici sont disponibles dans le C 11 et plus tard. Dans le compilateur Microsoft CMD, vous pouvez définir l’option [compilateur /std](../build/reference/std-specify-language-standard-version.md) pour spécifier la version de la norme à utiliser pour votre projet.

## <a name="resources-and-smart-pointers"></a>Ressources et pointeurs intelligents

Une des principales classes de bugs dans la programmation de style C est la *fuite de mémoire*. Les fuites sont souvent causées par un défaut d’appeler **supprimer** pour la mémoire qui a été alloué avec **de nouveaux**. Modern CMD met l’accent sur le principe de l’acquisition de *ressources est l’initialisation* (RAII). L’idée est simple. Les ressources (mémoire de tas, poignées de fichiers, prises, etc.) doivent *être détenues* par un objet. Cet objet crée, ou reçoit, la ressource nouvellement allouée dans son constructeur, et la supprime dans son destructurateur. Le principe de RAII garantit que toutes les ressources sont correctement retournées au système d’exploitation lorsque l’objet propriétaire n’est pas de portée.

Pour soutenir l’adoption facile des principes RAII, la Bibliothèque standard CMD fournit trois types de pointeurs intelligents: [std::unique_ptr](../standard-library/unique-ptr-class.md), [std::shared_ptr](../standard-library/shared-ptr-class.md), et [std::weak_ptr](../standard-library/weak-ptr-class.md). Un pointeur intelligent gère l’allocation et la suppression de la mémoire qu’il possède. L’exemple suivant montre une classe avec un membre du tableau `make_unique()`qui est alloué sur le tas dans l’appel à . Les appels vers **le nouveau** et **supprimer** sont encapsulés par la `unique_ptr` classe. Lorsqu’un `widget` objet sort de portée, le unique_ptr destructeur sera invoqué et il libérera la mémoire qui a été allouée pour le tableau.  

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

Dans la mesure du possible, utilisez un pointeur intelligent lors de l’attribution de la mémoire de tas. Si vous devez utiliser les nouveaux opérateurs et supprimer explicitement les opérateurs, suivez le principe de RAII. Pour plus d’informations, voir [la durée de vie de l’objet et la gestion des ressources (RAII)](object-lifetime-and-resource-management-modern-cpp.md).

## <a name="stdstring-and-stdstring_view"></a>std::string et std::string_view

Les cordes de style C sont une autre source importante de bogues. En utilisant [std::string et std::wstring](../standard-library/basic-string-class.md), vous pouvez éliminer pratiquement toutes les erreurs associées aux cordes de style C. Vous bénéficiez également de l’avantage des fonctions des membres pour la recherche, l’appending, le pré-dépenses, et ainsi de suite. Les deux sont très optimisés pour la vitesse. Lorsque vous passez une corde à une fonction qui ne nécessite qu’un accès à la lecture seulement, dans le C 17, vous pouvez utiliser [std::string_view](../standard-library/basic-string-view-class.md) pour un avantage de performance encore plus grand.

## <a name="stdvector-and-other-standard-library-containers"></a>std::vector et autres conteneurs Standard Library

Les conteneurs standard de la Bibliothèque suivent tous le principe de RAII. Ils fournissent des itérateurs pour la traversée sécuritaire des éléments. Et, ils sont très optimisés pour les performances et ont été soigneusement testés pour la justesse. En utilisant ces conteneurs, vous éliminez le potentiel de bogues ou d’inefficacités qui pourraient être introduits dans les structures de données personnalisées. Au lieu de tableaux bruts, utilisez [le vecteur](../standard-library/vector-class.md) comme récipient séquentiel dans le C.

```cpp
vector<string> apples;
apples.push_back("Granny Smith");
```

Utilisez [la](../standard-library/map-class.md) `unordered_map`carte (pas ) comme conteneur associatif par défaut. Utiliser [l’ensemble,](../standard-library/set-class.md) [multimap](../standard-library/multimap-class.md), et [multiset](../standard-library/multiset-class.md) pour dégénérer et multi-cas.

```cpp
map<string, string> apple_color;
// ...
apple_color["Granny Smith"] = "Green";
```

Lorsque l’optimisation des performances est nécessaire, envisagez d’utiliser :

- Le type [de tableau](../standard-library/array-class-stl.md) lors de l’intégration est important, par exemple, en tant que membre de la classe.

- Conteneurs associatifs non ordonnés tels que [unordered_map](../standard-library/unordered-map-class.md). Ceux-ci ont des frais généraux par élément plus bas et un examen constant, mais ils peuvent être plus difficiles à utiliser correctement et efficacement.

- Trié `vector`. Pour plus d’informations, consultez [Algorithmes](../cpp/algorithms-modern-cpp.md).

N’utilisez pas de tableaux de style C. Pour les API plus anciennes qui ont besoin d’un accès direct aux données, utilisez des méthodes d’accesseur telles que `f(vec.data(), vec.size());` la place. Pour plus d’informations sur les conteneurs, consultez [les conteneurs de bibliothèque standard CMD](../standard-library/stl-containers.md).

## <a name="standard-library-algorithms"></a>Algorithmes de bibliothèque standard

Avant de supposer que vous devez écrire un algorithme personnalisé pour votre programme, passez d’abord en revue les [algorithmes](../standard-library/algorithm.md)de la Bibliothèque standard C . La Bibliothèque Standard contient un assortiment sans cesse croissant d’algorithmes pour de nombreuses opérations courantes telles que la recherche, le tri, le filtrage et la randomisation. La bibliothèque de mathématiques est vaste. À partir de C 17, des versions parallèles de nombreux algorithmes sont fournies.

Voici quelques exemples importants :

- **for_each**, l’algorithme traversal par défaut (avec la portée basée sur les boucles).

- **transformer**, pour la modification non-place des éléments de conteneur

- **find_if**, l’algorithme de recherche par défaut.

- **trier**, **lower_bound**, et les autres algorithmes de tri et de recherche par défaut.

Pour écrire un comparateur, utilisez strict **<** et utilisez des *lambdas nommés* quand vous le pouvez.

```cpp
auto comp = [](const widget& w1, const widget& w2)
     { return w1.weight() < w2.weight(); }

sort( v.begin(), v.end(), comp );

auto i = lower_bound( v.begin(), v.end(), comp );
```

## <a name="auto-instead-of-explicit-type-names"></a>auto au lieu de noms de type explicites

Le mot clé auto pour une utilisation dans les déclarations variables, de fonction et de modèle a introduit le mot clé [automatique](auto-cpp.md) pour une utilisation variable, fonction et modèle. **auto** indique au compilateur de déduire le type de l’objet de sorte que vous n’avez pas à le taper explicitement. **l’automobile** est particulièrement utile lorsque le type déduit est un modèle imbriqué :

```cpp
map<int,list<string>>::iterator i = m.begin(); // C-style
auto i = m.begin(); // modern C++
```

## <a name="range-based-for-loops"></a>Portée basée sur les boucles

L’itération de style C sur les tableaux et les conteneurs est sujette à des erreurs d’indexation et est également fastidieuse à taper. Pour éliminer ces erreurs et rendre votre code plus lisible, utilisez la portée pour les boucles avec des conteneurs Standard Library et des tableaux bruts. Pour plus d’informations, voir [Range-based for statement](../cpp/range-based-for-statement-cpp.md).

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

Les macros en C et en C sont des jetons qui sont traités par le préprocesseur avant la compilation. Chaque instance d’un jeton macro est remplacée par sa valeur ou son expression définie avant que le fichier ne soit compilé. Les macros sont couramment utilisés dans la programmation de type C pour définir les valeurs constantes de compile-temps. Cependant, les macros sont sujettes aux erreurs et difficiles à déboiffer. Dans le C moderne, vous devriez préférer les variables [constexpr](constexpr-cpp.md) pour les constantes de temps de compilation :

```cpp
#define SIZE 10 // C-style
constexpr int size = 10; // modern C++
```

### <a name="uniform-initialization"></a>Initialisation uniforme

Dans le C moderne, vous pouvez utiliser l’initialisation d’accolade pour n’importe quel type. Cette forme d’initialisation est particulièrement pratique lors de l’initialisation des tableaux, des vecteurs ou d’autres conteneurs. Dans l’exemple `v2` suivant, est paradé avec trois cas de `S`. `v3`est parasécé `S` avec trois cas qui sont eux-mêmes parasésifés à l’aide d’accolades. Le compilateur déduit le type de chaque élément `v3`en fonction du type déclaré de .

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

Pour plus d’informations, voir [l’initialisation Brace](initializing-classes-and-structs-without-constructors-cpp.md).

## <a name="move-semantics"></a>Déplacer la sémantique

Le Cmd moderne fournit la *sémantique de mouvement,* qui permettent d’éliminer les copies inutiles de mémoire. Dans les versions antérieures de la langue, les copies étaient inévitables dans certaines situations. Une opération *de déménagement* transfère la propriété d’une ressource d’un objet à l’autre sans en faire une copie. Lors de la mise en œuvre d’une classe qui possède une ressource (comme la mémoire de tas, poignées de fichiers, et ainsi de suite), vous pouvez définir un *constructeur de mouvement* et déplacer *l’opérateur d’affectation* pour elle. Le compilateur choisira ces membres spéciaux lors de la résolution de surcharge dans les situations où une copie n’est pas nécessaire. Les types de conteneurs Standard Library invoquent le constructeur de mouvement sur les objets si l’on est défini. Pour plus d’informations, voir [Move Constructors et Move Assignment Operators (CMD)](move-constructors-and-move-assignment-operators-cpp.md).

## <a name="lambda-expressions"></a>Expressions lambda

Dans la programmation de style C, une fonction peut être transmise à une autre fonction en utilisant un *pointeur de fonction*. Les pointeurs de fonction sont gênants à maintenir et à comprendre. La fonction à laquelle ils se réfèrent peut être définie ailleurs dans le code source, loin du point où elle est invoquée. En outre, ils ne sont pas de type-sûr. Le Cmd moderne fournit des *objets de fonction,* des classes qui remplacent l’opérateur [()](function-call-operator-parens.md) qui leur permet d’être appelés comme une fonction. La façon la plus pratique de créer des objets de fonction est avec [des expressions lambda](../cpp/lambda-expressions-in-cpp.md)en ligne . L’exemple suivant montre comment utiliser une expression lambda pour `for_each` passer un objet de fonction, que la fonction invoquera sur chaque élément du vecteur :

```cpp
    std::vector<int> v {1,2,3,4,5};
    int x = 2;
    int y = 4;
    auto result = find_if(begin(v), end(v), [=](int i) { return i > x && i < y; });
```

L’expression `[=](int i) { return i > x && i < y; }` lambda peut être lu comme "fonction `int` qui prend un seul argument de `x` type et `y`renvoie un boolean qui indique si l’argument est plus grand et moins que ." Notez que `x` `y` les variables et du contexte environnant peuvent être utilisés dans le lambda. Le `[=]` spécifie que ces variables sont *capturées* par la valeur; en d’autres termes, l’expression lambda a ses propres copies de ces valeurs.

## <a name="exceptions"></a>Exceptions

Le CMD moderne met l’accent sur les exceptions plutôt que les codes d’erreur comme la meilleure façon de signaler et de gérer les conditions d’erreur. Pour plus d’informations, consultez [les meilleures pratiques modernes de CMD pour les exceptions et le traitement des erreurs.](errors-and-exception-handling-modern-cpp.md)

## <a name="stdatomic"></a>std::atomique

Utilisez le std de la Bibliothèque standard [de CMD : :](../standard-library/atomic-structure.md) struct atomique et types connexes pour les mécanismes de communication inter-thread.

## <a name="stdvariant-c17"></a>std::variant (C 17)

Les syndicats sont couramment utilisés dans la programmation de type C pour conserver la mémoire en permettant aux membres de différents types d’occuper le même emplacement de mémoire. Cependant, les syndicats ne sont pas sûrs de type et sont sujets à des erreurs de programmation. Le C-17 introduit la catégorie [std::variant](../standard-library/variant-class.md) comme une alternative plus robuste et plus sûre aux syndicats. Le [std::la](../standard-library/variant-functions.md#visit) fonction de visite peut `variant` être utilisée pour accéder aux membres d’un type d’une manière de type-sûr.

## <a name="see-also"></a>Voir aussi

[Référence linguistique de CMD](../cpp/cpp-language-reference.md)\
[Lambda Expressions](../cpp/lambda-expressions-in-cpp.md)\
[Bibliothèque standard de CMD](../standard-library/cpp-standard-library-reference.md)\
[Table de conformité linguistique Microsoft CMD](../overview/visual-cpp-language-conformance.md)
