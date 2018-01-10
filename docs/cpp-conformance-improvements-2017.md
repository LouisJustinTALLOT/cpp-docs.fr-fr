---
title: "Améliorations de la conformité de C++ | Microsoft Docs"
ms.custom: 
ms.date: 11/16/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8801dbdb-ca0b-491f-9e33-01618bff5ae9
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3a1010d7061fb8df20cc821e26e903e356050850
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="c-conformance-improvements-in-visual-studio-2017-versions-150-153improvements153-and-155improvements155"></a>Améliorations de la conformité de C++ dans Visual Studio 2017 versions 15.0, [15.3](#improvements_153) et [15.5](#improvements_155).


Avec la prise en charge des expressions constexpr généralisées et de NSDMI pour les agrégats, le compilateur est désormais complet pour les fonctionnalités ajoutées à la norme C++14. Notez que le compilateur ne dispose pas encore de certaines fonctionnalités des normes C++11 et C++98. Consultez [Conformité du langage Visual C++](visual-cpp-language-conformance.md) pour obtenir un tableau affichant l’état actuel du compilateur.

## <a name="c11"></a>C++11
**Prise en charge de la fonctionnalité SFINAE pour les expressions dans d’autres bibliothèques** Le compilateur Visual C++ continue d’améliorer sa prise en charge de la fonctionnalité SFINAE pour les expressions, qui est nécessaire pour la déduction et la substitution d’argument de modèle dans lesquelles les expressions decltype et constexpr peuvent apparaître en tant que paramètres de modèle. Pour plus d’informations, consultez [Expression SFINAE improvements in Visual Studio 2017 RC](https://blogs.msdn.microsoft.com/vcblog/2016/06/07/expression-sfinae-improvements-in-vs-2015-update-3). 


## <a name="c-14"></a>C++14
**NSDMI pour les agrégats** Un agrégat est un tableau ou une classe sans constructeur fourni par l’utilisateur, sans membres de données non statiques privés ou protégés, sans classes de base et sans fonctions virtuelles. À compter de C++14, les agrégats peuvent contenir des initialiseurs de membres. Pour plus d’informations, consultez [Member initializers and aggregates](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3605.html).

**Expressions constexpr étendues** Les expressions déclarées en tant qu’expressions constexpr sont désormais autorisées à contenir certains types de déclarations, des instructions if et switch, des instructions de boucle et une mutation d’objets dont la vie a commencé dans l’évaluation de l’expression constexpr. En outre, il n’est plus nécessaire qu’une fonction membre non statique constexpr soit implicitement de type const. Pour plus d’informations, consultez [Relaxing constraints on constexpr functions](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3652.html). 

## <a name="c17"></a>C++17
**static_assert laconique** (disponible avec /std:c++17) Dans C++17, le paramètre de message pour static_assert est facultatif. Pour plus d’informations, consultez [Extending static_assert, v2](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n3928.pdf). 

**Attribut [[fallthrough]]** (disponible avec /std:c++17) L’attribut [[fallthrough]] est utilisable dans le contexte des instructions switch en tant qu’indicateur informant le compilateur que le comportement fallthrough est prévu. Ce dispositif empêche le compilateur d’émettre des avertissements dans de tels cas. Pour plus d’informations, consultez [Wording for [[fallthrough]] attribute](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0188r0.pdf). 

**Boucles range-based for généralisées** (aucun commutateur de compilateur nécessaire) Les Boucles range-based for n’exigent plus que begin() et end() retournent des objets du même type. Ainsi, end() peut retourner un objet sentinel, à l’image de ceux utilisés par les plages définies dans [range-v3](https://github.com/ericniebler/range-v3) et la spécification technique d’autres plages disponibles mais pas encore publiées. Pour plus d’informations, consultez [Generalizing the Range-Based For Loop](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0184r0.html). 

## <a name="improvements_153"></a> Améliorations dans Visual Studio 2017 version 15.3

**constexpr lambdas** Les expressions lambda peuvent désormais être utilisées dans les expressions constantes. Pour plus d’informations, consultez [Constexpr Lambda](http://open-std.org/JTC1/SC22/WG21/docs/papers/2015/n4487.pdf).

**if constexpr dans des modèles de fonction** Un modèle de fonction peut contenir des instructions `if constexpr` permettant de créer une branche au moment de la compilation. Pour plus d’informations, consultez [if constexpr](http://open-std.org/JTC1/SC22/WG21/docs/papers/2016/p0128r1.html).

**Instructions Selection avec initialiseurs** Une instruction `if` peut inclure un initialiseur qui présente une variable à portée de bloc dans l’instruction elle-même. Pour plus d’informations, consultez [Selection statements with initializer](http://www.open-std.org/JTC1/SC22/WG21/docs/papers/2016/p0305r1.html).

**Attributs [[maybe_unused]] et [[nodiscard]]** Nouveaux attributs permettant de mettre en silence les avertissements lorsqu’une entité n’est pas utilisée, ou pour créer un avertissement si la valeur de retour d’un appel de fonction est ignorée. Pour plus d’informations, consultez [Wording for maybe_unused attribute](http://open-std.org/JTC1/SC22/WG21/docs/papers/2016/p0212r0.pdf) et [Proposal of unused,nodiscard and fallthrough attributes](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0068r0.pdf).

**Utilisation des espaces de noms d’attribut sans répétition** Nouvelle syntaxe pour activer uniquement un seul identificateur d’espace de noms dans une liste d’attributs. Pour plus d’informations, consultez [Attributes in C++](cpp/attributes2.md).

**Liaisons structurées** Il est désormais possible dans une déclaration unique de stocker une valeur avec des noms individuels pour ses composants, lorsque la valeur est un tableau, un std::tuple ou std::pair, ou contient uniquement des membres de données non statiques publiques. Pour plus d’informations, consultez [Structured Bindings](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0144r0.pdf).

**Règles de construction pour les valeurs de classe enum** Il existe désormais une conversion implicite/non restrictive à partir du type sous-jacent d’une énumération étendue vers l’énumération elle-même, lorsque sa définition ne présente aucun énumérateur et que la source utilise une syntaxe d’initialisation de liste. Pour plus d’informations, consultez [Construction Rules for enum class Values ](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0138r2.pdf).

**Capture de *this par sa valeur** L’objet « \*this » dans une expression lambda peut désormais être capturé par sa valeur. Cela permet des scénarios dans lesquels l’expression lambda est invoquée dans des opérations parallèles et asynchrones, en particulier sur des architectures de machines plus récentes. Pour plus d’informations, consultez [Lambda Capture of \*this by Value as [=,\*this]](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0018r3.html).

**Suppression de operator++ pour bool** operator++ n’est plus pris en charge sur les types `bool`. Pour plus d’informations, consultez [Remove Deprecated operator++(bool)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0002r1.html).

**Suppression du mot clé « register » déconseillé** Le mot clé `register`, précédemment déconseillé (et ignoré par le compilateur Visual C++), est supprimé du langage. Pour plus d’informations, consultez [Remove Deprecated Use of the register Keyword](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0001r1.html).

Pour obtenir la liste complète des améliorations de la conformité jusqu’à Visual Studio 2015, Update 3, consultez [Visual C++ What’s New 2003 through 2015](https://msdn.microsoft.com/en-us/library/mt723604.aspx).

## <a name="improvements_155"></a>  Améliorations dans Visual Studio 2017 version 15.5
Les fonctionnalités marquées avec [14] sont disponibles sans condition même en mode /std:c++14.

**Nouveau commutateur de compilateur pour extern constexpr** Dans les versions antérieures de Visual Studio, le compilateur retournait toujours une liaison interne pour la variable `constexpr`, même quand la variable était marquée comme `extern`. Dans Visual Studio 2017 version 15.5, un nouveau commutateur de compilateur, [/Zc:externConstexpr](build/reference/zc-externconstexpr.md), active le comportement correct de conformité aux normes. Pour plus d’informations, consultez [Liaison extern constexpr](#extern_linkage).

**Suppression des spécifications d’exceptions dynamiques** : [P0003R5](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0003r5.html). Les spécifications d’exceptions dynamiques ont été dépréciées dans C++11. La fonctionnalité est supprimée dans C++17, mais la spécification (toujours) dépréciée `throw()` est conservée uniquement comme alias pour `noexcept(true)`. Pour plus d’informations, consultez [Suppression des spécifications d’exceptions dynamiques et noexcept](#noexcept_removal). 

**not_fn()** : [P0005R4](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0005r4.html) substitue not1 et not2.

**Reformulation d’enable_shared_from_this** : [P0033R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0033r1.html) `enable_shared_from_this` a été ajouté dans C++11. La norme C++17 met à jour la spécification pour mieux gérer certains cas extrêmes. [14]

**Transfert de mappages et d’ensembles** : [P0083R3](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0083r3.pdf). Cette fonctionnalité permet d’extraire des nœuds de conteneurs associatifs (par exemple, map, set, unordered_map, unordered_set) pour les modifier, puis de les réinsérer dans le même conteneur ou dans un autre conteneur qui utilise le même type de nœud. (Un cas d’usage courant consiste à extraire un nœud d’un std::map, à changer la clé et à réinsérer le nœud.)

**Composants de bibliothèque rudimentaires dépréciés** : [P0174R2](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0174r2.html). Plusieurs fonctionnalités de la bibliothèque standard C++ ont été remplacées par de nouvelles fonctionnalités au fil des années, ou ont été jugées inutiles ou problématiques. Ces fonctionnalités sont officiellement dépréciées dans C++17. 

**Suppression de la prise en charge d’un allocateur dans std::function** : [P0302R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0302r1.html). Dans les versions antérieures à C++17, le modèle de classe `std::function` avait plusieurs constructeurs avec un argument allocateur. Toutefois, l’utilisation d’allocateurs dans ce contexte était problématique et la sémantique n’était pas claire. Les constructeurs en question ont été supprimés.

**Correctifs pour not_fn()** : [P0358R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0358r1.html). La nouvelle formulation pour `std::not_fn` permet de prendre en charge la propagation de la catégorie de valeur quand un wrapper est appelé.

**shared_ptr<T[]>, shared_ptr<T[N]>** : [P0414R2](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0414r2.html). Les modifications apportées à shared_ptr dans les notions de base de la bibliothèque ont été fusionnées dans C++17. [14]

**Correction de shared_ptr pour les tableaux** : [P0497R0](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0497r0.html). Correctifs apportés à la prise en charge de shared_ptr pour les tableaux. [14]

**Clarification d’insert_return_type** : [P0508R0](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0508r0.html). Les conteneurs associatifs ou non ordonnés avec des clés uniques ont une fonction membre `insert` qui retourne un type imbriqué `insert_return_type`. Le type de retour est maintenant défini comme une spécialisation d’un type qui est paramétré sur les éléments Iterator et NodeType du conteneur. 

**Variables inline pour la bibliothèque STL** : [P0607R0](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0607r0.html). 

**Fonctionnalités de l’annexe D dépréciées** : L’annexe D de la norme C++ contient toutes les fonctionnalités qui ont été dépréciées, y compris `shared_ptr::unique()`, `<codecvt>` et `namespace std::tr1`. Quand le commutateur de compilateur /std:c++17 est défini, presque toutes les fonctionnalités de la bibliothèque standard répertoriées dans l’annexe D sont marquées comme dépréciées. Pour plus d’informations, consultez [Les fonctionnalités de la bibliothèque standard répertoriées dans l’annexe D sont marquées comme dépréciées](#annex_d).

Maintenant, l’espace de noms `std::tr2::sys` dans `<experimental/filesystem>` affiche un avertissement de désapprobation en mode /std:c++14 par défaut, et est supprimé en mode /std:c++17 par défaut.

La conformité est améliorée dans iostreams, car l’utilisation d’une extension non standard (spécialisations de classe explicites) n’est plus nécessaire.

La bibliothèque standard utilise désormais les modèles de variable en interne.

La bibliothèque standard a été mise à jour en réponse aux modifications apportées au compilateur C++17, notamment l’ajout de noexcept dans le système de type et la suppression des spécifications d’exceptions dynamiques.

## <a name="bug-fixes-in-visual-studio-versions-150-153update153-and-155update155"></a>Correctifs de bogues dans Visual Studio versions 15.0, [15.3](#update_153) et [15.5](#update_155)
### <a name="copy-list-initialization"></a>Copy-list-initialization
Visual Studio 2017 déclenche correctement les erreurs de compilateur liées à la création d’objets à l’aide de listes d’initialiseurs qui n’étaient pas interceptées dans Visual Studio 2015 et qui pouvaient entraîner des blocages ou un comportement d’exécution non défini. Conformément au document N4594, point 13.3.1.7p1, dans copy-list-initialization, le compilateur doit envisager un constructeur explicite pour la résolution de la surcharge, mais doit générer une erreur si cette surcharge est choisie. 

Les deux exemples suivants se compilent dans Visual Studio 2015, mais pas dans Visual Studio 2017.
```cpp  
struct A
{
    explicit A(int) {} 
    A(double) {}
};

int main()
{
    A a1 = { 1 }; // error C3445: copy-list-initialization of 'A' cannot use an explicit constructor
    const A& a2 = { 1 }; // error C2440: 'initializing': cannot convert from 'int' to 'const A &'

}
```
Pour corriger l’erreur, utilisez une initialisation directe :
```cpp  
A a1{ 1 };
const A& a2{ 1 };
```

Dans Visual Studio 2015, le compilateur traitait à tort copy-list-initialization de la même façon que l’instruction copy-initialization ordinaire ; il envisageait uniquement de convertir les constructeurs pour résoudre la surcharge. Dans l’exemple suivant, Visual Studio 2015 choisit MyInt(23), mais Visual Studio 2017 déclenche l’erreur correctement. 

```cpp  
// From http://www.open-std.org/jtc1/sc22/wg21/docs/cwg_closed.html#1228
struct MyStore {
       explicit MyStore(int initialCapacity);
};

struct MyInt {
       MyInt(int i);
};

struct Printer {
       void operator()(MyStore const& s);
       void operator()(MyInt const& i);
};

void f() {
       Printer p;
       p({ 23 }); // C3066: there are multiple ways that an object of this type can be called with these arguments
}
```

Cet exemple est semblable au précédent, mais génère une erreur différente. Il réussit dans Visual Studio 2015, mais échoue dans Visual Studio 2017 avec l’erreur C2668. 

```cpp  
struct A {
    explicit A(int) {}
};

struct B {
    B(int) {}
};

void f(const A&) {}
void f(const B&) {}

int main()
{
    f({ 1 }); // error C2668: 'f': ambiguous call to overloaded function
}
```

### <a name="deprecated-typedefs"></a>Typedefs dépréciées
Visual Studio 2017 émet désormais l’avertissement correct pour les typedefs dépréciées qui sont déclarées dans une classe ou une structure. L’exemple suivant se compile sans avertissements dans Visual Studio 2015, mais génère l’erreur C4996 dans Visual Studio 2017.

```cpp  
struct A 
{
    // also for __declspec(deprecated) 
    [[deprecated]] typedef int inttype;
};

int main()
{
    A::inttype a = 0; // C4996 'A::inttype': was declared deprecated
}
```

### <a name="constexpr"></a>constexpr
Visual Studio 2017 génère correctement une erreur quand l’opérande de gauche d’une opération à évaluation conditionnelle n’est pas valide dans un contexte constexpr. Le code suivant compile dans Visual Studio 2015, mais pas dans Visual Studio 2017 (C3615, la fonction constexpr 'f' ne peut pas produire une expression constante) :

```cpp  
template<int N>
struct array 
{
       int size() const { return N; }
};

constexpr bool f(const array<1> &arr)
{
       return arr.size() == 10 || arr.size() == 11; // C3615    
}
```
Pour corriger cette erreur, déclarez la fonction array::size() en tant que constexpr ou supprimez le qualificateur constexpr de f. 

### <a name="class-types-passed-to-variadic-functions"></a>Types de classe transmis aux fonctions variadiques
Dans Visual Studio 2017, les classes ou structures qui sont passées à une fonction variadique telle que printf doivent être copiables de manière triviale. Quand de tels objets sont passés, le compilateur effectue simplement une copie au niveau du bit et n’appelle pas le constructeur ou le destructeur. 

```cpp  
#include <atomic>
#include <memory>
#include <stdio.h>

int main()
{
    std::atomic<int> i(0);
    printf("%i\n", i); // error C4839: non-standard use of class 'std::atomic<int>'
                        // as an argument to a variadic function
                        // note: the constructor and destructor will not be called; 
                        // a bitwise copy of the class will be passed as the argument
                        // error C2280: 'std::atomic<int>::atomic(const std::atomic<int> &)':
                        // attempting to reference a deleted function

    struct S {
        S(int i) : i(i) {}
        S(const S& other) : i(other.i) {}
        operator int() { return i; }
    private:
        int i;
    } s(0);
    printf("%i\n", s); // warning C4840 : non-portable use of class 'main::S'
                      // as an argument to a variadic function
}
```
Pour corriger cette erreur, vous pouvez appeler une fonction membre qui retourne un type copiable de manière triviale, 

```cpp  
    std::atomic<int> i(0);
    printf("%i\n", i.load());
```
ou effectuer un cast statique pour convertir l’objet avant de le transmettre :
```cpp  
    struct S {/* as before */} s(0);
    printf("%i\n", static_cast<int>(s))
```
Pour les chaînes générées et gérées à l’aide de CStringW, vous devez utiliser le `operator LPCWSTR()` fourni pour caster un objet CStringW vers le pointeur C attendu par la chaîne de format.

```cpp  
CStringW str1;
CStringW str2;
str1.Format(L"%s", static_cast<LPCWSTR>(str2));
```

### <a name="cv-qualifiers-in-class-construction"></a>Qualificateurs cv dans la construction de la classe
Dans Visual Studio 2015, le compilateur ignore parfois à tort le qualificateur cv pendant la génération d’un objet de classe par le biais d’un appel de constructeur. Cela peut provoquer un incident ou un comportement inattendu au moment de l’exécution. L’exemple suivant se compile dans Visual Studio 2015, mais génère une erreur de compilateur dans Visual Studio 2017 :

```cpp  
struct S 
{
    S(int);
    operator int();
};

int i = (const S)0; // error C2440
```
Pour corriger cette erreur, déclarez l’opérateur int() en tant que const. 

### <a name="access-checking-on-qualified-names-in-templates"></a>Contrôle d’accès sur les noms qualifiés dans les modèles
Les versions précédentes du compilateur n’effectuaient pas de contrôle d’accès sur les noms qualifiés dans certains contextes de modèle. Cela peut interférer avec le comportement attendu de la fonctionnalité SFINAE où la substitution est supposée échouer en raison de l’inaccessibilité d’un nom. Cette situation peut entraîner un incident ou un comportement inattendu au moment de l’exécution en raison de l’appel par le compilateur de la surcharge incorrecte de l’opérateur. Dans Visual Studio 2017, une erreur de compilateur est générée. L’erreur spécifique peut varier, mais, en général, il s’agit de « C2672 fonction correspondante surchargée introuvable ». Le code suivant se compile dans Visual Studio 2015, mais génère une erreur dans Visual Studio 2017 :

```cpp  
#include <type_traits>

template <class T> class S {
       typedef typename T type;
};

template <class T, std::enable_if<std::is_integral<typename S<T>::type>::value, T> * = 0>
bool f(T x);

int main()
{
       f(10); // C2672: No matching overloaded function found. 
}
```

### <a name="missing-template-argument-lists"></a>Listes d’arguments de modèle manquantes
Dans Visual Studio 2015 et versions antérieures, le compilateur ne diagnostiquait pas les listes d’arguments de modèle manquantes quand le modèle apparaissait dans une liste de paramètres de modèle (par exemple, dans le cadre d’un argument de modèle par défaut ou d’un paramètre de modèle sans type). Cela peut entraîner un comportement imprévisible, y compris des pannes du compilateur ou un comportement inattendu au moment de l’exécution. Le code suivant se compile dans Visual Studio 2015, mais génère une erreur dans Visual Studio 2017 :

```cpp  
template <class T> class ListNode;
template <class T> using ListNodeMember = ListNode<T> T::*;
template <class T, ListNodeMember M> class ListHead; // C2955: 'ListNodeMember': use of alias 
                                                     // template requires template argument list

// correct:  template <class T, ListNodeMember<T> M> class ListHead;  
```

### <a name="expression-sfinae"></a>Fonctionnalité SFINAE pour les expressions
Pour prendre en charge la fonctionnalité SFINAE pour les expressions, le compilateur analyse maintenant les arguments decltype quand les modèles sont déclarés et non instanciés. Ainsi, si une spécialisation non dépendante est trouvée dans l’argument decltype, elle n’est pas reportée à l’instanciation et est traitée immédiatement, et toute erreur résultante est diagnostiquée à ce moment-là.  

L’exemple suivant montre une erreur de compilateur de ce type générée au moment de la déclaration :

```cpp  
#include <utility>
template <class T, class ReturnT, class... ArgsT> class IsCallable
{
public:
       struct BadType {};
       template <class U>
       static decltype(std::declval<T>()(std::declval<ArgsT>()...)) Test(int); //C2064. Should be declval<U>
       template <class U>
       static BadType Test(...);
       static constexpr bool value = std::is_convertible<decltype(Test<T>(0)), ReturnT>::value;
};

constexpr bool test1 = IsCallable<int(), int>::value;
static_assert(test1, "PASS1");
constexpr bool test2 = !IsCallable<int*, int>::value;
static_assert(test2, "PASS2");
```
### <a name="classes-declared-in-anonymous-namespaces"></a>Classes déclarées dans des espaces de noms anonymes
Selon la norme C++, une classe déclarée dans un espace de noms anonyme a une liaison interne et, par conséquent, ne peut pas être exportée. Dans Visual Studio 2015 et versions antérieures, cette règle n’était pas appliquée. Dans Visual Studio 2017, la règle est partiellement appliquée. L’exemple suivant génère cette erreur dans Visual Studio 2017 : « erreur C2201 : const anonymous namespace::S1::vftable doit avoir une liaison externe afin d’être exporté/importé. »

```cpp
struct __declspec(dllexport) S1 { virtual void f() {} }; //C2201
```

### <a name="default-initializers-for-value-class-members-ccli"></a>Initialiseurs par défaut pour les membres de classe value (C++/CLI)
Dans Visual Studio 2015 et antérieur, le compilateur autorisait (mais ignorait) un initialiseur de membre par défaut pour un membre d’une classe value. L’initialisation par défaut d’une classe value initialise systématiquement les membres à zéro ; un constructeur par défaut n’est pas autorisé. Dans Visual Studio 2017, les initialiseurs de membres par défaut déclenchent une erreur de compilateur, comme illustré dans cet exemple :

```cpp  
value struct V
{
       int i = 0; // error C3446: 'V::i': a default member initializer  
                  // is not allowed for a member of a value class
};
```

### <a name="default-indexers-ccli"></a>Indexeurs par défaut (C++/CLI)
Dans Visual Studio 2015 et antérieur, le compilateur identifiait à tort une propriété par défaut en tant qu’indexeur par défaut dans certaines circonstances. Il était possible de contourner le problème en utilisant l’identificateur « default » pour accéder à la propriété. La solution de contournement elle-même est devenue problématique dès que default a été introduit comme mot clé dans C++11. Ainsi, dans Visual Studio 2017, les bogues qui nécessitaient la solution de contournement ont été corrigés, et le compilateur génère maintenant une erreur quand l’utilisateur recourt à « default » pour accéder à la propriété par défaut d’une classe.

```cpp  
//class1.cs

using System.Reflection;
using System.Runtime.InteropServices;

namespace ClassLibrary1
{
    [DefaultMember("Value")]
    public class Class1
    {
        public int Value
        {
            // using attribute on the return type triggers the compiler bug
            [return: MarshalAs(UnmanagedType.I4)]
            get;
        }
    }
    [DefaultMember("Value")]
    public class Class2
    {
        public int Value
        {
            get;
        }
    }
}

 
// code.cpp
#using "class1.dll"

void f(ClassLibrary1::Class1 ^r1, ClassLibrary1::Class2 ^r2)
{
       r1->Value; // error
       r1->default;
       r2->Value;
       r2->default; // error
}
```

Dans Visual Studio 2017, vous pouvez accéder aux deux propriétés Value par leur nom :

```cpp  
#using "class1.dll"

void f(ClassLibrary1::Class1 ^r1, ClassLibrary1::Class2 ^r2)
{
       r1->Value;
       r2->Value;
}
```

## <a name="update_153"></a> Correctifs de bogues dans Visual Studio 2017 version 15.3
### <a name="calls-to-deleted-member-templates"></a>Appels à des modèles membres supprimés
Dans les versions précédentes de Visual Studio, le compilateur ne parvenait pas dans certains cas à émettre une erreur pour les appels incorrects à un modèle membre supprimé qui pouvaient éventuellement provoquer des incidents lors de l’exécution. Le code suivant génère désormais l’erreur C2280, « 'int S<int>::f<int>(void)' : tentative de référencement d’une fonction supprimée » :
```cpp
template<typename T> 
struct S { 
   template<typename U> static int f() = delete; 
}; 
 
void g() 
{ 
   decltype(S<int>::f<int>()) i; // this should fail 
}
```
Pour corriger cette erreur, déclarez i comme `int`.

### <a name="pre-condition-checks-for-type-traits"></a>Vérifications de conditions préalables pour les traits de type
Visual Studio 2017 version 15.3 améliore les vérifications de conditions préalables pour les traits de type afin de suivre plus strictement la norme. Une telle vérification doit être affectée. Le code suivant génère l’erreur C2139 dans Visual Studio 2017 version 15.3 :

```cpp
struct S; 
enum E; 
 
static_assert(!__is_assignable(S, S), "fail"); // C2139 in 15.3
static_assert(__is_convertible_to(E, E), "fail"); // C2139 in 15.3
```

### <a name="new-compiler-warning-and-runtime-checks-on-native-to-managed-marshaling"></a>Nouvel avertissement du compilateur et nouvelles vérifications à l’exécution sur du marshaling de fonctions natives à managées
L’appel des fonctions managées aux fonctions natives nécessite un marshaling. Le CLR exécute le marshaling, mais il ne comprend pas la sémantique C++. Si vous passez un objet natif par valeur, le CLR appelle le constructeur de copie de l’objet ou utilise BitBlt, ce qui peut provoquer un comportement non défini lors de l’exécution. 
 
Désormais, le compilateur émet un avertissement s’il peut savoir au moment de la compilation qu’un objet natif avec un constructeur de copie supprimé est transmis entre les limites native et managée par valeur. Pour les cas où le compilateur ne sait rien au moment de la compilation, il injecte une vérification à l’exécution afin que le programme appelle std::terminate immédiatement dès qu’un marshaling incorrect se produit. Dans Visual Studio 2017 version 15.3, le code suivant génère l’erreur C4606, « 'A' : le passage d’un argument par valeur à travers une frontière native/managée nécessite un constructeur de copie valide. Sinon, le comportement au moment de l’exécution est non défini. »
```cpp
class A 
{ 
public: 
   A() : p_(new int) {} 
   ~A() { delete p_; } 
 
   A(A const &) = delete; 
   A(A &&rhs) { 
   p_ = rhs.p_; 
} 
 
private: 
   int *p_; 
}; 
 
#pragma unmanaged 
 
void f(A a) 
{ 
} 
 
#pragma managed 
 
int main() 
{ 
    f(A()); // This call from managed to native requires marshalling. The CLR doesn't understand C++ and uses BitBlt, which will result in a double-free later. 
}
```
Pour corriger cette erreur, supprimez la directive `#pragma managed` pour marquer l’appelant comme natif et éviter le marshaling. 

### <a name="experimental-api-warning-for-winrt"></a>Avertissement d’API expérimentale pour WinRT
Les API WinRT publiées pour l’expérimentation et les commentaires sont décorées avec `Windows.Foundation.Metadata.ExperimentalAttribute`. Dans Visual Studio 2017 version 15.3, le compilateur génère l’avertissement C4698 quand il rencontre l’attribut. Certaines API dans les versions précédentes du SDK Windows ont déjà été décorées avec l’attribut et les appels à ces API déclenchent cet avertissement du compilateur. L’attribut est supprimé de tous les types fournis dans les SDK Windows plus récents mais, si vous utilisez un SDK plus ancien, vous devez supprimer ces avertissements pour tous les appels aux types fournis.
Le code suivant génère l’avertissement C4698 : « 'Windows::Storage::IApplicationDataStatics2::GetForUserAsync' est utilisé à des fins d’évaluation uniquement. Il sera peut-être changé ou supprimé au cours des prochaines mises à jour. » :
```cpp
Windows::Storage::IApplicationDataStatics2::GetForUserAsync() //C4698
```

Pour désactiver l’avertissement, ajoutez un #pragma :

```cpp
#pragma warning(push) 
#pragma warning(disable:4698) 
 
Windows::Storage::IApplicationDataStatics2::GetForUserAsync() 
 
#pragma warning(pop)
```
### <a name="out-of-line-definition-of-a-template-member-function"></a>Définition hors ligne d’une fonction membre de modèle 
**Visual Studio 2017 version 15.3** génère une erreur quand elle rencontre une définition hors ligne d’une fonction membre de modèle qui n’a pas été déclarée dans la classe. Le code suivant génère désormais l’erreur C2039 : 'f' : n’est pas un membre de 'S' :

```cpp
struct S {}; 
 
template <typename T> 
void S::f(T t) {} //C2039: 'f': is not a member of 'S'
```

Pour corriger cette erreur, ajoutez une déclaration à la classe :

```cpp
struct S { 
    template <typename T> 
    void f(T t); 
}; 
template <typename T> 
void S::f(T t) {}
```

### <a name="attempting-to-take-the-address-of-this-pointer"></a>Tentative de prendre l’adresse du pointeur 'this'
En C++, 'this' est une prvalue de pointeur de type vers X. Vous ne pouvez pas prendre l’adresse de 'this' ni la lier à une référence lvalue. Dans les versions précédentes de Visual Studio, le compilateur vous permettait de contourner cette restriction en effectuant un cast. Dans Visual Studio 2017 version 15.3, le compilateur génère l’erreur C2664.

### <a name="conversion-to-an-inaccessible-base-class"></a>Conversion vers une classe de base inaccessible
**Visual Studio 2017 version 15.3** génère une erreur quand vous essayez de convertir un type en une classe de base qui n’est pas accessible. Le compilateur génère désormais « erreur C2243 : 'cast de type' : la conversion de 'D *' en 'B *' existe, mais n’est pas accessible ». Le code suivant est incorrect et peut éventuellement provoquer un incident lors de l’exécution. Le compilateur génère désormais l’erreur C2243 quand il rencontre un code tel que le suivant :

```cpp
#include <memory> 
 
class B { }; 
class D : B { }; // C2243. should be public B { }; 
 
void f() 
{ 
   std::unique_ptr<B>(new D()); 
}
```
### <a name="default-arguments-are-not-allowed-on-out-of-line-definitions-of-member-functions"></a>Les arguments par défaut ne sont pas autorisés sur les définitions hors ligne des fonctions membres
Les arguments par défaut ne sont pas autorisés sur les définitions hors ligne des fonctions membres dans les classes de modèles Le compilateur émet un avertissement sous /permissive et une erreur matérielle sous /permissive-. 

Dans les versions précédentes de Visual Studio, le code incorrect suivant peut entraîner un incident lors de l’exécution. Visual Studio 2017 version 15.3 génère l’avertissement C5034 : 'A<T>::f' : une définition hors ligne d’un membre d’un modèle de classe ne peut pas avoir d’arguments par défaut :
```cpp
 
template <typename T> 
struct A { 
    T f(T t, bool b = false); 
}; 
 
template <typename T> 
T A<T>::f(T t, bool b = false) // C5034
{ 
... 
}
```
Pour corriger cette erreur, supprimez l’argument par défaut « = false ». 

### <a name="use-of-offsetof-with-compound-member-designator"></a>Utilisation d’offsetof avec désignateur de membre composé
Dans Visual Studio 2017 version 15.3, l’utilisation d’offsetof(T, m) où m est un « désignateur de membre composé » aboutit à un avertissement quand vous compilez avec l’option /Wall. Le code suivant est incorrect et peut éventuellement provoquer un incident lors de l’exécution. Visual Studio 2017 version 15.3 génère « l’avertissement C4841 : extension non standard utilisée : désignateur de membre composé dans offsetof » :

```cpp
  
struct A { 
int arr[10]; 
}; 
 
// warning C4841: non-standard extension used: compound member designator in offsetof 
constexpr auto off = offsetof(A, arr[2]);
```
Pour corriger le code, désactivez l’avertissement avec un pragma ou modifiez le code pour ne pas utiliser offsetof : 

```cpp
#pragma warning(push) 
#pragma warning(disable: 4841) 
constexpr auto off = offsetof(A, arr[2]); 
#pragma warning(pop) 
```

### <a name="using-offsetof-with-static-data-member-or-member-function"></a>Utilisation d’offsetof avec des données membres static ou une fonction membre
Dans Visual Studio 2017 version 15.3, l’utilisation d’offsetof(T, m) où m fait référence à des données membres static ou une fonction membre aboutit à une erreur. Le code suivant génère « erreur C4597 : comportement non défini : offsetof appliqué à la fonction membre « foo » » et « erreur C4597 : comportement non défini : offsetof appliqué à des données membres static 'bar' » :
```cpp
 
#include <cstddef> 
 
struct A { 
int foo() { return 10; } 
static constexpr int bar = 0; 
}; 
 
constexpr auto off = offsetof(A, foo); 
Constexpr auto off2 = offsetof(A, bar);
```
 
Ce code est incorrect et peut éventuellement provoquer un incident lors de l’exécution. Pour corriger cette erreur, modifiez le code pour ne plus appeler un comportement non défini. Il s’agit de code non portable qui n’est pas autorisé par la norme C++.

### <a name="declspec"></a> Nouvel avertissement sur les attributs declspec
Dans Visual Studio 2017 version 15.3, le compilateur n’ignore plus les attributs si __declspec(…) est appliqué avant une spécification de liaison 'C' externe. Auparavant, le compilateur ignorait l’attribut, ce qui pouvait avoir des implications lors de l’exécution. Quand l’option `/Wall /WX` est définie, le code suivant génère « avertissement C4768 : les attributs __declspec avant la spécification de liaison sont ignorés » :

```cpp
 
__declspec(noinline) extern "C" HRESULT __stdcall //C4768
```

Pour corriger l’avertissement, placez 'C' externe en premier :

```cpp
extern "C" __declspec(noinline) HRESULT __stdcall
```
Cet avertissement est désactivé par défaut (activé par défaut dans la version 15.5) et impacte uniquement le code compilé avec `/Wall /WX`.

### <a name="decltype-and-calls-to-deleted-destructors"></a>decltype et appels à des destructeurs supprimés
Dans les versions précédentes de Visual Studio, le compilateur ne détectait pas quand un appel à un destructeur supprimé se produisait dans le contexte de l’expression associée à « decltype ». Dans Visual Studio 2017 version 15.3, le code suivant génère « erreur C2280 : 'A<T>::~A(void)' : tentative de référencement d’une fonction supprimée » :

```cpp
template<typename T> 
struct A 
{ 
   ~A() = delete; 
}; 
 
template<typename T> 
auto f() -> A<T>; 
 
template<typename T> 
auto g(T) -> decltype((f<T>())); 
 
void h() 
{ 
   g(42); 
}
```
### <a name="uninitialized-const-variables"></a>Variables const non initialisées
La version Visual Studio 2017 RTW avait une régression dans laquelle le compilateur C++ n’émettait pas de diagnostic si une variable 'const' n’était pas initialisée. Cette régression a été corrigée dans Visual Studio 2017 version 15.3. Le code suivant génère désormais « avertissement C4132 : 'Value' : un objet const doit être initialisé » :

```cpp
const int Value; //C4132
```
Pour corriger cette erreur, attribuez une valeur à `Value`.

### <a name="empty-declarations"></a>Déclarations vides
**Visual Studio 2017 version 15.3** affiche désormais un avertissement en cas de déclarations vides pour tous les types (pas seulement pour les types intégrés). Le code suivant génère désormais un avertissement C4091 de niveau 2 pour les quatre déclarations :

```cpp
struct A {};
template <typename> struct B {};
enum C { c1, c2, c3 };
 
int;    // warning C4091 : '' : ignored on left of 'int' when no variable is declared
A;      // warning C4091 : '' : ignored on left of 'main::A' when no variable is declared
B<int>; // warning C4091 : '' : ignored on left of 'B<int>' when no variable is declared
C;      // warning C4091 : '' : ignored on left of 'C' when no variable is declared
```

Pour supprimer les avertissements, il vous suffit de commenter ou de supprimer les déclarations vides. Dans les cas où l’objet sans nom doit avoir un effet secondaire (par exemple, RAII), vous devez lui affecter un nom.
 
L’avertissement est exclu sous /Wv:18 et est activé par défaut sous le niveau d’avertissement W2.


### <a name="stdisconvertible-for-array-types"></a>std::is_convertible pour les types tableau
Les versions précédentes du compilateur ont donné des résultats incorrects avec [std::is_convertible](standard-library/is-convertible-class.md) pour les types tableau. Cela obligeait les auteurs de bibliothèques à particulariser le compilateur Visual C++ lors de l’utilisation du trait de type `std::is_convertible<…>`. Dans l’exemple suivant, les assertions statiques passent dans les versions antérieures de Visual Studio, mais échouent dans Visual Studio 2017 version 15.3 :

```cpp
#include <type_traits>
 
using Array = char[1];
 
static_assert(std::is_convertible<Array, Array>::value);
static_assert(std::is_convertible<const Array, const Array>::value, "");
static_assert(std::is_convertible<Array&, Array>::value, "");
static_assert(std::is_convertible<Array, Array&>::value, "");
```

Le calcul de **std::is_convertible<From, To>** s’effectue en vérifiant si une définition de fonction imaginaire est correcte :
```cpp 
   To test() { return std::declval<From>(); }
``` 

### <a name="private-destructors-and-stdisconstructible"></a>Les destructeurs privés et std::is_constructible
Les versions précédentes du compilateur ignoraient si un destructeur était privé lors de la détermination du résultat de [std::is_constructible](standard-library/is-constructible-class.md). Il en tient compte désormais. Dans l’exemple suivant, les assertions statiques passent dans les versions antérieures de Visual Studio, mais échouent dans Visual Studio 2017 version 15.3 :

```cpp
#include <type_traits>
 
class PrivateDtor {
   PrivateDtor(int) { }
private:
   ~PrivateDtor() { }
};
 
// This assertion used to succeed. It now correctly fails.
static_assert(std::is_constructible<PrivateDtor, int>::value);
```  

Les destructeurs privés entraînent la non-constructibilité d’un type. Le calcul de **std::is_constructible<T, Args...>** est effectué comme si la déclaration suivante était écrite :
```cpp 
   T obj(std::declval<Args>()…)
``` 
Cet appel implique un appel de destructeur.

### <a name="c2668-ambiguous-overload-resolution"></a>C2668 : Résolution de surcharge ambiguë
Parfois, les versions précédentes du compilateur ne parvenaient pas à détecter une ambiguïté lors de la découverte de plusieurs candidats par le biais simultanément des déclarations et des recherches dépendantes d’arguments. Cela pouvait conduire à choisir une surcharge incorrecte et entraîner un comportement inattendu au moment de l’exécution. Dans l’exemple suivant, Visual Studio 2017 version 15.3 déclenche correctement C2668, 'f' : appel ambigu à une fonction surchargée :

```cpp
namespace N {
   template<class T>
   void f(T&, T&);
 
   template<class T>
   void f();
}
 
template<class T>
void f(T&, T&);
 
struct S {};
void f()
{
   using N::f; 
 
   S s1, s2;
   f(s1, s2); // C2668
}
```
Pour corriger le code, supprimez l’instruction using N::f si vous souhaitez appeler :: f().

### <a name="c2660-local-function-declarations-and-argument-dependent-lookup"></a>C2660 : Déclarations de fonction locale et recherche dépendante d’argument
Les déclarations de fonction locale masquent la déclaration de fonction dans la portée englobante et désactivent la recherche dépendante d’argument.
Pourtant, les versions précédentes du compilateur Visual C++ effectuaient une recherche dépendante d’argument dans ce cas, conduisant éventuellement à choisir une surcharge incorrecte et entraînant un comportement inattendu au moment de l’exécution. En règle générale, l’erreur est due à une signature incorrecte de la déclaration de fonction locale. Dans l’exemple suivant, Visual Studio 2017 version 15.3 déclenche correctement C2660, 'f' : la fonction n’accepte pas 2 arguments :

```cpp
struct S {}; 
void f(S, int);
 
void g()
{
   void f(S); // C2660 'f': function does not take 2 arguments:
   // or void f(S, int);
   S s;
   f(s, 0);
}
```

Pour résoudre le problème, changez la signature **f(S)** ou supprimez-la.

### <a name="c5038-order-of-initialization-in-initializer-lists"></a>C5038 : Ordre d’initialisation dans les listes d’initialiseurs
Les membres de classe sont initialisés dans l’ordre suivant lequel ils sont déclarés, et non selon celui de leur apparition dans les listes d’initialiseurs. Les versions précédentes du compilateur n’avertissaient pas lorsque l’ordre de la liste d’initialiseurs était différent de celui des déclarations. Cela pouvait aboutir à un comportement d’exécution non défini si l’initialisation d’un membre dépendait d’un autre membre dans la liste déjà en cours d’initialisation. Dans l’exemple suivant, Visual Studio 2017 version 15.3 (avec /Wall) génère l’avertissement C5038 : le membre de données 'A::y' sera initialisé après le membre de données 'A::x' :

```cpp
struct A
{
    A(int a) : y(a), x(y) {} // Initialized in reverse, y reused
    int x;
    int y;
};

```
Pour résoudre le problème, réorganisez la liste d’initialiseurs afin d’avoir le même ordre que dans les déclarations. Un avertissement similaire est déclenché lorsqu’un ou les deux initialiseurs se réfèrent aux membres de classe de base.

Notez que l’avertissement est désactivé par défaut et affecte uniquement le code compilé avec /Wall.

## <a name="update_155"></a> Correctifs de bogues et autres changements du comportement dans Visual Studio 2017 version 15.5
### <a name="partial-ordering-change"></a>Changement de classement partiel

Le compilateur rejette maintenant le code suivant et génère le message d’erreur approprié :

```cpp

template<typename... T>
int f(T* ...)
{
    return 1;
}

template<typename T>
int f(const T&)
{
    return 2;
}

int main()
{
    int i = 0;
    f(&i);    // C2668
}
```
```output
t161.cpp
t161.cpp(16): error C2668: 'f': ambiguous call to overloaded function
t161.cpp(8): note: could be 'int f<int*>(const T &)'
        with
        [
            T=int*
        ]
t161.cpp(2): note: or       'int f<int>(int*)'
t161.cpp(16): note: while trying to match the argument list '(int*)'
``` 
Dans l’exemple ci-dessus, le problème provient de l’utilisation de fonctions de deux types différents (const/non-const et pack/non-pack). Pour éviter l’erreur du compilateur, utilisez des fonctions d’un même type. Le compilateur pourra ainsi classer les fonctions sans ambiguïté.

```cpp
template<typename... T>
int f(T* ...)
{
    return 1;
}

template<typename T>
int f(T&)
{
    return 2;
}

int main()
{
    int i = 0;
    f(&i);
}
```


### <a name="exception-handlers"></a>Gestionnaires d’exceptions
Les gestionnaires de référence au type tableau ou fonction ne sont plus mis en correspondance pour les objets exception. Le compilateur applique maintenant cette règle correctement et déclenche un avertissement de niveau 4. De plus, il ne met plus en correspondance un gestionnaire de `char*` ou `wchar_t*` avec un littéral de chaîne quand **/Zc:strictStrings** est utilisé.

```cpp
int main()
{
    try {
        throw "";
    }
    catch (int (&)[1]) {} // C4843 (This should always be dead code.)
    catch (void (&)()) {} // C4843 (This should always be dead code.)
    catch (char*) {} // This should not be a match under /Zc:strictStrings
}
```

```output
warning C4843: 'int (&)[1]': An exception handler of reference to array or function type is unreachable, use 'int*' instead
warning C4843: 'void (__cdecl &)(void)': An exception handler of reference to array or function type is unreachable, use 'void (__cdecl*)(void)' instead
```
Le code suivant permet d’éviter cette erreur :

```cpp
catch (int (*)[1]) {}
```

### <a name="tr1"></a>L’espace de noms std::tr1 est déprécié
L’espace de noms std::tr1 non standard est désormais marqué comme déprécié dans les deux modes C++14 et C++17. Dans Visual Studio 2017 version 15.5, le code suivant génère l’erreur C4996 :

```cpp
#include <functional>
#include <iostream>
using namespace std;

int main() {
    std::tr1::function<int (int, int)> f = std::plus<int>(); //C4996
    cout << f(3, 5) << std::endl;
    f = std::multiplies<int>();
    cout << f(3, 5) << std::endl;
}
```

```output
warning C4996: 'std::tr1': warning STL4002: The non-Standard std::tr1 namespace and TR1-only machinery are deprecated and will be REMOVED. You can define _SILENCE_TR1_NAMESPACE_DEPRECATION_WARNING to acknowledge that you have received this warning.
```

Pour corriger cette erreur, supprimez la référence à l’espace de noms tr1 :

```cpp
#include <functional>
#include <iostream>
using namespace std;

int main() {
    std::function<int (int, int)> f = std::plus<int>();
    cout << f(3, 5) << std::endl;
    f = std::multiplies<int>();
    cout << f(3, 5) << std::endl;
}
```


### <a name="annex_d"></a>Les fonctionnalités de la bibliothèque standard répertoriées dans l’annexe D sont marquées comme dépréciées.
Quand le commutateur de compilateur en mode /std:c++17 est défini, presque toutes les fonctionnalités de la bibliothèque standard répertoriées dans l’annexe D sont marquées comme dépréciées.

Dans Visual Studio 2017 version 15.5, le code suivant génère l’erreur C4996 :

```cpp
#include <iterator>

class MyIter : public std::iterator<std::random_access_iterator_tag, int> {
public:
    // ... other members ...
};

#include <type_traits>

static_assert(std::is_same<MyIter::pointer, int*>::value, "BOOM");
```

```output
warning C4996: 'std::iterator<std::random_access_iterator_tag,int,ptrdiff_t,_Ty*,_Ty &>::pointer': warning STL4015: The std::iterator class template (used as a base class to provide typedefs) is deprecated in C++17. (The <iterator> header is NOT deprecated.) The C++ Standard has never required user-defined iterators to derive from std::iterator. To fix this warning, stop deriving from std::iterator and start providing publicly accessible typedefs named iterator_category, value_type, difference_type, pointer, and reference. Note that value_type is required to be non-const, even for constant iterators. You can define _SILENCE_CXX17_ITERATOR_BASE_CLASS_DEPRECATION_WARNING or _SILENCE_ALL_CXX17_DEPRECATION_WARNINGS to acknowledge that you have received this warning.
```

Pour corriger cette erreur, suivez les instructions données dans le texte d’avertissement, comme illustré dans le code suivant :

```cpp
#include <iterator>

class MyIter {
public:
    typedef std::random_access_iterator_tag iterator_category;
    typedef int value_type;
    typedef ptrdiff_t difference_type;
    typedef int* pointer;
    typedef int& reference;

    // ... other members ...
};

#include <type_traits>

static_assert(std::is_same<MyIter::pointer, int*>::value, "BOOM");
```

### <a name="unreferenced-local-variables"></a>Variables locales non référencées
Dans Visual Studio 15.5, l’avertissement C4189 est affiché dans plus de cas, comme indiqué dans le code suivant :

```cpp
void f() {
    char s[2] = {0}; // C4189. Either use the variable or remove it.
}

```

```output
warning C4189: 's': local variable is initialized but not referenced
```

Pour corriger cette erreur, supprimez la variable inutilisée.

### <a name="single-line-comments"></a>Commentaires sur une seule ligne 
Dans Visual Studio 2017 version 15.5, les avertissements C4001 et C4179 ne sont plus générés par le compilateur C. Auparavant, ils étaient uniquement générés quand le commutateur du compilateur **/Za** était défini.  Ces avertissements ne sont plus utiles, car les commentaires sur une seule ligne sont intégrés à la norme C depuis la version C99. 

```cpp
/* C only */
#pragma warning(disable:4001) //C4619
#pragma warning(disable:4179)
// single line comment
//* single line comment */
```

```output
warning C4619: #pragma warning: there is no warning number '4001'   
```

Si le code n’a pas besoin d’offrir une compatibilité descendante, vous pouvez éviter la génération des avertissements en supprimant C4001 et C4179. Si le code doit offrir une compatibilité descendante, supprimez uniquement C4619.

```cpp
/* C only */

#pragma warning(disable:4619)
#pragma warning(disable:4001)
#pragma warning(disable:4179)

// single line comment
/* single line comment */
```


### <a name="declspec-attributes-with-extern-c-linkage"></a>Attributs __declspec avec une liaison extern "C" 

Dans les versions antérieures de Visual Studio, le compilateur ignorait les attributs `__declspec(…)` quand `__declspec(…)` était appliqué avant la spécification de la liaison `extern "C"`. Ce comportement provoquait la génération de code de façon inattendue pour l’utilisateur, avec un impact possible sur l’exécution. L’avertissement, ajouté dans Visual Studio 2017 version 15.3, était désactivé par défaut. Dans Visual Studio 2017 version 15.5, l’avertissement est activé par défaut.

```cpp
__declspec(noinline) extern "C" HRESULT __stdcall //C4768
```

```output
warning C4768: __declspec attributes before linkage specification are ignored
```

Pour corriger cette erreur, ajoutez la spécification de liaison avant l’attribut __declspec :

```cpp
extern "C" __declspec(noinline) HRESULT __stdcall
```
Le nouvel avertissement C4768 ci-dessous est généré sur certains en-têtes Windows SDK fournis avec Visual Studio 2017 version 15.3 ou antérieure (par exemple, dans la version 10.0.15063.0, appelée RS2 SDK). Les versions ultérieures des en-têtes Windows SDK (en particulier, ShlObj.h et ShlObj_core.h) ont été corrigées pour ne plus générer cet avertissement. Si vous voyez cet avertissement généré par les en-têtes Windows SDK, effectuez les actions suivantes :
1)  Installez le dernier Windows SDK, fourni avec Visual Studio 2017 version 15.5.
2)  Désactivez l’avertissement pour l’élément #include de l’instruction d’en-tête Windows SDK :
```cpp
#pragma warning (push) 
#pragma warning(disable:4768)
#include <shlobj.h>
#pragma warning (pop) 
```

### <a name="extern_linkage"></a>Liaison extern constexpr 

Dans les versions antérieures de Visual Studio, le compilateur retournait toujours une liaison interne pour la variable `constexpr`, même quand la variable était marquée comme `extern`. Dans Visual Studio 2017 version 15.5, un nouveau commutateur de compilateur (/Zc:externConstexpr) active le comportement correct de conformité aux normes. Cela deviendra le comportement par défaut.

```cpp
extern constexpr int x = 10; 
```

```output
error LNK2005: "int const x" already defined
```

Si un fichier d’en-tête contient une variable déclarée `extern constexpr`, la variable doit être marquée comme `__declspec(selectany)` pour permettre la combinaison correcte de ses déclarations dupliquées :

```cpp
extern constexpr __declspec(selectany) int x = 10;
```

### <a name="typeid-cant-be-used-on-incomplete-class-type"></a>typeid ne peut pas être utilisé sur un type classe incomplète.
Dans les versions antérieures de Visual Studio, le compilateur autorisait à tort le code suivant, ce qui pouvait produire des informations de type incorrectes. Dans Visual Studio 2017 version 15.5, le compilateur génère une erreur :

```cpp
#include <typeinfo>

struct S;

void f() { typeid(S); } //C2027 in 15.5
```

```output
error C2027: use of undefined type 'S'
```


### <a name="stdisconvertible-target-type"></a>Type de cible std::is_convertible

`std::is_convertible` exige que le type de cible soit un type de retour valide. Dans les versions antérieures de Visual Studio, le compilateur autorisait à tort les types abstraits, ce qui pouvait entraîner une résolution de surcharge incorrecte et un comportement inattendu au moment de l’exécution.  Le code suivant génère désormais correctement l’erreur C2338 :

```cpp
#include <type_traits>
 
struct B { virtual ~B() = 0; };
struct D : public B { virtual ~D(); };
 
static_assert(std::is_convertible<D, B>::value, "fail"); // C2338 in 15.5

```
Pour éviter cette erreur, quand vous utilisez `is_convertible`, vous devez comparer les types de pointeur, car une comparaison de type non pointeur peut échouer si un type est abstrait :

```cpp
#include <type_traits>
 
struct B { virtual ~B() = 0; };
struct D : public B { virtual ~D(); };
 
static_assert(std::is_convertible<D *, B *>::value, "fail");

```
### <a name="noexcept_removal"></a> Suppression des spécifications d’exceptions dynamiques et noexcept
Dans C++17, `throw()` est un alias de `noexcept`, les exceptions `throw(<type list>)` et `throw(…)` sont supprimées, et certains types peuvent inclure `noexcept`. Ces changements entraînent parfois des problèmes de compatibilité avec le code conforme à C++14 ou une version antérieure. Vous pouvez utiliser le commutateur **/Zc:noexceptTypes-** pour rétablir la version C++14 de `noexcept` si vous utilisez généralement le mode C++17. Cela vous permet de mettre à jour votre code source pour le rendre conforme à C++17 sans pour autant avoir à réécrire tout votre code `throw()`.

Avec le nouvel avertissement C5043, le compilateur diagnostique également maintenant davantage de spécifications d’exceptions incompatibles dans les déclarations en mode C++17 ou avec **/permissive-**.

Le code suivant génère les avertissements C5043 et C5040 dans Visual Studio 2017 version 15.5 quand le commutateur /std:c++17 est défini :

```cpp
void f() throw(); // equivalent to void f() noexcept;
void f() {} // warning C5043
void g() throw(); // warning C5040

struct A {
    virtual void f() throw();
};

struct B : A {
    virtual void f() { } // error C2694
};
```
Pour éviter ces erreurs quand vous utilisez **/std:c++17**, ajoutez le commutateur **/Zc:noexceptTypes-** dans la ligne de commande ou bien mettez à jour votre code pour utiliser `noexcept`, comme illustré dans l’exemple suivant :

```cpp
void f() noexcept;
void f() noexcept { }
void g() noexcept(false);

struct A {
    virtual void f() noexcept;
};

struct B : A {
    virtual void f() noexcept { }
};
```
### <a name="inline-variables"></a>Variables inline
Les membres de données static constexpr sont désormais implicitement inline, ce qui signifie que leur déclaration dans une classe correspond maintenant à leur définition. L’utilisation d’une définition hors ligne pour un membre de données static constexpr est redondante et est donc maintenant dépréciée. Dans Visual Studio 2017 version 15.5, quand le commutateur /std:c++17 est défini, le code suivant génère désormais l’avertissement C5041 *'size' : la définition hors ligne du membre de données statique constexpr n’est pas nécessaire et est dépréciée en C++17* :

```cpp
struct X {
    static constexpr int size = 3;
};
const int X::size; // C5041
```
### <a name="extern-c-declspec-warning-c4768-now-on-by-default"></a>L’avertissement C4768 extern "C" __declspec(...) est maintenant activé par défaut
L’avertissement, ajouté dans Visual Studio 2017 version 15.3, était désactivé par défaut. Dans Visual Studio 2017 version 15.5, il est activé par défaut. Pour plus d’informations, consultez [Nouvel avertissement sur les attributs declspec](#declspec).

### <a name="defaulted-functions-and-declspecnothrow"></a>Fonctions par défaut et __declspec(nothrow)
Auparavant, le compilateur autorisait la déclaration de fonctions par défaut à l’aide de `__declspec(nothrow)` quand les fonctions de base/membres correspondantes autorisaient les exceptions. Ce comportement non conforme à la norme C++ peut entraîner un comportement inattendu au moment de l’exécution. La norme exige que ces fonctions soient marquées comme supprimées en cas de non-correspondance d’une spécification d’exception.  En mode /std:c++17, le code suivant déclenche l’avertissement C2280 *Tentative de référencement d’une fonction supprimée. La fonction a été supprimée implicitement, car la spécification d’exception explicite est incompatible avec la spécification de déclaration implicite.* :


```cpp
struct A {
    A& operator=(const A& other) { // No exception specification; this function may throw.
        ...
    }
};

struct B : public A {
    __declspec(nothrow) B& operator=(const B& other) = default;
};

int main()
{
    B b1, b2;
    b2 = b1; // error C2280
}
```

Pour corriger ce code, supprimez __declspec (nothrow) dans la fonction par défaut, ou supprimez `= default` et ajoutez une définition de la fonction et la gestion d’exceptions nécessaire :

```cpp
struct A {
    A& operator=(const A& other) {
        ...
    }
};

struct B : public A {
    B& operator=(const B& other) = default;
};

int main()
{
    B b1, b2;
    b2 = b1;
}
```
### <a name="noexcept-and-partial-specializations"></a>noexcept et spécialisations partielles
Quand noexcept est utilisé dans le système de type, les spécialisations partielles pour la correspondance de certains types « pouvant être appelés » peuvent ne pas réussir à compiler ou choisir le modèle principal en raison d’une spécialisation partielle manquante pour les pointeurs de fonctions noexcept.

Dans ce cas de figure, vous devrez peut-être ajouter d’autres spécialisations partielles pour gérer les pointeurs de fonctions noexcept ainsi que les pointeurs noexcept de fonctions membres. Ces surcharges sont uniquement autorisées en mode /std:c++17. Si vous devez garantir la compatibilité descendante avec C++14 et que votre code est destiné à être utilisé par d’autres personnes, vous devez protéger ces nouvelles surcharges à l’intérieur de directives `#ifdef`. Si votre code fait partie d’un module autonome, au lieu d’utiliser des protections `#ifdef`, vous pouvez simplement compiler le code avec le commutateur **/Zc:noexceptTypes-**. 

Le code suivant se compile correctement en mode /std:c++14, mais échoue en mode /std:c++17 avec l’erreur C2027 : *utilisation du type non défini 'A<T>'* :

```cpp
template <typename T> struct A;

template <>
struct A<void(*)()>
{
    static const bool value = true;
};

template <typename T>
bool g(T t)
{
    return A<T>::value;
}

void f() noexcept {}

int main()
{
    return g(&f) ? 0 : 1; // C2027
}
```

Le code suivant se compile correctement en mode /std:c++17, car le compilateur choisit la nouvelle spécialisation partielle `A<void (*)() noexcept>` :

```cpp
template <typename T> struct A;

template <>
struct A<void(*)()>
{
    static const bool value = true;
};

template <>
struct A<void(*)() noexcept>
{
    static const bool value = true;
};

template <typename T>
bool g(T t)
{
    return A<T>::value;
}

void f() noexcept {}

int main()
{
    return g(&f) ? 0 : 1; // OK
}
```

## <a name="see-also"></a>Voir aussi  
[Conformité du langage Visual C++](visual-cpp-language-conformance.md)  
