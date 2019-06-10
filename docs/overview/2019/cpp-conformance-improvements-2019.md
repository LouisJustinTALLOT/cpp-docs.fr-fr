---
title: Améliorations de la conformité de C++
ms.date: 05/16/2019
description: Microsoft C++ dans Visual Studio 2019 arrive progressivement à une conformité totale avec la norme du langage C ++20.
ms.technology: cpp-language
author: mikeblome
ms.author: mblome
ms.openlocfilehash: 02b778f10ad94342c922a4e79a856cc2a7d53076
ms.sourcegitcommit: 28eae422049ac3381c6b1206664455dbb56cbfb6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/31/2019
ms.locfileid: "66451222"
---
# <a name="c-conformance-improvements-in-visual-studio-2019-rtw-and-version-161improvements161"></a>Améliorations de la conformité de C++ dans Visual Studio 2019 RTW et version [16.1](#improvements_161)

## <a name="improvements-in-visual-studio-2019-rtw"></a>Améliorations dans Visual Studio 2019 RTW

Visual Studio 2019 RTW contient les améliorations, les correctifs de bogues et les changements de comportement relatifs à la conformité suivants dans le compilateur Microsoft C++ (MSVC).

**Remarque :** Les fonctionnalités C++20 seront disponibles en mode `/std:c++latest` tant que l’implémentation de C++20 n’est pas terminée pour le compilateur et IntelliSense. Une fois qu’elle sera terminée, le mode de compilateur `/std:c++20` sera introduit.

### <a name="improved-modules-support-for-templates-and-error-detection"></a>Amélioration de la prise en charge des modules pour les modèles et la détection d’erreur

Les modules sont désormais officiellement dans la norme C++20. Une meilleure prise en charge a été ajoutée dans Visual Studio 2017 version 15.9. Pour plus d’informations, consultez [Better template support and error detection in C++ Modules with MSVC 2017 version 15.9](https://devblogs.microsoft.com/cppblog/better-template-support-and-error-detection-in-c-modules-with-msvc-2017-version-15-9/).

### <a name="modified-specification-of-aggregate-type"></a>Changement de spécification du type d’agrégat

La spécification d’un type d’agrégat a changé dans C++20 (consultez [Prohibit aggregates with user-declared constructors](https://wg21.link/p1008r1)). Dans Visual Studio 2019, sous `/std:c++latest`, une classe avec un constructeur déclaré par l’utilisateur (par exemple, un constructeur déclaré `= default` ou `= delete`) n’est pas un agrégat. Avant, seuls les constructeurs fournis par l’utilisateur empêchaient une classe d’être un agrégat. Ce changement ajoute des restrictions supplémentaires sur la façon dont ces types peuvent être initialisés.

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

### <a name="partial-support-for-operator-"></a>Prise en charge partielle de l’opérateur <=>

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

Pour éviter les erreurs, insérez un espace dans la ligne incriminée avant le dernier chevron : `U<&S::operator<= > u;`.

### <a name="references-to-types-with-mismatched-cv-qualifiers"></a>Références aux types avec des qualificateurs cv non correspondants

Avant, MSVC autorisait la liaison directe d’une référence d’un type avec des qualificateurs cv non correspondants sous le niveau supérieur. Cela pouvait permettre la modification des données const supposément référencées par la référence. Maintenant, le compilateur crée un fichier temporaire comme le demande la norme. Dans Visual Studio 2017, le code suivant se compile sans avertissement. Dans Visual Studio 2019, le compilateur génère un *avertissement C4172 : \<func:#1 "?PData@X@@QBEABQBXXZ"> retournant l’adresse d’une variable locale ou d’un fichier temporaire*.

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
### <a name="reinterpretcast-from-an-overloaded-function"></a>`reinterpret_cast` d’une fonction surchargée

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

Dans C++14, les types de fermeture d’expression lambda ne sont pas littéraux. La première conséquence de cette règle est qu’une expression lambda ne doit pas être affectée à une variable `constexpr`. Le code suivant compile sans erreur dans Visual Studio 2017, alors que dans Visual Studio 2019 il déclenche *C2127 : 'l' : initialisation illégale de l’entité 'constexpr' avec une expression non constante* :

```cpp
int main()
{
    constexpr auto l = [] {}; // C2127 in VS2019
}
```

Pour éviter cette erreur, supprimez le qualificateur `constexpr` ou changez le mode de conformité en le remplaçant par `/std:c++17`.

### <a name="stdcreatedirectory-failure-codes"></a>Codes d’échec std::create_directory

[P1164](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2019/p1164r1.pdf) implémenté depuis C++20 sans condition. Cela change `std::create_directory` pour vérifier si la cible était déjà un répertoire en échec. Avant, toutes les erreurs de type ERROR_ALREADY_EXISTS étaient converties en codes success-but-directory-not-created.

### <a name="operatorstdostream-nullptrt"></a>operator<<(std::ostream, nullptr_t)

Conformément à [LWG 2221](https://cplusplus.github.io/LWG/issue2221), ajout de `operator<<(std::ostream, nullptr_t)` pour écrire nullptrs dans les flux. 

### <a name="additional-parallel-algorithms"></a>Algorithmes parallèles supplémentaires

Nouvelles versions parallèles de `is_sorted`, `is_sorted_until`, `is_partitioned`, `set_difference`, `set_intersection`, `is_heap` et `is_heap_until`.

### <a name="atomic-initialization"></a>Initialisation atomique

Le [P0883 "Fixing atomic initialization"](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0883r1.pdf) change `std::atomic` pour l’initialiser avec la valeur du T contenu plutôt que de l’initialiser avec la valeur par défaut. Le correctif est activé lorsque vous utilisez Clang/LLVM avec la bibliothèque standard de Microsoft. Il est actuellement désactivé pour le compilateur Microsoft C++ comme solution de contournement pour un bogue dans le traitement de constexpr.

### <a name="removecvref-and-removecvreft"></a>remove_cvref et remove_cvref_t

Caractéristiques de type `remove_cvref` et `remove_cvref_t` implémentées selon le [P0550](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0550r2.pdf). Cela supprime reference-ness et cv-qualification d’un type sans dégrader les fonctions et les tableaux en pointeurs (contrairement à `std::decay` et `std::decay_t`).

### <a name="feature-test-macros"></a>Macros Feature-test

[P0941R2 - macros de test de fonctionnalité](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0941r2.html) est terminé, avec la prise en charge de `__has_cpp_attribute`. Les macros de test de fonctionnalité sont prises en charge dans tous les modes Standard.

### <a name="prohibit-aggregates-with-user-declared-constructors"></a>Interdire les agrégats avec les constructeurs déclarés par l’utilisateur

[C++20 P1008R1 - prohibiting aggregates with user-declared constructors](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p1008r1.pdf) est terminé.

## <a name="improvements_161"></a> Améliorations dans Visual Studio 2019 version 16.1

### <a name="char8t"></a>char8_t

[P0482r6](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0482r6.html). C++20 ajoute un nouveau type de caractère qui est utilisé pour représenter les unités de code UTF-8. Les littéraux de chaîne u8 dans C++20 ont le type `const char8_t[N]` au lieu de `const char[N]`, ce qui était le cas auparavant. Des changements similaires ont été proposés pour la norme C dans [N2231](http://www.open-std.org/jtc1/sc22/wg14/www/docs/n2231.htm). Vous trouverez des suggestions de correction de la compatibilité descendante de char8_t dans [P1423r0](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2019/p1423r0.html). Le compilateur Microsoft C++ ajoute une prise en charge de char8_t dans Visual Studio 2019 version 16.1 quand vous spécifiez l’option de compilateur **/Zc:char8_t**. À l’avenir, il sera pris en charge avec [/std:c++latest](../../build/reference/std-specify-language-standard-version.md), qui peut revenir au comportement C++17 via **/Zc:char8_t-** . Le compilateur EDG qui alimente IntelliSense ne le prend pas encore en charge, donc vous verrez des erreurs parasites propres à IntelliSense qui n’impactent pas la compilation effective.

#### <a name="example"></a>Exemple

```cpp
const char* s = u8"Hello"; // C++17
const char8_t* s = u8"Hello"; // C++20
```

### <a name="stdtypeidentity-metafunction-and-stdidentity-function-object"></a>Métafonction std::type_identity et objet de fonction std::identity

[P0887R1 type_identity](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0887r1.pdf). L’extension de modèle de classe `std::identity` dépréciée a été supprimée et remplacée par la métafonction `std::type_identity` et l’objet de fonction `std::identity` C++20. Les deux sont disponibles uniquement sous [/std:c++latest](../../build/reference/std-specify-language-standard-version.md). 

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

Le nouveau processeur lambda autorise des vérifications syntaxiques du mode de conformité dans les expressions lambda génériques, sous [/std:c++latest](../../build/reference/std-specify-language-standard-version.md) ou sous n’importe quel autre mode de langage avec **/experimental:newLambdaProcessor**. 

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
- `remove()`, `remove_if()` et `unique()` pour ` list` et `forward_list` retournent maintenant `size_type`.
- Ajout de `shift_left()` et `shift_right()` à \<algorithm>.

## <a name="bug-fixes-and-behavior-changes-in-visual-studio-2019-rtw"></a>Correctifs de bogues et changements de comportement dans Visual Studio 2019 RTW

### <a name="correct-diagnostics-for-basicstring-range-constructor"></a>Diagnostics corrects pour le constructeur de plage basic_string

Dans Visual Studio 2019, le constructeur de plage `basic_string` ne supprime plus les diagnostics du compilateur avec `static_cast`. Le code suivant se compile sans avertissement dans Visual Studio 2017, malgré la perte de données possible de `wchar_t` à `char` lors de l’initialisation de `out` :

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

Les accès à des membres non valides dans les initialiseurs `inline` et `static constexpr` sont maintenant correctement détectés. L’exemple suivant se compile sans erreur dans Visual Studio 2017, alors que dans Visual Studio 2019 sous le mode `/std:c++17`, il déclenche l’*erreur C2248 : impossible d’accéder à un membre privé déclaré dans la classe 'X'* .

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

MSVC utilisait un avertissement de performance C4800 sur la conversion implicite en bool qui était trop bruyant et insupprimable, ce qui nous a conduit à le supprimer dans Visual Studio 2017. Toutefois, pendant le cycle de vie de Visual Studio 2017, nous avons eu beaucoup de commentaires disant qu’il était utile pour résoudre de nombreux cas. Du coup, nous réintégrons dans Visual Studio 2019 un avertissement C4800 adapté ave son acolyte C4165, les deux pouvant être facilement supprimés avec une comparaison ou un cast explicite en 0 du type approprié. C4800 est un avertissement de niveau 4 désactivé par défaut, tandis que C4165 est un avertissement de niveau 3 désactivé par défaut. Les deux sont découvrables à l’aide de l’option de compilateur `/Wall`.

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
void foo()
{
    struct A
        {
            int boo(); // warning C4822
        };
}
```

### <a name="function-template-bodies-containing-constexpr-if-statements"></a>Corps de modèle de fonction contenant des instructions if constexpr

Les corps de fonction de modèle contenant des instructions `if constexpr` ont des vérifications relatives à l’analyse de `/permissive-` activées. Par exemple, dans Visual Studio 2017, le code suivant génère C*7510 : 'Type' : l’utilisation du nom de type dépendant doit être préfixée de 'typename'* seulement si l’option `/permissive-` n’est pas définie. Dans Visual Studio 2019, le même code génère des erreurs, que l’option `/permissive-` soit définie ou non :

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

Pour éviter cette erreur, ajoutez le mot clé `typename` à la déclaration de `a` : `typename T::Type a;`.

### <a name="inline-assembly-code-is-not-supported-in-a-lambda-expression"></a>Le code de l’assembleur inline n’est pas pris en charge dans une expression lambda

L’équipe Visual C++ a récemment été informée d’un problème de sécurité où l’utilisation de inline-assembler dans une expression lambda pouvait entraîner l’altération de 'ebp' (l’enregistrement de l’adresse de retour) lors de l’exécution. Un utilisateur malveillant risque de pouvoir tirer parti de ce scénario. Étant donné la nature du problème, le fait que l’assembleur inline est uniquement pris en charge sur x86 et l’interaction médiocre de l’assembleur inline avec le reste du compilateur, nous en avons conclu que la solution la plus sûre à ce problème était d’interdire l’assembleur inline dans une expression lambda.

Remarque : La seule utilisation de l’assembleur inline dans une expression lambda que nous avons rencontrée avait pour but de capturer l’adresse de retour. Dans ce scénario, vous pouvez capturer l’adresse de retour sur toutes les plateformes simplement à l’aide de `_ReturnAddress()` intrinsèque au compilateur.

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

### <a name="iterator-debugging-and-stdmoveiterator"></a>Débogage d’itérateur et std::move_iterator

La fonctionnalité de débogage d’itérateur a été adaptée pour unwrapper correctement `std::move_iterator`. Par exemple, `std::copy(std::move_iterator<std::vector<int>::iterator>, std::move_iterator<std::vector<int>::iterator>, int*)` peut maintenant engager le chemin rapide `memcpy`.

### <a name="fixes-for-xkeycheckh-keyword-enforcement"></a>Correctifs pour l’application du mot clé \<xkeycheck.h>

L’application du mot clé « macro-isé » de la bibliothèque Standard \<xkeycheck.h> a été corrigée pour émettre l’actuel mot-clé à problème détecté plutôt qu’un message générique. Elle prend aussi en charge les mots clés C++20 et évite qu’IntelliSense indique que des mots clés aléatoires sont des macros.

### <a name="allocator-types-un-deprecated"></a>Types d’allocateur plus dépréciés

`std::allocator<void>`, `std::allocator::size_type` et `std::allocator::difference_type` ne sont plus dépréciés.

### <a name="correct-warning-for-narrowing-string-conversions"></a>Avertissement correct pour les conversions de chaîne restrictives

Un `static_cast` parasite, non demandé par la norme, qui supprimait accidentellement les avertissements restrictifs C4244 a été supprimé de std::string. Une tentative d’appel à `std::string::string(const wchar_t*, const wchar_t*)` va désormais émettre correctement *C4244 "narrowing a wchar_t into a char."*

### <a name="various-filesystem-correctness-fixes"></a>Corrections diverses de \<filesystem>

- Correction de l’échec de `std::filesystem::last_write_time` lors d’une tentative de changement de l’heure de la dernière écriture d’un répertoire.
- Désormais, le constructeur `std::filesystem::directory_entry` stocke un résultat en échec plutôt que de lever une exception quand un chemin cible qui n’existe pas est fourni.
- La version à 2 paramètres `std::filesystem::create_directory` a été changée pour appeler la version à 1 paramètre, car la fonction `CreateDirectoryExW` sous-jacente exécuterait `copy_symlink` si existing_p était un symlink.
- `std::filesystem::directory_iterator` n’échoue plus quand il rencontre un symlink rompu.
- `std::filesystem::space` accepte désormais les chemins relatifs.
- `std::filesystem::path::lexically_relative` n’est plus dérouté par les barres obliques de fin, signalé dans [LWG 3096](https://cplusplus.github.io/LWG/issue3096).
- Le problème a été contourné avec `CreateSymbolicLinkW` qui rejette les chemins avec des barres obliques dans `std::filesystem::create_symlink`.
- Nous avons contourné le problème du mode de suppression POSIX de la fonction `delete` existant sur Windows 10 LTSB 1609, mais en fait nous n’avons pas été capables de supprimer des fichiers.
- Les constructeurs de copie de `std::boyer_moore_searcher` et `std::boyer_moore_horspool_searcher` et les opérateurs d'affectation de copie arrivent maintenant à copier.

### <a name="parallel-algorithms-on-windows-8-and-later"></a>Algorithmes parallèles sur Windows 8 et ultérieur

La bibliothèque d’algorithmes parallèles utilise la vraie famille `WaitOnAddress` sur Windows 8 et ultérieur, au lieu d’utiliser tout le temps les versions fausses de Windows 7 et antérieur.

### <a name="stdsystemcategorymessage-whitespace"></a>std::system_category::message() et espace

`std::system_category::message()` supprime désormais l’espace de fin du message retourné.

### <a name="stdlinearcongruentialengine-divide-by-zero"></a>std::linear_congruential_engine et division par zéro

Certaines conditions qui faisaient que `std::linear_congruential_engine` déclenchait la division par 0 ont été corrigées.

### <a name="fixes-for-iterator-unwrapping"></a>Correctifs pour l’unwrapping d’itérateurs

Le système d’unwrapping d’itérateurs qui était au départ exposé pour l’intégration d’utilisateurs programmeurs dans Visual Studio 2017 15.8 (comme décrit dans https://devblogs.microsoft.com/cppblog/stl-features-and-fixes-in-vs-2017-15-8/) n’unwrappe plus les itérateurs dérivés à partir des itérateurs de la bibliothèque standard. Par exemple, un utilisateur qui dérive de `std::vector<int>::iterator` et qui essaie de personnaliser le comportement obtient son comportement personnalisé lors de l’appel des algorithmes de la bibliothèque standard au lieu du comportement d’un pointeur.
La fonction de réserve de conteneur non ordonnée réserve maintenant pour N éléments, comme décrit dans [LWG 2156](https://cplusplus.github.io/LWG/issue2156).

### <a name="time-handling"></a>Gestion de l’heure

- Avant, certaines valeurs de temps passées à la bibliothèque de concurrence provoquaient un dépassement, par exemple, `condition_variable::wait_for(seconds::max())`. Ces dépassements, maintenant corrigés, changeaient le comportement selon un cycle apparemment aléatoire de 29 jours (quand les millisecondes uint32_t acceptées par les API Win32 sous-jacentes dépassaient).

- L’en-tête <ctime> déclare correctement timespec et timespec_get dans l’espace de noms std, en plus de les déclarer dans l’espace de noms global.

### <a name="various-fixes-for-containers"></a>Divers correctifs pour les conteneurs

- De nombreuses fonctions de conteneur internes à la bibliothèque Standard ont été rendues privées pour une meilleure expérience IntelliSense. Des correctifs supplémentaires pour marquer les membres comme privés sont attendus dans les prochaines versions de MSVC.

- Les problèmes de sécurité d’exception, où les conteneurs basés sur des nœuds comme `list`, `map` et `unordered_map` étaient altérés, ont été résolus. Pendant une opération de réaffectation `propagate_on_container_copy_assignment` ou `propagate_on_container_move_assignment`, nous libérons le nœud sentinelle du conteneur avec l’ancien allocateur, procédons à l’affectation de POCCA/POCMA sur l’ancien allocateur, puis tentons d’obtenir le nœud sentinelle auprès du nouvel allocateur. Si cette allocation échoue, le conteneur est altéré et ne peut même pas être détruit, car un nœud sentinelle est un invariant codé en dur dans la structure de données. Ce problème a été résolu pour allouer le nouveau nœud sentinelle de l’allocateur du conteneur source avant de détruire le nœud sentinelle existant.

- Les conteneurs ont été résolus pour toujours copier/déplacer/échanger les allocateurs en fonction de `propagate_on_container_copy_assignment`, `propagate_on_container_move_assignment` et `propagate_on_container_swap`, même pour les allocateurs déclarés `is_always_equal`.

- Ajout de surcharges pour les fonctions de fusion de conteneurs et d’extraction de membres qui acceptent des conteneurs rvalue, conformément à [P0083 "Splicing Maps And Sets"](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0083r3.pdf)

### <a name="stdbasicistreamread-processing-of-rn--n"></a>Traitement std::basic_istream::read de \r\n => \n

`std::basic_istream::read` a été corrigé pour ne pas écrire temporairement dans des parties de la mémoire tampon fournie lors du traitement de \r\n => \n. Vous perdez une partie des performances que vous aviez gagnées dans Visual Studio 2017 15.8 pour les lectures supérieures à 4 Ko, mais vous bénéficiez toujours des améliorations de l’efficacité permettant d’éviter 3 appels virtuels par caractère.

### <a name="stdbitset-constructor"></a>Constructeur de std::bitset

Le constructeur de `std::bitset` ne lit plus les uns et les zéros dans l’ordre inverse pour les grands bitsets.

### <a name="stdpairoperator-regression"></a>Régression de std::pair::operator=

Correction d’une régression dans l’opérateur d’affectation de `std::pair` introduite lors de l’implémentation de [LWG 2729 "Missing SFINAE on std::pair::operator=";](https://cplusplus.github.io/LWG/issue2729). Maintenant, il accepte de nouveau les types convertibles en `std::pair` correctement.

### <a name="non-deduced-contexts-for-addconstt"></a>Contextes non déduits pour add_const_t

Correction d’un bogue de traits de type mineur, où `add_const_t` et les fonctions associées sont censés être un contexte non déduit. En d’autres termes, `add_const_t` doit être un alias pour `typename add_const<T>::type`, pas `const T`.

## <a name="see-also"></a>Voir aussi

[Nouveautés de Visual Studio 2019](../what-s-new-for-visual-cpp-in-visual-studio.md)