---
title: /permissive - (Conformité aux standards)
description: Guide de référence de l’option compilateur Microsoft CMD/permissive(Standards conformance).
ms.date: 04/14/2020
f1_keywords:
- /permissive
- VC.Project.VCCLCompilerTool.ConformanceMode
helpviewer_keywords:
- /permissive compiler options [C++]
- -permissive compiler options [C++]
- Standards conformance compiler options
- permissive compiler options [C++]
ms.assetid: db1cc175-6e93-4a2e-9396-c3725d2d8f71
ms.openlocfilehash: 695f84e64f07128ac7744dc99e736f2a71ab3e79
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81337404"
---
# <a name="permissive--standards-conformance"></a>/permissive - (Conformité aux standards)

Spécifier le mode de conformité aux normes au compilateur. Utilisez cette option pour vous aider à identifier et à résoudre les problèmes de conformité dans votre code, pour le rendre à la fois plus correct et plus portable.

## <a name="syntax"></a>Syntaxe

> **/permissive-**

## <a name="remarks"></a>Notes

Cette option est prise en charge dans Visual Studio 2017 et plus tard.

Vous pouvez utiliser l’option **/permissive-** compilateur pour spécifier le comportement compilateur conforme aux normes. Cette option désactive les comportements permissifs, et définit les options de compilateur [/Zc](zc-conformance.md) pour une conformité stricte. Dans l’IDE, cette option rend également le moteur IntelliSense souligner le code non conforme.

Par défaut, l’option **/permissive-** est définie dans de nouveaux projets créés par Visual Studio 2017 version 15.5 et versions ultérieures. Il n’est pas défini par défaut dans les versions précédentes. Lorsque l’option est définie, le compilateur génère des erreurs diagnostiques ou des avertissements lorsque des constructions linguistiques non standard sont détectées dans votre code, y compris certains bogues courants dans le code pré-C-11.

**L’option /permissive-** est compatible avec presque tous les fichiers d’en-tête des derniers kits Windows, tels que le kit de développement logiciel (SDK) ou Windows Driver Kit (WDK), à partir de windows Fall Creators SDK (10.16299.0). Les versions plus anciennes du SDK peuvent ne pas se compiler sous **/permissive-** pour diverses raisons de conformité au code source. Le compilateur et les SDKs expédient selon des délais de libération différents, il reste donc quelques problèmes. Pour des problèmes spécifiques de fichier d’en-tête, voir [les problèmes d’en-tête Windows](#windows-header-issues) ci-dessous.

**L’option /permissive-** définit le [/Zc:referenceBinding](zc-referencebinding-enforce-reference-binding-rules.md), [/Zc:strictStrings](zc-strictstrings-disable-string-literal-type-conversion.md), et [/Zc:rvalueCast](zc-rvaluecast-enforce-type-conversion-rules.md) options à la conformité du comportement. Ces options par défaut à un comportement non conforme. Vous pouvez passer des options spécifiques **/Zc** après **/permissive-** sur la ligne de commande pour remplacer ce comportement.

Dans les versions du compilateur à partir de Visual Studio 2017 version 15.3, **l’option /permissive-** définit l’option [/Zc:ternary.](zc-ternary.md) Le compilateur met également en œuvre une plus grande partie des exigences pour le look-up de noms en deux phases. Lorsque l’option **/permissive** est définie, le compilateur analyse les définitions de la fonction et du modèle de classe, et identifie les noms dépendants et non dépendants utilisés dans les modèles. Dans cette version, seule l’analyse de la dépendance au nom est effectuée.

Les extensions et les zones linguistiques spécifiques à l’environnement que la norme laisse à la mise en œuvre ne sont pas affectées par **/permissive-**. Par exemple, la `__declspec`convention d’appel spécifique à Microsoft et les mots clés de manutention d’exception structurés, ainsi que les directives ou attributs pragma spécifiques au compilateur ne sont pas signalés par le compilateur en mode **/permissive-permissive.**

**L’option /permissive-** utilise le support de conformité dans la version compilateur actuelle pour déterminer quelles constructions linguistiques ne sont pas conformes. L’option ne détermine pas si votre code est conforme à une version spécifique de la norme C. Pour activer tous les support compilateurs mis en œuvre pour le dernier projet de norme, utilisez [l’option /std:latest.](std-specify-language-standard-version.md) Pour limiter le support compilateur à la norme C-17 actuellement mise en œuvre, utilisez l’option [/std:c -17.](std-specify-language-standard-version.md) Pour limiter le support compilateur pour correspondre plus étroitement à la norme C 14, utilisez l’option [/std:c -14,](std-specify-language-standard-version.md) qui est la valeur par défaut.

Tous les codes conformes aux normes de la C-11, du C-14 ou du C-17 ne sont pas tous pris en charge par le compilateur MSVC dans toutes les versions de Visual Studio 2017. Selon la version de Visual Studio, **l’option /permissive-** peut ne pas détecter les problèmes concernant certains aspects de la recherche de noms en deux phases, liant une référence non-const à un temporaire, traitant l’init de copie comme un init direct, permettant plusieurs conversions définies par l’utilisateur dans l’initialisation, ou des jetons alternatifs pour les opérateurs logiques, et d’autres zones de conformation non-soutenues. Pour plus d’informations sur les problèmes de conformité dans Visual C++, consultez [Nonstandard Behavior](../../cpp/nonstandard-behavior.md). Pour tirer le meilleur parti de **/permissive-**, mettre à jour Visual Studio à la dernière version.

### <a name="how-to-fix-your-code"></a>Comment corriger votre code

Voici quelques exemples de code qui est détecté comme non-conformiste lorsque vous utilisez **/permissive-**, ainsi que des moyens suggérés pour résoudre les problèmes.

#### <a name="use-default-as-an-identifier-in-native-code"></a>Utiliser par défaut comme identifiant dans le code natif

```cpp
void func(int default); // Error C2321: 'default' is a keyword, and
                        // cannot be used in this context
```

#### <a name="look-up-members-in-dependent-base"></a>Rechercher des membres dans la base dépendante

```cpp
template <typename T>
struct B {
    void f();
};

template <typename T>
struct D : public B<T> // B is a dependent base because its type
                       // depends on the type of T.
{
    // One possible fix is to uncomment the following line.
    // If this is a type, don't forget the 'typename' keyword.
    // using B<T>::f;

    void g() {
        f(); // error C3861: 'f': identifier not found
             // Another fix is to change it to 'this->f();'
    }
};

void h() {
    D<int> d;
    d.g();
}
```

#### <a name="use-of-qualified-names-in-member-declarations"></a>Utilisation de noms qualifiés dans les déclarations des membres

```cpp
struct A {
    void A::f() { } // error C4596: illegal qualified name in member
                    // declaration.
                    // Remove redundant 'A::' to fix.
};
```

#### <a name="initialize-multiple-union-members-in-a-member-initializer"></a>Initialiser plusieurs membres du syndicat dans un initialisateur membre

```cpp
union U
{
    U()
        : i(1), j(1) // error C3442: Initializing multiple members of
                     // union: 'U::i' and 'U::j'.
                     // Remove all but one of the initializations to fix.
    {}
    int i;
    int j;
};
```

#### <a name="hidden-friend-name-lookup-rules"></a>Règles cachées de recherche de nom d’ami

```cpp
// Example 1
struct S {
    friend void f(S *);
};
// Uncomment this declaration to make the hidden friend visible:
// void f(S *); // This declaration makes the hidden friend visible

using type = void (*)(S *);
type p = &f; // error C2065: 'f': undeclared identifier.
```

```cpp
// Example 2
struct S {
    friend void f(S *);
};
void g() {
    // Using nullptr instead of S prevents argument dependent lookup in S
    f(nullptr); // error C3861: 'f': identifier not found

    S *p = nullptr;
    f(p); // Hidden friend now found via argument-dependent lookup.
}
```

#### <a name="use-scoped-enums-in-array-bounds"></a>Utiliser des enums scoped dans des limites de tableau

```cpp
enum class Color {
    Red, Green, Blue
};

int data[Color::Blue]; // error C3411: 'Color' is not valid as the size
                       // of an array as it is not an integer type.
                       // Cast to type size_t or int to fix.
```

#### <a name="use-for-each-in-native-code"></a>Utilisation pour chacun dans le code natif

```cpp
void func() {
    int array[] = {1, 2, 30, 40};
    for each (int i in array) // error C4496: nonstandard extension
                              // 'for each' used: replace with
                              // ranged-for statement:
                              // for (int i: array)
    {
        // ...
    }
}
```

#### <a name="use-of-atl-attributes"></a>Utilisation d’attributs ATL

```cpp
// Example 1
[uuid("594382D9-44B0-461A-8DE3-E06A3E73C5EB")]
class A {};
```

```cpp
// Fix for example 1
class __declspec(uuid("594382D9-44B0-461A-8DE3-E06A3E73C5EB")) B {};
```

```cpp
// Example 2
[emitidl];
[module(name="Foo")];

[object, local, uuid("9e66a290-4365-11d2-a997-00c04fa37ddb")]
__interface ICustom {
    HRESULT Custom([in] longl, [out, retval] long*pLong);
    [local] HRESULT CustomLocal([in] longl, [out, retval] long*pLong);
};

[coclass, appobject, uuid("9e66a294-4365-11d2-a997-00c04fa37ddb")]
class CFoo : public ICustom
{};
```

```cpp
// Fix for example 2
// First, create the *.idl file. The vc140.idl generated file can be
// used to automatically obtain a *.idl file for the interfaces with
// annotation. Second, add a midl step to your build system to make
// sure that the C++ interface definitions are outputted.
// Last, adjust your existing code to use ATL directly as shown in
// the atl implementation section.

-- IDL  FILE--
import "docobj.idl";

[object, local, uuid(9e66a290-4365-11d2-a997-00c04fa37ddb)]
interface ICustom : IUnknown {
    HRESULT Custom([in] longl, [out,retval] long*pLong);
    [local] HRESULT CustomLocal([in] longl, [out,retval] long*pLong);
};

[ version(1.0), uuid(29079a2c-5f3f-3325-99a1-3ec9c40988bb) ]
library Foo {
    importlib("stdole2.tlb");
    importlib("olepro32.dll");

    [version(1.0), appobject, uuid(9e66a294-4365-11d2-a997-00c04fa37ddb)]
    coclass CFoo { interface ICustom; };
}

-- ATL IMPLEMENTATION--
#include <idl.header.h>
#include <atlbase.h>

class ATL_NO_VTABLE CFooImpl : public ICustom,
    public ATL::CComObjectRootEx<CComMultiThreadModel>
{
    public:BEGIN_COM_MAP(CFooImpl)
    COM_INTERFACE_ENTRY(ICustom)
    END_COM_MAP()
};
```

#### <a name="ambiguous-conditional-operator-arguments"></a>Arguments ambigus de l’opérateur conditionnel

Dans les versions du compilateur avant Visual Studio 2017 version 15.3, le compilateur `?:` a accepté des arguments à l’opérateur conditionnel (ou opérateur ternaire) qui sont considérés comme ambigus par le Standard. En **mode /permissive,** le compilateur émet maintenant un ou plusieurs diagnostics dans les cas qui ont compilé sans diagnostic dans les versions antérieures.

Les erreurs courantes qui peuvent résulter de ce changement sont les suivantes :

- erreur C2593: 'opérateur ?' est ambigu

- erreur C2679: binaire '?': aucun opérateur trouvé qui prend un opératoire droit de type 'B' (ou il n’y a pas de conversion acceptable)

- erreur C2678: binaire '?': aucun opérateur trouvé qui prend un opératoire gauche de type 'A' (ou il n’y a pas de conversion acceptable)

- erreur C2446: ':': pas de conversion de 'B' à 'A'

Un modèle de code typique qui peut causer ce problème est quand une certaine classe C fournit à la fois un constructeur non explicite d’un autre type T et un opérateur de conversion non explicite au type T. En l’espèce, la conversion du deuxième argument au type du troisième argument et la conversion du troisième argument au type du deuxième argument sont des conversions valides. Puisque les deux sont valides, c’est ambigu selon la norme.

```cpp
// Example 1: class that provides conversion to and initialization from some type T
struct A
{
    A(int);
    operator int() const;
};

extern bool cond;

A a(42);
// Accepted when /Zc:ternary or /permissive- is not used:
auto x = cond ? 7 : a; // A: permissive behavior prefers A(7) over (int)a
// Accepted always:
auto y = cond ? 7 : int(a);
auto z = cond ? A(7) : a;
```

Il ya une exception importante à ce modèle commun lorsque T représente l’un des types de cordes non terminés (par exemple, `const char *`, , `const char16_t *`et ainsi de suite) et l’argument réel à `?:` est une chaîne littérale de type correspondant. La sémantique a changé de Sémantique par le fait de la 14e. En conséquence, le code dans l’exemple 2 est accepté sous **/std:c '14** et rejeté sous **/std:c '17** lorsque **/Zc:ternary** ou **/permissive-** est utilisé.

```cpp
// Example 2: exception from the above
struct MyString
{
    MyString(const char* s = "") noexcept;  // from char*
    operator const char* () const noexcept; //   to char*
};

extern bool cond;

MyString s;
// Using /std:c++14, /permissive- or /Zc:ternary behavior
// is to prefer MyString("A") over (const char*)s
// but under /std:c++17 this line causes error C2445:
auto x = cond ? "A" : s;
// You can use a static_cast to resolve the ambiguity:
auto y = cond ? "A" : static_cast<const char*>(s);
```

Un autre cas où vous pouvez voir des `void`erreurs est dans les opérateurs conditionnels avec un argument de type . Ce cas peut être commun dans les macros ASSERT-like.

```cpp
// Example 3: void arguments
void myassert(const char* text, const char* file, int line);
// Accepted when /Zc:ternary or /permissive- is not used:
#define ASSERT_A(ex) (void)((ex) ? 1 : myassert(#ex, __FILE__, __LINE__))
// Accepted always:
#define ASSERT_B(ex) (void)((ex) ? void() : myassert(#ex, __FILE__, __LINE__))
```

Vous pouvez également voir des erreurs dans la métaprogrammation de modèle, où les types conditionnels de résultat d’opérateur peuvent changer sous **/Zc:ternary** et **/permissive-**. Une façon de résoudre ce problème est d’utiliser [std::remove_reference](../../standard-library/remove-reference-class.md) sur le type résultant.

```cpp
// Example 4: different result types
extern bool cond;
extern int count;
char  a = 'A';
const char  b = 'B';
decltype(auto) x = cond ? a : b; // char without, const char& with /Zc:ternary
const char (&z)[2] = count > 3 ? "A" : "B"; // const char* without /Zc:ternary
```

#### <a name="two-phase-name-look-up"></a>Recherche de nom en deux phases

Lorsque l’option **/permissive** est définie, le compilateur analyse les définitions de la fonction et du modèle de classe, identifiant les noms dépendants et non dépendants utilisés dans les modèles au besoin pour la recherche de noms en deux phases. Dans Visual Studio 2017 version 15.3, l’analyse de la dépendance au nom est effectuée. En particulier, les noms non dépendants qui ne sont pas déclarés dans le cadre d’une définition de modèle causent un message diagnostique comme l’exigent les normes ISO C. Dans Visual Studio 2017 version 15.7, la liaison des noms non dépendants qui nécessitent un suivi d’argument-dépendant dans le contexte de définition est également faite.

```cpp
// dependent base
struct B {
    void g() {}
};

template<typename T>
struct D : T {
    void f() {
        // The call to g was incorrectly allowed in VS2017:
        g();  // Now under /permissive-: C3861
        // Possible fixes:
        // this->g();
        // T::g();
    }
};

int main()
{
    D<B> d;
    d.f();
}
```

Si vous voulez un comportement hérité pour la recherche en deux phases, mais autrement veulent **/permissive-** comportement, ajouter le **/Zc:twoPhase-** option.

### <a name="windows-header-issues"></a>Problèmes d’en-tête Windows

**L’option /permissive-** est trop stricte pour les versions des kits Windows avant Windows Fall Creators Update SDK (10.16299.0), ou la version 1709 du Windows Driver Kit (WDK). Nous vous recommandons de mettre à jour les dernières versions des kits Windows afin d’utiliser **/permissive-** dans votre code windows ou appareil.

Certains fichiers d’en-tête dans le Windows Avril 2018 Mise à jour SDK (10.0.17134.0), le Windows Fall Creators Update SDK (10.0.16299.0), ou le Windows Driver Kit (WDK) 1709, ont encore des problèmes qui les rendent incompatibles avec l’utilisation de **/ permissive-**. Pour contourner ces problèmes, nous vous recommandons de limiter l’utilisation de ces en-têtes uniquement aux fichiers de code source qui les nécessitent, et de supprimer **l’option /permissive** lorsque vous compilez ces fichiers de code source spécifiques.

Ces en-têtes WinRT WRL sortis dans le Windows Avril 2018 Mise à jour SDK (10.17134.0) ne sont pas propres avec **/permissive-**. Pour contourner ces questions, soit ne pas utiliser **/permissive-**, ou utiliser **/permissive-** avec **/Zc:twoPhase-** lorsque vous travaillez avec ces en-têtes:

- Questions dans winrt/wrl/async.h

   ```Output
   C:\Program Files (x86)\Windows Kits\10\Include\10.0.17134.0\winrt\wrl\async.h(483): error C3861: 'TraceDelegateAssigned': identifier not found
   C:\Program Files (x86)\Windows Kits\10\Include\10.0.17134.0\winrt\wrl\async.h(491): error C3861: 'CheckValidStateForDelegateCall': identifier not found
   C:\Program Files (x86)\Windows Kits\10\Include\10.0.17134.0\winrt\wrl\async.h(509): error C3861: 'TraceProgressNotificationStart': identifier not found
   C:\Program Files (x86)\Windows Kits\10\Include\10.0.17134.0\winrt\wrl\async.h(513): error C3861: 'TraceProgressNotificationComplete': identifier not found
   ```

- Problème dans winrt/wrl/implements.h

   ```Output
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\winrt\wrl\implements.h(2086): error C2039: 'SetStrongReference': is not a member of 'Microsoft::WRL::Details::WeakReferenceImpl'
   ```

Ces en-têtes mode utilisateur sortis dans le Windows Avril 2018 Mise à jour SDK (10.0.17134.0) ne sont pas propres avec **/permissive-**. Pour contourner ces questions, n’utilisez pas **/permissive-** lorsque vous travaillez avec ces en-têtes:

- Questions dans um/Tune.h

   ```Output
   C:\ProgramFiles(x86)\Windows Kits\10\include\10.0.17134.0\um\tune.h(139): error C3861: 'Release': identifier not found
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\tune.h(559): error C3861: 'Release': identifier not found
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\tune.h(1240): error C3861: 'Release': identifier not found
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\tune.h(1240): note: 'Release': function declaration must be available as none of the arguments depend on a template parameter
   ```

- Question dans um/spddkhlp.h

   ```Output
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\spddkhlp.h(759): error C3861: 'pNode': identifier not found
   ```

- Questions dans um/refptrco.h

   ```Output
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\refptrco.h(179): error C2760: syntax error: unexpected token 'identifier', expected 'type specifier'
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\refptrco.h(342): error C2760: syntax error: unexpected token 'identifier', expected 'type specifier'
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\refptrco.h(395): error C2760: syntax error: unexpected token 'identifier', expected 'type specifier'
   ```

Ces problèmes sont spécifiques aux en-têtes en mode utilisateur dans la mise à jour des créateurs d’automne windows SDK (10.16299.0):

- Question dans um/Query.h

   Lors de l’utilisation de **l’interrupteur /permissive-** compilateur, la `tagRESTRICTION` structure ne compile pas en raison du cas (RTOr) membre «ou».

   ```cpp
   struct tagRESTRICTION
   {
       ULONG rt;
       ULONG weight;
       /* [switch_is][switch_type] */ union _URes
       {
           /* [case()] */ NODERESTRICTION ar;
           /* [case()] */ NODERESTRICTION or;  // error C2059: syntax error: '||'
           /* [case()] */ NODERESTRICTION pxr;
           /* [case()] */ VECTORRESTRICTION vr;
           /* [case()] */ NOTRESTRICTION nr;
           /* [case()] */ CONTENTRESTRICTION cr;
           /* [case()] */ NATLANGUAGERESTRICTION nlr;
           /* [case()] */ PROPERTYRESTRICTION pr;
           /* [default] */  /* Empty union arm */
       } res;
   };
   ```

   Pour résoudre ce problème, compilez des fichiers qui incluent Query.h sans l’option **/permissive-.**

- Question dans um/cellularapi_oem.h

   Lors de l’utilisation de **l’interrupteur /permissive-** compilateur, la déclaration à terme de `enum UICCDATASTOREACCESSMODE` provoque un avertissement:

   ```cpp
   typedef enum UICCDATASTOREACCESSMODE UICCDATASTOREACCESSMODE; // C4471
   ```

   La déclaration à terme de l’enum nonscoped est une extension Microsoft. Pour résoudre ce problème, compilez des fichiers qui incluent cellularapi_oem.h sans l’option **/permissive-,** ou utilisez [l’option /wd](compiler-option-warning-level.md) pour réduire au silence l’avertissement C4471.

- Question dans um/omscript.h

   Dans le C 03, une conversion d’une chaîne littérale à BSTR (qui est un dactylographe à «wchar_t») est dépréciée mais autorisée. Dans le C 11, la conversion n’est plus autorisée.

   ```cpp
   virtual /* [id] */ HRESULT STDMETHODCALLTYPE setExpression(
       /* [in] */ __RPC__in BSTR propname,
       /* [in] */ __RPC__in BSTR expression,
       /* [in][defaultvalue] */ __RPC__in BSTR language = L"") = 0; // C2440
   ```

   Pour résoudre ce problème, compilez des fichiers qui incluent omscript.h sans l’option **/permissive-** ou utilisez **/Zc:strictStrings-** au lieu.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

Dans Visual Studio 2017 version 15.5 et versions ultérieures, utilisez cette procédure:

1. Ouvrez la boîte de dialogue **propriété de** votre projet.

1. Sélectionnez la page **Propriétés** > Configuration**C/CMD** > **Language.**

1. Modifier la valeur de propriété **du mode Conformance** à **Oui (/permissive-)**. Choisissez **OK** ou **appliquez** pour enregistrer vos modifications.

Dans les versions avant Visual Studio 2017 version 15.5, utilisez cette procédure:

1. Ouvrez la boîte de dialogue **propriété de** votre projet.

1. Sélectionnez la page propriété **Configuration Properties** > **C/CMD** > **Command Line.**

1. Entrez l’option **/permissive-** compilateur dans la boîte **Options supplémentaires.** Choisissez **OK** ou **appliquez** pour enregistrer vos modifications.

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Voir aussi

[Options de compilateur MSVC](compiler-options.md)\
[Syntaxe de la ligne de commande du compilateur MSVC](compiler-command-line-syntax.md)
