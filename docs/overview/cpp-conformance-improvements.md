---
title: Améliorations de la conformité de C++
ms.date: 08/04/2020
description: Microsoft C++ dans Visual Studio arrive progressivement à une conformité totale avec la norme du langage C ++20.
ms.technology: cpp-language
ms.openlocfilehash: 3a0e21bf08fcf7861feedd3fd43666bd3768deee
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2020
ms.locfileid: "90042119"
---
# <a name="c-conformance-improvements-in-visual-studio"></a>Améliorations de la conformité de C++ dans Visual Studio

Microsoft C++ apporte des améliorations de conformité et des correctifs de bogues avec chaque version. Cet article répertorie les améliorations apportées par version majeure, puis par version. Il répertorie également les principaux correctifs de bogues par version. Pour aller directement aux modifications apportées à une version spécifique, utilisez la liste **Dans cet article**.

::: moniker range="vs-2019"

## <a name="conformance-improvements-in-visual-studio-2019-rtw-version-160"></a><a name="improvements_160"></a> Améliorations de la conformité dans Visual Studio 2019 RTW (version 16,0)

Visual Studio 2019 RTW contient les améliorations de conformité, les correctifs de bogues et les modifications de comportement suivants dans le compilateur Microsoft C++ (MSVC)

**Remarque :** Les fonctionnalités c++ 20 seront mises à disposition en **`/std:c++latest`** mode jusqu’à ce que l’implémentation c++ 20 soit terminée pour le compilateur et IntelliSense. À ce moment-là, le **`/std:c++20`** mode du compilateur sera introduit.

### <a name="improved-modules-support-for-templates-and-error-detection"></a>Amélioration de la prise en charge des modules pour les modèles et la détection d’erreur

Les modules sont désormais officiellement dans la norme C++20. Une meilleure prise en charge a été ajoutée dans Visual Studio 2017 version 15.9. Pour plus d’informations, consultez [Better template support and error detection in C++ Modules with MSVC 2017 version 15.9](https://devblogs.microsoft.com/cppblog/better-template-support-and-error-detection-in-c-modules-with-msvc-2017-version-15-9/).

### <a name="modified-specification-of-aggregate-type"></a>Changement de spécification du type d’agrégat

La spécification d’un type d’agrégat a changé dans C++20 (consultez [Prohibit aggregates with user-declared constructors](https://wg21.link/p1008r1)). Dans Visual Studio 2019, sous **`/std:c++latest`** , une classe avec un constructeur déclaré par l’utilisateur (par exemple, y compris un constructeur déclaré `= default` ou `= delete` ) n’est pas un agrégat. Avant, seuls les constructeurs fournis par l’utilisateur empêchaient une classe d’être un agrégat. Ce changement ajoute des restrictions supplémentaires sur la façon dont ces types peuvent être initialisés.

Le code suivant se compile sans erreur dans Visual Studio 2017, mais génère des erreurs C2280 et C2440 dans Visual Studio 2019 sous **`/std:c++latest`** :

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

[P0515R3](https://wg21.link/p0515r3)C++20 introduit l’opérateur de comparaison trilatérale `<=>`, également appelé « opérateur vaisseau spatial ». Visual Studio 2019 en **`/std:c++latest`** mode introduit une prise en charge partielle de l’opérateur en déclenchant des erreurs pour la syntaxe qui est désormais interdite. Par exemple, le code suivant se compile sans erreur dans Visual Studio 2017, mais génère plusieurs erreurs dans Visual Studio 2019 sous **`/std:c++latest`** :

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

Avant, MSVC autorisait la liaison directe d’une référence d’un type avec des qualificateurs cv non correspondants sous le niveau supérieur. Cette liaison pouvait permettre la modification des données const supposément référencées par la référence. À présent, le compilateur crée une table temporaire, comme requis par la norme. Dans Visual Studio 2017, le code suivant se compile sans avertissement. Dans Visual Studio 2019, le compilateur déclenche l’avertissement C4172 : `<func:#1 "?PData@X@@QBEABQBXXZ"> returning address of local variable or temporary.` :

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

L’argument de **`reinterpret_cast`** n’est pas l’un des contextes dans lesquels l’adresse d’une fonction surchargée est autorisée. Le code suivant se compile sans erreur dans Visual Studio 2017, mais dans Visual Studio 2019, il génère l’erreur C2440 : `cannot convert from 'overloaded-function' to 'fp'` :

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

Dans C++14, les types de fermeture d’expression lambda ne sont pas littéraux. La conséquence principale de cette règle est qu’une expression lambda ne peut pas être assignée à une **`constexpr`** variable. Le code suivant se compile sans erreur dans Visual Studio 2017, mais dans Visual Studio 2019, il génère l’erreur C2127 : `'l': illegal initialization of 'constexpr' entity with a non-constant expression` :

```cpp
int main()
{
    constexpr auto l = [] {}; // C2127 in VS2019
}
```

Pour éviter cette erreur, supprimez le **`constexpr`** qualificateur ou remplacez le mode de conformité par **`/std:c++17`** .

### <a name="stdcreate_directory-failure-codes"></a>Codes d’échec `std::create_directory`

[P1164](https://wg21.link/p1164r1) implémenté depuis C++20 sans condition. Cela change `std::create_directory` pour vérifier si la cible était déjà un répertoire en échec. Avant, toutes les erreurs de type ERROR_ALREADY_EXISTS étaient converties en codes success-but-directory-not-created.

### `operator<<(std::ostream, nullptr_t)`

Conformément à [LWG 2221](https://cplusplus.github.io/LWG/issue2221), ajout de `operator<<(std::ostream, nullptr_t)` pour écrire nullptrs dans les flux.

### <a name="additional-parallel-algorithms"></a>Algorithmes parallèles supplémentaires

Nouvelles versions parallèles de `is_sorted`, `is_sorted_until`, `is_partitioned`, `set_difference`, `set_intersection`, `is_heap` et `is_heap_until`.

### <a name="atomic-initialization"></a>Initialisation atomique

Le [P0883 "Fixing atomic initialization"](https://wg21.link/p0883r1) change `std::atomic` pour l’initialiser avec la valeur du T contenu plutôt que de l’initialiser avec la valeur par défaut. Le correctif est activé lorsque vous utilisez Clang/LLVM avec la bibliothèque standard de Microsoft. Elle est actuellement désactivée pour le compilateur Microsoft C++, en guise de solution de contournement pour un bogue de **`constexpr`** traitement.

### <a name="remove_cvref-and-remove_cvref_t"></a>`remove_cvref` et `remove_cvref_t`

Caractéristiques de type `remove_cvref` et `remove_cvref_t` implémentées selon le [P0550](https://wg21.link/p0550r2). Cela supprime reference-ness et cv-qualification d’un type sans dégrader les fonctions et les tableaux en pointeurs (contrairement à `std::decay` et `std::decay_t`).

### <a name="feature-test-macros"></a>Macros Feature-test

[P0941R2 - macros de test de fonctionnalité](https://wg21.link/p0941r2) est terminé, avec la prise en charge de `__has_cpp_attribute`. Les macros de test de fonctionnalité sont prises en charge dans tous les modes standard.

### <a name="prohibit-aggregates-with-user-declared-constructors"></a>Interdire les agrégats avec les constructeurs déclarés par l’utilisateur

[C++20 P1008R1 - prohibiting aggregates with user-declared constructors](https://wg21.link/p1008r1) est terminé.

## <a name="conformance-improvements-in-161"></a><a name="improvements_161"></a> Améliorations de la conformité dans 16,1

### <a name="char8_t"></a>char8_t

[P0482r6](https://wg21.link/p0482r6). C++20 ajoute un nouveau type de caractère qui est utilisé pour représenter les unités de code UTF-8. Les littéraux de chaîne `u8` dans C++20 ont le type `const char8_t[N]` au lieu de `const char[N]`, ce qui était le cas auparavant. Des changements similaires ont été proposés pour la norme C dans [N2231](https://wg14.link/n2231). Des suggestions de **`char8_t`** Correction de compatibilité descendante sont fournies dans [P1423r3](https://wg21.link/p1423r3). Le compilateur Microsoft C++ ajoute la prise en charge de **`char8_t`** dans Visual Studio 2019 version 16,1 quand vous spécifiez l' **`/Zc:char8_t`** option de compilateur. À l’avenir, il sera pris en charge avec [`/std:c++latest`](../build/reference/std-specify-language-standard-version.md) , qui peut être rétabli en mode c++ 17 via **`/Zc:char8_t-`** . Le compilateur EDG qui alimente IntelliSense ne le prend pas encore en charge. Il se peut que vous rencontriez des erreurs IntelliSense inexistantes qui n’ont pas d’impact sur la compilation réelle.

#### <a name="example"></a>Exemple

```cpp
const char* s = u8"Hello"; // C++17
const char8_t* s = u8"Hello"; // C++20
```

### <a name="stdtype_identity-metafunction-and-stdidentity-function-object"></a>Métafonction std::type_identity et objet de fonction std::identity

[P0887R1 TYPE_IDENTITY](https://wg21.link/p0887r1). L’extension de modèle de classe `std::identity` dépréciée a été supprimée et remplacée par la métafonction `std::type_identity` et l’objet de fonction `std::identity` C++20. Les deux sont disponibles uniquement sous [`/std:c++latest`](../build/reference/std-specify-language-standard-version.md) .

L’exemple suivant génère l’avertissement de désapprobation C4996 pour `std::identity` (défini dans \<type_traits> ) dans Visual Studio 2017 :

```cpp
#include <type_traits>

using T = std::identity<int>::type;
T x, y = std::identity<T>{}(x);
int i = 42;
long j = std::identity<long>{}(i);
```

L’exemple suivant montre comment utiliser le nouveau `std::identity` (défini dans \<functional> ) avec le nouveau `std::type_identity` :

```cpp
#include <type_traits>
#include <functional>

using T = std::type_identity<int>::type;
T x, y = std::identity{}(x);
int i = 42;
long j = static_cast<long>(i);
```

### <a name="syntax-checks-for-generic-lambdas"></a>Vérifications syntaxiques pour les expressions lambda génériques

Le nouveau processeur lambda permet des vérifications syntaxiques en mode de conformité dans les expressions lambda génériques, sous [`/std:c++latest`](../build/reference/std-specify-language-standard-version.md) ou sous tout autre mode de langage avec **`/experimental:newLambdaProcessor`** .

Dans Visual Studio 2017, ce code se compile sans avertissements, mais dans Visual Studio 2019, il génère l’erreur C2760 `syntax error: unexpected token '\<id-expr>', expected 'id-expression'` :

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

[P0846R0](https://wg21.link/p0846r0) (c++ 20) capacité à rechercher des modèles de fonction via une recherche dépendante d’un argument pour les expressions d’appel de fonction avec des arguments template explicites. Requiert **`/std:c++latest`** .

### <a name="designated-initialization"></a>Initialisation désignée

[P0329R4](https://wg21.link/p0329r4) (c++ 20) une *initialisation désignée* permet de sélectionner des membres spécifiques dans l’initialisation d’agrégats à l’aide de la `Type t { .member = expr }` syntaxe. Requiert **`/std:c++latest`** .

### <a name="new-and-updated-standard-library-functions-c20"></a>Fonctions de bibliothèque standard nouvelles et mises à jour (C++20)

- `starts_with()` et `ends_with()` pour `basic_string` et `basic_string_view`.
- `contains()` pour les conteneurs associatifs.
- `remove()`, `remove_if()` et `unique()` pour `list` et `forward_list` retournent maintenant `size_type`.
- `shift_left()` et `shift_right()` ajoutés à \<algorithm>.

## <a name="conformance-improvements-in-162"></a><a name="improvements_162"></a> Améliorations de la conformité dans 16,2

### <a name="noexcept-constexpr-functions"></a>`noexcept``constexpr`fonctions

**`constexpr`** les fonctions ne sont plus considérées **`noexcept`** par défaut lorsqu’elles sont utilisées dans une expression constante. Ce changement de comportement provient de la résolution de [CWG 1351](https://wg21.link/cwg1351) et est activé dans [`/permissive-`](../build/reference/permissive-standards-conformance.md) . L’exemple suivant compile dans Visual Studio 2019 version 16,1 et les versions antérieures, mais produit C2338 dans Visual Studio 2019 version 16,2 :

```cpp
constexpr int f() { return 0; }

int main() {
    static_assert(noexcept(f()), "f should be noexcept"); // C2338 in 16.2
}
```

Pour corriger l’erreur, ajoutez l' **`noexcept`** expression à la déclaration de fonction :

```cpp
constexpr int f() noexcept { return 0; }

int main() {
    static_assert(noexcept(f()), "f should be noexcept");
}
```

### <a name="binary-expressions-with-different-enum-types"></a>Expressions binaires avec différents types ENUM

C++ 20 a déconseillé les conversions arithmétiques habituelles sur les opérandes, où :

- Un opérande est de type énumération, et

- l’autre est un type d’énumération différent ou un type à virgule flottante.

Pour plus d’informations, consultez [P1120R0](https://wg21.link/p1120r0).

Dans Visual Studio 2019 version 16,2 et versions ultérieures, le code suivant génère un avertissement de niveau 4 lorsque l' [`/std:c++latest`](../build/reference/std-specify-language-standard-version.md) option de compilateur est activée :

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

L’utilisation d’une opération binaire entre une énumération et un type à virgule flottante est désormais un avertissement lorsque l' [`/std:c++latest`](../build/reference/std-specify-language-standard-version.md) option de compilateur est activée :

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

Les comparaisons d’égalité et relationnelles entre deux opérandes de type tableau sont dépréciées en C++ 20 ([P1120R0](https://wg21.link/p1120r0)). En d’autres termes, une opération de comparaison entre deux tableaux (Nonobstant le rang et les similarités d’étendue) est désormais un avertissement. À compter de Visual Studio 2019 version 16,2, le code suivant génère C5056 : `operator '==': deprecated for array types` lorsque l' [`/std:c++latest`](../build/reference/std-specify-language-standard-version.md) option de compilateur est activée :

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

### <a name="effect-of-defining-spaceship-operator-on--and-"></a>Effet de la définition de l’opérateur d’espacement sur `==` et `!=`

Une définition de l’opérateur d’espacement ( **`<=>`** ) seul ne réécrit plus les expressions impliquant **`==`** ou **`!=`** sauf si l’opérateur d’espacement est marqué comme **`= default`** ([P1185R2](https://wg21.link/p1185r2)). L’exemple suivant compile dans Visual Studio 2019 RTW et la version 16,1, mais produit C2678 dans Visual Studio 2019 version 16,2 :

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

- \<charconv>`to_chars()`avec une précision fixe/scientifique. (La précision générale est actuellement planifiée pour 16,4.)
- [P0020R6](https://wg21.link/p0020r6): Atomic atomique, Atomic atomique \<float> \<double> , Atomic\<long double>
- [P0463R1](https://wg21.link/p0463r1): endian
- [P0482R6](https://wg21.link/p0482r6): prise en charge de la bibliothèque pour char8_t
- [P0600R1](https://wg21.link/p0600r1): [ \[ noignore]] pour la bibliothèque STL, partie 1
- [P0653R2](https://wg21.link/p0653r2): to_address ()
- [P0754R2](https://wg21.link/p0754r2): \<version>
- [P0771R1](https://wg21.link/p0771r1): Noexcept pour le constructeur de déplacement de std :: function

## <a name="conformance-improvements-in-visual-studio-2019-version-163"></a><a name="improvements_163"></a> Améliorations de la conformité dans Visual Studio 2019 version 16,3

### <a name="stream-extraction-operators-for-char-removed"></a>Opérateurs d’extraction de flux pour char * supprimés

Les opérateurs d’extraction de flux de pointeur vers des caractères ont été supprimés et remplacés par les opérateurs d’extraction pour les tableaux de caractères (par [P0487R1](https://wg21.link/p0487r1)). WG21 considère que les surcharges supprimées sont risquées. En [`/std:c++latest`](../build/reference/std-specify-language-standard-version.md) mode, l’exemple suivant génère désormais C2679 : `binary '>>': no operator found which takes a right-hand operand of type 'char*' (or there is no acceptable conversion)` :

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

### <a name="new-keywords-requires-and-concept"></a>Nouveaux mots clés `requires` et `concept`

De nouveaux mots clés **`requires`** et **`concept`** ont été ajoutés au compilateur Microsoft C++. Si vous essayez d’utiliser l’un ou l’autre comme identificateur en [`/std:c++latest`](../build/reference/std-specify-language-standard-version.md) mode, le compilateur déclenche l’opération C2059 : `syntax error` .

### <a name="constructors-as-type-names-disallowed"></a>Constructeurs en tant que noms de types interdits

Dans ce cas, le compilateur ne considère plus les noms de constructeurs comme des noms de classe injectés : lorsqu’ils apparaissent dans un nom qualifié après un alias d’une spécialisation de modèle de classe. Auparavant, les constructeurs étaient utilisables comme un nom de type pour déclarer d’autres entités. L’exemple suivant génère désormais C3646 : `'TotalDuration': unknown override specifier` :

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

### <a name="stricter-checking-of-extern-c-functions"></a>Contrôle plus strict des `extern "C"` fonctions

Si une **`extern "C"`** fonction a été déclarée dans des espaces de noms différents, les versions précédentes du compilateur Microsoft C++ n’ont pas vérifié si les déclarations étaient compatibles. À compter de Visual Studio 2019 version 16,3, le compilateur vérifie la compatibilité. En [`/permissive-`](../build/reference/permissive-standards-conformance.md) mode, le code suivant génère des erreurs C2371 `redefinition; different basic types` et C2733 `you cannot overload a function with C linkage` :

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

Pour éviter les erreurs dans l’exemple précédent, utilisez **`bool`** plutôt que de `BOOL` manière cohérente dans les deux déclarations de `f` .

### <a name="standard-library-improvements"></a>Améliorations de la bibliothèque standard

Les en-têtes non standard \<stdexcpt.h> et \<typeinfo.h> ont été supprimés. Le code qui les inclut doit plutôt inclure les en-têtes standard \<exception> et \<typeinfo> , respectivement.

## <a name="conformance-improvements-in-visual-studio-2019-version-164"></a><a name="improvements_164"></a> Améliorations de la conformité dans Visual Studio 2019 version 16,4

### <a name="better-enforcement-of-two-phase-name-lookup-for-qualified-ids-in-permissive-"></a>Meilleure mise en œuvre de la recherche de nom en deux phases pour les ID qualifiés dans `/permissive-`

La recherche de nom en deux phases nécessite que les noms non dépendants utilisés dans les corps de modèle soient visibles par le modèle au moment de la définition. Auparavant, ces noms peuvent avoir été trouvés lors de l’instanciation du modèle. Grâce à cette modification, il est plus facile d’écrire du code portable et conforme dans MSVC sous l' [`/permissive-`](../build/reference/permissive-standards-conformance.md) indicateur.

Dans Visual Studio 2019 version 16,4 avec l' **`/permissive-`**  indicateur défini, l’exemple suivant génère une erreur, car `N::f` n’est pas visible lorsque le `f<T>` modèle est défini :

```cpp
template <class T>
int f() {
    return N::f() + T{}; // error C2039: 'f': is not a member of 'N'
}

namespace N {
    int f() { return 42; }
}
```

En règle générale, cette erreur peut être corrigée en incluant des en-têtes manquants ou des fonctions ou variables de déclaration de redirection, comme indiqué dans l’exemple suivant :

```cpp
namespace N {
    int f();
}

template <class T>
int f() {
    return N::f() + T{};
}

namespace N {
    int f() { return 42; }
}
```

### <a name="implicit-conversion-of-integral-constant-expressions-to-null-pointer"></a>Conversion implicite d’expressions constantes intégrales en pointeur null

Le compilateur MSVC implémente désormais le [problème CWG 903](https://wg21.link/cwg903) en mode de conformité ( **`/permissive-`** ). Cette règle interdit la conversion implicite d’expressions constantes intégrales (à l’exception du littéral d’entier « 0 ») en constantes de pointeur null. L’exemple suivant produit l’C2440 en mode de conformité :

```cpp
int* f(bool* p) {
    p = false; // error C2440: '=': cannot convert from 'bool' to 'bool *'
    p = 0; // OK
    return false; // error C2440: 'return': cannot convert from 'bool' to 'int *'
}
```

Pour corriger l’erreur, utilisez à la **`nullptr`** place de **`false`** . Un littéral 0 est toujours autorisé :

```cpp
int* f(bool* p) {
    p = nullptr; // OK
    p = 0; // OK
    return nullptr; // OK
}
```

### <a name="standard-rules-for-types-of-integer-literals"></a>Règles standard pour les types de littéraux entiers

En mode conformité (activé par [`/permissive-`](../build/reference/permissive-standards-conformance.md) ), MSVC utilise les règles standard pour les types de littéraux entiers. Les littéraux décimaux trop grands pour être contenus dans un **`signed int`** type précédemment donné **`unsigned int`** . À présent, ces littéraux reçoivent le plus grand **`signed`** type d’entier suivant, **`long long`** . En outre, les littéraux dont le suffixe est trop grand pour tenir dans un **`signed`** type ont le même type **`unsigned long long`** .

Cette modification peut entraîner la génération de différents Diagnostics d’avertissement et des différences de comportement pour les opérations arithmétiques sur les littéraux.

L’exemple suivant illustre le nouveau comportement dans Visual Studio 2019 version 16,4. La `i` variable est désormais de type **`unsigned int`** . C’est la raison pour laquelle l’avertissement est déclenché. Les bits de poids fort de la variable `j` sont définis sur 0.

```cpp
void f(int r) {
    int i = 2964557531; // warning C4309: truncation of constant value
    long long j = 0x8000000000000000ll >> r; // literal is now unsigned, shift will fill high-order bits with 0
}
```

L’exemple suivant montre comment conserver l’ancien comportement et éviter la modification du comportement des avertissements et du Runtime :

```cpp
void f(int r) {
int i = 2964557531u; // OK
long long j = (long long)0x8000000000000000ll >> r; // shift will keep high-order bits
}
```

### <a name="function-parameters-that-shadow-template-parameters"></a>Paramètres de fonction qui occultent les paramètres de modèle

Le compilateur MSVC génère désormais une erreur lorsqu’un paramètre de fonction occulte un paramètre de modèle :

```cpp
template<typename T>
void f(T* buffer, int size, int& size_read);

template<typename T, int Size>
void f(T(&buffer)[Size], int& Size) // error C7576: declaration of 'Size' shadows a template parameter
{
    return f(buffer, Size, Size);
}
```

Pour corriger l’erreur, modifiez le nom de l’un des paramètres :

```cpp
template<typename T>
void f(T* buffer, int size, int& size_read);

template<typename T, int Size>
void f(T (&buffer)[Size], int& size_read)
{
    return f(buffer, Size, size_read);
}
```

### <a name="user-provided-specializations-of-type-traits"></a>Spécialisations fournies par l’utilisateur de traits de type

En conformité avec la sous-clause *meta. rqmts* de la norme, le compilateur MSVC génère désormais une erreur lorsqu’il trouve une spécialisation définie par l’utilisateur de l’un des modèles spécifiés `type_traits` dans l' `std` espace de noms. Sauf indication contraire, ces spécialisations entraînent un comportement indéfini. L’exemple suivant a un comportement indéfini, car il enfreint la règle et le **`static_assert`** échoue avec l’erreur C2338.

```cpp
#include <type_traits>
struct S;

template<>
struct std::is_fundamental<S> : std::true_type {};

static_assert(std::is_fundamental<S>::value, "fail");
```

Pour éviter cette erreur, définissez un struct qui hérite de la valeur par défaut `type_trait` et spécialisez-le comme suit :

```cpp
#include <type_traits>

struct S;

template<typename T>
struct my_is_fundamental : std::is_fundamental<T> {};

template<>
struct my_is_fundamental<S> : std::true_type { };

static_assert(my_is_fundamental<S>::value, "fail");
```

### <a name="changes-to-compiler-provided-comparison-operators"></a>Modifications apportées aux opérateurs de comparaison fournis par le compilateur

Le compilateur MSVC implémente désormais les modifications suivantes aux opérateurs de comparaison par [P1630R1](https://wg21.link/p1630r1) lorsque l' [`/std:c++latest`](../build/reference/std-specify-language-standard-version.md) option est activée :

Le compilateur ne réécrit plus les expressions à l’aide `operator==` de s’ils impliquent un type de retour qui n’est pas un **`bool`** . Le code suivant génère désormais l’erreur C2088 : `'!=': illegal for struct` :

```cpp
struct U {
    operator bool() const;
};

struct S {
    U operator==(const S&) const;
};

bool neq(const S& lhs, const S& rhs) {
    return lhs != rhs;
}
```

Pour éviter cette erreur, vous devez définir explicitement l’opérateur requis :

```cpp
struct U {
    operator bool() const;
};

struct S {
    U operator==(const S&) const;
    U operator!=(const S&) const;
};

bool neq(const S& lhs, const S& rhs) {
    return lhs != rhs;
}
```

Le compilateur ne définit plus d’opérateur de comparaison par défaut s’il est membre d’une classe de type Union. L’exemple suivant génère désormais une erreur C2120 : `'void' illegal with all types` :

```cpp
#include <compare>

union S {
    int a;
    char b;
    auto operator<=>(const S&) const = default;
};

bool lt(const S& lhs, const S& rhs) {
    return lhs < rhs;
}
```

Pour éviter cette erreur, définissez un corps pour l’opérateur :

```cpp
#include <compare>

union S {
    int a;
    char b;
    auto operator<=>(const S&) const { ... }
};

bool lt(const S& lhs, const S& rhs) {
    return lhs < rhs;
}
```

Le compilateur ne définit plus d’opérateur de comparaison par défaut si la classe contient un membre de référence. Le code suivant génère désormais l’erreur C2120 : `'void' illegal with all types` :

```cpp
#include <compare>

struct U {
    int& a;
    auto operator<=>(const U&) const = default;
};

bool lt(const U& lhs, const U& rhs) {
    return lhs < rhs;
}
```

Pour éviter cette erreur, définissez un corps pour l’opérateur :

```cpp
#include <compare>

struct U {
    int& a;
    auto operator<=>(const U&) const { ... };
};

bool lt(const U& lhs, const U& rhs) {
    return lhs < rhs;
}
```

## <a name="conformance-improvements-in-visual-studio-2019-version-165"></a><a name="improvements_165"></a> Améliorations de la conformité dans Visual Studio 2019 version 16,5

### <a name="explicit-specialization-declaration-without-an-initializer-isnt-a-definition"></a>Une déclaration de spécialisation explicite sans initialiseur n’est pas une définition

Sous `/permissive-` , MSVC applique désormais une règle standard selon laquelle les déclarations de spécialisation explicite sans initialiseurs ne sont pas des définitions. Auparavant, la déclaration serait considérée comme une définition avec un initialiseur par défaut. L’effet est observable au moment de la liaison, car un programme qui dépend de ce comportement peut maintenant avoir des symboles non résolus. Cet exemple génère désormais une erreur :

```cpp
template <typename> struct S {
    static int a;
};

// In permissive-, this declaration isn't a definition, and the program won't link.
template <> int S<char>::a;

int main() {
    return S<char>::a;
}
```

```Output
error LNK2019: unresolved external symbol "public: static int S<char>::a" (?a@?$S@D@@2HA) referenced in function _main
at link time.
```

Pour résoudre le problème, ajoutez un initialiseur :

```cpp
template <typename> struct S {
    static int a;
};

// Add an initializer for the declaration to be a definition.
template <> int S<char>::a{};

int main() {
    return S<char>::a;
}
```

### <a name="preprocessor-output-preserves-newlines"></a>La sortie du préprocesseur préserve les nouvelles lignes

Le préprocesseur expérimental préserve désormais les nouvelles lignes et l’espace blanc lors de l’utilisation de **`/P`** ou **`/E`** de **`/experimental:preprocessor`** .

Étant donné cet exemple de source,

```cpp
#define m()
line m(
) line
```

La sortie précédente de **`/E`** était :

```Output
line line
#line 2
```

La nouvelle sortie de **`/E`** est désormais :

```Output
line
 line
```

### <a name="import-and-module-keywords-are-context-dependent"></a>les mots clés’import’et’module’dépendent du contexte

Par P1857R1, les directives de préprocesseur d’importation et de module ont des restrictions supplémentaires sur leur syntaxe. Cet exemple n’est plus compilé :

```cpp
import // Invalid
m;
```

Il génère le message d’erreur suivant :

```Output
error C2146: syntax error: missing ';' before identifier 'm'
```

Pour résoudre le problème, conservez l’importation sur la même ligne :

```cpp
import m; // OK
```

### <a name="removal-of-stdweak_equality-and-stdstrong_equality"></a>Suppression de std :: weak_equality et std :: strong_equality

La fusion de P1959R0 requiert que le compilateur supprime le comportement et les références `std::weak_equality` aux `std::strong_equality` types et.

Le code de cet exemple n’est plus compilé :

```cpp
#include <compare>

struct S {
    std::strong_equality operator<=>(const S&) const = default;
};

void f() {
    nullptr<=>nullptr;
    &f <=> &f;
    &S::operator<=> <=> &S::operator<=>;
}
```

L’exemple génère désormais les erreurs suivantes :

```Output
error C2039: 'strong_equality': is not a member of 'std'
error C2143: syntax error: missing ';' before '<=>'
error C4430: missing type specifier - int assumed. Note: C++ does not support default-int
error C4430: missing type specifier - int assumed. Note: C++ does not support default-int
error C7546: binary operator '<=>': unsupported operand types 'nullptr' and 'nullptr'
error C7546: binary operator '<=>': unsupported operand types 'void (__cdecl *)(void)' and 'void (__cdecl *)(void)'
error C7546: binary operator '<=>': unsupported operand types 'int (__thiscall S::* )(const S &) const' and 'int (__thiscall S::* )(const S &) const'
```

Pour résoudre le problème, mettez à jour pour préférer les opérateurs relationnels intégrés et remplacez les types supprimés :

```cpp
#include <compare>

struct S {
    std::strong_ordering operator<=>(const S&) const = default; // prefer 'std::strong_ordering'
};

void f() {
    nullptr != nullptr; // use pre-existing builtin operator != or ==.
    &f != &f;
    &S::operator<=> != &S::operator<=>;
}
```

### <a name="tls-guard-changes"></a>Modifications de la protection TLS

Auparavant, les variables locales de thread dans les dll n’étaient pas correctement initialisées. En dehors du thread qui a chargé la DLL, elles n’ont pas été initialisées avant la première utilisation sur les threads qui existaient avant le chargement de la DLL. Ce défaut a été corrigé. Les variables locales de thread dans une telle DLL sont initialisées immédiatement avant leur première utilisation sur ces threads.

Ce nouveau comportement de test de l’initialisation sur les utilisations des variables locales de thread peut être désactivé à l’aide du **`/Zc:tlsGuards-`** commutateur du compilateur. Ou, en ajoutant l' `[[msvc:no_tls_guard]]` attribut à des variables locales de thread particulières.

### <a name="better-diagnosis-of-call-to-deleted-functions"></a>Meilleur diagnostic de l’appel aux fonctions supprimées

Notre compilateur était plus permissif sur les appels de fonctions supprimées précédemment. Par exemple, si les appels sont survenus dans le contexte d’un corps de modèle, nous ne diagnostiquerons pas l’appel. De plus, s’il existe plusieurs instances d’appels aux fonctions supprimées, nous n’allons émettre qu’un seul diagnostic. À présent, nous allons émettre un diagnostic pour chacun d’eux.

L’une des conséquences du nouveau comportement peut entraîner une petite modification avec rupture : le code qui a appelé une fonction supprimée n’est pas diagnostiqué s’il n’était jamais nécessaire pour la génération de code. À présent, nous le diagnostiquerons à l’avance.

Cet exemple montre le code qui génère désormais une erreur :

```cpp
struct S {
  S() = delete;
  S(int) { }
};

struct U {
  U() = delete;
  U(int i): s{ i } { }

  S s{};
};

U u{ 0 };
```

```Output
error C2280: 'S::S(void)': attempting to reference a deleted function
note: see declaration of 'S::S'
note: 'S::S(void)': function was explicitly deleted
```

Pour résoudre le problème, supprimez les appels aux fonctions supprimées :

```cpp
struct S {
  S() = delete;
  S(int) { }
};

struct U {
  U() = delete;
  U(int i): s{ i } { }

  S s;  // Do not call the deleted ctor of 'S'.
};

U u{ 0 };
```

## <a name="conformance-improvements-in-visual-studio-2019-version-166"></a><a name="improvements_166"></a> Améliorations de la conformité dans Visual Studio 2019 version 16,6

### <a name="standard-library-streams-reject-insertions-of-mis-encoded-character-types"></a>Les flux de bibliothèque standard rejettent les insertions de types de caractère mal codés

Traditionnellement, l’insertion d’un **`wchar_t`** dans un `std::ostream` , et l’insertion de **`char16_t`** ou **`char32_t`** dans `std::ostream` ou `std::wostream` , génèrent sa valeur intégrale. L’insertion de pointeurs vers ces types de caractères génère la valeur du pointeur. Les programmeurs ne trouvent pas les deux cas intuitifs. Ils s’attendent souvent à ce que la bibliothèque standard transcode le caractère ou la chaîne de caractères se terminant par un caractère null à la place, et à générer le résultat.

La proposition [P1423R3](https://wg21.link/p1423r3) c++ 20 ajoute des surcharges d’opérateur d’insertion de flux supprimées pour ces combinaisons de types de pointeurs de flux et de caractères ou de caractères. Sous **`/std:c++latest`** , les surcharges rendent ces insertions incorrectes, au lieu de se comporter dans ce qui est probablement une méthode involontaire. Le compilateur déclenche l’erreur C2280 lorsqu’un est trouvé. Vous pouvez définir la macro « trappe d’échappement » `_HAS_STREAM_INSERTION_OPERATORS_DELETED_IN_CXX20` pour `1` restaurer l’ancien comportement. (La proposition supprime également les opérateurs d’insertion de flux pour **`char8_t`** . Notre bibliothèque standard a implémenté des surcharges similaires lorsque nous avons ajouté **`char8_t`** la prise en charge, donc le comportement « incorrect » n’a jamais été disponible pour **`char8_t`** .)

Cet exemple montre le comportement de cette modification :

```cpp
#include <iostream>
int main() {
    const wchar_t cw = L'x', *pw = L"meow";
    const char16_t c16 = u'x', *p16 = u"meow";
    const char32_t c32 = U'x', *p32 = U"meow";
    std::cout << cw << ' ' << pw << '\n';
    std::cout << c16 << ' ' << p16 << '\n';
    std::cout << c32 << ' ' << p32 << '\n';
    std::wcout << c16 << ' ' << p16 << '\n';
    std::wcout << c32 << ' ' << p32 << '\n';
}
```

Le code génère désormais les messages de diagnostic suivants :

```Output
error C2280: 'std::basic_ostream<char,std::char_traits<char>> &std::<<<std::char_traits<char>>(std::basic_ostream<char,std::char_traits<char>> &,wchar_t)': attempting to reference a deleted function
error C2280: 'std::basic_ostream<char,std::char_traits<char>> &std::<<<std::char_traits<char>>(std::basic_ostream<char,std::char_traits<char>> &,char16_t)': attempting to reference a deleted function
error C2280: 'std::basic_ostream<char,std::char_traits<char>> &std::<<<std::char_traits<char>>(std::basic_ostream<char,std::char_traits<char>> &,char32_t)': attempting to reference a deleted function
error C2280: 'std::basic_ostream<wchar_t,std::char_traits<wchar_t>> &std::<<<std::char_traits<wchar_t>>(std::basic_ostream<wchar_t,std::char_traits<wchar_t>> &,char16_t)': attempting to reference a deleted function
error C2280: 'std::basic_ostream<wchar_t,std::char_traits<wchar_t>> &std::<<<std::char_traits<wchar_t>>(std::basic_ostream<wchar_t,std::char_traits<wchar_t>> &,char32_t)': attempting to reference a deleted function
```

Vous pouvez obtenir l’effet de l’ancien comportement dans tous les modes de langage en convertissant les types de caractères en **`unsigned int`** , ou en types de pointeur en caractères en `const void*` :

```c++
#include <iostream>
int main() {
    const wchar_t cw = L'x', *pw = L"meow";
    const char16_t c16 = u'x', *p16 = u"meow";
    const char32_t c32 = U'x', *p32 = U"meow";
    std::cout << (unsigned)cw << ' ' << (const void*)pw << '\n'; // Outputs "120 0052B1C0"
    std::cout << (unsigned)c16 << ' ' << (const void*)p16 << '\n'; // Outputs "120 0052B1CC"
    std::cout << (unsigned)c32 << ' ' << (const void*)p32 << '\n'; // Outputs "120 0052B1D8"
    std::wcout << (unsigned)c16 << ' ' << (const void*)p16 << '\n'; // Outputs "120 0052B1CC"
    std::wcout << (unsigned)c32 << ' ' << (const void*)p32 << '\n'; // Outputs "120 0052B1D8"
}
```

### <a name="changed-return-type-of-stdpow-for-stdcomplex"></a>Type de retour modifié de `std::pow()` pour `std::complex`

Auparavant, l’implémentation MSVC des règles de promotion pour le type de retour du modèle de fonction `std::pow()` était incorrecte. Par exemple, précédemment `pow(complex<float>, int)` retourné `complex<float>` . À présent, il retourne correctement `complex<double>` . Le correctif a été implémenté de manière inconditionnelle pour tous les modes standard de Visual Studio 2019 version 16,6.

Cette modification peut provoquer des erreurs de compilation. Par exemple, auparavant, vous pouviez multiplier `pow(complex<float>, int)` par un **`float`** . Étant donné que `complex<T> operator*` attend des arguments du même type, l’exemple suivant émet désormais l’erreur de compilateur C2676 : `binary '*': 'std::complex<double>' does not define this operator or a conversion to a type acceptable to the predefined operator` :

```cpp
// pow_error.cpp
// compile by using: cl /EHsc /nologo /W4 pow_error.cpp
#include <complex>

int main() {
    std::complex<float> cf(2.0f, 0.0f);
    (void) (std::pow(cf, -1) * 3.0f);
}
```

Il existe de nombreux correctifs possibles :

- Remplacez le type de **`float`** multiplicande par **`double`** . Cet argument peut être converti directement en `complex<double>` pour correspondre au type retourné par `pow` .

- Réduisez le résultat de `pow` à `complex<float>` en disant `complex<float>{pow(ARG, ARG)}` . Vous pouvez ensuite continuer à multiplier par une **`float`** valeur.

- Passe **`float`** au lieu de **`int`** à `pow` . Cette opération peut être plus lente.

- Dans certains cas, vous pouvez éviter `pow` totalement. Par exemple, `pow(cf, -1)` peut être remplacé par division.

### <a name="switch-related-warnings-for-c"></a>Avertissements liés au commutateur pour C

À compter de Visual Studio 2019 version 16,6, le compilateur implémente certains avertissements C++ préexistants pour le code compilé en tant que C. Les avertissements suivants sont désormais activés à différents niveaux : C4060, C4061, C4062, avertissement C4063, C4064, C4065, C4808 et C4809. Les avertissements C4065 et C4060 sont désactivés par défaut dans C.

Le déclencheur avertissements sur les instructions manquantes **`case`** , les **`enum`** commutateurs non définis et les commutateurs incorrects **`bool`** (c’est-à-dire ceux qui contiennent trop de cas). Par exemple :

```c
#include <stdbool.h>

int main() {
    bool b = true;
    switch (b) {
        case true: break;
        case false: break;
        default: break; // C4809: switch statement has redundant 'default' label;
                        // all possible 'case' labels are given
    }
}
```

Pour corriger ce code, supprimez le **`default`** cas redondant :

```c
#include <stdbool.h>

int main() {
    bool b = true;
    switch (b) {
        case true: break;
        case false: break;
    }
}
```

### <a name="unnamed-classes-in-typedef-declarations"></a>Classes sans nom dans les `typedef` déclarations

À compter de Visual Studio 2019 version 16,6, le comportement des **`typedef`** déclarations a été limité à la conformité à [P1766R1](https://wg21.link/P1766R1). Avec cette mise à jour, les classes sans nom au sein d’une **`typedef`** déclaration ne peuvent pas avoir de membres autres que :

- données membres non statiques,
- classes membres,
- les énumérations de membres,
- et les initialiseurs de membres par défaut.

Les mêmes restrictions sont appliquées de manière récursive à chaque classe imbriquée. La restriction vise à garantir la simplicité des structures qui ont des **`typedef`** noms à des fins de liaison. Ils doivent être suffisamment simples pour qu’aucun calcul de liaison ne soit nécessaire avant que le compilateur n’ait le **`typedef`** nom de la liaison.

Cette modification affecte tous les modes standard du compilateur. Dans les modes par défaut ( **`/std:c++14`** ) et  **`/std:c++17`** , le compilateur émet un avertissement C5208 pour le code non conforme. Si **`/permissive-`** est spécifié, le compilateur émet un avertissement C5208 en tant qu’erreur sous **`/std:c++14`** et émet l’erreur C7626 sous **`/std:c++17`** . Le compilateur émet une erreur C7626 pour du code non conforme quand **`/std:c++latest`** est spécifié.

L’exemple suivant montre les constructions qui ne sont plus autorisées dans les structs sans nom. Selon le mode standard spécifié, les erreurs ou les avertissements C5208 ou C7626 sont émis :

```cpp
struct B { };
typedef struct : B { // inheriting from 'B'; ill-formed
    void f(); // ill-formed
    static int i; // ill-formed
    struct U {
        void f(); // nested class has non-data member; ill-formed
    };
    int j = 10; // default member initializer; ill-formed
} S;
```

Le code ci-dessus peut être corrigé en donnant un nom à la classe sans nom :

```cpp
struct B { };
typedef struct S_ : B {
    void f();
    static int i;
    struct U {
        void f();
    };
    int j = 10;
} S;
```

### <a name="default-argument-import-in-ccli"></a>Importation d’arguments par défaut en C++/CLI

Un nombre plus important d’API ont des arguments par défaut dans .NET Core. C’est la raison pour laquelle nous prenons désormais en charge l’importation d’arguments par défaut en C++/CLI. Cette modification peut interrompre le code existant dans lequel plusieurs surcharges sont déclarées, comme dans cet exemple :

```cpp
public class R {
    public void Func(string s) {}   // overload 1
    public void Func(string s, string s2 = "") {} // overload 2;
}
```

Quand cette classe est importée dans C++/CLI, un appel à l’une des surcharges génère une erreur :

```cpp
    (gcnew R)->Func("abc"); // error C2668: 'R::Func' ambiguous call to overloaded function
```

Le compilateur émet l’erreur C2668, car les deux surcharges correspondent à cette liste d’arguments. Dans la deuxième surcharge, le deuxième argument est renseigné par l’argument par défaut. Pour contourner ce problème, vous pouvez supprimer la surcharge redondante (1). Ou utilisez la liste d’arguments complète et fournissez explicitement les arguments par défaut.

## <a name="conformance-improvements-in-visual-studio-2019-version-167"></a><a name="improvements_167"></a> Améliorations de la conformité dans Visual Studio 2019 version 16,7

### <a name="definition-of-is-trivially-copyable"></a>La définition de *est à copier* triviale

C++ 20 modifié la définition de *est copiée*de façon triviale. Quand une classe a un membre de données non statiques avec **`volatile`** le type Qualified, elle n’implique plus que tout constructeur de copie ou de déplacement généré par le compilateur, ou l’opérateur d’assignation de copie ou de déplacement, est non trivial. Le Comité C++ standard a appliqué cette modification rétroactivement comme un rapport d’erreurs. Dans MSVC, le comportement du compilateur ne change pas dans les différents modes de langue, tels que **`/std:c++14`** ou **`/std:c++latest`** .

Voici un exemple du nouveau comportement :

```cpp
#include <type_traits>

struct S
{
    volatile int m;
};

static_assert(std::is_trivially_copyable_v<S>, "Meow!");
```

Ce code ne compile pas dans les versions de MSVC avant Visual Studio 2019 version 16,7. Un avertissement du compilateur est désactivé par défaut, que vous pouvez utiliser pour détecter cette modification. Si vous compilez le code ci-dessus à l’aide de **`cl /W4 /w45220`** , vous verrez l’avertissement suivant :

AVERTISSEMENT C5220 : `'S::m': a non-static data member with a volatile qualified type no longer implies that compiler generated copy/move constructors and copy/move assignment operators are non trivial`

### <a name="pointer-to-member-and-string-literal-conversions-to-bool-are-narrowing"></a>Les conversions de littéraux de type pointeur vers membre et chaîne en `bool` sont restrictives

Le Comité C++ standard a récemment adopté le rapport de défaut [P1957R2](https://wg21.link/p1957r2), qui considère `T*`  ->  **`bool`** comme une conversion restrictive. MSVC a corrigé un bogue dans son implémentation, qui aurait précédemment fait l’outil de diagnostic `T*`  ->  **`bool`** étroit, mais n’a pas diagnostiqué la conversion d’un littéral de chaîne en **`bool`** ou de pointeur vers membre en **`bool`** .

Le programme suivant est incorrect dans Visual Studio 2019 version 16,7 :

```cpp
struct X { bool b; };
void f(X);

int main() {
    f(X { "whoops?" }); // error: conversion from 'const char [8]' to 'bool' requires a narrowing conversion

    int (X::* p) = nullptr;
    f(X { p }); // error: conversion from 'int X::*' to 'bool' requires a narrowing conversion
}
```

Pour corriger ce code, ajoutez des comparaisons explicites à **`nullptr`** ou évitez les contextes dans lesquels les conversions restrictives sont incorrectes :

```cpp
struct X { bool b; };
void f(X);

int main() {
    f(X { "whoops?" != nullptr }); // Absurd, but OK

    int (X::* p) = nullptr;
    f(X { p != nullptr }); // OK
}
```

### <a name="nullptr_t-is-only-convertible-to-bool-as-a-direct-initialization"></a>`nullptr_t` est uniquement convertible en `bool` en tant qu’initialisation directe

En C++ 11, **`nullptr`** est convertible uniquement en **`bool`** en tant que *conversion directe*; par exemple, lorsque vous initialisez un à **`bool`** l’aide d’une liste d’initialiseurs entre accolades. Cette restriction n’a jamais été appliquée par MSVC. MSVC implémente désormais la règle sous [`/permissive-`](../build/reference/permissive-standards-conformance.md) . Les conversions implicites sont désormais diagnostiquées comme incorrectes. Une conversion contextuelle en **`bool`** est toujours autorisée, car l’initialisation directe `bool b(nullptr)` est valide.

Dans la plupart des cas, l’erreur peut être corrigée en remplaçant par **`nullptr`** **`false`** , comme illustré dans cet exemple :

```cpp
struct S { bool b; };
void g(bool);
bool h() { return nullptr; } // error, should be 'return false;'

int main() {
    bool b1 = nullptr; // error: cannot convert from 'nullptr' to 'bool'
    S s { nullptr }; // error: cannot convert from 'nullptr' to 'bool'
    g(nullptr); // error: cannot convert argument 1 from 'nullptr' to 'bool'

    bool b2 { nullptr }; // OK: Direct-initialization
    if (!nullptr) {} // OK: Contextual conversion to bool
}
```

### <a name="conforming-initialization-behavior-for-array-initializations-with-missing-initializers"></a>Comportement de l’initialisation pour les initialisations de tableau avec des initialiseurs manquants

Auparavant, MSVC avait un comportement non conforme pour les initialisations de tableau qui ne disposaient pas d’initialiseurs. MSVC appelle toujours le constructeur par défaut pour chaque élément de tableau qui n’a pas d’initialiseur. Le comportement standard consiste à initialiser chaque élément avec une accolade-initializer-List () vide **`{}`** . Le contexte d’initialisation pour une liste à accolades vides vide est l’initialisation de copie, qui n’autorise pas les appels aux constructeurs explicites. Il peut également y avoir des différences au moment de l’exécution, car l’utilisation de `{}` pour initialiser peut appeler un constructeur qui accepte un `std::initializer_list` , au lieu du constructeur par défaut. Le comportement de conformité est activé sous [`/permissive-`](../build/reference/permissive-standards-conformance.md) .

Voici un exemple de comportement modifié :

```cpp
struct B {
    explicit B() {}
};

void f() {
    B b1[1]{}; // Error in /permissive-, because aggregate init calls explicit ctor
    B b2[1]; // OK: calls default ctor for each array element
}
```

## <a name="bug-fixes-and-behavior-changes-in-visual-studio-2019"></a><a name="update_160"></a> Correctifs de bogues et modifications de comportement dans Visual Studio 2019

### <a name="reinterpret_cast-in-a-constexpr-function"></a>`reinterpret_cast` dans une `constexpr` fonction

Un **`reinterpret_cast`** est non conforme dans une **`constexpr`** fonction. Le compilateur Microsoft C++ rejetait auparavant **`reinterpret_cast`** uniquement s’il était utilisé dans un **`constexpr`** contexte. Dans Visual Studio 2019, dans tous les modes de normes de langage, le compilateur diagnostique correctement un **`reinterpret_cast`** dans la définition d’une **`constexpr`** fonction. Le code suivant génère désormais C3615 : `constexpr function 'f' cannot result in a constant expression` .

```cpp
long long i = 0;
constexpr void f() {
    int* a = reinterpret_cast<int*>(i);
}
```

Pour éviter cette erreur, supprimez le **`constexpr`** modificateur de la déclaration de la fonction.

### <a name="correct-diagnostics-for-basic_string-range-constructor"></a>Diagnostics corrects pour le constructeur de plage basic_string

Dans Visual Studio 2019, le `basic_string` constructeur Range ne supprime plus les diagnostics du compilateur avec **`static_cast`** . Le code suivant compile sans avertissements dans Visual Studio 2017, en dépit de la perte possible de données de **`wchar_t`** à **`char`** lors de l’initialisation `out` :

```cpp
std::wstring ws = /* … */;
std::string out(ws.begin(), ws.end());
```

Visual Studio 2019 génère correctement l’avertissement C4244 : `'argument': conversion from 'wchar_t' to 'const _Elem', possible loss of data` . Pour éviter cet avertissement, vous pouvez initialiser le std::string comme illustré dans cet exemple :

```cpp
std::wstring ws = L"Hello world";
std::string out;
for (wchar_t ch : ws)
{
    out.push_back(static_cast<char>(ch));
}
```

### <a name="incorrect-calls-to--and---under-clr-or-zw-are-now-correctly-detected"></a>Les appels incorrects à `+=` et `-=` sous `/clr` ou `/ZW` sont maintenant détectés correctement

Un bogue a été introduit dans Visual Studio 2017 qui a fait en sorte que le compilateur ignore silencieusement les erreurs et ne génère aucun code pour les appels non valides à **`+=`** et **`-=`** sous **`/clr`** ou **`/ZW`** . Le code suivant compile sans erreurs dans Visual Studio 2017, mais dans Visual Studio 2019, il génère correctement l’erreur C2845 : `'System::String ^': pointer arithmetic not allowed on this type` :

```cpp
public enum class E { e };

void f(System::String ^s)
{
    s += E::e; // C2845 in VS2019
}
```

Pour éviter l’erreur dans cet exemple, utilisez l' **`+=`** opérateur avec la `ToString()` méthode : `s += E::e.ToString();` .

### <a name="initializers-for-inline-static-data-members"></a>Initialiseurs pour les membres de données statiques inline

Les accès aux membres non valides dans **`inline`** et les **`static constexpr`** initialiseurs sont désormais correctement détectés. L’exemple suivant compile sans erreur dans Visual Studio 2017, mais dans Visual Studio 2019 en mode, **`/std:c++17`** il génère l’erreur C2248 : `cannot access private member declared in class 'X'` .

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

MSVC utilisé pour obtenir un avertissement de performance C4800 sur la conversion implicite en **`bool`** . Il était trop bruyant et n’a pas pu être supprimé, ce qui nous permet de le supprimer dans Visual Studio 2017. Toutefois, pendant le cycle de vie de Visual Studio 2017, nous avons eu beaucoup de commentaires disant qu’il était utile pour résoudre de nombreux cas. Nous avons rajouté à Visual Studio 2019 un avertissement C4800 soigneusement adapté, ainsi qu’un C4165 explicatif. Ces deux avertissements sont faciles à supprimer : soit en utilisant un cast explicite, soit par comparaison à 0 du type approprié. C4800 est un avertissement de niveau 4 désactivé par défaut, tandis que C4165 est un avertissement de niveau 3 désactivé par défaut. Les deux sont détectables à l’aide de l' **`/Wall`** option du compilateur.

L’exemple suivant déclenche C4800 et C4165 sous **`/Wall`** :

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

Dans Visual Studio 2017, Warning C4822 : `Local class member function doesn't have a body` est déclenché uniquement lorsque l’option de compilateur **`/w14822`** est définie explicitement. Elle n’est pas affichée avec **`/Wall`** . Dans Visual Studio 2019, C4822 est un avertissement désactivé par défaut, ce qui le rend détectable sous **`/Wall`** sans avoir à définir **`/w14822`** explicitement.

```cpp
void example()
{
    struct A
        {
            int boo(); // warning C4822
        };
}
```

### <a name="function-template-bodies-containing-if-constexpr-statements"></a>Corps de modèle de fonction contenant des `if constexpr` instructions

**`if constexpr`** Des [`/permissive-`](../build/reference/permissive-standards-conformance.md) contrôles liés à l’analyse sont activés pour les corps de fonction de modèle contenant des instructions. Par exemple, dans Visual Studio 2017, le code suivant génère C7510 : `'Type': use of dependent type name must be prefixed with 'typename'` uniquement si l' **`/permissive-`** option n’est pas définie. Dans Visual Studio 2019, le même code déclenche des erreurs même lorsque l' **`/permissive-`** option est définie :

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

Pour éviter cette erreur, ajoutez le **`typename`** mot clé à la déclaration de `a` : `typename T::Type a;` .

### <a name="inline-assembly-code-isnt-supported-in-a-lambda-expression"></a>Le code de l’assembleur inline n’est pas pris en charge dans une expression lambda

L’équipe Microsoft C++ a récemment été informée d’un problème de sécurité dans lequel l’utilisation de l’assembleur inline dans une expression lambda pouvait entraîner l’altération de `ebp` (le registre d’adresses de retour) au moment de l’exécution. Une personne malveillante pouvait éventuellement tirer parti de ce scénario. L’assembleur inline est uniquement pris en charge sur x86 et l’interaction entre l’assembleur inline et le reste du compilateur est médiocre. Compte tenu de ces faits et de la nature du problème, la solution la plus sûre à ce problème consistait à interdire l’assembleur inline dans une expression lambda.

La seule utilisation de l’assembleur inline dans une expression lambda que nous avons rencontrée avait pour but de capturer l’adresse de retour. Dans ce scénario, vous pouvez capturer l’adresse de retour sur toutes les plateformes simplement à l’aide de `_ReturnAddress()` intrinsèque au compilateur.

Le code suivant génère C7552 : `inline assembler is not supported in a lambda` dans Visual studio 2017 15,9 et dans Visual studio 2019 :

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

### <a name="fixes-for-xkeycheckh-keyword-enforcement"></a>Correctifs pour la \<xkeycheck.h> mise en œuvre des mots clés

La mise en œuvre de la bibliothèque standard dans \<xkeycheck.h> pour les macros remplaçant un mot clé a été corrigée. La bibliothèque émet désormais le mot clé de problème réel détecté plutôt qu’un message générique. Elle prend aussi en charge les mots clés C++20 et évite qu’IntelliSense indique que des mots clés aléatoires sont des macros.

### <a name="allocator-types-no-longer-deprecated"></a>Les types d’allocateurs ne sont plus déconseillés

`std::allocator<void>`, `std::allocator::size_type` et `std::allocator::difference_type` ne sont plus déconseillés.

### <a name="correct-warning-for-narrowing-string-conversions"></a>Avertissement correct pour les conversions de chaîne restrictives

Suppression d’un parasite **`static_cast`** de `std::string` qui n’a pas été appelé pour par la norme, et qui a supprimé accidentellement des avertissements restrictifs de l’erreur C4244. Les tentatives d’appel à `std::string::string(const wchar_t*, const wchar_t*)` présent émettent correctement C4244 `narrowing a wchar_t into a char` .

### <a name="various-fixes-for-filesystem-correctness"></a>Différents correctifs pour l' \<filesystem> exactitude

- Résolution de `std::filesystem::last_write_time` l’échec lors de la tentative de modification de l’heure de la dernière écriture d’un répertoire.
- Désormais, le constructeur `std::filesystem::directory_entry` stocke un résultat en échec plutôt que de lever une exception quand un chemin cible qui n’existe pas est fourni.
- La version à 2 paramètres `std::filesystem::create_directory` a été changée pour appeler la version à 1 paramètre, car la fonction `CreateDirectoryExW` sous-jacente utiliserait `copy_symlink` si `existing_p` était un symlink.
- `std::filesystem::directory_iterator` n’échoue plus lorsqu’un symkink rompu est trouvé.
- `std::filesystem::space` accepte désormais les chemins relatifs.
- `std::filesystem::path::lexically_relative` n’est plus dérouté par les barres obliques de fin, signalé dans [LWG 3096](https://cplusplus.github.io/LWG/issue3096).
- Le problème a été contourné avec `CreateSymbolicLinkW` qui rejette les chemins avec des barres obliques dans `std::filesystem::create_symlink`.
- A fonctionné autour de la `delete` fonction de mode de suppression POSIX qui existait dans Windows 10 LTSB 1609, mais ne peut pas réellement supprimer des fichiers.
- Les constructeurs de copie de `std::boyer_moore_searcher` et `std::boyer_moore_horspool_searcher` et les opérateurs d'affectation de copie arrivent maintenant à copier.

### <a name="parallel-algorithms-on-windows-8-and-later"></a>Algorithmes parallèles sur Windows 8 et ultérieur

La bibliothèque d’algorithmes parallèles utilise la vraie famille `WaitOnAddress` sur Windows 8 et ultérieur, au lieu d’utiliser tout le temps les versions fausses de Windows 7 et antérieur.

### <a name="stdsystem_categorymessage-whitespace"></a>Espace blanc `std::system_category::message()`

`std::system_category::message()` supprime désormais l’espace de fin du message retourné.

### <a name="stdlinear_congruential_engine-divide-by-zero"></a>Division par zéro de `std::linear_congruential_engine`

Certaines conditions qui faisaient que `std::linear_congruential_engine` déclenchait la division par 0 ont été corrigées.

### <a name="fixes-for-iterator-unwrapping"></a>Correctifs pour l’unwrapping d’itérateurs

Certaines machines à dévoiler des itérateurs ont d’abord été exposées pour l’intégration des utilisateurs du programmeur dans Visual Studio 2017 15,8. Elle a été décrite dans l’article du blog de l’équipe C++ [fonctionnalités et correctifs de Visual studio 2017 15,8](https://devblogs.microsoft.com/cppblog/stl-features-and-fixes-in-vs-2017-15-8/). Cette machine ne désencapsule plus les itérateurs dérivés des itérateurs de bibliothèque standard. Par exemple, un utilisateur qui dérive de `std::vector<int>::iterator` et qui essaie de personnaliser le comportement obtient son comportement personnalisé lors de l’appel des algorithmes de la bibliothèque standard au lieu du comportement d’un pointeur.

La fonction de réserve de conteneur non ordonnée `reserve` maintenant pour N éléments, comme décrit dans [LWG 2156](https://cplusplus.github.io/LWG/issue2156).

### <a name="time-handling"></a>Gestion de l’heure

- Avant, certaines valeurs de temps passées à la bibliothèque de concurrence provoquaient un dépassement, par exemple, `condition_variable::wait_for(seconds::max())`. Ces dépassements, maintenant corrigés, changeaient le comportement selon un cycle apparemment aléatoire de 29 jours (quand les millisecondes uint32_t acceptées par les API Win32 sous-jacentes dépassaient).

- L' \<ctime> en-tête déclare désormais correctement `timespec` et `timespec_get` dans l’espace de noms `std` , et les déclare également dans l’espace de noms global.

### <a name="various-fixes-for-containers"></a>Divers correctifs pour les conteneurs

- De nombreuses fonctions de conteneur internes à la bibliothèque Standard ont été rendues privées pour une meilleure expérience IntelliSense. Des correctifs supplémentaires pour marquer les membres comme privés sont attendus dans les prochaines versions de MSVC.

- Les problèmes de sécurité d’exception, où les conteneurs basés sur des nœuds comme `list`, `map` et `unordered_map` étaient altérés, ont été résolus. Pendant une `propagate_on_container_copy_assignment` opération ou une `propagate_on_container_move_assignment` réaffectation, nous libérerions le nœud de sentinelle du conteneur avec l’ancien allocateur, nous effectuons l’assignation POCCA/POCMA sur l’ancien allocateur, puis essayons d’acquérir le nœud Sentinel à partir du nouvel allocateur. Si cette allocation a échoué, le conteneur a été endommagé. Elle n’a même pas pu être détruite, car la possession d’un nœud Sentinel est un invariant de structure de données matérielles. Ce code a été corrigé pour créer le nouveau nœud Sentinel à l’aide de l’allocateur du conteneur source avant de détruire le nœud Sentinel existant.

- Les conteneurs ont été résolus pour toujours copier/déplacer/échanger les allocateurs en fonction de `propagate_on_container_copy_assignment`, `propagate_on_container_move_assignment` et `propagate_on_container_swap`, même pour les allocateurs déclarés `is_always_equal`.

- Ajout des surcharges pour la fusion de conteneurs et extraction des fonctions membres qui acceptent les conteneurs rvalue. Pour plus d’informations, consultez la section « Ajout de [mappages et de jeux P0083](https://wg21.link/p0083r3) ».

### <a name="stdbasic_istreamread-processing-of-rn--n"></a>`std::basic_istream::read` traitement de `\r\n`` => ` \n'

`std::basic_istream::read`a été corrigé pour ne pas écrire temporairement dans des parties de la mémoire tampon fournie dans le cadre du `\r\n`  =>  `\n` traitement. Ce changement offre une partie de l’avantage en matière de performances acquis dans Visual Studio 2017 15.8 pour les lectures supérieures à 4 ko. Toutefois, les améliorations de l’efficacité obtenues en évitant les trois appels virtuels par caractère restent présentes.

### <a name="stdbitset-constructor"></a>Constructeur `std::bitset`

Le constructeur `std::bitset` ne lit plus les uns et les zéros dans l’ordre inverse pour les grands bitsets.

### <a name="stdpairoperator-regression"></a>Régression `std::pair::operator=`

Correction d’une régression dans l’opérateur d’affectation de `std::pair` introduite lors de l’implémentation de [LWG 2729 "Missing SFINAE on std::pair::operator=";](https://cplusplus.github.io/LWG/issue2729). Maintenant, il accepte de nouveau les types convertibles en `std::pair` correctement.

### <a name="non-deduced-contexts-for-add_const_t"></a>Contextes non déduits pour `add_const_t`

Correction d’un bogue de traits de type mineur, où `add_const_t` et les fonctions associées sont censés être un contexte non déduit. En d’autres termes, `add_const_t` doit être un alias pour `typename add_const<T>::type`, pas `const T`.

## <a name="bug-fixes-and-behavior-changes-in-162"></a><a name="update_162"></a> Correctifs de bogues et modifications de comportement dans 16,2

### <a name="const-comparators-for-associative-containers"></a>Comparateurs const pour les conteneurs associatifs

Le code pour la recherche et l’insertion dans [Set](../standard-library/set-class.md), [Map](../standard-library/map-class.md), [multijeu](../standard-library/multiset-class.md)et [Multimap](../standard-library/multimap-class.md) a été fusionné pour réduire la taille du code. Les opérations d’insertion appellent maintenant la comparaison « inférieur à » sur un **`const`** functor de comparaison, de la même façon que les opérations de recherche ont été effectuées précédemment. Le code suivant compile dans Visual Studio 2019 version 16,1 et versions antérieures, mais génère C3848 dans Visual Studio 2019 version 16,2 :

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

Pour éviter cette erreur, créez l’opérateur de comparaison **`const`** :

```cpp
struct Comparer  {
   bool operator() (K a, K b) const {
      return a.a < b.a;
   }
};

```

## <a name="bug-fixes-and-behavior-changes-in-visual-studio-2019-version-167"></a><a name="updates_167"></a> Correctifs de bogues et modifications de comportement dans Visual Studio 2019 version 16,7

### <a name="initialization-of-class-members-with-overloaded-names-is-correctly-sequenced"></a>L’initialisation des membres de classe avec des noms surchargés est correctement séquencée

Nous avons identifié un bogue dans la représentation interne des données membres de la classe lorsqu’un nom de type est également surchargé en tant que nom d’un membre de données. Ce bogue est dû à des incohérences dans l’initialisation de l’agrégat et l’ordre d’initialisation des membres. Le code d’initialisation généré est maintenant correct. Toutefois, cette modification peut entraîner des erreurs ou des avertissements dans la source qui s’appuient par inadvertance sur les membres mal ordonnés, comme dans cet exemple :

```cpp
// Compiling with /w15038 now gives:
// warning C5038: data member 'Outer::Inner' will be initialized after data member 'Outer::v'
struct Outer {
    Outer(int i, int j) : Inner{ i }, v{ j } {}

    struct Inner { int x; };
    int v;
    Inner Inner; // 'Inner' is both a type name and data member name in the same scope
};
```

Dans les versions précédentes, le constructeur initialiserait incorrectement les données membres `Inner` avant les données membres `v` . (La norme C++ requiert un ordre d’initialisation identique à l’ordre de déclaration des membres). Maintenant que le code généré suit le standard, Member-init-List est dans le désordre. Le compilateur génère un avertissement pour cet exemple. Pour le corriger, réorganisez le membre-initializer-List pour refléter l’ordre de déclaration.

### <a name="overload-resolution-involving-integral-overloads-and-long-arguments"></a>Résolution de surcharge impliquant des surcharges et des arguments intégraux `long`

La norme C++ requiert le classement d’un en conversion **`long`** **`int`** standard. Les compilateurs MSVC précédents le classent incorrectement comme une promotion intégrale, qui classe plus haut pour la résolution de surcharge. Ce classement peut entraîner la résolution de la résolution de surcharge lorsqu’elle doit être considérée comme ambiguë.

Le compilateur considère maintenant le rang correctement en [`/permissive-`](../build/reference/permissive-standards-conformance.md) mode. Un code non valide est correctement diagnostiqué, comme dans cet exemple :

```cpp
void f(long long);
void f(int);

int main() {
    long x {};
    f(x); // error: 'f': ambiguous call to overloaded function
    f(static_cast<int>(x)); // OK
}
```

Vous pouvez résoudre ce problème de plusieurs façons :

- Sur le site d’appel, remplacez le type de l’argument passé par **`int`** . Vous pouvez modifier le type de variable ou le convertir.

- S’il existe de nombreux sites d’appel, vous pouvez ajouter une autre surcharge qui prend un **`long`** argument. Dans cette fonction, effectuez un cast et un transfert de l’argument vers la **`int`** surcharge.

### <a name="use-of-undefined-variable-with-internal-linkage"></a>Utilisation d’une variable non définie avec une liaison interne

Les versions de MSVC antérieures à la version 16,7 de Visual Studio 2019 ont accepté l’utilisation d’une variable déclarée **`extern`** qui avait une liaison interne et n’a pas été définie. Ces variables ne peuvent pas être définies dans une autre unité de traduction et ne peuvent pas former un programme valide. Le compilateur diagnostique désormais ce cas au moment de la compilation. L’erreur est similaire à l’erreur pour les fonctions statiques non définies.

```cpp
namespace {
    extern int x; // Not a definition, but has internal linkage because of the anonymous namespace
}

int main()
{
    return x; // Use of 'x' that no other translation unit can possibly define.
}
```

Ce programme n’a pas été correctement compilé et lié, mais il émet maintenant :

erreur C7631 : `'anonymous-namespace'::x': variable with internal linkage declared but not defined`

Ces variables doivent être définies dans la même unité de traduction que celle dans laquelle elles sont utilisées. Par exemple, vous pouvez fournir un initialiseur explicite ou une définition distincte.

### <a name="type-completeness-and-derived-to-base-pointer-conversions"></a>Conversions de type complet et Derived-to-base

Dans les normes C++ antérieures à C++ 20, une conversion d’une classe dérivée vers une classe de base n’a pas besoin que la classe dérivée soit un type de classe complet. Le Comité C++ standard a approuvé une modification de rapport de défaut rétroactif qui s’applique à toutes les versions du langage C++. Cette modification aligne le processus de conversion avec des traits de type, tels que `std::is_base_of` , qui requièrent que la classe dérivée soit un type de classe complet.

Voici un exemple :

```cpp
template<typename A, typename B>
struct check_derived_from
{
    static A a;
    static constexpr B* p = &a;
};

struct W { };
struct X { };
struct Y { };

// With this change this code will fail as Z1 is not a complete class type
struct Z1 : X, check_derived_from<Z1, X>
{
};

// This code failed before and it will still fail after this change
struct Z2 : check_derived_from<Z2, Y>, Y
{
};

// With this change this code will fail as Z3 is not a complete class type
struct Z3 : W
{
    check_derived_from<Z3, W> cdf;
};
```

Ce changement de comportement s’applique à tous les modes de langage C++ de MSVC, pas seulement **`/std:c++latest`** .

### <a name="narrowing-conversions-are-more-consistently-diagnosed"></a>Les conversions restrictives sont diagnostiquées de façon plus cohérente

MSVC émet un avertissement pour les conversions restrictives dans un initialiseur de liste entre accolades. Auparavant, le compilateur ne diagnostiquerait pas les conversions restrictives de **`enum`** types sous-jacents plus grands en types intégraux plus étroits. (Le compilateur les a considérées de manière incorrecte comme une promotion intégrale au lieu d’une conversion). Si la conversion restrictive est intentionnelle, vous pouvez éviter l’avertissement en utilisant un **`static_cast`** sur l’argument de l’initialiseur. Ou choisissez un type intégral de destination plus grand.

Voici un exemple d’utilisation d’un Explicit **`static_cast`** pour traiter l’avertissement :

```cpp
enum E : long long { e1 };
struct S { int i; };

void f(E e) {
    S s = { e }; // warning: conversion from 'E' to 'int' requires a narrowing conversion
    S s1 = { static_cast<int>(e) }; // Suppress warning with explicit conversion
}
```

::: moniker-end

::: moniker range="vs-2017"

## <a name="conformance-improvements-in-visual-studio-2017-rtw-version-150"></a><a name="improvements_150"></a> Améliorations de la conformité dans Visual Studio 2017 RTW (version 15,0)

Avec la prise en charge d’une initialisation de membre de données généralisée **`constexpr`** et non statique (NSDMI) pour les agrégats, le compilateur Microsoft c++ dans Visual Studio 2017 est maintenant terminé pour les fonctionnalités ajoutées à la norme C++ 14. Cependant, le compilateur ne dispose pas encore de certaines fonctionnalités des normes C++11 et C++98. Consultez la [table de conformité du langage Microsoft C++](../visual-cpp-language-conformance.md) pour obtenir une table qui indique l’état actuel du compilateur.

### <a name="c11-expression-sfinae-support-in-more-libraries"></a>C++ 11 : expression SFINAE prise en charge dans plus de bibliothèques

Le compilateur continue d’améliorer la prise en charge de l’expression SFINAE. Elle est requise pour la déduction d’argument de modèle et la substitution d' **`decltype`** expressions où les **`constexpr`** expressions et peuvent apparaître en tant que paramètres de modèle. Pour plus d’informations, consultez [Expression SFINAE improvements in Visual Studio 2017 RC](https://devblogs.microsoft.com/cppblog/expression-sfinae-improvements-in-vs-2015-update-3/).

### <a name="c14-nsdmi-for-aggregates"></a>C++ 14 : NSDMI pour les agrégats

Un agrégat est un tableau ou une classe qui a : aucun constructeur fourni par l’utilisateur, pas de membres de données non statiques privés ou protégés, aucune classe de base et aucune fonction virtuelle. À compter de C++ 14, les agrégats peuvent contenir des initialiseurs de membres. Pour plus d’informations, consultez [Member initializers and aggregates](https://wg21.link/n3605).

### <a name="c14-extended-constexpr"></a>C++ 14 : étendu `constexpr`

Les expressions déclarées comme **`constexpr`** sont désormais autorisées à contenir certains types de déclarations, des instructions If et Switch, des instructions de boucle et une mutation d’objets dont la durée de vie a commencé dans l’évaluation de l' **`constexpr`** expression. Il n’est plus nécessaire qu’une **`constexpr`** fonction membre non statique doive être implicitement **`const`** . Pour plus d’informations, consultez assouplissement [des contraintes sur les `constexpr` fonctions](https://wg21.link/n3652).

### <a name="c17-terse-static_assert"></a>C++ 17 : laconique `static_assert`

le paramètre de message pour **`static_assert`** est facultatif. Pour plus d’informations, consultez [Extending static_assert, v2](https://wg21.link/n3928).

### <a name="c17-fallthrough-attribute"></a>C++17 : Attribut `[[fallthrough]]`

En **`/std:c++17`** mode, l' `[[fallthrough]]` attribut peut être utilisé dans le contexte des instructions Switch en tant qu’indicateur pour le compilateur que le comportement de passage est prévu. Cet attribut empêche le compilateur d’émettre des avertissements dans de tels cas. Pour plus d’informations, consultez [formulation de l' `[[fallthrough]]` attribut](https://wg21.link/p0188r0).

### <a name="generalized-range-based-for-loops"></a>Boucles For basées sur une plage généralisées

Range-based pour les boucles ne nécessitent plus que `begin()` et `end()` retournent des objets du même type. Avec ce changement, `end()` peut retourner un objet sentinel, à l’image de ceux utilisés par les plages définies dans [range-v3](https://github.com/ericniebler/range-v3) et la spécification technique d’autres plages disponibles mais pas encore publiées. Pour plus d’informations, consultez [généralisation de la `for` boucle basée sur une plage](https://wg21.link/p0184r0).

## <a name="conformance-improvements-in-153"></a><a name="improvements_153"></a> Améliorations de la conformité dans 15,3

### <a name="constexpr-lambdas"></a>`constexpr` expressions lambda

Les expressions lambda peuvent désormais être utilisées dans les expressions constantes. Pour plus d’informations, consultez [ `constexpr` expressions lambda en C++](../cpp/lambda-expressions-constexpr.md).

### <a name="if-constexpr-in-function-templates"></a>`if constexpr` dans les modèles de fonctions

Un modèle de fonction peut contenir **`if constexpr`** des instructions pour activer la branche au moment de la compilation. Pour plus d’informations, consultez [ `if constexpr` instructions](../cpp/if-else-statement-cpp.md#if_constexpr).

### <a name="selection-statements-with-initializers"></a>Instructions Selection avec initialiseurs

Une **`if`** instruction peut inclure un initialiseur qui introduit une variable au niveau de la portée de bloc dans l’instruction elle-même. Pour plus d’informations, consultez [ `if` instructions with initializer](../cpp/if-else-statement-cpp.md#if_with_init).

### <a name="maybe_unused-and-nodiscard-attributes"></a>Attributs `[[maybe_unused]]` et `[[nodiscard]]`

Le nouvel attribut `[[maybe_unused]]` réduit au silence les avertissements lorsqu’une entité n’est pas utilisée. L’attribut `[[nodiscard]]` crée un avertissement si la valeur de retour d’un appel de fonction est ignorée. Pour plus d’informations, consultez [Attributes in C++](../cpp/attributes.md).

### <a name="using-attribute-namespaces-without-repetition"></a>Utilisation des espaces de noms d’attribut sans répétition

Nouvelle syntaxe pour activer uniquement un seul identificateur d’espace de noms dans une liste d’attributs. Pour plus d’informations, consultez [Attributes in C++](../cpp/attributes.md).

### <a name="structured-bindings"></a>Liaisons structurées

Il est désormais possible dans une déclaration unique de stocker une valeur avec des noms individuels pour ses composants, lorsque la valeur est un tableau, un `std::tuple` ou un `std::pair`, ou contient uniquement des membres de données non statiques publiques. Pour plus d’informations, consultez [Liaisons structurées](https://wg21.link/p0144r0) et [Retour de plusieurs valeurs à partir d’une fonction](../cpp/functions-cpp.md#multi_val).

### <a name="construction-rules-for-enum-class-values"></a>Règles de construction pour les valeurs `enum class`

Il existe désormais une conversion implicite pour les énumérations délimitées qui ne sont pas restrictives. Il convertit le type sous-jacent d’une énumération délimitée en l’énumération elle-même. La conversion est disponible lorsque sa définition n’introduit pas d’énumérateur et lorsque la source utilise une syntaxe d’initialisation de liste. Pour plus d’informations, consultez [Règles de construction pour les valeurs de classe enum](https://wg21.link/p0138r2) et [Énumérations](../cpp/enumerations-cpp.md#no_enumerators).

### <a name="capturing-this-by-value"></a>Capture de `*this` par valeur

L' **`*this`** objet dans une expression lambda peut désormais être capturé par valeur. Ce changement permet des scénarios dans lesquels l’expression lambda est invoquée dans des opérations parallèles et asynchrones, en particulier sur des architectures de machines plus récentes. Pour plus d’informations, consultez [Lambda Capture of \*this by Value as \[=,\*this\]](https://wg21.link/p0018r3).

### <a name="removing-operator-for-bool"></a>Suppression de `operator++` pour `bool`

`operator++` n’est plus pris en charge sur les **`bool`** types. Pour plus d’informations, consultez [Remove Deprecated operator++(bool)](https://wg21.link/p0002r1).

### <a name="removing-deprecated-register-keyword"></a>Suppression du mot clé `register` déconseillé

Le **`register`** mot clé, précédemment déconseillé (et ignoré par le compilateur), est maintenant supprimé du langage. Pour plus d’informations, consultez [Supprimer l’utilisation déconseillée du `register` mot clé](https://wg21.link/p0001r1).

## <a name="conformance-improvements-in-155"></a><a name="improvements_155"></a> Améliorations de la conformité dans 15,5

Les fonctionnalités marquées de \[ 14] sont disponibles sans condition, même en **`/std:c++14`** mode.

### <a name="new-compiler-switch-for-extern-constexpr"></a>Nouveau commutateur de compilateur pour `extern constexpr`

Dans les versions antérieures de Visual Studio, le compilateur offrait toujours une **`constexpr`** liaison interne variable, même quand la variable était marquée **`extern`** . Dans Visual Studio 2017 version 15,5, un nouveau commutateur de compilateur, [`/Zc:externConstexpr`](../build/reference/zc-externconstexpr.md) , permet un comportement correct et conforme aux normes. Pour plus d’informations, consultez [Liaison extern constexpr](#extern_linkage).

### <a name="removing-dynamic-exception-specifications"></a>Suppression des spécifications d’exceptions dynamiques

[P0003R5](https://wg21.link/p0003r5)Les spécifications d’exceptions dynamiques ont été dépréciées dans C++11. La fonctionnalité est supprimée dans C++17, mais la spécification (toujours) dépréciée `throw()` est conservée uniquement comme alias pour `noexcept(true)`. Pour plus d’informations, consultez [Suppression des spécifications d’exceptions dynamiques et noexcept](#noexcept_removal).

### `not_fn()`

[P0005R4](https://wg21.link/p0005r4) `not_fn` vient remplacer `not1` et `not2`.

### <a name="rewording-enable_shared_from_this"></a>Reformulation de `enable_shared_from_this`

[P0033R1](https://wg21.link/p0033r1) `enable_shared_from_this` a été ajouté dans C++11. La norme C++17 met à jour la spécification pour mieux gérer certains cas extrêmes. \[14,5

### <a name="splicing-maps-and-sets"></a>Ajout de mappages et d’ensembles

[P0083R3](https://wg21.link/p0083r3) Cette fonctionnalité permet l’extraction de nœuds à partir de conteneurs associatifs (c’est-à-dire,,, `map` `set` `unordered_map` , `unordered_set` ) qui peuvent ensuite être modifiés et insérés dans le même conteneur ou dans un conteneur différent qui utilise le même type de nœud. (Un cas d’usage courant consiste à extraire un nœud d’un `std::map`, à changer la clé et à réinsérer le nœud.)

### <a name="deprecating-vestigial-library-parts"></a>Composants de bibliothèque rudimentaires dépréciés

[P0174R2](https://wg21.link/p0174r2) Plusieurs fonctionnalités de la bibliothèque standard C++ ont été remplacées par de nouvelles fonctionnalités au fil des années, ou ont été jugées inutiles ou problématiques. Ces fonctionnalités sont officiellement dépréciées dans C++17.

### <a name="removing-allocator-support-in-stdfunction"></a>Suppression de la prise en charge d’un allocateur dans `std::function`

[P0302R1](https://wg21.link/p0302r1) Dans les versions antérieures à C++17, le modèle de classe `std::function` avait plusieurs constructeurs avec un argument allocateur. Toutefois, l’utilisation d’allocateurs dans ce contexte était problématique et la sémantique n’était pas claire. Les constructeurs problématiques ont été supprimés.

### <a name="fixes-for-not_fn"></a>Corrections pour `not_fn()`

[P0358R1](https://wg21.link/p0358r1) La nouvelle formulation pour `std::not_fn` permet de prendre en charge la propagation de la catégorie de valeur quand un wrapper est appelé.

### <a name="shared_ptrt-shared_ptrtn"></a>`shared_ptr<T[]>`, `shared_ptr<T[N]>`

[P0414R2](https://wg21.link/p0414r2) Fusion des modifications apportées à `shared_ptr` dans C++17 dans Library Fundamentals. \[14,5

### <a name="fixing-shared_ptr-for-arrays"></a>Correction de `shared_ptr` pour les tableaux

[P0497R0](https://wg21.link/p0497r0) Correctifs apportés à la prise en charge de shared_ptr pour les tableaux. \[14,5

### <a name="clarifying-insert_return_type"></a>Clarification de `insert_return_type`

[P0508R0](https://wg21.link/p0508r0) Les conteneurs associatifs ou non ordonnés avec des clés uniques ont une fonction membre `insert` qui retourne un type imbriqué `insert_return_type`. Le type de retour est maintenant défini comme une spécialisation d’un type qui est paramétré sur les éléments Iterator et NodeType du conteneur.

### <a name="inline-variables-for-the-standard-library"></a>Variables inline pour la bibliothèque standard

[P0607R0](https://wg21.link/p0607r0)

### <a name="annex-d-features-deprecated"></a>Fonctionnalités dépréciées de l’annexe D

L’annexe D de la norme C++ contient toutes les fonctionnalités qui ont été dépréciées, notamment `shared_ptr::unique()`, `<codecvt>` et `namespace std::tr1`. Quand le **`/std:c++17`** commutateur du compilateur est défini, presque toutes les fonctionnalités de la bibliothèque standard de l’annexe D sont marquées comme dépréciées. Pour plus d’informations, consultez les [fonctionnalités de la bibliothèque standard dans l’annexe D sont marquées comme dépréciées](#annex_d).

L' `std::tr2::sys` espace de noms dans `<experimental/filesystem>` émet désormais un avertissement de désapprobation sous par **`/std:c++14`** défaut, et est maintenant supprimé sous **`/std:c++17`** par défaut.

La conformité est améliorée dans `<iostream>`, car l’utilisation d’une extension non standard (spécialisations de classe explicites) n’est plus nécessaire.

La bibliothèque standard utilise désormais les modèles de variable en interne.

La bibliothèque standard a été mise à jour en réponse aux modifications du compilateur C++ 17. Les mises à jour incluent l’ajout de **`noexcept`** dans le système de type et la suppression des spécifications d’exceptions dynamiques.

## <a name="conformance-improvements-in-156"></a><a name="improvements_156"></a> Améliorations de la conformité dans 15,6

### <a name="c17-library-fundamentals-v1"></a>C++17 - Library Fundamentals V1

[P0220R1](https://wg21.link/p0220r1) incorpore la spécification technique relative aux notions de base des bibliothèques (Library Fundamentals TS) pour C++17 à la norme. Couvre les mises à jour de,,,,,, \<experimental/tuple> \<experimental/optional> \<experimental/functional> \<experimental/any> \<experimental/string_view> \<experimental/memory> \<experimental/memory_resource> et \<experimental/algorithm> .

### <a name="c17-improving-class-template-argument-deduction-for-the-standard-library"></a>C++ 17 : amélioration de la déduction d’argument de modèle de classe pour la bibliothèque standard

[P0739R0](https://wg21.link/p0739r0)`adopt_lock_t` est déplacé au début de la liste des paramètres de `scoped_lock` pour garantir une utilisation cohérente de `scoped_lock`. Le constructeur `std::variant` est autorisé à participer à la résolution de surcharge dans davantage de cas pour permettre l’assignation de copie.

## <a name="conformance-improvements-in-157"></a><a name="improvements_157"></a> Améliorations de la conformité dans 15,7

### <a name="c17-rewording-inheriting-constructors"></a>C++ 17 : reformulation des constructeurs qui héritent

[P0136R1](https://wg21.link/p0136r1) spécifie qu’une **`using`** déclaration qui nomme un constructeur rend désormais les constructeurs de classe de base correspondants visibles aux initialisations de la classe dérivée, plutôt que de déclarer des constructeurs de classes dérivées supplémentaires. Cette reformulation est un changement à compter de C++14. Dans Visual Studio 2017 version 15,7 et versions ultérieures, en **`/std:c++17`** mode, le code valide en c++ 14 et utilise des constructeurs qui héritent peut ne pas être valide ou peut avoir une sémantique différente.

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

L’exemple suivant illustre le **`/std:c++17`** comportement dans Visual Studio 15,7 :

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

### <a name="c17-extended-aggregate-initialization"></a>C++ 17 : initialisation d’agrégats étendue

[P0017R1](https://wg21.link/p0017r1)

Si le constructeur d’une classe de base n’est pas public, mais qu’il est accessible à une classe dérivée, alors sous **`/std:c++17`** mode dans Visual Studio 2017 version 15,7, vous ne pouvez plus utiliser d’accolades vides pour initialiser un objet du type dérivé.
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
L’exemple suivant montre le comportement C++ 17 dans Visual Studio version 15,7 en **`/std:c++17`** mode :

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

### <a name="c17-declaring-non-type-template-parameters-with-auto"></a>C++ 17 : déclaration de paramètres de modèle sans type avec auto

[P0127R2](https://wg21.link/p0127r2)

En **`/std:c++17`** mode, le compilateur peut maintenant déduire le type d’un argument de modèle sans type déclaré avec **`auto`** :

```cpp
template <auto x> constexpr auto constant = x;

auto v1 = constant<5>;      // v1 == 5, decltype(v1) is int
auto v2 = constant<true>;   // v2 == true, decltype(v2) is bool
auto v3 = constant<'a'>;    // v3 == 'a', decltype(v3) is char
```

L’une des conséquences de cette nouvelle fonctionnalité est que le code valide dans C++14 peut être non valide ou avoir une sémantique différente. Par exemple, certaines surcharges qui étaient précédemment non valides sont à présent valides. L’exemple suivant montre du code C++14 dont la compilation réussit car l’appel à `example(p)` est lié à `example(void*);`. Dans Visual Studio 2017 version 15,7, en **`/std:c++17`** mode, le `example` modèle de fonction est la meilleure correspondance.

```cpp
template <int N> struct A;
template <typename T, T N> int example(A<N>*) = delete;

void example(void *);

void sample(A<0> *p)
{
    example(p); // OK in C++14
}
```

L’exemple suivant montre le code C++ 17 dans Visual Studio 15,7 en **`/std:c++17`** mode :

```cpp
template <int N> struct A;
template <typename T, T N> int example(A<N>*);

void example(void *);

void sample(A<0> *p)
{
    example(p); // C2280: 'int example<int,0>(A<0>*)': attempting to reference a deleted function
}
```

### <a name="c17-elementary-string-conversions-partial"></a>C++ 17 : conversions de chaînes élémentaires (partielles)

[P0067R5](https://wg21.link/p0067r5) Fonctions de bas niveau indépendantes des paramètres régionaux pour les conversions entre entiers et chaînes et entre nombres à virgule flottante et chaînes.

### <a name="c20-avoiding-unnecessary-decay-partial"></a>C++ 20 : éviter la désintégration inutile (partielle)

[P0777R1](https://wg21.link/p0777r1) Ajoute une distinction entre le concept de « dégradation » et la simple opération consistant à supprimer const ou des qualificateurs de référence.  Le nouveau trait de type `remove_reference_t` remplace `decay_t` dans certains contextes. La prise en charge de `remove_cvref_t` est implémentée dans Visual Studio 2019.

### <a name="c17-parallel-algorithms"></a>C++ 17 : algorithmes parallèles

[P0024R2](https://wg21.link/p0024r2) La spécification technique relative au parallélisme (Parallelism TS) est intégrée à la norme, avec des modifications mineures.

### <a name="c17-hypotx-y-z"></a>C++17 : `hypot(x, y, z)`

[P0030R1](https://wg21.link/p0030r1) Ajoute trois nouvelles surcharges à `std::hypot` , pour les types **`float`** , **`double`** et **`long double`** , chacun d’entre eux ayant trois paramètres d’entrée.

### <a name="c17-filesystem"></a>C++17 : \<filesystem>

[P0218R1](https://wg21.link/p0218r1) Intègre la spécification technique relative au système de fichiers (File System TS) à la norme, avec quelques modifications de formulation.

### <a name="c17-mathematical-special-functions"></a>C++ 17 : fonctions mathématiques spéciales

[P0226R1](https://wg21.link/p0220r1) Adopte les spécifications techniques précédentes pour les fonctions mathématiques spéciales dans l' \<cmath> en-tête standard.

### <a name="c17-deduction-guides-for-the-standard-library"></a>C++ 17 : guides de déduction pour la bibliothèque standard

[P0433R2](https://wg21.link/p0433r2) Met à jour STL pour tirer parti de l’adoption par C++17 de [P0091R3](https://wg21.link/p0091r3), qui ajoute la prise en charge de la déduction d’arguments de modèle de classe.

### <a name="c17-repairing-elementary-string-conversions"></a>C++ 17 : réparation des conversions de chaînes élémentaires

[P0682R1](https://wg21.link/p0682r1) Déplacez les nouvelles fonctions de conversion de chaîne élémentaires de P0067R5 dans un nouvel en-tête \<charconv> et apportez d’autres améliorations, notamment la modification de la gestion des erreurs à utiliser `std::errc` au lieu de `std::error_code` .

### <a name="c17-constexpr-for-char_traits-partial"></a>C++17 : `constexpr` pour `char_traits` (partiel)

[P0426R1](https://wg21.link/p0426r1) Modifications apportées aux `std::traits_type` fonctions membres `length` , `compare` et `find` pour rendre `std::string_view` utilisables dans les expressions constantes. (Dans Visual Studio 2017 version 15.6, prise en charge pour Clang/LLVM uniquement. Dans la version 15.7 Preview 2, la prise en charge est presque complète pour ClXX.)

## <a name="conformance-improvements-in-159"></a><a name="improvements_159"></a> Améliorations de la conformité dans 15,9

### <a name="left-to-right-evaluation-order-for-operators-----and-"></a>Ordre d’évaluation de gauche à droite pour les opérateurs `->*`, `[]`, `>>`, et `<<`

À compter de C++17, les opérandes des opérateurs `->*`, `[]`, `>>`, et `<<` doivent être évalués de gauche à droite. Il existe deux cas dans lesquels le compilateur est incapable de garantir cet ordre :

- lorsqu’une des expressions de l’opérande est un objet passé par une valeur ou contient un objet passé par une valeur, ou

- en cas de compilation à l’aide de **`/clr`** , et l’un des opérandes est un champ d’un objet ou d’un élément de tableau.

Le compilateur émet l’avertissement [C4866](../error-messages/compiler-warnings/c4866.md) quand il ne peut pas garantir l’évaluation de gauche à droite. Le compilateur génère cet avertissement uniquement si **`/std:c++17`** ou une version ultérieure est spécifié, car l’ordre de gauche à droite de ces opérateurs a été introduit dans c++ 17.

Pour résoudre cet avertissement, commencez par déterminer si l’évaluation de gauche à droite des opérandes est nécessaire. Par exemple, il peut être nécessaire lorsque l’évaluation des opérandes peut produire des effets secondaires dépendants de la commande. L’ordre dans lequel les opérandes sont évalués n’a aucun effet observable dans de nombreux cas. Si l’ordre d’évaluation doit être de gauche à droite, réfléchissez si vous pouvez passer les opérandes par référence const à la place. Cette modification supprime l’avertissement dans l’exemple de code suivant :

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

## <a name="bug-fixes-in-visual-studio-2017-rtw-version-150"></a><a name="update_150"></a> Correctifs de bogues dans Visual Studio 2017 RTW (version 15.0)

### <a name="copy-list-initialization"></a>Copy-list-initialization

Visual Studio 2017 génère correctement des erreurs de compilateur liées à la création d’objets à l’aide de listes d’initialiseurs. Ces erreurs n’ont pas été interceptées dans Visual Studio 2015 et peuvent entraîner des blocages ou un comportement d’exécution non défini. Comme pour N4594 13.3.1.7 P1, dans l’initialisation de copie de liste, le compilateur est tenu de prendre en compte un constructeur explicite pour la résolution de surcharge. Toutefois, elle doit déclencher une erreur si cette surcharge particulière est choisie.

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

Dans Visual Studio 2015, le compilateur a traité par erreur l’initialisation de copie de liste de la même façon que l’initialisation de copie normale : il considérait uniquement les constructeurs de conversion pour la résolution de surcharge. Dans l’exemple suivant, Visual Studio 2015 choisit `MyInt(23)` . Visual Studio 2017 génère correctement l’erreur.

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

Visual Studio 2017 émet désormais un avertissement correct pour les typedefs déconseillés déclarés dans une classe ou un struct. L’exemple suivant compile sans avertissements dans Visual Studio 2015. Il génère l’C4996 dans Visual Studio 2017.

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

### `constexpr`

Visual Studio 2017 génère correctement une erreur quand l’opérande de gauche d’une opération à évaluation conditionnelle n’est pas valide dans un contexte constexpr. Le code suivant se compile dans Visual Studio 2015, mais pas dans Visual Studio 2017, où il déclenche C3615 `constexpr function 'f' cannot result in a constant expression` :

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

Pour corriger l’erreur, déclarez la `array::size()` fonction comme **`constexpr`** ou supprimez le **`constexpr`** qualificateur de `f` .

### <a name="class-types-passed-to-variadic-functions"></a>Types de classe transmis aux fonctions variadiques

Dans Visual Studio 2017, les classes ou les structs passés à une fonction variadiques telle que `printf` doit être copiable de manière triviale. Quand de tels objets sont passés, le compilateur effectue simplement une copie au niveau du bit et n’appelle pas le constructeur ou le destructeur.

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

Pour les chaînes générées et gérées à l’aide de `CString` , le fourni `operator LPCTSTR()` doit être utilisé pour effectuer un cast d’un `CString` objet en pointeur C attendu par la chaîne de format.

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

Pour corriger l’erreur, déclarez `operator int()` comme **`const`** .

### <a name="access-checking-on-qualified-names-in-templates"></a>Contrôle d’accès sur les noms qualifiés dans les modèles

Les versions précédentes du compilateur n’ont pas vérifié l’accès aux noms qualifiés dans certains contextes de modèle. Ce problème peut interférer avec le comportement SFINAE attendu, où la substitution est supposée échouer en raison de l’inaccessibilité d’un nom. Elle peut avoir provoqué un incident ou un comportement inattendu lors de l’exécution, car le compilateur a incorrectement appelé la surcharge incorrecte de l’opérateur. Dans Visual Studio 2017, une erreur de compilateur est générée. L’erreur spécifique peut varier, mais elle est généralement C2672 `no matching overloaded function found` . Le code suivant se compile dans Visual Studio 2015, mais génère une erreur dans Visual Studio 2017 :

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

Dans Visual Studio 2015 et les versions antérieures, le compilateur n’a pas diagnostiqué toutes les listes d’arguments de modèle manquantes. Cela ne signifie pas que le modèle manquant apparaissait dans une liste de paramètres de modèle : par exemple, lorsqu’une partie d’un argument de modèle par défaut ou un paramètre de modèle sans type était manquant. Ce problème peut entraîner un comportement imprévisible, y compris des pannes du compilateur ou un comportement inattendu au moment de l’exécution. Le code suivant se compile dans Visual Studio 2015, mais génère une erreur dans Visual Studio 2017.

```cpp
template <class T> class ListNode;
template <class T> using ListNodeMember = ListNode<T> T::*;
template <class T, ListNodeMember M> class ListHead; // C2955: 'ListNodeMember': use of alias
                                                     // template requires template argument list

// correct:  template <class T, ListNodeMember<T> M> class ListHead;
```

### <a name="expression-sfinae"></a>Fonctionnalité SFINAE pour les expressions

Pour prendre en charge expression-SFINAE, le compilateur analyse désormais les **`decltype`** arguments quand les modèles sont déclarés au lieu d’être instanciés. Par conséquent, si une spécialisation non dépendante est trouvée dans l’argument decltype, elle n’est pas différée à l’instanciation. Elle est traitée immédiatement, et toute erreur résultante est diagnostiquée à ce moment-là.

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

Selon la norme C++, une classe déclarée dans un espace de noms anonyme a une liaison interne et, par conséquent, ne peut pas être exportée. Dans Visual Studio 2015 et versions antérieures, cette règle n’était pas appliquée. Dans Visual Studio 2017, la règle est partiellement appliquée. Dans Visual Studio 2017, l’exemple suivant génère l’erreur C2201 : `const anonymous namespace::S1::vftable: must have external linkage in order to be exported/imported.`

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

Dans Visual Studio 2015 et antérieur, le compilateur identifiait à tort une propriété par défaut en tant qu’indexeur par défaut dans certaines circonstances. Il était possible de contourner le problème en utilisant l’identificateur **`default`** pour accéder à la propriété. La solution de contournement elle-même est devenue problématique après que **`default`** a été introduit comme mot clé dans c++ 11. Dans Visual Studio 2017, les bogues qui nécessitaient la solution de contournement ont été corrigés. Le compilateur génère désormais une erreur lorsque **`default`** est utilisé pour accéder à la propriété par défaut d’une classe.

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

## <a name="bug-fixes-in-153"></a><a name="update_153"></a> Correctifs de bogues dans 15,3

### <a name="calls-to-deleted-member-templates"></a>Appels à des modèles membres supprimés

Dans les versions précédentes de Visual Studio, le compilateur ne parviendrait pas à émettre une erreur pour les appels incorrects à un modèle de membre supprimé. Ces appels pourraient provoquer des incidents lors de l’exécution. Le code suivant génère désormais C2280, `'int S<int>::f<int>(void)': attempting to reference a deleted function` :

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

Pour corriger l’erreur, déclarez `i` comme **`int`** .

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

Désormais, le compilateur émet un avertissement s’il trouve cette erreur au moment de la compilation : un objet natif avec un constructeur de copie supprimé est passé entre une limite native et managée par valeur. Pour les cas où le compilateur ne sait rien au moment de la compilation, il injecte une vérification à l’exécution afin que le programme appelle `std::terminate` immédiatement dès qu’un marshaling incorrect se produit. Dans Visual Studio 2017 version 15,3, le code suivant génère un avertissement C4606 `'A': passing argument by value across native and managed boundary requires valid copy constructor. Otherwise, the runtime behavior is undefined.`

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

Les API WinRT publiées pour l’expérimentation et les commentaires sont décorées avec `Windows.Foundation.Metadata.ExperimentalAttribute`. Dans Visual Studio 2017 version 15,3, le compilateur génère un avertissement C4698 pour cet attribut. Certaines API dans les versions précédentes du SDK Windows ont déjà été décorées avec l’attribut et les appels à ces API déclenchent cet avertissement du compilateur. L’attribut des nouveaux kits de développement logiciel Windows est supprimé de tous les types fournis. Si vous utilisez un SDK plus ancien, vous devez supprimer ces avertissements pour tous les appels aux types fournis.

Le code suivant génère l’avertissement C4698 : `'Windows::Storage::IApplicationDataStatics2::GetForUserAsync' is for evaluation purposes only and is subject to change or removal in future updates` :

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

Visual Studio 2017 version 15,3 génère une erreur pour une définition hors ligne d’une fonction membre de modèle qui n’a pas été déclarée dans la classe. Le code suivant génère désormais l’erreur C2039 : `'f': is not a member of 'S'` :

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

### <a name="attempting-to-take-the-address-of-this-pointer"></a>Tentative de prendre l’adresse du pointeur `this`

En C++, **`this`** est un prvalue de type pointeur vers X. Vous ne pouvez pas prendre l’adresse de **`this`** ou la lier à une référence lvalue. Dans les versions précédentes de Visual Studio, le compilateur vous permettait de contourner cette restriction en utilisant un cast. Dans Visual Studio 2017 version 15.3, le compilateur génère l’erreur C2664.

### <a name="conversion-to-an-inaccessible-base-class"></a>Conversion vers une classe de base inaccessible

Visual Studio 2017 version 15.3 génère une erreur quand vous essayez de convertir un type en une classe de base qui n’est pas accessible. Le compilateur génère désormais l’erreur C2243 : `'type cast': conversion from 'D *' to 'B *' exists, but is inaccessible` . Le code suivant est incorrect et peut éventuellement provoquer un incident lors de l’exécution. Le compilateur produit désormais C2243 lorsqu’il voit du code comme celui-ci :

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

Les arguments par défaut ne sont pas autorisés sur les définitions hors ligne des fonctions membres dans les classes de modèles. Le compilateur émet un avertissement sous **`/permissive`** , et une erreur matérielle sous [`/permissive-`](../build/reference/permissive-standards-conformance.md) .

Dans les versions précédentes de Visual Studio, le code incorrect suivant peut entraîner un incident lors de l’exécution. Visual Studio 2017 version 15,3 génère un avertissement C5034 : `'A\<T>::f': an out-of-line definition of a member of a class template cannot have default arguments` :

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

Dans Visual Studio 2017 version 15,3, l’utilisation de `offsetof(T, m)` où *m* est un « désignateur de membre composé » génère un avertissement quand vous compilez avec l' **`/Wall`** option. Le code suivant est incorrect et peut éventuellement provoquer un incident lors de l’exécution. Visual Studio 2017 version 15,3 génère un avertissement C4841 : `non-standard extension used: compound member designator in offsetof` :

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

Dans Visual Studio 2017 version 15.3, l’utilisation de `offsetof(T, m)` où *m* fait référence à des données membres static ou une fonction membre aboutit à une erreur. Le code suivant génère l’erreur C4597 : `undefined behavior: offsetof applied to member function 'example'` et l’erreur C4597 : `undefined behavior: offsetof applied to static data member 'sample'` :

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

### <a name="new-warning-on-__declspec-attributes"></a><a name="declspec"></a> Nouvel avertissement sur les attributs `__declspec`

Dans Visual Studio 2017 version 15.3, le compilateur n’ignore plus les attributs si `__declspec(...)` est appliqué avant une spécification de liaison `extern "C"` externe. Avant, le compilateur ignorait l’attribut, ce qui pouvait avoir des implications lors de l’exécution. Lorsque les **`/Wall`** **`/WX`** options et sont définies, le code suivant génère l’avertissement C4768 : `__declspec attributes before linkage specification are ignored` :

```cpp
__declspec(noinline) extern "C" HRESULT __stdcall //C4768
```

Pour résoudre l’avertissement, placez `extern "C"` d’abord :

```cpp
extern "C" __declspec(noinline) HRESULT __stdcall
```

Cet avertissement est désactivé par défaut dans 15,3, mais activé par défaut dans 15,5, et n’affecte que le code compilé avec  **`/Wall`** **`/WX`** .

### <a name="decltype-and-calls-to-deleted-destructors"></a>`decltype` et appels à des destructeurs supprimés

Dans les versions précédentes de Visual Studio, le compilateur ne détectait pas quand un appel à un destructeur supprimé s’est produit dans le contexte de l’expression associée à **`decltype`** . Dans Visual Studio 2017 version 15,3, le code suivant génère l’erreur C2280 : `'A<T>::~A(void)': attempting to reference a deleted function` :

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

La version RTW de Visual Studio 2017 a subi une régression : le compilateur C++ n’émet pas de diagnostic pour une variable non initialisée **`const`** . Cette régression a été corrigée dans Visual Studio 2017 version 15.3. Le code suivant génère désormais l’avertissement C4132 : `'Value': const object should be initialized` :

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

L’avertissement est exclu sous **`/Wv:18`** et est activé par défaut sous le niveau d’avertissement W2.

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

Parfois, les versions précédentes du compilateur ne parvenaient pas à détecter une ambiguïté lors de la découverte de plusieurs candidats par le biais simultanément des déclarations et des recherches dépendantes d’arguments. Cet échec pouvait conduire à choisir une surcharge incorrecte et entraîner un comportement inattendu au moment de l’exécution. Dans l’exemple suivant, Visual Studio 2017 version 15,3 déclenche correctement C2668 `'f': ambiguous call to overloaded function` :

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

Les déclarations de fonction locale masquent la déclaration de fonction dans la portée englobante et désactivent la recherche dépendante d’argument. Toutefois, les versions précédentes du compilateur ont toujours effectué une recherche dépendante d’un argument dans ce cas. Cela peut entraîner la sélection incorrecte de la surcharge et un comportement inattendu au moment de l’exécution. En règle générale, l’erreur est causée par une signature incorrecte de la déclaration de fonction locale. Dans l’exemple suivant, Visual Studio 2017 version 15,3 déclenche correctement C2660 `'f': function does not take two arguments` :

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

Les membres de classe sont initialisés dans l’ordre dans lequel ils sont déclarés, et non dans l’ordre dans lequel ils apparaissent dans les listes d’initialiseurs. Les versions précédentes du compilateur n’avertissaient pas lorsque l’ordre de la liste d’initialiseurs était différent de celui des déclarations. Ce problème peut entraîner un comportement d’exécution non défini si l’initialisation d’un membre dépendait d’un autre membre de la liste déjà initialisé. Dans l’exemple suivant, Visual Studio 2017 version 15,3 (avec **`/Wall`** ) génère un avertissement C5038 : `data member 'A::y' will be initialized after data member 'A::x'` :

```cpp
struct A
{
    A(int a) : y(a), x(y) {} // Initialized in reverse, y reused
    int x;
    int y;
};
```

Pour résoudre le problème, réorganisez la liste d’initialiseurs afin d’avoir le même ordre que dans les déclarations. Un avertissement similaire est déclenché lorsqu’un ou les deux initialiseurs se réfèrent aux membres de classe de base.

Cet avertissement est désactivé par défaut et affecte uniquement le code compilé avec **`/Wall`** .

## <a name="bug-fixes-and-other-behavior-changes-in-155"></a><a name="update_155"></a> Correctifs de bogues et autres changements de comportement dans 15,5

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

Dans l’exemple ci-dessus, le problème provient de l’utilisation de fonctions de deux types différents (const/non-const et pack/non-pack). Pour éviter l’erreur du compilateur, utilisez des fonctions d’un même type. Le compilateur peut ensuite trier les fonctions de manière non ambiguë.

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

Les gestionnaires de référence au type tableau ou fonction ne sont plus mis en correspondance pour les objets exception. Le compilateur applique maintenant cette règle correctement et déclenche un avertissement de niveau 4. En outre, il ne correspond plus à un gestionnaire de `char*` ou `wchar_t*` à un littéral de chaîne lorsque **`/Zc:strictStrings`** est utilisé.

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

### <a name="stdtr1-namespace-is-deprecated"></a> L’espace de noms <a name="tr1"></a> `std::tr1` est déprécié

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

### <a name="standard-library-features-in-annex-d-are-marked-as-deprecated"></a><a name="annex_d"></a> Les fonctionnalités de la bibliothèque standard de l’annexe D sont marquées comme dépréciées

Quand le **`/std:c++17`** commutateur du compilateur en mode est défini, presque toutes les fonctionnalités de la bibliothèque standard de l’annexe D sont marquées comme dépréciées.

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

Dans Visual Studio 2017 version 15.5, les avertissements C4001 et C4179 ne sont plus générés par le compilateur C. Auparavant, elles étaient uniquement émises sous le **`/Za`** commutateur du compilateur.  Ces avertissements ne sont plus utiles, car les commentaires sur une seule ligne sont intégrés à la norme C depuis la version C99.

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

Lorsque le code n’a pas besoin d’être à compatibilité descendante, vous pouvez éviter l’avertissement en supprimant la suppression de C4001/C4179. Si le code doit offrir une compatibilité descendante, supprimez uniquement C4619.

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

### <a name="extern-constexpr-linkage"></a><a name="extern_linkage"></a>`extern constexpr`liaison

Dans les versions antérieures de Visual Studio, le compilateur a toujours donné une **`constexpr`** liaison interne variable même lorsque la variable a été marquée **`extern`** . Dans Visual Studio 2017 version 15,5, un nouveau commutateur de compilateur ( **`/Zc:externConstexpr`** ) permet un comportement correct et conforme aux normes. Cela deviendra le comportement par défaut.

```cpp
extern constexpr int x = 10;
```

```Output
error LNK2005: "int const x" already defined
```

Si un fichier d’en-tête contient une variable déclarée **`extern constexpr`** , il doit être marqué `__declspec(selectany)` pour que ses déclarations dupliquées soient correctement combinées :

```cpp
extern constexpr __declspec(selectany) int x = 10;
```

### <a name="typeid-cant-be-used-on-incomplete-class-type"></a>`typeid` ne peut pas être utilisé sur un type de classe incomplet

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

### <a name="dynamic-exception-specification-removal-and-noexcept"></a><a name="noexcept_removal"></a> Suppression des spécifications d’exceptions dynamiques et `noexcept`

En C++ 17, `throw()` est un alias pour **`noexcept`** , `throw(<type list>)` et `throw(...)` sont supprimés, et certains types peuvent inclure **`noexcept`** . Ces changements entraînent parfois des problèmes de compatibilité avec le code conforme à C++14 ou une version antérieure. Le **`/Zc:noexceptTypes-`** commutateur peut être utilisé pour revenir à la version c++ 14 de **`noexcept`** tout en utilisant le mode c++ 17 en général. Cela vous permet de mettre à jour votre code source pour le rendre conforme à C++17 sans pour autant avoir à réécrire tout votre code `throw()`.

Le compilateur diagnostique également les spécifications d’exceptions plus incompatibles dans les déclarations en mode C++ 17 ou avec [`/permissive-`](../build/reference/permissive-standards-conformance.md) avec le nouvel avertissement avertissements c5043.

Le code suivant génère avertissements c5043 et C5040 dans Visual Studio 2017 version 15,5 quand le **`/std:c++17`** commutateur est appliqué :

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

Pour supprimer les erreurs tout en utilisant **`/std:c++17`** , ajoutez le **`/Zc:noexceptTypes-`** commutateur à la ligne de commande, ou mettez à jour votre code pour utiliser **`noexcept`** , comme illustré dans l’exemple suivant :

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

Les **`constexpr`** membres de données statiques sont désormais implicitement, ce qui **`inline`** signifie que leur déclaration dans une classe est désormais leur définition. L’utilisation d’une définition hors ligne pour un **`static constexpr`** membre de données est redondante et maintenant dépréciée. Dans Visual Studio 2017 version 15,5, lorsque le **`/std:c++17`** commutateur est appliqué, le code suivant génère désormais un avertissement C5041 `'size': out-of-line definition for constexpr static data member is not needed and is deprecated in C++17` :

```cpp
struct X {
    static constexpr int size = 3;
};
const int X::size; // C5041
```

### <a name="extern-c-__declspec-warning-c4768-now-on-by-default"></a>L’avertissement C4768 `extern "C" __declspec(...)` est maintenant activé par défaut

L’avertissement, ajouté dans Visual Studio 2017 version 15.3, était désactivé par défaut. Dans Visual Studio 2017 version 15.5, l’avertissement est activé par défaut. Pour plus d’informations, consultez [nouvel avertissement sur les \_ \_ attributs declspec](#declspec).

### <a name="defaulted-functions-and-__declspecnothrow"></a>Fonctions utilisées par défaut et `__declspec(nothrow)`

Auparavant, le compilateur autorisait la déclaration de fonctions par défaut à l’aide de `__declspec(nothrow)` quand les fonctions de base/membres correspondantes autorisaient les exceptions. Ce comportement non conforme à la norme C++ peut entraîner un comportement inattendu au moment de l’exécution. La norme exige que ces fonctions soient marquées comme supprimées en cas de non-correspondance d’une spécification d’exception.  Sous **`/std:c++17`** , le code suivant déclenche C2280 `attempting to reference a deleted function. Function was implicitly deleted because the explicit exception specification is incompatible with that of the implicit declaration.`

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

### <a name="noexcept-and-partial-specializations"></a>`noexcept` et spécialisations partielles

Avec **`noexcept`** dans le système de type, les spécialisations partielles pour la correspondance de types « pouvant être appelés » spécifiques peuvent ne pas se compiler ou ne pas choisir le modèle principal, en raison d’une spécialisation partielle manquante pour les pointeurs vers les fonctions noexcept.

Dans ce cas, vous devrez peut-être ajouter des spécialisations partielles supplémentaires pour gérer les **`noexcept`** pointeurs de fonction et les **`noexcept`** pointeurs vers des fonctions membres. Ces surcharges sont valides uniquement dans le **`/std:c++17`** mode. Si vous devez garantir la compatibilité descendante avec C++14 et que votre code est destiné à être utilisé par d’autres personnes, vous devez protéger ces nouvelles surcharges à l’intérieur de directives `#ifdef`. Si vous travaillez dans un module autonome, au lieu d’utiliser des gardes, `#ifdef` vous pouvez simplement compiler avec le **`/Zc:noexceptTypes-`** commutateur.

Le code suivant est compilé sous **`/std:c++14`** mais échoue sous **`/std:c++17`** avec `error C2027: use of undefined type 'A<T>'` :

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

Le code suivant est correctement sous **`/std:c++17`** , car le compilateur choisit la nouvelle spécialisation partielle `A<void (*)() noexcept>` :

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

## <a name="bug-fixes-and-other-behavior-changes-in-157"></a><a name="update_157"></a> Correctifs de bogues et autres changements de comportement dans 15,7

### <a name="c17-default-argument-in-the-primary-class-template"></a>C++ 17 : argument par défaut dans le modèle de classe primaire

Ce changement de comportement est une condition préalable pour la [Déduction d’arguments de modèle pour les modèles de classe - P0091R3](https://wg21.link/p0091r3).

Auparavant, le compilateur ignorait l’argument par défaut dans le modèle de classe primaire :

```cpp
template<typename T>
struct S {
    void f(int = 0);
};

template<typename T>
void S<T>::f(int = 0) {} // Re-definition necessary
```

En **`/std:c++17`** mode dans Visual Studio 2017 version 15,7, l’argument par défaut n’est pas ignoré :

```cpp
template<typename T>
struct S {
    void f(int = 0);
};

template<typename T>
void S<T>::f(int) {} // Default argument is used
```

### <a name="dependent-name-resolution"></a>Résolution de noms indépendante

Ce changement de comportement est une condition préalable pour la [Déduction d’arguments de modèle pour les modèles de classe - P0091R3](https://wg21.link/p0091r3).

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

Visual Studio 2017 version 15,7, en **`/std:c++17`** mode, requiert le **`typename`** mot clé dans l' **`using`** instruction dans D. Sans **`typename`** , le compilateur déclenche l’avertissement C4346 : `'B<T*>::type': dependent name is not a type` et l’erreur C2061 : `syntax error: identifier 'type'` :

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

Dans Visual Studio 2017 version 15,7 en **`/std:c++17`** mode, le niveau d’avertissement C4834 `discarding return value of function with 'nodiscard' attribute` est augmenté de W3 à W1. Vous pouvez désactiver l’avertissement avec un cast en **`void`** ou en passant **`/wd:4834`** au compilateur

```cpp
[[nodiscard]] int f() { return 0; }

int main() {
    f(); // warning: discarding return value
         // of function with 'nodiscard'
}
```

### <a name="variadic-template-constructor-base-class-initialization-list"></a>Liste d’initialisation de classe de base du constructeur de modèle variadique

Dans les éditions précédentes de Visual Studio, une liste d’initialisation de classe de base du constructeur de modèle variadique dont des arguments de modèle étaient manquants était autorisée par erreur sans signaler d’erreur. Dans Visual Studio 2017 version 15.7, une erreur de compilateur est générée.

L’exemple de code suivant dans Visual Studio 2017 version 15,7 génère une erreur C2614 : `D<int>: illegal member initialization: 'B' is not a base or member` .

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

Pour corriger l’erreur, remplacez l’expression B () par B \<T> ().

### <a name="constexpr-aggregate-initialization"></a>Initialisation d'agrégats `constexpr`

Les versions précédentes du compilateur C++ ne géraient pas correctement l’initialisation de l' **`constexpr`** agrégat. Le compilateur a accepté un code non valide dans lequel Aggregate-init-List avait trop d’éléments et produit un CodeGen incorrect pour celui-ci. Le code suivant en est un exemple :

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

Dans Visual Studio 2017 version 15,7 Update 3 et versions ultérieures, l’exemple précédent déclenche désormais C2078 `too many initializers` . L’exemple de code suivant montre corriger le code. Lors de l’initialisation d’un `std::array` avec nested brace-init-lists, attribuez au tableau interne son propre braced-list :

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

## <a name="bug-fixes-and-behavior-changes-in-158"></a><a name="update_158"></a> Correctifs de bogues et modifications de comportement dans 15,8

Les modifications apportées au compilateur dans Visual Studio 2017 version 15,8 sont tous des correctifs de bogues et des changements de comportement. Ils sont listés ci-dessous :

### <a name="typename-on-unqualified-identifiers"></a>`typename` sur les identificateurs non qualifiés

En [`/permissive-`](../build/reference/permissive-standards-conformance.md) mode, **`typename`** les mots clés paraparasites sur les identificateurs non qualifiés dans les définitions de modèle d’alias ne sont plus acceptés par le compilateur. Le code suivant génère désormais C7511 `'T': 'typename' keyword must be followed by a qualified name` :

```cpp
template <typename T>
using  X = typename T;
```

Pour corriger cette erreur, remplacez la deuxième ligne par `using  X = T;`.

### <a name="__declspec-on-right-side-of-alias-template-definitions"></a>`__declspec()` dans la partie droite des définitions de modèle d’alias

[__declspec](../cpp/declspec.md) n’est plus autorisé dans la partie droite d’une définition de modèle d’alias. Auparavant, le compilateur acceptait, mais ignorait ce code. Cela ne provoque jamais d’avertissement de désapprobation lorsque l’alias a été utilisé.

L’attribut C++ standard [ \[ \[ \] \] déconseillé](../cpp/attributes.md) peut être utilisé à la place et est respecté dans Visual Studio 2017 version 15,6. Le code suivant génère désormais C2760 `syntax error: unexpected token '__declspec', expected 'type specifier'` :

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

Cela peut notamment se manifester par une recherche dans les classes de base dépendantes. Auparavant, le compilateur permettait d’utiliser des noms définis dans les classes de base dépendantes. C’est parce qu’ils seraient recherchés pendant l’instanciation lorsque tous les types sont résolus. Ce code est désormais traité comme une erreur. Dans ces cas, vous pouvez forcer la recherche de la variable au moment de l’instanciation en la qualifiant avec le type de classe de base ou en la rendant dépendante, par exemple en ajoutant un pointeur `this->`.

En [`/permissive-`](../build/reference/permissive-standards-conformance.md) mode, le code suivant déclenche désormais C3861 : `'base_value': identifier not found` :

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

Pour corriger l’erreur, remplacez l' **`return`** instruction par `return this->base_value;` .

**Remarque :** Dans la bibliothèque python Boost, il y a eu une solution de contournement spécifique à MSVC pour une déclaration anticipée de modèle dans [unwind_type. HPP](https://github.com/boostorg/python/blame/develop/include/boost/python/detail/unwind_type.hpp). [`/permissive-`](../build/reference/permissive-standards-conformance.md)En mode débutant dans Visual Studio 2017 version 15,8 ( \_ MSC \_ ver = 1915), le compilateur MSVC effectue une recherche de nom dépendante d’argument (ADL) correctement. Il est désormais cohérent avec d’autres compilateurs, ce qui rend cette solution de contournement inutile. Pour éviter les erreurs C3861 : `'unwind_type': identifier not found` , consultez [PR 229](https://github.com/boostorg/python/pull/229) dans le référentiel Boost pour mettre à jour le fichier d’en-tête. Nous avons déjà corrigé le package Boost [vcpkg](../build/vcpkg.md), donc si vous obtenez ou mettez à niveau vos sources Boost à partir de vcpkg, il est inutile d’appliquer le correctif séparément.

### <a name="forward-declarations-and-definitions-in-namespace-std"></a>définitions et déclarations anticipées dans l’espace de noms `std`

La norme C++ ne permet pas à un utilisateur d’ajouter des définitions ou des déclarations anticipées dans l’espace de noms `std`. L’ajout de définitions ou de déclarations à l’espace de noms `std` ou à un espace de noms dans l’espace de noms `std` donne désormais lieu à un comportement non défini.

Il est prévu que Microsoft affecte la définition de certains types de bibliothèque standard à un autre emplacement. Ce changement entraînera l’arrêt de tout code existant qui ajoute des déclarations anticipées à l’espace de noms `std`. Un nouvel avertissement, C4643, vous aide à identifier de tels problèmes liés la source. L’avertissement est activé en **`/default`** mode et est désactivé par défaut. Cela aura un impact sur les programmes qui sont compilés avec **`/Wall`** ou **`/WX`** .

Le code suivant génère désormais C4643 : `Forward declaring 'vector' in namespace std is not permitted by the C++ Standard` .

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

La norme C++ suggère qu’un compilateur doit émettre un diagnostic quand un constructeur de délégation délègue à lui-même. Le compilateur Microsoft C++ dans [`/std:c++17`](../build/reference/std-specify-language-standard-version.md) les [`/std:c++latest`](../build/reference/std-specify-language-standard-version.md) modes et déclenche désormais C7535 : `'X::X': delegating constructor calls itself` .

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

[offsetof](../c-runtime-library/reference/offsetof-macro.md) est habituellement implémenté à l’aide d’une macro qui nécessite un [reinterpret_cast](../cpp/reinterpret-cast-operator.md). Cette utilisation n’est pas conforme dans les contextes nécessitant une expression constante, le compilateur Microsoft C++ l’a toujours autorisée. La macro `offsetof` fournie dans le cadre de la bibliothèque standard utilise correctement une fonction intrinsèque du compilateur (**__builtin_offsetof**), mais de nombreuses personnes utilisent l’astuce de la macro pour définir leur propre `offsetof`.

Dans Visual Studio 2017 version 15,8, le compilateur limite les zones que ces **`reinterpret_cast`** opérateurs peuvent afficher dans le mode par défaut, pour aider le code à se conformer au comportement C++ standard. Sous [`/permissive-`](../build/reference/permissive-standards-conformance.md) , les contraintes sont encore plus strictes. L’utilisation du résultat d’un `offsetof` dans des endroits qui requièrent des expressions constantes peut entraîner un code qui émet un avertissement C4644 `usage of the macro-based offsetof pattern in constant expressions is non-standard; use offsetof defined in the C++ standard library instead` ou C2975 `invalid template argument, expected compile-time constant expression` .

Le code suivant déclenche C4644 dans **`/default`** les **`/std:c++17`** modes et et C2975 en [`/permissive-`](../build/reference/permissive-standards-conformance.md) mode :

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

Pour corriger l’erreur, utilisez `offsetof` comme défini à l’aide de \<cstddef> :

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

Dans Visual Studio 2017 version 15,8, [`/permissive-`](../build/reference/permissive-standards-conformance.md) le code suivant déclenche C3770 `'const S': is not a valid base class` :

```cpp
template<typename... T>
class X : public T... { };

class S { };

int main()
{
    X<const S> x;
}
```

### <a name="template-keyword-and-nested-name-specifiers"></a>Mot clé `template` et spécificateurs de noms imbriqués

En [`/permissive-`](../build/reference/permissive-standards-conformance.md) mode, le compilateur requiert désormais que le **`template`** mot clé précède un nom de modèle lorsqu’il vient après un spécificateur-Name-Name-specifier dépendant.

Le code suivant en [`/permissive-`](../build/reference/permissive-standards-conformance.md) mode déclenche désormais C7510 : `'example': use of dependent template name must be prefixed with 'template'. note: see reference to class template instantiation 'X<T>' being compiled` :

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

Pour corriger l’erreur, ajoutez le **`template`** mot clé à l' `Base<T>::example<int>();` instruction, comme indiqué dans l’exemple suivant :

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

## <a name="bug-fixes-and-behavior-changes-in-159"></a><a name="update_159"></a> Correctifs de bogues et modifications de comportement dans 15,9

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

Dans Visual Studio 2017 version 15,9, en [`/permissive-`](../build/reference/permissive-standards-conformance.md) mode, le compilateur déclenche C3861 : `'from_template': identifier not found` .

Pour corriger cette erreur, déclarez `from_template` avant `from_template_t`.

### <a name="modules-changes"></a>Changements apportés aux modules

Dans Visual Studio 2017 version 15.9, le compilateur génère C5050 chaque fois que les options de ligne de commande pour les modules ne sont pas cohérentes entre la partie création et la partie consommation du module. L’exemple suivant présente deux problèmes :

- Sur le côté consommation (main. cpp), l’option **`/EHsc`** n’est pas spécifiée.

- La version C++ se trouve **`/std:c++17`** sur le côté création et **`/std:c++14`** sur le côté consommation.

```cmd
cl /EHsc /std:c++17 m.ixx /experimental:module
cl /experimental:module /module:reference m.ifc main.cpp /std:c++14
```

Le compilateur déclenche C5050 pour les deux cas suivants : `warning C5050: Possible incompatible environment while importing module 'm': mismatched C++ versions.  Current "201402" module version "201703"` .

Le compilateur génère aussi C7536 chaque fois que le fichier .ifc est falsifié. L’en-tête de l’interface de module contient un hachage SHA2 du contenu situé en dessous. Lors de l’importation, le fichier. IFC est haché, puis comparé au hachage fourni dans l’en-tête. Si elles ne correspondent pas, l’erreur C7536 est levée : `ifc failed integrity checks.  Expected SHA2: '66d5c8154df0c71d4cab7665bab4a125c7ce5cb9a401a4d8b461b706ddd771c6'` .

### <a name="partial-ordering-involving-aliases-and-non-deduced-contexts"></a>Classement partiel impliquant des alias et des contextes non déduits

Les implémentations des règles de classement partiel impliquant des alias dans des contextes non déduits font l’objet de divergences. Dans l’exemple suivant, GCC et le compilateur Microsoft C++ (en [`/permissive-`](../build/reference/permissive-standards-conformance.md) mode) génèrent une erreur, tandis que Clang accepte le code.

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

Pour éviter cette erreur, supprimez le **`constexpr`** qualificateur de l’instanciation explicite de la fonction `f()` .

::: moniker-end

::: moniker range="vs-2015"

## <a name="c-conformance-improvements-in-visual-studio-2015"></a>Améliorations de la conformité de C++ dans Visual Studio 2015

Nous disposons d’une liste complète des améliorations de la conformité dans Visual Studio 2015 Update 3. Pour plus d’informations, consultez [Nouveautés de Visual C++ entre 2003 et 2015](/cpp/porting/visual-cpp-what-s-new-2003-through-2015).

::: moniker-end

## <a name="see-also"></a>Voir aussi

[Table de conformité du langage Microsoft C++](visual-cpp-language-conformance.md)
