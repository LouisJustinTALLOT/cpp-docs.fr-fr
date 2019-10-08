---
title: Améliorations de la conformité de C++
ms.date: 10/04/2019
description: Microsoft C++ dans Visual Studio arrive progressivement à une conformité totale avec la norme du langage C ++20.
ms.technology: cpp-language
author: mikeblome
ms.author: mblome
ms.openlocfilehash: d313a9a1f9f2bc1aa091935658ca1214f929c048
ms.sourcegitcommit: c51b2c665849479fa995bc3323a22ebe79d9d7ce
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/07/2019
ms.locfileid: "71998883"
---
# <a name="c-conformance-improvements-in-visual-studio"></a>Améliorations de la conformité de C++ dans Visual Studio

Microsoft C++ apporte des améliorations de conformité et des correctifs de bogues avec chaque version. Cet article répertorie les améliorations apportées par version majeure, puis par version. Il répertorie également les principaux correctifs de bogues par version. Pour aller directement aux modifications apportées à une version spécifique, utilisez la liste **Dans cet article**.

::: moniker range="vs-2019"

## <a name="improvements_160"></a>Améliorations de la conformité dans Visual Studio 2019 RTW (version 16,0)

Visual Studio 2019 RTW contient les améliorations de conformité, les correctifs de bogues et les modifications de comportement C++ suivants dans le compilateur Microsoft (MSVC)

**Remarque :** Les fonctionnalités C++20 seront disponibles en mode `/std:c++latest` tant que l’implémentation de C++20 n’est pas terminée pour le compilateur et IntelliSense. Une fois qu’elle sera terminée, le mode de compilateur `/std:c++20` sera introduit.

### <a name="improved-modules-support-for-templates-and-error-detection"></a>Amélioration de la prise en charge des modules pour les modèles et la détection d’erreur

Les modules sont désormais officiellement dans la norme C++20. Une meilleure prise en charge a été ajoutée dans Visual Studio 2017 version 15.9. Pour plus d’informations, consultez [Better template support and error detection in C++ Modules with MSVC 2017 version 15.9](https://devblogs.microsoft.com/cppblog/better-template-support-and-error-detection-in-c-modules-with-msvc-2017-version-15-9/).

### <a name="modified-specification-of-aggregate-type"></a>Changement de spécification du type d’agrégat

La spécification d’un type d’agrégat a changé dans C++20 (consultez [Prohibit aggregates with user-declared constructors](https://wg21.link/p1008r1)). Dans Visual Studio 2019, sous `/std:c++latest`, une classe avec un constructeur déclaré par l’utilisateur (par exemple un constructeur déclaré `= default` ou `= delete`) n’est pas un agrégat. Avant, seuls les constructeurs fournis par l’utilisateur empêchaient une classe d’être un agrégat. Ce changement ajoute des restrictions supplémentaires sur la façon dont ces types peuvent être initialisés.

Le code suivant se compile sans erreur dans Visual Studio 2017, mais génère des erreurs C2280 et C2440 dans Visual Studio 2019 sous `/std:c++latest` :

```cpp
struct A
{
    A() = delete; // user-declared ctor
};

struct B
{
    B() = default; // user-declared ctor
    int i = 0;
};

A a{}; // ill-formed in C++20, previously well-formed
B b = { 1 }; // ill-formed in C++20, previously well-formed
```

### <a name="partial-support-for-operator-"></a>Prise en charge partielle de `operator <=>`

[P0515R3](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0515r3.pdf)C++20 introduit l’opérateur de comparaison trilatérale `<=>`, également appelé « opérateur vaisseau spatial ». Visual Studio 2019 en mode `/std:c++latest` introduit la prise en charge partielle de l’opérateur en générant des erreurs pour la syntaxe qui est maintenant interdite. Par exemple, le code suivant se compile sans erreur dans Visual Studio 2017, mais génère plusieurs erreurs dans Visual Studio 2019 sous `/std:c++latest` :

```cpp
struct S
{
    bool operator<=(const S&) const { return true; }
};

template <bool (S::*)(const S&) const>
struct U { };

int main(int argc, char** argv)
{
    U<&S::operator<=> u; // In Visual Studio 2019 raises C2039, 2065, 2146.
}
```

Pour éviter les erreurs, insérez un espace dans la ligne incriminée avant le crochet angulaire fermant : `U<&S::operator<= > u;`.

### <a name="references-to-types-with-mismatched-cv-qualifiers"></a>Références aux types avec des qualificateurs cv non correspondants

Avant, MSVC autorisait la liaison directe d’une référence d’un type avec des qualificateurs cv non correspondants sous le niveau supérieur. Cette liaison pouvait permettre la modification des données const supposément référencées par la référence. À présent, le compilateur crée une table temporaire, comme requis par la norme. Dans Visual Studio 2017, le code suivant se compile sans avertissement. Dans Visual Studio 2019, le compilateur génère un *avertissement C4172 : \<func:#1 "?PData@X@@QBEABQBXXZ"> retournant l’adresse d’une variable locale ou d’un fichier temporaire*.

```cpp
struct X
{
    const void* const& PData() const
    {
        return _pv;
    }

    void* _pv;
};

int main()
{
    X x;
    auto p = x.PData(); // C4172
}
```

### <a name="reinterpret_cast-from-an-overloaded-function"></a>`reinterpret_cast` d’une fonction surchargée

L’argument pour `reinterpret_cast` ne fait pas partie des contextes dans lesquels l’adresse d’une fonction surchargée est autorisée. Le code suivant se compile sans erreur dans Visual Studio 2017, alors que dans Visual Studio 2019 il déclenche *C2440 : Impossible de convertir 'overloaded-function' en 'fp'*  :

```cpp
int f(int) { return 1; }
int f(float) { return .1f; }
using fp = int(*)(int);

int main()
{
    fp r = reinterpret_cast<fp>(&f);
}
```

Pour éviter cette erreur, utilisez un cast autorisé pour ce scénario :

```cpp
int f(int);
int f(float);
using fp = int(*)(int);

int main()
{
    fp r = static_cast<fp>(&f); // or just &f;
}
```

### <a name="lambda-closures"></a>Fermetures lambda

Dans C++14, les types de fermeture d’expression lambda ne sont pas littéraux. La conséquence principale de cette règle est qu’une expression lambda ne peut pas être assignée à une variable **constexpr** . Le code suivant compile sans erreur dans Visual Studio 2017, alors que dans Visual Studio 2019 il déclenche *C2127 : 'l' : initialisation illégale de l’entité 'constexpr' avec une expression non constante* :

```cpp
int main()
{
    constexpr auto l = [] {}; // C2127 in VS2019
}
```

Pour éviter cette erreur, supprimez le qualificateur **constexpr** ou modifiez le mode de conformité en `/std:c++17`.

### <a name="stdcreate_directory-failure-codes"></a>Codes d’échec `std::create_directory`

[P1164](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2019/p1164r1.pdf) implémenté depuis C++20 sans condition. Cela change `std::create_directory` pour vérifier si la cible était déjà un répertoire en échec. Avant, toutes les erreurs de type ERROR_ALREADY_EXISTS étaient converties en codes success-but-directory-not-created.

### `operator<<(std::ostream, nullptr_t)`

Conformément à [LWG 2221](https://cplusplus.github.io/LWG/issue2221), ajout de `operator<<(std::ostream, nullptr_t)` pour écrire nullptrs dans les flux.

### <a name="additional-parallel-algorithms"></a>Algorithmes parallèles supplémentaires

Nouvelles versions parallèles de `is_sorted`, `is_sorted_until`, `is_partitioned`, `set_difference`, `set_intersection`, `is_heap` et `is_heap_until`.

### <a name="atomic-initialization"></a>Initialisation atomique

Le [P0883 "Fixing atomic initialization"](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0883r1.pdf) change `std::atomic` pour l’initialiser avec la valeur du T contenu plutôt que de l’initialiser avec la valeur par défaut. Le correctif est activé lorsque vous utilisez Clang/LLVM avec la bibliothèque standard de Microsoft. Elle est actuellement désactivée pour C++ le compilateur Microsoft, en guise de solution de contournement pour un bogue dans le traitement **constexpr** .

### <a name="remove_cvref-and-remove_cvref_t"></a>`remove_cvref` et `remove_cvref_t`

Caractéristiques de type `remove_cvref` et `remove_cvref_t` implémentées selon le [P0550](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0550r2.pdf). Cela supprime reference-ness et cv-qualification d’un type sans dégrader les fonctions et les tableaux en pointeurs (contrairement à `std::decay` et `std::decay_t`).

### <a name="feature-test-macros"></a>Macros Feature-test

[P0941R2 - macros de test de fonctionnalité](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0941r2.html) est terminé, avec la prise en charge de `__has_cpp_attribute`. Les macros de test de fonctionnalité sont prises en charge dans tous les modes standard.

### <a name="prohibit-aggregates-with-user-declared-constructors"></a>Interdire les agrégats avec les constructeurs déclarés par l’utilisateur

[C++20 P1008R1 - prohibiting aggregates with user-declared constructors](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p1008r1.pdf) est terminé.

## <a name="improvements_161"></a>Améliorations de la conformité dans 16,1

### <a name="char8_t"></a>char8_t

[P0482r6](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0482r6.html). C++20 ajoute un nouveau type de caractère qui est utilisé pour représenter les unités de code UTF-8. Les littéraux de chaîne `u8` dans C++20 ont le type `const char8_t[N]` au lieu de `const char[N]`, ce qui était le cas auparavant. Des changements similaires ont été proposés pour la norme C dans [N2231](http://www.open-std.org/jtc1/sc22/wg14/www/docs/n2231.htm). Vous trouverez des suggestions de correction de la compatibilité descendante de `char8_t` dans [P1423r0](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2019/p1423r0.html). Le compilateur Microsoft C++ ajoute une prise en charge de `char8_t` dans Visual Studio 2019 version 16.1 quand vous spécifiez l’option de compilateur **/Zc:char8_t**. À l’avenir, il sera pris en charge avec [/std:c++latest](../build/reference/std-specify-language-standard-version.md), qui peut revenir au comportement C++17 via **/Zc:char8_t-** . Le compilateur EDG qui alimente IntelliSense ne le prend pas encore en charge, donc vous verrez des erreurs parasites propres à IntelliSense qui n’impactent pas la compilation effective.

#### <a name="example"></a>Exemple

```cpp
const char* s = u8"Hello"; // C++17
const char8_t* s = u8"Hello"; // C++20
```

### <a name="stdtype_identity-metafunction-and-stdidentity-function-object"></a>Métafonction std::type_identity et objet de fonction std::identity

[P0887R1 type_identity](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0887r1.pdf). L’extension de modèle de classe `std::identity` dépréciée a été supprimée et remplacée par la métafonction `std::type_identity` et l’objet de fonction `std::identity` C++20. Les deux sont disponibles uniquement sous [/std:c++latest](../build/reference/std-specify-language-standard-version.md).

L’exemple suivant génère l’avertissement de dépréciation C4996 pour `std::identity` (défini dans \<type_traits>) dans Visual Studio 2017 :

```cpp
#include <type_traits>

using T = std::identity<int>::type;
T x, y = std::identity<T>{}(x);
int i = 42;
long j = std::identity<long>{}(i);
```

L’exemple suivant montre comment utiliser le nouveau `std::identity` (défini dans \<functional>) avec le nouveau `std::type_identity` :

```cpp
#include <type_traits>
#include <functional>

using T = std::type_identity<int>::type;
T x, y = std::identity{}(x);
int i = 42;
long j = static_cast<long>(i);
```

### <a name="syntax-checks-for-generic-lambdas"></a>Vérifications syntaxiques pour les expressions lambda génériques

Le nouveau processeur lambda autorise des vérifications syntaxiques du mode de conformité dans les expressions lambda génériques, sous [/std:c++latest](../build/reference/std-specify-language-standard-version.md) ou sous n’importe quel autre mode de langage avec **/experimental:newLambdaProcessor**.

Dans Visual Studio 2017, ce code se compile sans avertissement, alors que dans Visual Studio 2019 il génère l’erreur *Erreur de syntaxe C2760 : jeton inattendu '\<id-expr>', 'id-expression' attendu* :

```cpp
void f() {
    auto a = [](auto arg) {
        decltype(arg)::Type t;
    };
}
```

L’exemple suivant montre la syntaxe correcte, maintenant appliquée par le compilateur :

```cpp
void f() {
    auto a = [](auto arg) {
        typename decltype(arg)::Type t;
    };
}
```

### <a name="argument-dependent-lookup-for-function-calls"></a>Recherche dépendante des arguments pour les appels de fonction

[P0846R0](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0846r0.html) (C++20) Possibilité accrue de trouver des modèles de fonction par le biais d’une recherche dépendante des arguments pour les expressions d’appel de fonction avec des arguments de modèle explicites. Nécessite **/std:c++latest**.

### <a name="designated-initialization"></a>Initialisation désignée

[P0329R4](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0329r4.pdf) (C++20) L’initialisation désignée autorise la sélection de membres spécifiques dans l’initialisation d’agrégats en utilisant la syntaxe `Type t { .member = expr }`. Nécessite **/std:c++latest**.

### <a name="new-and-updated-standard-library-functions-c20"></a>Fonctions de bibliothèque standard nouvelles et mises à jour (C++20)

- `starts_with()` et `ends_with()` pour `basic_string` et `basic_string_view`.
- `contains()` pour les conteneurs associatifs.
- `remove()`, `remove_if()` et `unique()` pour `list` et `forward_list` retournent maintenant `size_type`.
- Ajout de `shift_left()` et `shift_right()` à \<algorithm>.


## <a name="improvements_162"></a>Améliorations de la conformité dans 16,2

### <a name="noexcept-constexpr-functions"></a>noexcept constexpr, fonctions

Les fonctions Constexpr ne sont plus considérées comme **noexcept** par défaut lorsqu’elles sont utilisées dans une expression constante. Ce changement de comportement provient de la résolution de [CWG 1351](http://www.open-std.org/jtc1/sc22/wg21/docs/cwg_defects.html#1351) et est activé dans [/permissive-](../build/reference/permissive-standards-conformance.md). L’exemple suivant compile dans Visual Studio 2019 version 16,1 et les versions antérieures, mais produit C2338 dans Visual Studio 2019 version 16,2 :

```cpp
constexpr int f() { return 0; }

int main() {
    static_assert(noexcept(f()), "f should be noexcept"); // C2338 in 16.2
}
```

Pour corriger l’erreur, ajoutez l’expression **noexcept** à la déclaration de fonction :

```cpp
constexpr int f() noexcept { return 0; }

int main() {
    static_assert(noexcept(f()), "f should be noexcept");
}
```

### <a name="binary-expressions-with-different-enum-types"></a>Expressions binaires avec différents types ENUM

La possibilité d’appliquer les conversions arithmétiques habituelles sur les opérandes dont l’un est de type énumération et l’autre est d’un type d’énumération différent ou un type à virgule flottante est déconseillé en C++ 20 ([P1120R0](https://wg21.link/p1120r0)). Dans Visual Studio 2019 version 16,2 et versions ultérieures, le code suivant génère un avertissement de niveau 4 lorsque l’option de compilateur [/std : c + + la plus récente](../build/reference/std-specify-language-standard-version.md) est activée :

```cpp
enum E1 { a };
enum E2 { b };
int main() {
    int i = a | b; // warning C5054: operator '|': deprecated between enumerations of different types
}
```

Pour éviter cet avertissement, utilisez [static_cast](../cpp/static-cast-operator.md) pour convertir le second opérande :

```cpp
enum E1 { a };
enum E2 { b };
int main() {
  int i = a | static_cast<int>(b);
}
```

### <a name="binary-expressions-with-enumeration-and-floating-point-types"></a>Expressions binaires avec énumération et types à virgule flottante

La possibilité d’appliquer les conversions arithmétiques habituelles sur les opérandes dont l’un est de type énumération et l’autre est d’un type d’énumération différent ou un type à virgule flottante est déconseillé en C++ 20 ([P1120R0](https://wg21.link/p1120r0)). En d’autres termes, l’utilisation d’une opération binaire entre une énumération et un type à virgule flottante est désormais un avertissement lorsque l’option de compilateur [/std : c + + la plus récente](../build/reference/std-specify-language-standard-version.md) est activée :

```cpp
enum E1 { a };
int main() {
  double i = a * 1.1;
}
```

Pour éviter cet avertissement, utilisez [static_cast](../cpp/static-cast-operator.md) pour convertir le second opérande :

```cpp
enum E1 { a };
int main() {
   double i = static_cast<int>(a) * 1.1;
}
```

### <a name="equality-and-relational-comparisons-of-arrays"></a>Comparaisons d’égalité et relationnelles de tableaux

Les comparaisons d’égalité et relationnelles entre deux opérandes de type tableau sont dépréciées en C++ 20 ([P1120R0](https://wg21.link/p1120r0)). En d’autres termes, une opération de comparaison entre deux tableaux (indépendamment du rang et des similarités d’extensions) est désormais un avertissement. À compter de Visual Studio 2019 version 16,2, le code suivant génère *C5056 : Operator' = = ' : déconseillé pour les types tableau* lorsque l’option de compilateur [/std : c + + la plus récente](../build/reference/std-specify-language-standard-version.md) est activée :

```cpp
int main() {
    int a[] = { 1, 2, 3 };
    int b[] = { 1, 2, 3 };
    if (a == b) { return 1; }
}
```

Pour éviter l’avertissement, vous pouvez comparer les adresses des premiers éléments :

```cpp
int main() {
    int a[] = { 1, 2, 3 };
    int b[] = { 1, 2, 3 };
    if (&a[0] == &b[0]) { return 1; }
}
```

Pour déterminer si le contenu de deux tableaux est égal, utilisez la fonction [std :: EQUAL](../standard-library/algorithm-functions.md#equal) :

```cpp
std::equal(std::begin(a), std::end(a), std::begin(b), std::end(b));
```

### <a name="effect-of-defining-spaceship-operator-on--and-"></a>Effet de la définition de l’opérateur d’espacement sur = = et ! =

Une définition de l’opérateur d’espacement ( **<=>** ) seul ne réécrit plus les expressions qui impliquent **==** ou **! =** , sauf si l’opérateur d’espacement est marqué comme `= default` ([P1185R2](https://wg21.link/p1185r2)). L’exemple suivant compile dans Visual Studio 2019 RTW et la version 16,1, mais produit C2678 dans Visual Studio 2019 version 16,2 :

```cpp
#include <compare>

struct S {
  int a;
  auto operator<=>(const S& rhs) const {
    return a <=> rhs.a;
  }
};
bool eq(const S& lhs, const S& rhs) {
  return lhs == rhs;
}
bool neq(const S& lhs, const S& rhs) {
    return lhs != rhs;
}
```

Pour éviter cette erreur, définissez l’opérateur = = ou déclarez-le comme valeur par défaut :

```cpp
#include <compare>

struct S {
  int a;
  auto operator<=>(const S& rhs) const {
    return a <=> rhs.a;
  }
  bool operator==(const S&) const = default;
};
bool eq(const S& lhs, const S& rhs) {
  return lhs == rhs;
}
bool neq(const S& lhs, const S& rhs) {
    return lhs != rhs;
}
```

### <a name="standard-library-improvements"></a>Améliorations de la bibliothèque standard

- \<charconv > `to_chars()` avec une précision fixe/scientifique. (La précision générale est actuellement planifiée pour 16,4.)
- [P0020R6](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0020r6.html): Atomic @ no__t-1float >, atomique @ no__t-2Double >, Atomic @ no__t-3long double >
- [P0463R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0463r1.html): endian
- [P0482R6](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0482r6.html): Prise en charge de la bibliothèque pour char8_t
- [P0600R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0600r1.pdf): [\[nodiscard]] pour la bibliothèque STL, partie 1
- [P0653R2](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0653r2.html): to_address ()
- [P0754R2](http://open-std.org/JTC1/SC22/WG21/docs/papers/2018/p0754r2.pdf): \<version >
- [P0771R1](http://open-std.org/JTC1/SC22/WG21/docs/papers/2018/p0771r1.pdf): Noexcept pour le constructeur de déplacement de std :: function

## <a name="improvements_163"></a>Améliorations de la conformité dans Visual Studio 2019 version 16,3

### <a name="stream-extraction-operators-for-char-removed"></a>Opérateurs d’extraction de flux pour char * supprimés

Les opérateurs d’extraction de flux de pointeur vers des caractères ont été supprimés et remplacés par les opérateurs d’extraction pour les tableaux de caractères (par [P0487R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0487r1.html)). WG21 considère que les surcharges supprimées sont risquées. Dans [/std : c + + mode le plus récent](../build/reference/std-specify-language-standard-version.md) , l’exemple suivant génère désormais *C2679 : binary' > > ' : aucun opérateur trouvé qui accepte un opérande de partie droite de type’Char @ no__t-2 ' (ou il n’existe aucune conversion acceptable)* :

```cpp
   char x[42];
   char* p = x;
   std::cin >> std::setw(42);
   std::cin >> p;
```

Pour éviter cette erreur, utilisez l’opérateur d’extraction avec une variable Char [] :

```cpp
char x[42];
std::cin >> x;
```

### <a name="new-keywords-requires-and-concept"></a>Nouveaux mots clés **requis** et **concept**

Les nouveaux mots clés **Requires** and **concept** ont été ajoutés C++ au compilateur Microsoft. Si vous essayez d’utiliser l’un ou l’autre comme identificateur dans [/std : c + + mode le plus récent](../build/reference/std-specify-language-standard-version.md) , le compilateur déclenche l' *erreur C2059 : Syntax*.

### <a name="constructors-as-type-names-disallowed"></a>Constructeurs en tant que noms de types interdits

Les noms de constructeurs ne sont plus considérés comme des noms de classe injectés lorsqu’ils apparaissent dans un nom qualifié après un alias d’une spécialisation de modèle de classe. Cela permettait précédemment d’utiliser des constructeurs comme nom de type pour déclarer d’autres entités. L’exemple suivant génère à présent *C3646 : 'TotalDuration' : spécificateur de substitution inconnu @ no__t-0 :

```cpp
#include <chrono>

class Foo {
   std::chrono::milliseconds::duration TotalDuration{};
};

```

Pour éviter cette erreur, déclarez `TotalDuration` comme indiqué ici :

```cpp
#include <chrono>

class Foo {
  std::chrono::milliseconds TotalDuration {};
};
```

### <a name="stricter-checking-of-extern-c-functions"></a>Contrôle plus strict des fonctions extern "C"

Si une fonction **extern "C"** a été déclarée dans des espaces de noms différents, les C++ versions précédentes du compilateur Microsoft ne vérifiaient pas si les déclarations étaient compatibles. Dans Visual Studio 2019 version 16,3, le compilateur effectue une telle vérification. En mode [/permissive-](../build/reference/permissive-standards-conformance.md) , le code suivant produit *C2371 : redéfinition ; différents types de base* et *C2733 vous ne pouvez pas surcharger une fonction avec une liaison C*:

```cpp
using BOOL = int;

namespace N
{
   extern "C" void f(int, int, int, bool);
}

void g()
{
   N::f(0, 1, 2, false);
}

extern "C" void f(int, int, int, BOOL){}
```

Pour éviter les erreurs dans l’exemple précédent, utilisez **bool** au lieu de **bool** de manière cohérente dans les deux déclarations de `f`.

### <a name="standard-library-improvements"></a>Améliorations de la bibliothèque standard

Les en-têtes non standard \<stdexcpt. h > et \<typeinfo. h > ont été supprimés. Le code qui les inclut doit plutôt inclure les en-têtes standard \<exception > et \<typeinfo >, respectivement.

## <a name="update_160"></a>Correctifs de bogues et modifications de comportement dans Visual Studio 2019

### <a name="reinterpret_cast-in-a-constexpr-function"></a>Reinterpret_cast dans une fonction constexpr

Un **reinterpret_cast** n’est pas conforme dans une fonction **constexpr** . Le compilateur C++ Microsoft rejetait alors **reinterpret_cast** uniquement s’il était utilisé dans un contexte **constexpr** . Dans Visual Studio 2019, dans tous les modes de normes de langage, le compilateur diagnostique correctement un **reinterpret_cast** dans la définition d’une fonction **constexpr** . Le code suivant génère désormais *C3615 : la fonction constexpr’f’ne peut pas générer une expression constante*.

```cpp
long long i = 0;
constexpr void f() {
    int* a = reinterpret_cast<int*>(i);
}
```

Pour éviter cette erreur, supprimez le modificateur **constexpr** de la déclaration de la fonction.

### <a name="correct-diagnostics-for-basic_string-range-constructor"></a>Diagnostics corrects pour le constructeur de plage basic_string

Dans Visual Studio 2019, le constructeur de plage `basic_string` ne supprime plus les diagnostics du compilateur avec `static_cast`. Le code suivant compile sans avertissements dans Visual Studio 2017, en dépit de la perte possible de données de `wchar_t` à **char** lors de l’initialisation `out` :

```cpp
std::wstring ws = /* … */;
std::string out(ws.begin(), ws.end());
```

Visual Studio 2019 déclenche correctement *C4244 : 'argument' : conversion de 'wchar_t' en 'const _Elem', perte de données possible*. Pour éviter cet avertissement, vous pouvez initialiser le std::string comme illustré dans cet exemple :

```cpp
std::wstring ws = L"Hello world";
std::string out;
for (wchar_t ch : ws)
{
    out.push_back(static_cast<char>(ch));
}
```

### <a name="incorrect-calls-to--and---under-clr-or-zw-are-now-correctly-detected"></a>Les appels incorrects à += et -= sous /clr ou /ZW sont maintenant correctement détectés

Un bogue a été introduit dans Visual Studio 2017 qui faisait que le compilateur ignorait les erreurs en mode silencieux et ne générait aucun code pour les appels non valides à += et -= sous `/clr` ou `/ZW`. Le code suivant se compile sans erreur dans Visual Studio 2017, alors que dans Visual Studio 2019 il déclenche correctement l’*erreur C2845 : 'System::String ^': opération arithmétique de pointeur non autorisée sur ce type* :

```cpp
public enum class E { e };

void f(System::String ^s)
{
    s += E::e; // C2845 in VS2019
}
```

Pour éviter l’erreur dans cet exemple, utilisez l’opérateur avec la méthode ToString() : `s += E::e.ToString();`.

### <a name="initializers-for-inline-static-data-members"></a>Initialiseurs pour les membres de données statiques inline

Les accès aux membres non valides dans **inline** et les initialiseurs **constexpr statiques** sont maintenant détectés correctement. L’exemple suivant se compile sans erreur dans Visual Studio 2017, alors que dans Visual Studio 2019 sous le mode `/std:c++17`, il déclenche l’*erreur C2248 : impossible d’accéder à un membre privé déclaré dans la classe 'X'* .

```cpp
struct X
{
    private:
        static inline const int c = 1000;
};

struct Y : X
{
    static inline int d = c; // C2248 in Visual Studio 2019
};
```

Pour éviter cette erreur, déclarez le membre `X::c` comme protégé :

```cpp
struct X
{
    protected:
        static inline const int c = 1000;
};
```

### <a name="c4800-reinstated"></a>C4800 réintégré

MSVC utilisé pour obtenir un avertissement de performance C4800 sur la conversion implicite en **bool**. Il était trop « bruyant » et ne pouvait pas être supprimé ; nous avons donc choisi de le supprimer dans Visual Studio 2017. Toutefois, pendant le cycle de vie de Visual Studio 2017, nous avons eu beaucoup de commentaires disant qu’il était utile pour résoudre de nombreux cas. Nous avons rajouté à Visual Studio 2019 un avertissement C4800 soigneusement adapté, ainsi qu’un C4165 explicatif. Ces deux avertissements peuvent être facilement supprimés avec un cast explicite, ou une comparaison à 0 du type approprié. C4800 est un avertissement de niveau 4 désactivé par défaut, tandis que C4165 est un avertissement de niveau 3 désactivé par défaut. Les deux sont découvrables à l’aide de l’option de compilateur `/Wall`.

L’exemple suivant déclenche C4800 et C4165 sous `/Wall` :

```cpp
bool test(IUnknown* p)
{
    bool valid = p; // warning C4800: Implicit conversion from 'IUnknown*' to bool. Possible information loss
    IDispatch* d = nullptr;
    HRESULT hr = p->QueryInterface(__uuidof(IDispatch), reinterpret_cast<void**>(&d));
    return hr; // warning C4165: 'HRESULT' is being converted to 'bool'; are you sure this is what you want?
}
```

Pour éviter les avertissements dans l’exemple précédent, vous pouvez écrire le code comme ceci :

```cpp
bool test(IUnknown* p)
{
    bool valid = p != nullptr; // OK
    IDispatch* d = nullptr;
    HRESULT hr = p->QueryInterface(__uuidof(IDispatch), reinterpret_cast<void**>(&d));
    return SUCCEEDED(hr);  // OK
}
```

### <a name="local-class-member-function-doesnt-have-a-body"></a>La fonction membre de classe locale n’a pas de corps

Dans Visual Studio 2017, *C4822 : la fonction membre de classe locale n’a pas de corps* est déclenché seulement si l’option de compilateur `/w14822` est explicitement définie ; elle n’est pas affichée avec `/Wall`. Dans Visual Studio 2019, C4822 est un avertissement désactivé par défaut, ce qui le rend découvrable sous `/Wall` sans avoir à définir `/w14822` explicitement.

```cpp
void example()
{
    struct A
        {
            int boo(); // warning C4822
        };
}
```

### <a name="function-template-bodies-containing-constexpr-if-statements"></a>Corps de modèle de fonction contenant des instructions if constexpr

Les corps de fonction de modèle qui contiennent si des instructions **constexpr** ont des vérifications liées à l’analyse des [/permissive-](../build/reference/permissive-standards-conformance.md) activées. Par exemple, dans Visual Studio 2017, le code suivant génère *C7510 : 'Type' : l’utilisation d’un nom de type dépendant doit être précédée de’TypeName'*  uniquement si l’option **/permissive-** n’est pas définie. Dans Visual Studio 2019, le même code déclenche des erreurs même quand l’option **/permissive-** est définie :

```cpp
template <typename T>

int f()
{
    T::Type a; // error C7510

    if constexpr (T::val)
    {
        return 1;
    }
    else
    {
        return 2;
    }
}

struct X
{
    using Type = X;
    constexpr static int val = 1;
};

int main()
{
    return f<X>();
}
```

Pour éviter cette erreur, ajoutez le mot clé**TypeName** à la déclaration de `a` : `typename T::Type a;`.

### <a name="inline-assembly-code-isnt-supported-in-a-lambda-expression"></a>Le code de l’assembleur inline n’est pas pris en charge dans une expression lambda

L’équipe C++ Microsoft a récemment eu connaissance d’un problème de sécurité dans lequel l’utilisation de l’assembleur inline dans une expression lambda pouvait entraîner l’altération de `ebp` (le registre d’adresses de retour) au moment de l’exécution. Une personne malveillante pouvait éventuellement tirer parti de ce scénario. Étant donné la nature du problème, le fait que l’assembleur inline est uniquement pris en charge sur x86 et l’interaction médiocre de l’assembleur inline avec le reste du compilateur, nous en avons conclu que la solution la plus sûre à ce problème était d’interdire l’assembleur inline dans une expression lambda.

La seule utilisation de l’assembleur inline dans une expression lambda que nous avons rencontrée avait pour but de capturer l’adresse de retour. Dans ce scénario, vous pouvez capturer l’adresse de retour sur toutes les plateformes simplement à l’aide de `_ReturnAddress()` intrinsèque au compilateur.

Le code suivant génère *C7552 : l’assembleur inline n’est pas pris en charge dans une expression lambda* dans Visual Studio 2017 15.9 et dans Visual Studio 2019 :

```cpp
#include <cstdio>

int f()
{
    int y = 1724;
    int x = 0xdeadbeef;

    auto lambda = [&]
    {
        __asm {

            mov eax, x
            mov y, eax
        }
    };

    lambda();
    return y;
}
```

Pour éviter cette erreur, déplacez le code d’assembly dans une fonction nommée comme indiqué dans l’exemple suivant :

```cpp
#include <cstdio>

void g(int& x, int& y)
{
    __asm {
        mov eax, x
        mov y, eax
    }
}

int f()
{
    int y = 1724;
    int x = 0xdeadbeef;
    auto lambda = [&]
    {
        g(x, y);
    };
    lambda();
    return y;
}

int main()
{
    std::printf("%d\n", f());
}
```

### <a name="iterator-debugging-and-stdmove_iterator"></a>Débogage d’itérateur et `std::move_iterator`

La fonctionnalité de débogage d’itérateur a été adaptée pour unwrapper correctement `std::move_iterator`. Par exemple, `std::copy(std::move_iterator<std::vector<int>::iterator>, std::move_iterator<std::vector<int>::iterator>, int*)` peut maintenant engager le chemin rapide `memcpy`.

### <a name="fixes-for-xkeycheckh-keyword-enforcement"></a>Correctifs pour l’application du mot clé \<xkeycheck.h>

L’application du mot clé « macro-isé » de la bibliothèque Standard \<xkeycheck.h> a été corrigée pour émettre l’actuel mot-clé à problème détecté plutôt qu’un message générique. Elle prend aussi en charge les mots clés C++20 et évite qu’IntelliSense indique que des mots clés aléatoires sont des macros.

### <a name="allocator-types-no-longer-deprecated"></a>Les types d’allocateurs ne sont plus déconseillés

`std::allocator<void>`, `std::allocator::size_type` et `std::allocator::difference_type` ne sont plus déconseillés.

### <a name="correct-warning-for-narrowing-string-conversions"></a>Avertissement correct pour les conversions de chaîne restrictives

Un `static_cast` parasite, non demandé par la norme, qui supprimait accidentellement les avertissements restrictifs C4244 a été supprimé de `std::string`. Une tentative d’appel à `std::string::string(const wchar_t*, const wchar_t*)` va désormais émettre correctement *C4244 "narrowing a wchar_t into a char."*

### <a name="various-filesystem-correctness-fixes"></a>Corrections diverses de \<filesystem>

- Correction de l’échec de `std::filesystem::last_write_time` lors d’une tentative de changement de l’heure de la dernière écriture d’un répertoire.
- Désormais, le constructeur `std::filesystem::directory_entry` stocke un résultat en échec plutôt que de lever une exception quand un chemin cible qui n’existe pas est fourni.
- La version à 2 paramètres `std::filesystem::create_directory` a été changée pour appeler la version à 1 paramètre, car la fonction `CreateDirectoryExW` sous-jacente utiliserait `copy_symlink` si `existing_p` était un symlink.
- `std::filesystem::directory_iterator` n’échoue plus lorsqu’un symkink rompu est trouvé.
- `std::filesystem::space` accepte désormais les chemins relatifs.
- `std::filesystem::path::lexically_relative` n’est plus dérouté par les barres obliques de fin, signalé dans [LWG 3096](https://cplusplus.github.io/LWG/issue3096).
- Le problème a été contourné avec `CreateSymbolicLinkW` qui rejette les chemins avec des barres obliques dans `std::filesystem::create_symlink`.
- Nous avons contourné le problème du mode de suppression POSIX de la fonction `delete` existant sur Windows 10 LTSB 1609, mais en fait nous n’avons pas été capables de supprimer des fichiers.
- Les constructeurs de copie de `std::boyer_moore_searcher` et `std::boyer_moore_horspool_searcher` et les opérateurs d'affectation de copie arrivent maintenant à copier.

### <a name="parallel-algorithms-on-windows-8-and-later"></a>Algorithmes parallèles sur Windows 8 et ultérieur

La bibliothèque d’algorithmes parallèles utilise la vraie famille `WaitOnAddress` sur Windows 8 et ultérieur, au lieu d’utiliser tout le temps les versions fausses de Windows 7 et antérieur.

### <a name="stdsystem_categorymessage-whitespace"></a>Espace blanc `std::system_category::message()`

`std::system_category::message()` supprime désormais l’espace de fin du message retourné.

### <a name="stdlinear_congruential_engine-divide-by-zero"></a>Division par zéro de `std::linear_congruential_engine`

Certaines conditions qui faisaient que `std::linear_congruential_engine` déclenchait la division par 0 ont été corrigées.

### <a name="fixes-for-iterator-unwrapping"></a>Correctifs pour l’unwrapping d’itérateurs

Le système d’unwrapping d’itérateurs qui était au départ exposé pour l’intégration d’utilisateurs programmeurs dans Visual Studio 2017 15.8 (comme décrit dans l’article de blog de l’équipe C++ [STL Features and Fixes in VS 2017 15.8](https://devblogs.microsoft.com/cppblog/stl-features-and-fixes-in-vs-2017-15-8/)) n’unwrappe plus les itérateurs dérivés à partir des itérateurs de la bibliothèque standard. Par exemple, un utilisateur qui dérive de `std::vector<int>::iterator` et qui essaie de personnaliser le comportement obtient son comportement personnalisé lors de l’appel des algorithmes de la bibliothèque standard au lieu du comportement d’un pointeur.

La fonction de réserve de conteneur non ordonnée `reserve` maintenant pour N éléments, comme décrit dans [LWG 2156](https://cplusplus.github.io/LWG/issue2156).

### <a name="time-handling"></a>Gestion de l’heure

- Avant, certaines valeurs de temps passées à la bibliothèque de concurrence provoquaient un dépassement, par exemple, `condition_variable::wait_for(seconds::max())`. Ces dépassements, maintenant corrigés, changeaient le comportement selon un cycle apparemment aléatoire de 29 jours (quand les millisecondes uint32_t acceptées par les API Win32 sous-jacentes dépassaient).

- L’en-tête \<ctime > déclare désormais correctement `timespec` et `timespec_get` dans l’espace de noms `std`, en plus de les déclarer dans l’espace de noms global.

### <a name="various-fixes-for-containers"></a>Divers correctifs pour les conteneurs

- De nombreuses fonctions de conteneur internes à la bibliothèque Standard ont été rendues privées pour une meilleure expérience IntelliSense. Des correctifs supplémentaires pour marquer les membres comme privés sont attendus dans les prochaines versions de MSVC.

- Les problèmes de sécurité d’exception, où les conteneurs basés sur des nœuds comme `list`, `map` et `unordered_map` étaient altérés, ont été résolus. Pendant une opération de réaffectation `propagate_on_container_copy_assignment` ou `propagate_on_container_move_assignment`, nous libérons le nœud sentinelle du conteneur avec l’ancien allocateur, procédons à l’affectation de POCCA/POCMA sur l’ancien allocateur, puis tentons d’obtenir le nœud sentinelle auprès du nouvel allocateur. Si cette allocation échoue, le conteneur est altéré et ne peut même pas être détruit, car un nœud sentinelle est un invariant codé en dur dans la structure de données. Ce code a été corrigé pour allouer le nouveau nœud sentinelle de l’allocateur du conteneur source avant de détruire le nœud sentinelle existant.

- Les conteneurs ont été résolus pour toujours copier/déplacer/échanger les allocateurs en fonction de `propagate_on_container_copy_assignment`, `propagate_on_container_move_assignment` et `propagate_on_container_swap`, même pour les allocateurs déclarés `is_always_equal`.

- Ajout de surcharges pour les fonctions de fusion de conteneurs et d’extraction de membres qui acceptent des conteneurs rvalue, conformément à [P0083 "Splicing Maps And Sets"](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0083r3.pdf)

### <a name="stdbasic_istreamread-processing-of-rn--n"></a>Traitement par `std::basic_istream::read` de \\r\\n = > \\n

`std::basic_istream::read` a été corrigé pour ne pas écrire temporairement dans des parties de la mémoire tampon fournie lors du traitement de \\r\\n => \\n. Ce changement offre une partie de l’avantage en matière de performances acquis dans Visual Studio 2017 15.8 pour les lectures supérieures à 4 ko. Toutefois, les améliorations de l’efficacité obtenues en évitant les trois appels virtuels par caractère restent présentes.

### <a name="stdbitset-constructor"></a>Constructeur `std::bitset`

Le constructeur `std::bitset` ne lit plus les uns et les zéros dans l’ordre inverse pour les grands bitsets.

### <a name="stdpairoperator-regression"></a>Régression `std::pair::operator=`

Correction d’une régression dans l’opérateur d’affectation de `std::pair` introduite lors de l’implémentation de [LWG 2729 "Missing SFINAE on std::pair::operator=";](https://cplusplus.github.io/LWG/issue2729). Maintenant, il accepte de nouveau les types convertibles en `std::pair` correctement.

### <a name="non-deduced-contexts-for-add_const_t"></a>Contextes non déduits pour `add_const_t`

Correction d’un bogue de traits de type mineur, où `add_const_t` et les fonctions associées sont censés être un contexte non déduit. En d’autres termes, `add_const_t` doit être un alias pour `typename add_const<T>::type`, pas `const T`.

## <a name="update_162"></a>Correctifs de bogues et modifications de comportement dans 16,2

### <a name="const-comparators-for-associative-containers"></a>Comparateurs const pour les conteneurs associatifs

Le code pour la recherche et l’insertion dans [Set](../standard-library/set-class.md), [Map](../standard-library/map-class.md), [multijeu](../standard-library/multiset-class.md)et [Multimap](../standard-library/multimap-class.md) a été fusionné pour réduire la taille du code. Les opérations d’insertion appellent maintenant la comparaison « inférieur à » sur un functor de comparaison **const** , de la même façon que les opérations de recherche ont été effectuées précédemment. Le code suivant compile dans Visual Studio 2019 version 16,1 et versions antérieures, mais génère C3848 dans Visual Studio 2019 version 16,2 :

```cpp
#include <iostream>
#include <map>

using namespace std;

struct K
{
   int a;
   string b = "label";
};

struct Comparer  {
   bool operator() (K a, K b) {
      return a.a < b.a;
   }
};

map<K, double, Comparer> m;

K const s1{1};
K const s2{2};
K const s3{3};

int main() {

   m.emplace(s1, 1.08);
   m.emplace(s2, 3.14);
   m.emplace(s3, 5.21);

}
```

Pour éviter cette erreur, faites de l’opérateur de comparaison **const**:

```cpp
struct Comparer  {
   bool operator() (K a, K b) const {
      return a.a < b.a;
   }
};

```

::: moniker-end

::: moniker range="vs-2017"

## <a name="improvements_150"></a>Améliorations de la conformité dans Visual Studio 2017 RTW (version 15,0)

Avec la prise en charge des **constexpr** généralisées et des initialisations de membres de données non statiques (NSDMI) C++ pour les agrégats, le compilateur Microsoft dans Visual Studio 2017 est maintenant terminé pour les fonctionnalités ajoutées à la norme c++ 14. Cependant, le compilateur ne dispose pas encore de certaines fonctionnalités des normes C++11 et C++98. Consultez [Conformité du langage Visual C++](../visual-cpp-language-conformance.md) pour obtenir un tableau affichant l’état actuel du compilateur.

### <a name="c11-expression-sfinae-support-in-more-libraries"></a>C++11 : Prise en charge de la fonctionnalité SFINAE pour les expressions dans d’autres bibliothèques

Le compilateur continue d’améliorer la prise en charge de l’expression SFINAE, qui est nécessaire pour la déduction d’argument de modèle et la substitution où les expressions **decltype** et **constexpr** peuvent apparaître en tant que paramètres de modèle. Pour plus d’informations, consultez [Expression SFINAE improvements in Visual Studio 2017 RC](https://blogs.msdn.microsoft.com/vcblog/2016/06/07/expression-sfinae-improvements-in-vs-2015-update-3).

### <a name="c14-nsdmi-for-aggregates"></a>C++14 : NSDMI pour les agrégats

Un agrégat est un tableau ou une classe sans constructeur fourni par l’utilisateur, sans membres de données non statiques privés ou protégés, sans classes de base et sans fonctions virtuelles. À compter de C++14, les agrégats peuvent contenir des initialiseurs de membres. Pour plus d’informations, consultez [Member initializers and aggregates](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3605.html).

### <a name="c14-extended-constexpr"></a>C++14 : **Constexpr** étendu

Les expressions déclarées en tant que **constexpr** sont désormais autorisées à contenir certains types de déclarations, des instructions If et Switch, des instructions de boucle et une mutation d’objets dont la durée de vie a commencé dans l’évaluation de l’expression constexpr. En outre, il n’est plus nécessaire qu’une fonction membre non statique **constexpr** doive être implicitement **const**. Pour plus d’informations, consultez [Relaxing constraints on constexpr functions](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3652.html).

### <a name="c17-terse-static_assert"></a>C++17 : `static_assert` laconique

Le paramètre de message pour `static_assert` est facultatif. Pour plus d’informations, consultez [Extending static_assert, v2](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n3928.pdf).

### <a name="c17-fallthrough-attribute"></a>C++17 : Attribut `[[fallthrough]]`

En mode **/std:c++17** mode, l’attribut `[[fallthrough]]` est utilisable dans le contexte des instructions switch en tant qu’indicateur informant le compilateur que le comportement fallthrough est prévu. Cet attribut empêche le compilateur d’émettre des avertissements dans de tels cas. Pour plus d’informations, consultez [Wording for \[\[fallthrough\]\] attribute](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0188r0.pdf).

### <a name="generalized-range-based-for-loops"></a>Boucles For basées sur une plage généralisées

Range-based pour les boucles ne nécessitent plus que `begin()` et `end()` retournent des objets du même type. Avec ce changement, `end()` peut retourner un objet sentinel, à l’image de ceux utilisés par les plages définies dans [range-v3](https://github.com/ericniebler/range-v3) et la spécification technique d’autres plages disponibles mais pas encore publiées. Pour plus d’informations, consultez [Generalizing the Range-Based For Loop](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0184r0.html).

## <a name="improvements_153"></a>Améliorations de la conformité dans 15,3

### <a name="constexpr-lambdas"></a>Expressions lambda dans des contextes constexpr

Les expressions lambda peuvent désormais être utilisées dans les expressions constantes. Pour plus d’informations, consultez [Expressions lambda constexpr en C++](../cpp/lambda-expressions-constexpr.md).

### <a name="if-constexpr-in-function-templates"></a>**If constexpr** dans les modèles de fonction

Un modèle de fonction peut contenir des instructions **If constexpr** pour activer la branche au moment de la compilation. Pour plus d’informations, consultez [Instructions if constexpr](../cpp/if-else-statement-cpp.md#if_constexpr).

### <a name="selection-statements-with-initializers"></a>Instructions Selection avec initialiseurs

Une instruction **If** peut inclure un initialiseur qui introduit une variable au niveau de la portée de bloc dans l’instruction elle-même. Pour plus d’informations, consultez [Instructions if avec initialiseur](../cpp/if-else-statement-cpp.md#if_with_init).

### <a name="maybe_unused-and-nodiscard-attributes"></a>Attributs `[[maybe_unused]]` et `[[nodiscard]]`

Le nouvel attribut `[[maybe_unused]]` réduit au silence les avertissements lorsqu’une entité n’est pas utilisée. L’attribut `[[nodiscard]]` crée un avertissement si la valeur de retour d’un appel de fonction est ignorée. Pour plus d’informations, consultez [Attributes in C++](../cpp/attributes.md).

### <a name="using-attribute-namespaces-without-repetition"></a>Utilisation des espaces de noms d’attribut sans répétition

Nouvelle syntaxe pour activer uniquement un seul identificateur d’espace de noms dans une liste d’attributs. Pour plus d’informations, consultez [Attributes in C++](../cpp/attributes.md).

### <a name="structured-bindings"></a>Liaisons structurées

Il est désormais possible dans une déclaration unique de stocker une valeur avec des noms individuels pour ses composants, lorsque la valeur est un tableau, un `std::tuple` ou un `std::pair`, ou contient uniquement des membres de données non statiques publiques. Pour plus d’informations, consultez [Liaisons structurées](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0144r0.pdf) et [Retour de plusieurs valeurs à partir d’une fonction](../cpp/functions-cpp.md#multi_val).

### <a name="construction-rules-for-enum-class-values"></a>Règles de construction pour les valeurs de **classe enum**

Il existe désormais une conversion implicite/non restrictive à partir du type sous-jacent d’une énumération étendue vers l’énumération elle-même, lorsque sa définition ne présente aucun énumérateur et que la source utilise une syntaxe d’initialisation de liste. Pour plus d’informations, consultez [Règles de construction pour les valeurs de classe enum](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0138r2.pdf) et [Énumérations](../cpp/enumerations-cpp.md#no_enumerators).

### <a name="capturing-this-by-value"></a>Capture de `*this` par valeur

L’objet `*this` dans une expression lambda peut désormais être capturé par sa valeur. Ce changement permet des scénarios dans lesquels l’expression lambda est invoquée dans des opérations parallèles et asynchrones, en particulier sur des architectures de machines plus récentes. Pour plus d’informations, consultez [Lambda Capture of \*this by Value as \[=,\*this\]](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0018r3.html).

### <a name="removing-operator-for-bool"></a>Suppression de `operator++` pour **bool**

`operator++` n’est plus pris en charge sur les types **bool** . Pour plus d’informations, consultez [Remove Deprecated operator++(bool)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0002r1.html).

### <a name="removing-deprecated-register-keyword"></a>Suppression du mot clé **Register** déconseillé

Le mot clé **Register** , précédemment déconseillé (et ignoré par le compilateur), est maintenant supprimé du langage. Pour plus d’informations, consultez [Remove Deprecated Use of the register Keyword](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0001r1.html).

## <a name="improvements_155"></a>Améliorations de la conformité dans 15,5

Les fonctionnalités marquées avec \[14] sont disponibles sans conditions, même en mode **/std:c++14**.

### <a name="new-compiler-switch-for-extern-constexpr"></a>Nouveau commutateur de compilateur pour **extern constexpr**

Dans les versions antérieures de Visual Studio, le compilateur a toujours donné une liaison interne de variable **constexpr** même quand la variable était marquée comme **extern**. Dans Visual Studio 2017 version 15.5, un nouveau commutateur de compilateur, [/Zc:externConstexpr](../build/reference/zc-externconstexpr.md), active le comportement correct de conformité aux normes. Pour plus d’informations, consultez [Liaison extern constexpr](#extern_linkage).

### <a name="removing-dynamic-exception-specifications"></a>Suppression des spécifications d’exceptions dynamiques

[P0003R5](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0003r5.html)Les spécifications d’exceptions dynamiques ont été dépréciées dans C++11. La fonctionnalité est supprimée dans C++17, mais la spécification (toujours) dépréciée `throw()` est conservée uniquement comme alias pour `noexcept(true)`. Pour plus d’informations, consultez [Suppression des spécifications d’exceptions dynamiques et noexcept](#noexcept_removal).

### `not_fn()`

[P0005R4](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0005r4.html) `not_fn` vient remplacer `not1` et `not2`.

### <a name="rewording-enable_shared_from_this"></a>Reformulation de `enable_shared_from_this`

[P0033R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0033r1.html) `enable_shared_from_this` a été ajouté dans C++11. La norme C++17 met à jour la spécification pour mieux gérer certains cas extrêmes. [14]

### <a name="splicing-maps-and-sets"></a>Ajout de mappages et d’ensembles

[P0083R3](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0083r3.pdf) Cette fonctionnalité permet d’extraire des nœuds de conteneurs associatifs (par exemple `map`, `set`, `unordered_map`, `unordered_set`) pour les modifier, puis de les réinsérer dans le même conteneur ou dans un autre conteneur qui utilise le même type de nœud. (Un cas d’usage courant consiste à extraire un nœud d’un `std::map`, à changer la clé et à réinsérer le nœud.)

### <a name="deprecating-vestigial-library-parts"></a>Composants de bibliothèque rudimentaires dépréciés

[P0174R2](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0174r2.html) Plusieurs fonctionnalités de la bibliothèque standard C++ ont été remplacées par de nouvelles fonctionnalités au fil des années, ou ont été jugées inutiles ou problématiques. Ces fonctionnalités sont officiellement dépréciées dans C++17.

### <a name="removing-allocator-support-in-stdfunction"></a>Suppression de la prise en charge d’un allocateur dans `std::function`

[P0302R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0302r1.html) Dans les versions antérieures à C++17, le modèle de classe `std::function` avait plusieurs constructeurs avec un argument allocateur. Toutefois, l’utilisation d’allocateurs dans ce contexte était problématique et la sémantique n’était pas claire. Les constructeurs problématiques ont été supprimés.

### <a name="fixes-for-not_fn"></a>Corrections pour `not_fn()`

[P0358R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0358r1.html) La nouvelle formulation pour `std::not_fn` permet de prendre en charge la propagation de la catégorie de valeur quand un wrapper est appelé.

### <a name="shared_ptrt-shared_ptrtn"></a>`shared_ptr<T[]>`, `shared_ptr<T[N]>`

[P0414R2](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0414r2.html) Fusion des modifications apportées à `shared_ptr` dans C++17 dans Library Fundamentals. [14]

### <a name="fixing-shared_ptr-for-arrays"></a>Correction de `shared_ptr` pour les tableaux

[P0497R0](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0497r0.html) Correctifs apportés à la prise en charge de shared_ptr pour les tableaux. [14]

### <a name="clarifying-insert_return_type"></a>Clarification de `insert_return_type`

[P0508R0](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0508r0.html) Les conteneurs associatifs ou non ordonnés avec des clés uniques ont une fonction membre `insert` qui retourne un type imbriqué `insert_return_type`. Le type de retour est maintenant défini comme une spécialisation d’un type qui est paramétré sur les éléments Iterator et NodeType du conteneur.

### <a name="inline-variables-for-the-standard-library"></a>Variables inline pour la bibliothèque standard

[P0607R0](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0607r0.html)

### <a name="annex-d-features-deprecated"></a>Fonctionnalités dépréciées de l’annexe D

L’annexe D de la norme C++ contient toutes les fonctionnalités qui ont été dépréciées, notamment `shared_ptr::unique()`, `<codecvt>` et `namespace std::tr1`. Quand le commutateur de compilateur **/std:c++17** est défini, presque toutes les fonctionnalités de la bibliothèque standard listées dans l’annexe D sont marquées comme dépréciées. Pour plus d’informations, consultez [Les fonctionnalités de la bibliothèque standard répertoriées dans l’annexe D sont marquées comme dépréciées](#annex_d).

Maintenant, l’espace de noms `std::tr2::sys` dans `<experimental/filesystem>` émet un avertissement de dépréciation en mode **/std:c++14** par défaut, et est supprimé en mode **/std:c++17** par défaut.

La conformité est améliorée dans `<iostream>`, car l’utilisation d’une extension non standard (spécialisations de classe explicites) n’est plus nécessaire.

La bibliothèque standard utilise désormais les modèles de variable en interne.

La bibliothèque standard a été mise à jour en réponse aux modifications du compilateur C++ 17, y compris l’ajout de **noexcept** dans le système de type et la suppression des spécifications d’exception dynamique.

## <a name="improvements_156"></a>Améliorations de la conformité dans 15,6

### <a name="c17-library-fundamentals-v1"></a>C++17 - Library Fundamentals V1

[P0220R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0220r1.html) incorpore la spécification technique relative aux notions de base des bibliothèques (Library Fundamentals TS) pour C++17 à la norme. Ce document traite des mises à jour apportées à \<experimental/tuple>, \<experimental/optional>, \<experimental/functional>, \<experimental/any>, \<experimental/string_view>, \<experimental/memory>, \<experimental/memory_resource> et \<experimental/algorithm>.

### <a name="c17-improving-class-template-argument-deduction-for-the-standard-library"></a>C++17 : Amélioration de la déduction d’arguments de modèle de classe pour la bibliothèque standard

[P0739R0](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0739r0.html) `adopt_lock_t` est déplacé au début de la liste des paramètres de `scoped_lock` pour garantir une utilisation cohérente de `scoped_lock`. Le constructeur `std::variant` est autorisé à participer à la résolution de surcharge dans davantage de cas pour permettre l’assignation de copie.

## <a name="improvements_157"></a>Améliorations de la conformité dans 15,7

### <a name="c17-rewording-inheriting-constructors"></a>C++17 : Reformulation de l’héritage des constructeurs

[P0136R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0136r1.html) Dans une déclaration **using** qui nomme un constructeur, les initialisations de la classe dérivée peuvent désormais voir les constructeurs de la classe de base correspondante, évitant ainsi la déclaration de constructeurs supplémentaires pour la classe dérivée. Cette reformulation est un changement à compter de C++14. Dans Visual Studio 2017 versions 15.7 et ultérieures, en mode **/std:c++17**, le code qui utilise l’héritage de constructeurs et qui est valide dans C++14 peut être non valide ou avoir une sémantique différente.

L’exemple suivant montre le comportement de C++14 :

```cpp
struct A {
    template<typename T>
    A(T, typename T::type = 0);
    A(int);
};

struct B : A {
    using A::A;
    B(int n) = delete; // Error C2280
};

B b(42L); // Calls B<long>(long), which calls A(int)
          //  due to substitution failure in A<long>(long).
```

L’exemple suivant montre le comportement de **/std:c++17** dans Visual Studio 15.7 :

```cpp
struct A {
    template<typename T>
    A(T, typename T::type = 0);
    A(int);
};

struct B : A {
    using A::A;
    B(int n)
    {
        //do something
    }
};

B b(42L); // now calls B(int)
```

Pour plus d’informations, consultez [Constructeurs](../cpp/constructors-cpp.md#inheriting_constructors).

### <a name="c17-extended-aggregate-initialization"></a>C++17 : Initialisation d’agrégats étendue

[P0017R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0017r1.html)

Si le constructeur d’une classe de base est non public, mais qu’il est accessible à une classe dérivée, vous ne pouvez plus utiliser d’accolades vides pour initialiser un objet du type dérivé en mode **/std:c++17** dans Visual Studio version 15.7.

L’exemple suivant montre le comportement conforme à C++14 :

```cpp
struct Derived;

struct Base {
    friend struct Derived;
private:
    Base() {}
};

struct Derived : Base {};

Derived d1; // OK. No aggregate init involved.
Derived d2 {}; // OK in C++14: Calls Derived::Derived()
               // which can call Base ctor.
```

Dans C++17, `Derived` est désormais considéré comme un type d’agrégat. Cela signifie que l’initialisation de `Base` par le biais du constructeur par défaut privé se produit donc directement dans le cadre de la règle d’initialisation d’agrégats étendue. Auparavant, le constructeur privé `Base` était appelé par le biais du constructeur `Derived`, ce qui réussissait en raison de la déclaration friend.

L’exemple suivant montre le comportement de C++17 dans Visual Studio version 15.7 en mode **/std:c++17** :

```cpp
struct Derived;

struct Base {
    friend struct Derived;
private:
    Base() {}
};

struct Derived : Base {
    Derived() {} // add user-defined constructor
                 // to call with {} initialization
};

Derived d1; // OK. No aggregate init involved.

Derived d2 {}; // error C2248: 'Base::Base': cannot access
               // private member declared in class 'Base'
```

### <a name="c17-declaring-non-type-template-parameters-with-auto"></a>C++17 : Déclaration de paramètres de modèle sans type avec auto

[P0127R2](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0127r2.html)

En mode **/std:c++17**, le compilateur peut désormais déduire le type d’un argument de modèle sans type déclaré avec **auto** :

```cpp
template <auto x> constexpr auto constant = x;

auto v1 = constant<5>;      // v1 == 5, decltype(v1) is int
auto v2 = constant<true>;   // v2 == true, decltype(v2) is bool
auto v3 = constant<'a'>;    // v3 == 'a', decltype(v3) is char
```

L’une des conséquences de cette nouvelle fonctionnalité est que le code valide dans C++14 peut être non valide ou avoir une sémantique différente. Par exemple, certaines surcharges qui étaient précédemment non valides sont à présent valides. L’exemple suivant montre du code C++14 dont la compilation réussit car l’appel à `example(p)` est lié à `example(void*);`. Dans Visual Studio 2017 version 15.7, en mode **/std:c++17**, le modèle de fonction `example` offre la meilleure correspondance.

```cpp
template <int N> struct A;
template <typename T, T N> int example(A<N>*) = delete;

void example(void *);

void sample(A<0> *p)
{
    example(p); // OK in C++14
}
```

L’exemple suivant montre du code C++17 dans Visual Studio 15.7 en mode **/std:c++17** :

```cpp
template <int N> struct A;
template <typename T, T N> int example(A<N>*);

void example(void *);

void sample(A<0> *p)
{
    example(p); // C2280: 'int example<int,0>(A<0>*)': attempting to reference a deleted function
}
```

### <a name="c17-elementary-string-conversions-partial"></a>C++17 : Conversions de chaînes élémentaires (état partiel)

[P0067R5](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0067r5.html) Fonctions de bas niveau indépendantes des paramètres régionaux pour les conversions entre entiers et chaînes et entre nombres à virgule flottante et chaînes.

### <a name="c20-avoiding-unnecessary-decay-partial"></a>C++20 : Prévention des dégradations inutiles (état partiel)

[P0777R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0777r1.pdf) Ajoute une distinction entre le concept de « dégradation » et la simple opération consistant à supprimer const ou des qualificateurs de référence.  Le nouveau trait de type `remove_reference_t` remplace `decay_t` dans certains contextes. La prise en charge de `remove_cvref_t` est implémentée dans Visual Studio 2019.

### <a name="c17-parallel-algorithms"></a>C++17 : Algorithmes parallèles

[P0024R2](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0024r2.html) La spécification technique relative au parallélisme (Parallelism TS) est intégrée à la norme, avec des modifications mineures.

### <a name="c17-hypotx-y-z"></a>C++17 : `hypot(x, y, z)`

[P0030R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0030r1.pdf) Ajoute trois nouvelles surcharges à `std::hypot` pour les types **float**, **double** et **long double** (chacun d’eux ayant trois paramètres d’entrée).

### <a name="c17-filesystem"></a>C++17 : \<filesystem>

[P0218R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0218r1.html) Intègre la spécification technique relative au système de fichiers (File System TS) à la norme, avec quelques modifications de formulation.

### <a name="c17-mathematical-special-functions"></a>C++17 : Fonctions mathématiques spéciales

[P0226R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0220r1.html) Intègre les spécifications techniques précédentes pour les fonctions mathématiques spéciales à l’en-tête \<cmath> standard.

### <a name="c17-deduction-guides-for-the-standard-library"></a>C++17 : Guides de déduction pour la bibliothèque standard

[P0433R2](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0433r2.html) Met à jour STL pour tirer parti de l’adoption par C++17 de [P0091R3](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0091r3.html), qui ajoute la prise en charge de la déduction d’arguments de modèle de classe.

### <a name="c17-repairing-elementary-string-conversions"></a>C++17 : Réparation de conversions de chaînes élémentaires

[P0682R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0682r1.html) Déplace les nouvelles fonctions de conversion de chaîne élémentaire de P0067R5 vers un nouvel en-tête \<charconv> et apporte d’autres améliorations, notamment l’utilisation de `std::errc` pour la gestion des erreurs au lieu de `std::error_code`.

### <a name="c17-constexpr-for-char_traits-partial"></a>C++ 17 : **constexpr** pour `char_traits` (partielle)

[P0426R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0426r1.html) Changements apportés aux fonctions membres `std::traits_type` `length`, `compare` et `find` pour rendre `std::string_view` utilisable dans les expressions constantes. (Dans Visual Studio 2017 version 15.6, prise en charge pour Clang/LLVM uniquement. Dans la version 15.7 Preview 2, la prise en charge est presque complète pour ClXX.)

## <a name="improvements_159"></a>Améliorations de la conformité dans 15,9

### <a name="left-to-right-evaluation-order-for-operators-----and-"></a>Ordre d’évaluation de gauche à droite pour les opérateurs `->*`, `[]`, `>>`, et `<<`

À compter de C++17, les opérandes des opérateurs `->*`, `[]`, `>>`, et `<<` doivent être évalués de gauche à droite. Il existe deux cas dans lesquels le compilateur est incapable de garantir cet ordre :

- lorsqu’une des expressions de l’opérande est un objet passé par une valeur ou contient un objet passé par une valeur, ou

- lors de la compilation à l’aide de **/clr**, et l’une des opérandes est un champ d’un objet ou un élément de tableau.

Le compilateur émet l’avertissement [C4866](https://docs.microsoft.com/cpp/error-messages/compiler-warnings/c4866?view=vs-2017) quand il ne peut pas garantir l’évaluation de gauche à droite. Cet avertissement est généré par le compilateur uniquement si **/std:c++17** ou version ultérieure est spécifiée, car l’exigence d’ordre de gauche à droite de ces opérateurs a été introduite dans C++17.

Pour résoudre cet avertissement, évaluez d’abord si l’évaluation de gauche à droite des opérandes est nécessaire, par exemple lorsque l’évaluation des opérandes peut produire des effets collatéraux dépendants de l’ordre. Dans de nombreux cas, l’ordre dans lequel les opérandes sont évalués n’a pas d’effet visible. Si l’ordre d’évaluation doit être de gauche à droite, réfléchissez si vous pouvez passer les opérandes par référence const à la place. Cette modification supprime l’avertissement dans l’exemple de code suivant :

```cpp
// C4866.cpp
// compile with: /w14866 /std:c++17

class HasCopyConstructor
{
public:
    int x;

    HasCopyConstructor(int x) : x(x) {}
    HasCopyConstructor(const HasCopyConstructor& h) : x(h.x) { }
};

int operator>>(HasCopyConstructor a, HasCopyConstructor b) { return a.x >> b.x; }

// This version of operator>> does not trigger the warning:
// int operator>>(const HasCopyConstructor& a, const HasCopyConstructor& b) { return a.x >> b.x; }

int main()
{
    HasCopyConstructor a{ 1 };
    HasCopyConstructor b{ 2 };

    a>>b;        // C4866 for call to operator>>
};
```

## <a name="update_150"></a> Correctifs de bogues dans Visual Studio 2017 RTW (version 15.0)

### <a name="copy-list-initialization"></a>Copy-list-initialization

Visual Studio 2017 déclenche correctement les erreurs de compilateur liées à la création d’objets à l’aide de listes d’initialiseurs qui n’étaient pas interceptées dans Visual Studio 2015 et qui pouvaient entraîner des blocages ou un comportement d’exécution non défini. Conformément au document N4594, point 13.3.1.7p1, dans copy-list-initialization, le compilateur doit envisager un constructeur explicite pour la résolution de la surcharge, mais doit générer une erreur si cette surcharge particulière est choisie.

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

### <a name="constexpr"></a>**constexpr**

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

Pour corriger l’erreur, déclarez la fonction `array::size()` en tant que **constexpr** ou supprimez le qualificateur **constexpr** de `f`.

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
                        // as an argument to a variadic function.
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

ou utiliser un cast statique pour convertir l’objet avant de le transmettre :

```cpp
    struct S {/* as before */} s(0);
    printf("%i\n", static_cast<int>(s))
```

Pour les chaînes générées et gérées à l’aide de CString, vous devez utiliser le `operator LPCTSTR()` fourni pour caster un objet CString vers le pointeur C attendu par la chaîne de format.

```cpp
CString str1;
CString str2 = _T("hello!");
str1.Format(_T("%s"), static_cast<LPCTSTR>(str2));
```

### <a name="cv-qualifiers-in-class-construction"></a>Qualificateurs cv dans la construction de la classe

Dans Visual Studio 2015, le compilateur ignore parfois à tort le qualificateur cv pendant la génération d’un objet de classe par le biais d’un appel de constructeur. Ce problème peut provoquer un incident ou un comportement inattendu au moment de l’exécution. L’exemple suivant se compile dans Visual Studio 2015, mais génère une erreur de compilateur dans Visual Studio 2017 :

```cpp
struct S
{
    S(int);
    operator int();
};

int i = (const S)0; // error C2440
```

Pour corriger l’erreur, déclarez `operator int()` comme **const**.

### <a name="access-checking-on-qualified-names-in-templates"></a>Contrôle d’accès sur les noms qualifiés dans les modèles

Les versions précédentes du compilateur n’effectuaient pas de contrôle d’accès sur les noms qualifiés dans certains contextes de modèle. Ce problème peut interférer avec le comportement attendu de la fonctionnalité SFINAE où la substitution est supposée échouer en raison de l’inaccessibilité d’un nom. Cette situation peut entraîner un incident ou un comportement inattendu au moment de l’exécution en raison de l’appel par le compilateur de la surcharge incorrecte de l’opérateur. Dans Visual Studio 2017, une erreur de compilateur est générée. L’erreur spécifique peut varier, mais, en général, il s’agit de « C2672 fonction correspondante surchargée introuvable ». Le code suivant se compile dans Visual Studio 2015, mais génère une erreur dans Visual Studio 2017 :

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

Dans Visual Studio 2015 et versions antérieures, le compilateur ne diagnostiquait pas les listes d’arguments de modèle manquantes quand le modèle apparaissait dans une liste de paramètres de modèle, par exemple, dans le cadre d’un argument de modèle par défaut ou d’un paramètre de modèle sans type. Ce problème peut entraîner un comportement imprévisible, y compris des pannes du compilateur ou un comportement inattendu au moment de l’exécution. Le code suivant se compile dans Visual Studio 2015, mais génère une erreur dans Visual Studio 2017.

```cpp
template <class T> class ListNode;
template <class T> using ListNodeMember = ListNode<T> T::*;
template <class T, ListNodeMember M> class ListHead; // C2955: 'ListNodeMember': use of alias
                                                     // template requires template argument list

// correct:  template <class T, ListNodeMember<T> M> class ListHead;
```

### <a name="expression-sfinae"></a>Fonctionnalité SFINAE pour les expressions

Pour prendre en charge expression-SFINAE, le compilateur analyse désormais les arguments **decltype** lorsque les modèles sont déclarés au lieu d’être instanciés. Par conséquent, si une spécialisation non dépendante est trouvée dans l’argument decltype, elle n’est pas différée à l’instanciation. Elle est traitée immédiatement, et toute erreur résultante est diagnostiquée à ce moment-là.

L’exemple suivant montre une erreur de compilateur de ce type générée au moment de la déclaration :

```cpp
#include <utility>
template <class T, class ReturnT, class... ArgsT>
class IsCallable
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

Dans Visual Studio 2015 et antérieur, le compilateur autorisait (mais ignorait) un initialiseur de membre par défaut pour un membre d’une classe value. L’initialisation par défaut d’une classe value initialise systématiquement les membres à zéro. Un constructeur par défaut n’est pas autorisé. Dans Visual Studio 2017, les initialiseurs de membres par défaut déclenchent une erreur de compilateur, comme illustré dans cet exemple :

```cpp
value struct V
{
    int i = 0; // error C3446: 'V::i': a default member initializer
               // isn't allowed for a member of a value class
};
```

### <a name="default-indexers-ccli"></a>Indexeurs par défaut (C++/CLI)

Dans Visual Studio 2015 et antérieur, le compilateur identifiait à tort une propriété par défaut en tant qu’indexeur par défaut dans certaines circonstances. Il était possible de contourner le problème en utilisant l’identificateur **default** pour accéder à la propriété. La solution de contournement elle-même devient problématique une fois que la **valeur par défaut** a été introduite en tant que mot clé dans c++ 11. Dans Visual Studio 2017, les bogues qui nécessitaient la solution de contournement ont été corrigés, et le compilateur génère désormais une erreur quand la **valeur par défaut** est utilisée pour accéder à la propriété par défaut d’une classe.

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

## <a name="update_153"></a>Correctifs de bogues dans 15,3

### <a name="calls-to-deleted-member-templates"></a>Appels à des modèles membres supprimés

Dans les versions précédentes de Visual Studio, le compilateur ne parvenait pas dans certains cas à émettre une erreur pour les appels incorrects à un modèle membre supprimé qui pouvaient éventuellement provoquer des incidents lors de l’exécution. Le code suivant génère désormais l’erreur C2280, « 'int S\<int>::f\<int>(void)' : tentative de référencement d’une fonction supprimée » :

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

Pour corriger l’erreur, déclarez `i` comme **int**.

### <a name="pre-condition-checks-for-type-traits"></a>Vérifications de conditions préalables pour les traits de type

Visual Studio 2017 version 15.3 améliore les vérifications de conditions préalables pour les traits de type afin de suivre plus strictement la norme. Une telle vérification doit être affectée. Le code suivant génère l’erreur C2139 dans Visual Studio 2017 version 15.3 :

```cpp
struct S;
enum E;

static_assert(!__is_assignable(S, S), "fail"); // C2139 in 15.3
static_assert(__is_convertible_to(E, E), "fail"); // C2139 in 15.3
```

### <a name="new-compiler-warning-and-runtime-checks-on-native-to-managed-marshaling"></a>Nouvel avertissement du compilateur et nouvelles vérifications à l’exécution sur du marshaling de fonctions natives à managées

L’appel des fonctions managées aux fonctions natives nécessite un marshaling. Le CLR effectue le marshaling, mais il ne comprend pas la sémantique C++. Si vous passez un objet natif par valeur, le CLR appelle le constructeur de copie de l’objet ou utilise `BitBlt`, ce qui peut provoquer un comportement non défini lors de l’exécution.

Désormais, le compilateur émet un avertissement s’il peut savoir au moment de la compilation qu’un objet natif avec un constructeur de copie supprimé est transmis entre les limites native et managée par valeur. Pour les cas où le compilateur ne sait rien au moment de la compilation, il injecte une vérification à l’exécution afin que le programme appelle `std::terminate` immédiatement dès qu’un marshaling incorrect se produit. Dans Visual Studio 2017 version 15.3, le code suivant génère l’avertissement C4606, « 'A' : le passage d’un argument par valeur à travers une frontière native/managée nécessite un constructeur de copie valide. Sinon, le comportement au moment de l’exécution est non défini.

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
    f(A()); // This call from managed to native requires marshaling. The CLR doesn't understand C++ and uses BitBlt, which results in a double-free later.
}
```

Pour corriger cette erreur, supprimez la directive `#pragma managed` pour marquer l’appelant comme natif et éviter le marshaling.

### <a name="experimental-api-warning-for-winrt"></a>Avertissement d’API expérimentale pour WinRT

Les API WinRT publiées pour l’expérimentation et les commentaires sont décorées avec `Windows.Foundation.Metadata.ExperimentalAttribute`. Dans Visual Studio 2017 version 15.3, le compilateur génère l’avertissement C4698 quand il rencontre l’attribut. Certaines API dans les versions précédentes du SDK Windows ont déjà été décorées avec l’attribut et les appels à ces API déclenchent cet avertissement du compilateur. L’attribut est supprimé de tous les types fournis dans les SDK Windows plus récents mais, si vous utilisez un SDK plus ancien, vous devez supprimer ces avertissements pour tous les appels aux types fournis.

Le code suivant génère l’avertissement C4698 : « 'Windows::Storage::IApplicationDataStatics2::GetForUserAsync' est utilisé à des fins d’évaluation uniquement. Il sera peut-être changé ou supprimé au cours des prochaines mises à jour. » :

```cpp
Windows::Storage::IApplicationDataStatics2::GetForUserAsync(); //C4698
```

Pour désactiver l’avertissement, ajoutez un #pragma :

```cpp
#pragma warning(push)
#pragma warning(disable:4698)

Windows::Storage::IApplicationDataStatics2::GetForUserAsync();

#pragma warning(pop)
```

### <a name="out-of-line-definition-of-a-template-member-function"></a>Définition hors ligne d’une fonction membre de modèle

Visual Studio 2017 version 15.3 génère une erreur quand elle rencontre une définition hors ligne d’une fonction membre de modèle qui n’a pas été déclarée dans la classe. Le code suivant génère désormais l’erreur C2039 : 'f' : n’est pas un membre de 'S' :

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

### <a name="attempting-to-take-the-address-of-this-pointer"></a>Tentative de prise de l’adresse de **ce** pointeur

Dans C++ , **il** s’agit d’un prvalue de type pointeur vers X. Vous ne pouvez pas prendre l’adresse de **cette** ou la lier à une référence lvalue. Dans les versions précédentes de Visual Studio, le compilateur vous permettait de contourner cette restriction en utilisant un cast. Dans Visual Studio 2017 version 15.3, le compilateur génère l’erreur C2664.

### <a name="conversion-to-an-inaccessible-base-class"></a>Conversion vers une classe de base inaccessible

Visual Studio 2017 version 15.3 génère une erreur quand vous essayez de convertir un type en une classe de base qui n’est pas accessible. Le compilateur génère désormais « erreur C2243 : 'cast de type' : la conversion de 'D *' en 'B *' existe, mais n’est pas accessible ». Le code suivant est incorrect et peut éventuellement provoquer un incident lors de l’exécution. Le compilateur génère désormais l’erreur C2243 quand il rencontre un code tel que le suivant :

```cpp
#include <memory>

class B { };
class D : B { }; // C2243. should be public B { };

void f()
{
   std::unique_ptr<B>(new D());
}
```

### <a name="default-arguments-arent-allowed-on-out-of-line-definitions-of-member-functions"></a>Les arguments par défaut ne sont pas autorisés sur les définitions hors ligne des fonctions membres

Les arguments par défaut ne sont pas autorisés sur les définitions hors ligne des fonctions membres dans les classes de modèles. Le compilateur émet un avertissement sous **/permissive** et une erreur matérielle sous [/permissive-](../build/reference/permissive-standards-conformance.md).

Dans les versions précédentes de Visual Studio, le code incorrect suivant peut entraîner un incident lors de l’exécution. Visual Studio 2017 version 15.3 génère l’avertissement C5034 : 'A\<::f' : une définition hors ligne d’un membre d’un modèle de classe ne peut pas avoir d’arguments par défaut :

```cpp
template <typename T>
struct A {
    T f(T t, bool b = false);
};

template <typename T>
T A<T>::f(T t, bool b = false) // C5034
{
    // ...
}
```

Pour corriger cette erreur, supprimez l’argument par défaut `= false`.

### <a name="use-of-offsetof-with-compound-member-designator"></a>Utilisation de `offsetof` avec désignateur de membre composé

Dans Visual Studio 2017 version 15.3, l’utilisation de `offsetof(T, m)` où *m* est un « désignateur de membre composé » aboutit à un avertissement quand vous compilez avec l’option **/Wall**. Le code suivant est incorrect et peut éventuellement provoquer un incident lors de l’exécution. Visual Studio 2017 version 15.3 génère « l’avertissement C4841 : extension non standard utilisée : désignateur de membre composé dans offsetof » :

```cpp
struct A {
   int arr[10];
};

// warning C4841: non-standard extension used: compound member designator in offsetof
constexpr auto off = offsetof(A, arr[2]);
```

Pour corriger le code, désactivez l’avertissement avec un pragma ou modifiez le code pour ne pas utiliser `offsetof` :

```cpp
#pragma warning(push)
#pragma warning(disable: 4841)
constexpr auto off = offsetof(A, arr[2]);
#pragma warning(pop)
```

### <a name="using-offsetof-with-static-data-member-or-member-function"></a>Utilisation de `offsetof` avec des données membres static ou une fonction membre

Dans Visual Studio 2017 version 15.3, l’utilisation de `offsetof(T, m)` où *m* fait référence à des données membres static ou une fonction membre aboutit à une erreur. Le code suivant génère « erreur C4597 : comportement non défini : offsetof appliqué à la fonction membre 'example' » et « erreur C4597 : comportement non défini : offsetof appliqué à des données membres static 'sample' » :

```cpp
#include <cstddef>

struct A {
   int ten() { return 10; }
   static constexpr int two = 2;
};

constexpr auto off = offsetof(A, ten);
constexpr auto off2 = offsetof(A, two);
```

Ce code est incorrect et peut éventuellement provoquer un incident lors de l’exécution. Pour corriger cette erreur, modifiez le code pour ne plus appeler un comportement non défini. Il s’agit de code non portable qui n’est pas autorisé par la norme C++.

### <a name="declspec"></a> Nouvel avertissement sur les attributs `__declspec`

Dans Visual Studio 2017 version 15.3, le compilateur n’ignore plus les attributs si `__declspec(...)` est appliqué avant une spécification de liaison `extern "C"` externe. Avant, le compilateur ignorait l’attribut, ce qui pouvait avoir des implications lors de l’exécution. Quand les options **/Wall** et **/WX** sont définies, le code suivant génère « avertissement C4768 : les attributs __declspec avant la spécification de liaison sont ignorés » :

```cpp
__declspec(noinline) extern "C" HRESULT __stdcall //C4768
```

Pour résoudre l’avertissement, placez `extern "C"` d’abord :

```cpp
extern "C" __declspec(noinline) HRESULT __stdcall
```

Cet avertissement est désactivé par défaut dans la version  15.3 (mais activé par défaut dans la version 15.5) et impacte uniquement le code compilé avec **/Wall** **/WX**.

### <a name="decltype-and-calls-to-deleted-destructors"></a>**decltype** et appels aux destructeurs supprimés

Dans les versions précédentes de Visual Studio, le compilateur ne détectait pas quand un appel à un destructeur supprimé s’est produit dans le contexte de l’expression associée à **decltype**. Dans Visual Studio 2017 version 15.3, le code suivant génère « l’erreur C2280 : 'A\<T>::~A(void)' : tentative de référencement d’une fonction supprimée » :

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

La version RTW de Visual Studio 2017 a subi une régression C++ dans laquelle le compilateur n’émet pas de diagnostic si une variable **const** n’a pas été initialisée. Cette régression a été corrigée dans Visual Studio 2017 version 15.3. Le code suivant génère désormais « l’avertissement C4132 : 'Value' : un objet const doit être initialisé »:

```cpp
const int Value; //C4132
```

Pour corriger cette erreur, attribuez une valeur à `Value`.

### <a name="empty-declarations"></a>Déclarations vides

Visual Studio 2017 version 15.3 émet désormais un avertissement relatif aux déclarations vides pour tous les types, non seulement les types intégrés. Le code suivant génère désormais un avertissement C4091 de niveau 2 pour les quatre déclarations :

```cpp
struct A {};
template <typename> struct B {};
enum C { c1, c2, c3 };

int;    // warning C4091 : '' : ignored on left of 'int' when no variable is declared
A;      // warning C4091 : '' : ignored on left of 'main::A' when no variable is declared
B<int>; // warning C4091 : '' : ignored on left of 'B<int>' when no variable is declared
C;      // warning C4091 : '' : ignored on left of 'C' when no variable is declared
```

Pour supprimer les avertissements, commentez ou supprimez les déclarations vides. Dans les cas où l’objet sans nom doit avoir un effet secondaire (par exemple, RAII), vous devez lui affecter un nom.

L’avertissement est exclu sous **/Wv:18** et est activé par défaut sous le niveau d’avertissement W2.

### <a name="stdis_convertible-for-array-types"></a>`std::is_convertible` pour les types de tableaux

Les versions précédentes du compilateur ont donné des résultats incorrects avec [std::is_convertible](../standard-library/is-convertible-class.md) pour les types tableau. Cela obligeait les auteurs de bibliothèques à particulariser le compilateur Microsoft C++ lors de l’utilisation d’une caractéristique de type `std::is_convertible<...>`. Dans l’exemple suivant, les assertions statiques passent dans les versions antérieures de Visual Studio, mais échouent dans Visual Studio 2017 version 15.3 :

```cpp
#include <type_traits>

using Array = char[1];

static_assert(std::is_convertible<Array, Array>::value);
static_assert(std::is_convertible<const Array, const Array>::value, "");
static_assert(std::is_convertible<Array&, Array>::value, "");
static_assert(std::is_convertible<Array, Array&>::value, "");
```

`std::is_convertible<From, To>` est calculé en vérifiant si une définition de fonction imaginaire est correcte :

```cpp
   To test() { return std::declval<From>(); }
```

### <a name="private-destructors-and-stdis_constructible"></a>Destructeurs privés et `std::is_constructible`

Les versions précédentes du compilateur ignoraient si un destructeur était privé lors de la détermination du résultat de [std::is_constructible](../standard-library/is-constructible-class.md). Il en tient compte désormais. Dans l’exemple suivant, les assertions statiques passent dans les versions antérieures de Visual Studio, mais échouent dans Visual Studio 2017 version 15.3 :

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

Les destructeurs privés entraînent la non-constructibilité d’un type. `std::is_constructible<T, Args...>` est calculé comme si la déclaration suivante était écrite :

```cpp
   T obj(std::declval<Args>()...)
```

Cet appel implique un appel de destructeur.

### <a name="c2668-ambiguous-overload-resolution"></a>C2668 : Résolution de surcharge ambiguë

Parfois, les versions précédentes du compilateur ne parvenaient pas à détecter une ambiguïté lors de la découverte de plusieurs candidats par le biais simultanément des déclarations et des recherches dépendantes d’arguments. Cet échec pouvait conduire à choisir une surcharge incorrecte et entraîner un comportement inattendu au moment de l’exécution. Dans l’exemple suivant, Visual Studio 2017 version 15.3 déclenche correctement C2668, 'f' : appel ambigu à une fonction surchargée :

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

Pour corriger le code, supprimez l’instruction using `N::f` si vous souhaitez appeler `::f()`.

### <a name="c2660-local-function-declarations-and-argument-dependent-lookup"></a>C2660 : Déclarations de fonction locale et recherche dépendante d’argument

Les déclarations de fonction locale masquent la déclaration de fonction dans la portée englobante et désactivent la recherche dépendante d’argument. Pourtant, les versions précédentes du compilateur effectuaient une recherche dépendante d’argument dans ce cas, conduisant éventuellement à choisir une surcharge incorrecte et entraînant un comportement inattendu au moment de l’exécution. En règle générale, l’erreur est causée par une signature incorrecte de la déclaration de fonction locale. Dans l’exemple suivant, Visual Studio 2017 version 15.3 déclenche correctement C2660, 'f' : la fonction n’accepte pas deux arguments :

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

Pour résoudre le problème, changez la signature `f(S)` ou supprimez-la.

### <a name="c5038-order-of-initialization-in-initializer-lists"></a>C5038 : Ordre d’initialisation dans les listes d’initialiseurs

Les membres de classe sont initialisés dans l’ordre suivant lequel ils sont déclarés, et non selon celui de leur apparition dans les listes d’initialiseurs. Les versions précédentes du compilateur n’avertissaient pas lorsque l’ordre de la liste d’initialiseurs était différent de celui des déclarations. Ce problème pouvait causer un comportement d’exécution non défini si l’initialisation d’un membre dépendait d’un autre membre dans la liste déjà en cours d’initialisation. Dans l’exemple suivant, Visual Studio 2017 version 15.3 (avec **/Wall**) génère "l’avertissement C5038 : le membre de données 'A::y' sera initialisé après le membre de données 'A::x'" :

```cpp
struct A
{
    A(int a) : y(a), x(y) {} // Initialized in reverse, y reused
    int x;
    int y;
};
```

Pour résoudre le problème, réorganisez la liste d’initialiseurs afin d’avoir le même ordre que dans les déclarations. Un avertissement similaire est déclenché lorsqu’un ou les deux initialiseurs se réfèrent aux membres de classe de base.

Cet avertissement est désactivé par défaut et affecte uniquement le code compilé avec **/Wall**.

## <a name="update_155"></a>Correctifs de bogues et autres changements de comportement dans 15,5

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

```Output
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

```Output
warning C4843: 'int (&)[1]': An exception handler of reference to array or function type is unreachable, use 'int*' instead
warning C4843: 'void (__cdecl &)(void)': An exception handler of reference to array or function type is unreachable, use 'void (__cdecl*)(void)' instead
```

Le code suivant permet d’éviter cette erreur :

```cpp
catch (int (*)[1]) {}
```

### <a name="tr1"></a> L’espace de noms `std::tr1` est déprécié

L’espace de noms `std::tr1` non standard est désormais marqué comme déprécié dans les deux modes C++14 et C++17. Dans Visual Studio 2017 version 15.5, le code suivant génère l’erreur C4996 :

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

```Output
warning C4996: 'std::tr1': warning STL4002: The non-standard std::tr1 namespace and TR1-only machinery are deprecated and will be REMOVED. You can define _SILENCE_TR1_NAMESPACE_DEPRECATION_WARNING to acknowledge that you have received this warning.
```

Pour corriger cette erreur, supprimez la référence à l’espace de noms `tr1` :

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

### <a name="annex_d"></a>Les fonctionnalités de la bibliothèque standard dans l’annexe D sont marquées comme dépréciées

Quand le commutateur de compilateur en mode **/std:c++17** est défini, presque toutes les fonctionnalités de la bibliothèque standard listées dans l’annexe D sont marquées comme dépréciées.

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

```Output
warning C4996: 'std::iterator<std::random_access_iterator_tag,int,ptrdiff_t,_Ty*,_Ty &>::pointer': warning STL4015: The std::iterator class template (used as a base class to provide typedefs) is deprecated in C++17. (The <iterator> header is NOT deprecated.) The C++ standard has never required user-defined iterators to derive from std::iterator. To fix this warning, stop deriving from std::iterator and start providing publicly accessible typedefs named iterator_category, value_type, difference_type, pointer, and reference. Note that value_type is required to be non-const, even for constant iterators. You can define _SILENCE_CXX17_ITERATOR_BASE_CLASS_DEPRECATION_WARNING or _SILENCE_ALL_CXX17_DEPRECATION_WARNINGS to acknowledge that you have received this warning.
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

```Output
warning C4189: 's': local variable is initialized but not referenced
```

Pour corriger cette erreur, supprimez la variable inutilisée.

### <a name="single-line-comments"></a>Commentaires à ligne unique

Dans Visual Studio 2017 version 15.5, les avertissements C4001 et C4179 ne sont plus générés par le compilateur C. Auparavant, ils étaient uniquement générés quand le commutateur du compilateur **/Za** était défini.  Ces avertissements ne sont plus utiles, car les commentaires sur une seule ligne sont intégrés à la norme C depuis la version C99.

```cpp
/* C only */
#pragma warning(disable:4001) //C4619
#pragma warning(disable:4179)
// single line comment
//* single line comment */
```

```Output
warning C4619: #pragma warning: there is no warning number '4001'
```

Si le code n’a pas besoin d’offrir une compatibilité descendante, vous pouvez éviter la génération des avertissements en supprimant C4001 et C4179. Si le code doit offrir une compatibilité descendante, supprimez uniquement C4619.

```C

/* C only */

#pragma warning(disable:4619)
#pragma warning(disable:4001)
#pragma warning(disable:4179)

// single line comment
/* single line comment */
```

### <a name="__declspec-attributes-with-extern-c-linkage"></a>Attributs `__declspec` avec une liaison `extern "C"`

Dans les versions antérieures de Visual Studio, le compilateur ignorait les attributs `__declspec(...)` quand `__declspec(...)` était appliqué avant la spécification de la liaison `extern "C"`. Ce comportement provoquait la génération de code de façon inattendue pour l’utilisateur, avec un impact possible sur l’exécution. L’avertissement, ajouté dans Visual Studio 2017 version 15.3, était désactivé par défaut. Dans Visual Studio 2017 version 15.5, l’avertissement est activé par défaut.

```cpp
__declspec(noinline) extern "C" HRESULT __stdcall //C4768
```

```Output
warning C4768: __declspec attributes before linkage specification are ignored
```

Pour corriger cette erreur, ajoutez la spécification de liaison avant l’attribut __declspec :

```cpp
extern "C" __declspec(noinline) HRESULT __stdcall
```

Le nouvel avertissement C4768 ci-dessous est généré sur certains en-têtes Windows SDK fournis avec Visual Studio 2017 version 15.3 ou antérieure (par exemple, dans la version 10.0.15063.0, appelée RS2 SDK). Les versions ultérieures des en-têtes Windows SDK (en particulier, ShlObj.h et ShlObj_core.h) ont été corrigées pour ne plus générer cet avertissement. Si vous voyez cet avertissement généré par les en-têtes Windows SDK, effectuez les actions suivantes :

1. Installez le dernier Windows SDK, fourni avec Visual Studio 2017 version 15.5.

1. Désactivez l’avertissement pour l’élément #include de l’instruction d’en-tête Windows SDK :

```cpp
   #pragma warning (push)
   #pragma warning(disable:4768)
   #include <shlobj.h>
   #pragma warning (pop)
   ```

### <a name="extern_linkage"></a>Liaison extern constexpr

Dans les versions antérieures de Visual Studio, le compilateur a toujours donné une liaison interne de variable **constexpr** même quand la variable était marquée comme **extern**. Dans Visual Studio 2017 version 15.5, un nouveau commutateur de compilateur ( **/Zc:externConstexpr**) active le comportement correct de conformité aux normes. Cela deviendra le comportement par défaut.

```cpp
extern constexpr int x = 10;
```

```Output
error LNK2005: "int const x" already defined
```

Si un fichier d’en-tête contient une variable **extern constexpr**, il doit être marqué `__declspec(selectany)` pour que ses déclarations dupliquées soient correctement combinées :

```cpp
extern constexpr __declspec(selectany) int x = 10;
```

### <a name="typeid-cant-be-used-on-incomplete-class-type"></a>**typeid** ne peut pas être utilisé sur un type de classe incomplet

Dans les versions antérieures de Visual Studio, le compilateur autorisait à tort le code suivant, ce qui pouvait produire des informations de type incorrectes. Dans Visual Studio 2017 version 15.5, le compilateur génère une erreur :

```cpp
#include <typeinfo>

struct S;

void f() { typeid(S); } //C2027 in 15.5
```

```Output
error C2027: use of undefined type 'S'
```

### <a name="stdis_convertible-target-type"></a>Type cible `std::is_convertible`

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

### <a name="noexcept_removal"></a>Suppression des spécifications d’exceptions dynamiques et **noexcept**

En C++ 17, `throw()` est un alias pour **noexcept**, `throw(<type list>)` et `throw(...)` sont supprimés, et certains types peuvent inclure **noexcept**. Ces changements entraînent parfois des problèmes de compatibilité avec le code conforme à C++14 ou une version antérieure. Le commutateur **/Zc : noexceptTypes-** peut être utilisé pour revenir à la version c++ 14 de **nosauf** en mode c++ 17 en général. Cela vous permet de mettre à jour votre code source pour le rendre conforme à C++17 sans pour autant avoir à réécrire tout votre code `throw()`.

Avec le nouvel avertissement C5043, le compilateur diagnostique également maintenant davantage de spécifications d’exceptions incompatibles dans les déclarations en mode C++17 ou avec [/permissive-](../build/reference/permissive-standards-conformance.md).

Le code suivant génère les avertissements C5043 et C5040 dans Visual Studio 2017 version 15.5 quand le commutateur **/std:c++17** est défini :

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

Pour supprimer les erreurs tout en utilisant **/std : c++ 17**, ajoutez le commutateur **/Zc : noexceptTypes-** à la ligne de commande, ou mettez à jour votre code pour utiliser **noexcept**, comme indiqué dans l’exemple suivant :

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

Les membres de données static constexpr sont désormais implicitement inline, ce qui signifie que leur déclaration dans une classe correspond maintenant à leur définition. L’utilisation d’une définition hors ligne pour un membre de données static constexpr est redondante et est donc maintenant dépréciée. Dans Visual Studio 2017 version 15.5, quand le commutateur **/std:c++17** est défini, le code suivant génère désormais l’avertissement C5041 *'size' : la définition hors ligne du membre de données statique constexpr n’est pas nécessaire et est dépréciée en C++17* :

```cpp
struct X {
    static constexpr int size = 3;
};
const int X::size; // C5041
```

### <a name="extern-c-__declspec-warning-c4768-now-on-by-default"></a>L’avertissement C4768 `extern "C" __declspec(...)` est maintenant activé par défaut

L’avertissement, ajouté dans Visual Studio 2017 version 15.3, était désactivé par défaut. Dans Visual Studio 2017 version 15.5, l’avertissement est activé par défaut. Pour plus d’informations, consultez [Nouvel avertissement sur les \_\_attributs declspec](#declspec).

### <a name="defaulted-functions-and-__declspecnothrow"></a>Fonctions utilisées par défaut et `__declspec(nothrow)`

Auparavant, le compilateur autorisait la déclaration de fonctions par défaut à l’aide de `__declspec(nothrow)` quand les fonctions de base/membres correspondantes autorisaient les exceptions. Ce comportement non conforme à la norme C++ peut entraîner un comportement inattendu au moment de l’exécution. La norme exige que ces fonctions soient marquées comme supprimées en cas de non-correspondance d’une spécification d’exception.  En mode **/std:c++17**, le code suivant déclenche l’avertissement C2280 *Tentative de référencement d’une fonction supprimée. La fonction a été supprimée implicitement, car la spécification d’exception explicite est incompatible avec la spécification de déclaration implicite.*

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
        // ...
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

### <a name="noexcept-and-partial-specializations"></a>spécialisations **noexcept** et partial

Avec **noexcept** dans le système de type, les spécialisations partielles pour la correspondance de types « pouvant être appelés » particuliers peuvent ne pas réussir à compiler ou à choisir le modèle principal en raison d’une spécialisation partielle manquante pour les pointeurs vers les fonctions noexcept.

Dans ce cas, vous devrez peut-être ajouter des spécialisations partielles supplémentaires pour gérer les pointeurs de fonction **noexcept** et les pointeurs **noexcept** aux fonctions membres. Ces surcharges sont uniquement autorisées en mode **/std:c++17**. Si vous devez garantir la compatibilité descendante avec C++14 et que votre code est destiné à être utilisé par d’autres personnes, vous devez protéger ces nouvelles surcharges à l’intérieur de directives `#ifdef`. Si votre code fait partie d’un module autonome, au lieu d’utiliser des protections `#ifdef`, vous pouvez simplement compiler le code avec le commutateur **/Zc:noexceptTypes-** .

Le code suivant se compile correctement en mode **/std:c++14**, mais échoue en mode **/std:c++17** avec "l’erreur C2027 : utilisation du type non défini 'A\<T>'":

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

Le code suivant se compile correctement en mode **/std:c++17**, car le compilateur choisit la nouvelle spécialisation partielle `A<void (*)() noexcept>` :

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

## <a name="update_157"></a>Correctifs de bogues et autres changements de comportement dans 15,7

### <a name="c17-default-argument-in-the-primary-class-template"></a>C++17 : Argument par défaut dans le modèle de classe primaire

Ce changement de comportement est une condition préalable pour la [Déduction d’arguments de modèle pour les modèles de classe - P0091R3](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0091r3.html).

Auparavant, le compilateur ignorait l’argument par défaut dans le modèle de classe primaire :

```cpp
template<typename T>
struct S {
    void f(int = 0);
};

template<typename T>
void S<T>::f(int = 0) {} // Re-definition necessary
```

Dans Visual Studio 2017 version 15.7, en mode **/std:c++17**, l’argument par défaut n’est pas ignoré :

```cpp
template<typename T>
struct S {
    void f(int = 0);
};

template<typename T>
void S<T>::f(int) {} // Default argument is used
```

### <a name="dependent-name-resolution"></a>Résolution de noms indépendante

Ce changement de comportement est une condition préalable pour la [Déduction d’arguments de modèle pour les modèles de classe - P0091R3](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0091r3.html).

Dans l’exemple suivant, le compilateur dans Visual Studio 15.6 et antérieur résout `D::type` en `B<T>::type` dans le modèle de classe primaire.

```cpp
template<typename T>
struct B {
    using type = T;
};

template<typename T>
struct D : B<T*> {
    using type = B<T*>::type;
};
```

Visual Studio 2017 version 15,7, en mode **/std : c++ 17** , requiert le mot clé**TypeName** dans l’instruction **using** dans D. Sans**TypeName**, le compilateur génère un avertissement C4346 : 'B<T>::type' : le nom dépendant n’est pas un type* et erreur C2061 : *erreur de syntaxe : 'type' d’identificateur* :

```cpp
template<typename T>
struct B {
    using type = T;
};

template<typename T>
struct D : B<T*> {
    using type = typename B<T*>::type;
};
```

### <a name="c17-nodiscard-attribute---warning-level-increase"></a>C++17 - Attribut `[[nodiscard]]` - élévation du niveau d’avertissement

Dans Visual Studio 2017 version 15.7, en mode **/std:c++17**, le niveau d’avertissement de C4834 (« abandon de la valeur de retour de la fonction ayant l’attribut 'nodiscard' ») passe de W3 à W1. Vous pouvez désactiver l’avertissement avec un cast en **void**ou en passant **/WD : 4834** au compilateur

```cpp
[[nodiscard]] int f() { return 0; }

int main() {
    f(); // warning: discarding return value
         // of function with 'nodiscard'
}
```

### <a name="variadic-template-constructor-base-class-initialization-list"></a>Liste d’initialisation de classe de base du constructeur de modèle variadique

Dans les éditions précédentes de Visual Studio, une liste d’initialisation de classe de base du constructeur de modèle variadique dont des arguments de modèle étaient manquants était autorisée par erreur sans signaler d’erreur. Dans Visual Studio 2017 version 15.7, une erreur de compilateur est générée.

L’exemple de code suivant dans Visual Studio 2017 version 15.7 déclenche l’*erreur C2614 : D\<int> : Initialisation de membre non conforme : 'B' n’est ni une base ni un membre*

```cpp
template<typename T>
struct B {};

template<typename T>
struct D : B<T>
{

    template<typename ...C>
    D() : B() {} // C2614. Missing template arguments to B.
};

D<int> d;
```

Pour corriger l’erreur, remplacez l’expression B() par B\<T>().

### <a name="constexpr-aggregate-initialization"></a>initialisation d’agrégats **constexpr**

Les versions précédentes du C++ compilateur géraient de manière incorrecte l’initialisation d’agrégats **constexpr** ; Il a accepté un code non valide dans lequel Aggregate-init-List avait trop d’éléments et produit un CodeGen incorrect pour celui-ci. Le code suivant en est un exemple :

```cpp
#include <array>
struct X {
    unsigned short a;
    unsigned char b;
};

int main() {
    constexpr std::array<X, 2> xs = {
        { 1, 2 },
        { 3, 4 }
    };
    return 0;
}
```

Dans Visual Studio 2017 version 15.7 mise à jour 3 et ultérieures, l’exemple précédent génère désormais l’erreur *C2078 initialiseurs trop nombreux*. L’exemple de code suivant montre corriger le code. Lors de l’initialisation d’un `std::array` avec nested brace-init-lists, attribuez au tableau interne son propre braced-list :

```cpp
#include <array>
struct X {
    unsigned short a;
    unsigned char b;
};

int main() {
    constexpr std::array<X, 2> xs = {{ // note double braces
        { 1, 2 },
        { 3, 4 }
    }}; // note double braces
    return 0;
}
```

## <a name="update_158"></a>Correctifs de bogues et modifications de comportement dans 15,8

Les modifications apportées au compilateur dans Visual Studio 2017 version 15.8 appartiennent toutes à la catégorie des correctifs de bogues et des changements de comportement. Elles sont répertoriées ci-dessous :

###<a name="typename-on-unqualified-identifiers"></a>**TypeName** sur les identificateurs non qualifiés

En mode [/permissive-](../build/reference/permissive-standards-conformance.md) , les mots clés**TypeName** paraparasites sur les identificateurs non qualifiés dans les définitions de modèle d’alias ne sont plus acceptés par le compilateur. Le code suivant génère désormais l’erreur C7511 *'T' : le mot clé 'typename' doit être suivi d’un nom qualifié* :

```cpp
template <typename T>
using  X = typename T;
```

Pour corriger cette erreur, remplacez la deuxième ligne par `using  X = T;`.

### <a name="__declspec-on-right-side-of-alias-template-definitions"></a>`__declspec()` dans la partie droite des définitions de modèle d’alias

[__declspec](../cpp/declspec.md) n’est plus autorisé dans la partie droite d’une définition de modèle d’alias. Ce code était précédemment accepté mais ignoré par le complètement, aucun avertissement de dépréciation n’était donc généré quand l’alias était utilisé.

Vous pouvez utiliser l’attribut C++ standard [\[\[deprecated\]\]](../cpp/attributes.md) à la place. Celui-ci sera pris en compte à compter de Visual Studio 2017 version 15.6. Le code suivant génère désormais l’erreur C2760 *erreur de syntaxe : jeton inattendu '__declspec', attendu 'type specifier'* :

```cpp
template <typename T>
using X = __declspec(deprecated("msg")) T;
```

Pour corriger cette erreur, remplacez le code par ce qui suit (attribut placé avant le signe '=' de la définition d’alias) :

```cpp
template <typename T>
using  X [[deprecated("msg")]] = T;
```

### <a name="two-phase-name-lookup-diagnostics"></a>Diagnostics de la recherche de nom en deux phases

La recherche de nom en deux phases nécessite que les noms non dépendants utilisés dans les corps de modèle soient visibles par le modèle au moment de la définition. Avant, le compilateur Microsoft C++ ne procédait pas à la recherche d’un nom introuvable avant l’instanciation. Il exige désormais que les noms non dépendants soient liés dans le corps du modèle.

Cela peut notamment se manifester par une recherche dans les classes de base dépendantes. Le compilateur autorisait précédemment l’utilisation de noms définis dans des classes de base dépendantes, car ils faisaient l’objet d’une recherche au moment de l’instanciation (une fois tous les types résolus). Ce code est désormais traité comme une erreur. Dans ces cas, vous pouvez forcer la recherche de la variable au moment de l’instanciation en la qualifiant avec le type de classe de base ou en la rendant dépendante, par exemple en ajoutant un pointeur `this->`.

Dans le mode [/permissive-](../build/reference/permissive-standards-conformance.md), le code suivant génère désormais l’erreur C3861 *'base_value' : identificateur introuvable* :

```cpp
template <class T>
struct Base {
    int base_value = 42;
};

template <class T>
struct S : Base<T> {
    int f() {
        return base_value;
    }
};
```

Pour corriger cette erreur, remplacez l’instruction `return` par `return this->base_value;`.

**Remarque :** Dans la bibliothèque python Boost, il a existé pendant longtemps une solution de contournement spécifique à MSVC pour une déclaration anticipée de modèle dans [unwind_type.hpp](https://github.com/boostorg/python/blame/develop/include/boost/python/detail/unwind_type.hpp). Sous le mode [/permissive-](../build/reference/permissive-standards-conformance.md) à partir de Visual Studio 2017 version 15.8 (_MSC_VER=1915), le compilateur MSVC effectue la recherche de nom dépendante d’un argument (ADL) correctement et est cohérent avec d’autres compilateurs, rendant cette solution de contournement inutile. Afin d’éviter l’erreur *C3861: 'unwind_type': identificateur introuvable*, consultez [PR 229](https://github.com/boostorg/python/pull/229) dans le référentiel Boost pour mettre à jour le fichier d’en-tête. Nous avons déjà corrigé le package Boost [vcpkg](../build/vcpkg.md), donc si vous obtenez ou mettez à niveau vos sources Boost à partir de vcpkg, il est inutile d’appliquer le correctif séparément.

### <a name="forward-declarations-and-definitions-in-namespace-std"></a>définitions et déclarations anticipées dans l’espace de noms `std`

La norme C++ ne permet pas à un utilisateur d’ajouter des définitions ou des déclarations anticipées dans l’espace de noms `std`. L’ajout de définitions ou de déclarations à l’espace de noms `std` ou à un espace de noms dans l’espace de noms `std` donne désormais lieu à un comportement non défini.

Il est prévu que Microsoft affecte la définition de certains types de bibliothèque standard à un autre emplacement. Ce changement entraînera l’arrêt de tout code existant qui ajoute des déclarations anticipées à l’espace de noms `std`. Un nouvel avertissement, C4643, vous aide à identifier de tels problèmes liés la source. Cet avertissement est activé dans le mode **/default** (il est désactivé par défaut). Il impacte les programmes compilés avec **/Wall** ou **/WX**.

Le code suivant génère maintenant l’erreur C4643 : *La déclaration anticipée de 'vector' dans l’espace de noms std n’est pas autorisée par la norme C++* .

```cpp
namespace std {
    template<typename T> class vector;
}
```

Pour corriger cette erreur, utilisez une directive **include** plutôt qu’une déclaration anticipée :

```cpp
#include <vector>
```

### <a name="constructors-that-delegate-to-themselves"></a>Constructeurs déléguant à eux-mêmes

La norme C++ suggère qu’un compilateur doit émettre un diagnostic quand un constructeur de délégation délègue à lui-même. Le compilateur Microsoft C++ en mode [/std:c++17](../build/reference/std-specify-language-standard-version.md) et [/std:c++latest](../build/reference/std-specify-language-standard-version.md) génère désormais l’erreur C7535 : *'X::X': le constructeur de délégation s’appelle lui-même*.

Sans cette erreur, la compilation du programme suivant aboutit, mais une boucle infinie est générée :

```cpp
class X {
public:
    X(int, int);
    X(int v) : X(v){}
};
```

Pour éviter la boucle infinie, déléguez à un autre constructeur :

```cpp
class X {
public:

    X(int, int);
    X(int v) : X(v, 0) {}
};
```

### <a name="offsetof-with-constant-expressions"></a>`offsetof` avec expressions constantes

[offsetof](../c-runtime-library/reference/offsetof-macro.md) est habituellement implémenté à l’aide d’une macro qui nécessite un [reinterpret_cast](../cpp/reinterpret-cast-operator.md). Cette utilisation n’est pas conforme dans les contextes nécessitant une expression constante, le compilateur Microsoft C++ l’a toujours autorisée. La macro `offsetof` fournie dans le cadre de la bibliothèque standard utilise correctement une fonction intrinsèque du compilateur ( **__builtin_offsetof**), mais de nombreuses personnes utilisent l’astuce de la macro pour définir leur propre `offsetof`.

Dans Visual Studio 2017 version 15.8, le compilateur contraint les zones dans lesquelles ces opérateurs `reinterpret_cast` peuvent apparaître dans le mode par défaut pour améliorer la conformité du code au comportement C++ standard. Sous [/permissive-](../build/reference/permissive-standards-conformance.md), les contraintes sont encore plus strictes. L’utilisation du résultat d’un `offsetof` dans les emplacements qui nécessitent des expressions constantes peut générer du code qui émet l’avertissement C4644 *utilisation non standard du modèle offsetof de type macro dans les expressions constantes ; utilisez plutôt l’offsetof défini dans la bibliothèque standard C++* ou C2975 *argument template non valide, expression constante évaluée au moment de la compilation attendue*.

Le code suivant génère l’erreur C4644 dans les modes **/default** et **/std:c++17**, et l’erreur C2975 dans le mode [/permissive-](../build/reference/permissive-standards-conformance.md) :

```cpp
struct Data {
    int x;
};

// Common pattern of user-defined offsetof
#define MY_OFFSET(T, m) (unsigned long long)(&(((T*)nullptr)->m))

int main()

{
    switch (0) {
    case MY_OFFSET(Data, x): return 0;
    default: return 1;
    }
}
```

Pour corriger cette erreur, utilisez `offsetof` tel que défini par le biais de \<cstddef> :

```cpp
#include <cstddef>

struct Data {
    int x;
};

int main()
{
    switch (0) {
    case offsetof(Data, x): return 0;
    default: return 1;
    }
}
```

### <a name="cv-qualifiers-on-base-classes-subject-to-pack-expansion"></a>qualificateurs cv sur les classes de base soumises à une expansion de pack

Les versions précédentes du compilateur Microsoft C++ ne détectaient pas la présence de qualificateurs cv dans une classe de base si celle-ci était également soumise à une expansion de pack.

Dans Visual Studio 2017 version 15.8, dans le mode [/permissive-](../build/reference/permissive-standards-conformance.md), le code suivant génère l’erreur C3770 *'const S' : n’est pas une classe de base valide* :

```cpp
template<typename... T>
class X : public T... { };

class S { };

int main()
{
    X<const S> x;
}
```

### <a name="template-keyword-and-nested-name-specifiers"></a>mot clé **template** et spécificateurs-nom imbriqués

En mode [/permissive-](../build/reference/permissive-standards-conformance.md) , le compilateur requiert désormais que le mot clé **template** précède un template-Name lorsqu’il vient après un spécificateur-Name-Name-specifier dépendant.

Le code suivant dans le mode [/permissive-](../build/reference/permissive-standards-conformance.md) génère désormais l’erreur C7510 *'example' : un nom de modèle dépendant doit être précédé de 'template'. Remarque : voir la référence à l’instanciation du modèle de classe 'X<T>' en cours de compilation* :

```cpp
template<typename T> struct Base
{
    template<class U> void example() {}
};

template<typename T>
struct X : Base<T>
{
    void example()
    {
        Base<T>::example<int>();
    }
};
```

Pour corriger l’erreur, ajoutez le mot clé **template** à l’instruction `Base<T>::example<int>();`, comme indiqué dans l’exemple suivant :

```cpp
template<typename T> struct Base
{
    template<class U> void example() {}
};

template<typename T>
struct X : Base<T>
{
    void example()
    {
        // Add template keyword here:
        Base<T>::template example<int>();
    }
};
```

## <a name="update_159"></a>Correctifs de bogues et modifications de comportement dans 15,9

### <a name="identifiers-in-member-alias-templates"></a>Identificateurs dans les modèles d’alias de membre

Un identificateur utilisé dans une définition de modèle d’alias de membre doit être déclaré avant toute utilisation.

Dans les versions précédentes du compilateur, le code suivant était autorisé :

```cpp
template <typename... Ts>
struct A
{
  public:
    template <typename U>
    using from_template_t = decltype(from_template(A<U>{}));

  private:
    template <template <typename...> typename Type, typename... Args>
    static constexpr A<Args...> from_template(A<Type<Args...>>);
};

A<>::from_template_t<A<int>> a;
```

Dans Visual Studio 2017 version 15.9, en mode [/permissive-](../build/reference/permissive-standards-conformance.md), le compilateur génère C3861 : *'from_template' : identificateur introuvable*.

Pour corriger cette erreur, déclarez `from_template` avant `from_template_t`.

### <a name="modules-changes"></a>Changements apportés aux modules

Dans Visual Studio 2017 version 15.9, le compilateur génère C5050 chaque fois que les options de ligne de commande pour les modules ne sont pas cohérentes entre la partie création et la partie consommation du module. L’exemple suivant présente deux problèmes :

- Dans la partie consommation (main.cpp), l’option **/EHsc** n’est pas spécifiée.

- La version C++ est **/std:c++17** dans la partie création et **/std:c++14** dans la partie consommation.

```cmd
cl /EHsc /std:c++17 m.ixx /experimental:module
cl /experimental:module /module:reference m.ifc main.cpp /std:c++14
```

Le compilateur génère l’avertissement C5050 pour ces deux cas : *avertissement C5050 : Environnement potentiellement incompatible durant l’importation du module 'm' : incompatibilité des versions C++.  Version actuelle "201402", version du module "201703"* .

Le compilateur génère aussi C7536 chaque fois que le fichier .ifc est falsifié. L’en-tête de l’interface de module contient un hachage SHA2 du contenu situé en dessous. Lors de l’importation, le fichier .ifc est haché de la même façon puis comparé au hachage fourni dans l’en-tête. S’ils ne correspondent pas, l’erreur C7536 est générée : *ifc failed integrity checks.  SHA2 attendu : '66d5c8154df0c71d4cab7665bab4a125c7ce5cb9a401a4d8b461b706ddd771c6'* .

### <a name="partial-ordering-involving-aliases-and-non-deduced-contexts"></a>Classement partiel impliquant des alias et des contextes non déduits

Les implémentations des règles de classement partiel impliquant des alias dans des contextes non déduits font l’objet de divergences. Dans l’exemple suivant, GCC et le compilateur Microsoft C++ (en mode [/permissive-](../build/reference/permissive-standards-conformance.md)) génèrent une erreur, alors que Clang accepte le code.

```cpp
#include <utility>
using size_t = std::size_t;

template <typename T>
struct A {};
template <size_t, size_t>
struct AlignedBuffer {};
template <size_t len>
using AlignedStorage = AlignedBuffer<len, 4>;

template <class T, class Alloc>
int f(Alloc &alloc, const AlignedStorage<T::size> &buffer)
{
    return 1;
}

template <class T, class Alloc>
int f(A<Alloc> &alloc, const AlignedStorage<T::size> &buffer)
{
    return 2;
}

struct Alloc
{
    static constexpr size_t size = 10;
};

int main()
{
    A<void> a;
    AlignedStorage<Alloc::size> buf;
    if (f<Alloc>(a, buf) != 2)
    {
        return 1;
    }

    return 0;
}
```

L’exemple précédent génère C2668 :

```Output
partial_alias.cpp(32): error C2668: 'f': ambiguous call to overloaded function
partial_alias.cpp(18): note: could be 'int f<Alloc,void>(A<void> &,const AlignedBuffer<10,4> &)'
partial_alias.cpp(12): note: or       'int f<Alloc,A<void>>(Alloc &,const AlignedBuffer<10,4> &)'
        with
        [
            Alloc=A<void>
        ]
partial_alias.cpp(32): note: while trying to match the argument list '(A<void>, AlignedBuffer<10,4>)'
```

La divergence de l’implémentation existe en raison d’une régression dans la formulation de la norme C++. La résolution du problème de base 2235 a supprimé le texte qui permettait le classement de ces surcharges. La norme C++ actuelle ne fournissant pas de mécanisme pour classer partiellement ces fonctions, elles sont considérées comme ambiguës.

Pour résoudre ce problème, nous vous recommandons de ne pas recourir au classement partiel. À la place, utilisez SFINAE pour supprimer des surcharges particulières. Dans l’exemple suivant, nous utilisons une classe d’assistance `IsA` pour supprimer la première surcharge quand `Alloc` est une spécialisation de `A` :

```cpp
#include <utility>
using size_t = std::size_t;

template <typename T>
struct A {};
template <size_t, size_t>
struct AlignedBuffer {};
template <size_t len>
using AlignedStorage = AlignedBuffer<len, 4>;

template <typename T> struct IsA : std::false_type {};
template <typename T> struct IsA<A<T>> : std::true_type {};

template <class T, class Alloc, typename = std::enable_if_t<!IsA<Alloc>::value>>
int f(Alloc &alloc, const AlignedStorage<T::size> &buffer)
{
    return 1;
}

template <class T, class Alloc>
int f(A<Alloc> &alloc, const AlignedStorage<T::size> &buffer)
{
    return 2;
}

struct Alloc
{
    static constexpr size_t size = 10;
};

int main()
{
    A<void> a;
    AlignedStorage<Alloc::size> buf;
    if (f<Alloc>(a, buf) != 2)
    {
        return 1;
    }

    return 0;
}
```

### <a name="illegal-expressions-and-non-literal-types-in-templated-function-definitions"></a>Expressions non conformes et types non littéraux dans les définitions de fonctions basées sur un modèle

Les expressions non conformes et les types non littéraux sont maintenant correctement diagnostiqués dans les définitions de fonctions basées sur un modèle qui sont explicitement spécialisées. Auparavant, ces erreurs n’étaient pas émises pour la définition de fonction. Cependant, l’expression non conforme ou le type non littéral étaient néanmoins diagnostiqués s’ils étaient évalués dans le cadre d’une expression de constante.

Dans les versions précédentes de Visual Studio, le code suivant se compile sans avertissement :

```cpp
void g();

template<typename T>
struct S
{
    constexpr void f();
};
 
template<>
constexpr void S<int>::f()
{
    g(); // C3615 in 15.9
}
```

Dans Visual Studio 2017 version 15.9, le code génère cette erreur :

```Output
error C3615: constexpr function 'S<int>::f' cannot result in a constant expression.
note: failure was caused by call of undefined function or one not declared 'constexpr'
note: see usage of 'g'.
```

Pour éviter cette erreur, supprimez le qualificateur **constexpr** de l’instanciation explicite de la fonction `f()`.

::: moniker-end

::: moniker range="vs-2015"

## <a name="c-conformance-improvements-in-visual-studio-2015"></a>Améliorations de la conformité de C++ dans Visual Studio 2015

Pour obtenir la liste complète des améliorations de la conformité jusqu’à Visual Studio 2015 Update 3, consultez [Visual C++ What’s New 2003 through 2015](/cpp/porting/visual-cpp-what-s-new-2003-through-2015).

::: moniker-end

## <a name="see-also"></a>Voir aussi

[Conformité du langage Visual C++](../visual-cpp-language-conformance.md)
