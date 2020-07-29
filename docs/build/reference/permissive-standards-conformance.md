---
title: /permissive - (Conformité aux standards)
description: Guide de référence de l’option du compilateur Microsoft C++/permissive-(conformité aux normes).
ms.date: 06/04/2020
f1_keywords:
- /permissive
- VC.Project.VCCLCompilerTool.ConformanceMode
helpviewer_keywords:
- /permissive compiler options [C++]
- -permissive compiler options [C++]
- Standards conformance compiler options
- permissive compiler options [C++]
ms.assetid: db1cc175-6e93-4a2e-9396-c3725d2d8f71
ms.openlocfilehash: 69a6b413ec6d9d6897e5f11a11aac8c75db2cf5f
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87217205"
---
# <a name="permissive--standards-conformance"></a>/permissive - (Conformité aux standards)

Spécifiez le mode de conformité aux normes pour le compilateur. Utilisez cette option pour vous aider à identifier et à résoudre les problèmes de conformité dans votre code, afin de le rendre plus facile et plus portable.

## <a name="syntax"></a>Syntaxe

> **`/permissive-`**

## <a name="remarks"></a>Notes

Cette option est prise en charge dans Visual Studio 2017 et versions ultérieures.

Vous pouvez utiliser l' **`/permissive-`** option du compilateur pour spécifier le comportement du compilateur conforme aux normes. Cette option désactive les comportements permissif et définit les [**`/Zc`**](zc-conformance.md) Options du compilateur pour une conformité stricte. Dans l’IDE, cette option permet également au moteur IntelliSense de souligner le code non conforme.

Par défaut, l' **`/permissive-`** option est définie dans les nouveaux projets créés par Visual Studio 2017, version 15,5 et versions ultérieures. Elle n’est pas définie par défaut dans les versions antérieures. Lorsque l’option est définie, le compilateur génère des erreurs ou des avertissements de diagnostic quand des constructions de langage non standard sont détectées dans votre code. Ces constructions incluent des bogues courants dans le code antérieur à C + + 11.

L' **`/permissive-`** option est compatible avec presque tous les fichiers d’en-tête des derniers kits Windows, tels que le kit de développement logiciel (SDK) ou Windows Driver Kit (WDK), à partir du kit de développement logiciel (SDK) Windows automne Creators (10.0.16299.0). La compilation des versions antérieures du kit de développement logiciel (SDK) peut échouer sous **`/permissive-`** pour différentes raisons de conformité du code source. Le compilateur et les kits de développement logiciel (SDK) sont fournis sur différentes chronologies de version. il y a donc des problèmes restants. Pour obtenir des problèmes spécifiques au fichier d’en-tête, consultez [problèmes d’en-tête Windows](#windows-header-issues) ci-dessous.

L' **`/permissive-`** option définit les [**`/Zc:referenceBinding`**](zc-referencebinding-enforce-reference-binding-rules.md) [**`/Zc:strictStrings`**](zc-strictstrings-disable-string-literal-type-conversion.md) options, et [**`/Zc:rvalueCast`**](zc-rvaluecast-enforce-type-conversion-rules.md) pour la conformité au comportement. Par défaut, ces options ont un comportement non conforme. Vous pouvez passer des **`/Zc`** options spécifiques après **`/permissive-`** sur la ligne de commande pour remplacer ce comportement.

Dans les versions du compilateur qui commencent dans Visual Studio 2017 version 15,3, l' **`/permissive-`** option définit l' [**`/Zc:ternary`**](zc-ternary.md) option. Le compilateur implémente également davantage d’exigences pour la recherche de nom en deux phases. Lorsque l' **`/permissive-`** option est définie, le compilateur analyse les définitions de fonction et de modèle de classe et identifie les noms dépendants et non dépendants utilisés dans les modèles. Dans cette version, seule l’analyse des dépendances de nom est exécutée.

Les extensions spécifiques à l’environnement et les zones de langage que le standard laisse à l’implémentation ne sont pas affectées par **`/permissive-`** . Par exemple, les mots clés spécifiques à Microsoft **`__declspec`** , la Convention d’appel et la gestion structurée des exceptions, ainsi que les directives ou attributs pragma spécifiques au compilateur, ne sont pas signalés par le compilateur en **`/permissive-`** mode.

L' **`/permissive-`** option utilise la prise en charge de la conformité dans la version actuelle du compilateur pour déterminer les constructions de langage qui ne sont pas conformes. L’option ne détermine pas si votre code est conforme à une version spécifique de la norme C++. Pour activer toutes les prises en charge du compilateur implémentées pour la dernière norme préliminaire, utilisez l' [**`/std:c++latest`**](std-specify-language-standard-version.md) option. Pour limiter la prise en charge du compilateur à la norme C++ 17 actuellement implémentée, utilisez l' [**`/std:c++17`**](std-specify-language-standard-version.md) option. Pour limiter la prise en charge du compilateur à une correspondance plus étroite avec la norme C++ 14, utilisez l' [**`/std:c++14`**](std-specify-language-standard-version.md) option, qui est la valeur par défaut.

Tous les codes conformes aux normes C++ 11, C++ 14 ou C++ 17 ne sont pas pris en charge par le compilateur MSVC dans toutes les versions de Visual Studio 2017. Selon la version de Visual Studio, l' **`/permissive-`** option peut ne pas détecter les problèmes dans certains aspects de la recherche de nom en deux phases, en liant une référence non const à un temporaire, en traitant l’initialisation de copie en tant qu’initialisation directe, en autorisant plusieurs conversions définies par l’utilisateur dans l’initialisation, ou des jetons alternatifs pour les opérateurs logiques et d’autres zones de Pour plus d’informations sur les problèmes de conformité dans Visual C++, consultez [Nonstandard Behavior](../../cpp/nonstandard-behavior.md). Pour tirer le meilleur parti de **`/permissive-`** , mettez à jour Visual Studio vers la dernière version.

### <a name="how-to-fix-your-code"></a>Comment corriger votre code

Voici quelques exemples de code qui est détecté comme non conforme quand vous utilisez **`/permissive-`** , ainsi que des méthodes suggérées pour résoudre les problèmes.

#### <a name="use-default-as-an-identifier-in-native-code"></a>Utiliser la valeur par défaut comme identificateur dans le code natif

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

#### <a name="use-of-qualified-names-in-member-declarations"></a>Utilisation de noms qualifiés dans les déclarations de membre

```cpp
struct A {
    void A::f() { } // error C4596: illegal qualified name in member
                    // declaration.
                    // Remove redundant 'A::' to fix.
};
```

#### <a name="initialize-multiple-union-members-in-a-member-initializer"></a>Initialiser plusieurs membres Union dans un initialiseur de membre

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

#### <a name="hidden-friend-name-lookup-rules"></a>Règles de recherche des noms d’amis masqués

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

#### <a name="use-scoped-enums-in-array-bounds"></a>Utiliser des enums délimités dans des limites de tableau

```cpp
enum class Color {
    Red, Green, Blue
};

int data[Color::Blue]; // error C3411: 'Color' is not valid as the size
                       // of an array as it is not an integer type.
                       // Cast to type size_t or int to fix.
```

#### <a name="use-for-each-in-native-code"></a>Utiliser for each en code natif

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

#### <a name="ambiguous-conditional-operator-arguments"></a>Arguments d’opérateur conditionnel ambigus

Dans les versions du compilateur antérieures à Visual Studio 2017 version 15,3, le compilateur a accepté les arguments de l’opérateur conditionnel (ou de l’opérateur ternaire) `?:` qui sont considérés comme ambigus par la norme. En **`/permissive-`** mode, le compilateur émet désormais un ou plusieurs Diagnostics dans les cas qui ont été compilés sans Diagnostics dans les versions antérieures.

Les erreurs courantes qui peuvent résulter de cette modification sont les suivantes :

- **`error C2593`**`: 'operator ?' is ambiguous`

- **`error C2679`**`: binary '?': no operator found which takes a right-hand operand of type 'B' (or there is no acceptable conversion)`

- **`error C2678`**`: binary '?': no operator found which takes a left-hand operand of type 'A' (or there is no acceptable conversion)`

- **`error C2446`**`: ':': no conversion from 'B' to 'A'`

Un modèle de code classique qui peut provoquer ce problème est quand une classe C fournit à la fois un constructeur non explicite d’un autre type T et un opérateur de conversion non explicite au type T. Dans ce cas, la conversion du deuxième argument vers le type du troisième argument et la conversion du troisième argument en type du deuxième argument sont des conversions valides. Étant donné que les deux sont valides, elles sont ambiguës en fonction de la norme.

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

Il y a une exception importante à ce modèle commun quand T représente l’un des types de chaînes terminées par le caractère null (par exemple,,, etc `const char *` `const char16_t *` .) et que l’argument réel de `?:` est un littéral de chaîne de type correspondant. C++ 17 a modifié la sémantique de C++ 14. Par conséquent, le code de l’exemple 2 est accepté sous **`/std:c++14`** et rejeté sous **`/std:c++17`** quand **`/Zc:ternary`** ou **`/permissive-`** est utilisé.

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

Vous pouvez également voir des erreurs dans les opérateurs conditionnels avec un argument de type **`void`** . Ce cas de figure peut être courant dans les macros de type assertion.

```cpp
// Example 3: void arguments
void myassert(const char* text, const char* file, int line);
// Accepted when /Zc:ternary or /permissive- is not used:
#define ASSERT_A(ex) (void)((ex) ? 1 : myassert(#ex, __FILE__, __LINE__))
// Accepted always:
#define ASSERT_B(ex) (void)((ex) ? void() : myassert(#ex, __FILE__, __LINE__))
```

Vous pouvez également voir des erreurs dans la programmation de modèles, où les types de résultats d’opérateur conditionnel peuvent changer sous **`/Zc:ternary`** et **`/permissive-`** . Une façon de résoudre ce problème consiste à utiliser [`std::remove_reference`](../../standard-library/remove-reference-class.md) sur le type résultant.

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

Lorsque l' **`/permissive-`** option est définie, le compilateur analyse les définitions de fonction et de modèle de classe, en identifiant les noms dépendants et non dépendants utilisés dans les modèles comme requis pour la recherche de nom en deux phases. Dans Visual Studio 2017 version 15,3, l’analyse des dépendances de noms est effectuée. En particulier, les noms non dépendants qui ne sont pas déclarés dans le contexte d’une définition de modèle provoquent un message de diagnostic comme requis par les normes ISO C++. Dans Visual Studio 2017 version 15,7, la liaison des noms non dépendants qui requièrent une recherche dépendante d’un argument dans le contexte de définition est également effectuée.

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

Si vous souhaitez un comportement hérité pour la recherche en deux phases, mais que vous souhaitez utiliser **`/permissive-`** le comportement, ajoutez l' **`/Zc:twoPhase-`** option.

### <a name="windows-header-issues"></a>Problèmes d’en-tête Windows

L' **`/permissive-`** option est trop stricte pour les versions des kits Windows antérieures à Windows automne Creators Update SDK (10.0.16299.0) ou Windows Driver Kit (WDK) version 1709. Nous vous recommandons d’effectuer la mise à jour vers les dernières versions des kits Windows à utiliser **`/permissive-`** dans votre code de pilote de périphérique ou Windows.

Certains fichiers d’en-tête dans le kit de développement logiciel (SDK) 2018 d’avril, le kit de développement logiciel (SDK) Windows automne Creators (10.0.16299.0) ou Windows Driver Kit (WDK) 1709 présentent toujours des problèmes qui les rendent incompatibles avec l’utilisation de **`/permissive-`** . Pour contourner ces problèmes, nous vous recommandons de limiter l’utilisation de ces en-têtes uniquement aux fichiers de code source qui en ont besoin, et de supprimer l' **`/permissive-`** option quand vous compilez ces fichiers de code source spécifiques.

Ces en-têtes WRL WinRT publiés dans le kit de développement logiciel (SDK) de mise à jour 2018 de Windows (10.0.17134.0) ne sont pas propres à **`/permissive-`** . Pour contourner ces problèmes, n’utilisez pas **`/permissive-`** , ou utilisez **`/permissive-`** avec **`/Zc:twoPhase-`** lorsque vous travaillez avec ces en-têtes :

- Problèmes dans WinRT/WRL/Async. h

   ```Output
   C:\Program Files (x86)\Windows Kits\10\Include\10.0.17134.0\winrt\wrl\async.h(483): error C3861: 'TraceDelegateAssigned': identifier not found
   C:\Program Files (x86)\Windows Kits\10\Include\10.0.17134.0\winrt\wrl\async.h(491): error C3861: 'CheckValidStateForDelegateCall': identifier not found
   C:\Program Files (x86)\Windows Kits\10\Include\10.0.17134.0\winrt\wrl\async.h(509): error C3861: 'TraceProgressNotificationStart': identifier not found
   C:\Program Files (x86)\Windows Kits\10\Include\10.0.17134.0\winrt\wrl\async.h(513): error C3861: 'TraceProgressNotificationComplete': identifier not found
   ```

- Problème dans WinRT/WRL/Implements. h

   ```Output
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\winrt\wrl\implements.h(2086): error C2039: 'SetStrongReference': is not a member of 'Microsoft::WRL::Details::WeakReferenceImpl'
   ```

Ces en-têtes de mode utilisateur publiés dans le kit de développement logiciel (SDK) de mise à jour 2018 de Windows (10.0.17134.0) ne sont pas propres à **`/permissive-`** . Pour contourner ces problèmes, n’utilisez pas **`/permissive-`** lors de l’utilisation de ces en-têtes :

- Problèmes dans la messagerie unifiée/réglage. h

   ```Output
   C:\ProgramFiles(x86)\Windows Kits\10\include\10.0.17134.0\um\tune.h(139): error C3861: 'Release': identifier not found
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\tune.h(559): error C3861: 'Release': identifier not found
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\tune.h(1240): error C3861: 'Release': identifier not found
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\tune.h(1240): note: 'Release': function declaration must be available as none of the arguments depend on a template parameter
   ```

- Problème dans um/spddkhlp. h

   ```Output
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\spddkhlp.h(759): error C3861: 'pNode': identifier not found
   ```

- Problèmes dans um/refptrco. h

   ```Output
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\refptrco.h(179): error C2760: syntax error: unexpected token 'identifier', expected 'type specifier'
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\refptrco.h(342): error C2760: syntax error: unexpected token 'identifier', expected 'type specifier'
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\refptrco.h(395): error C2760: syntax error: unexpected token 'identifier', expected 'type specifier'
   ```

Ces problèmes sont spécifiques aux en-têtes en mode utilisateur dans le kit de développement logiciel (SDK) Windows automne Creators Update (10.0.16299.0) :

- Problème dans la messagerie unifiée/Query. h

   Lors de l’utilisation du **`/permissive-`** commutateur de compilateur, la `tagRESTRICTION` structure ne se compile pas en raison du membre (RTOr) 'ou'.

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

   Pour résoudre ce problème, compilez les fichiers qui incluent Query. h sans l' **`/permissive-`** option.

- Problème dans um/cellularapi_oem. h

   Lors de l’utilisation du **`/permissive-`** commutateur de compilateur, la déclaration anticipée de `enum UICCDATASTOREACCESSMODE` génère un avertissement :

   ```cpp
   typedef enum UICCDATASTOREACCESSMODE UICCDATASTOREACCESSMODE; // C4471
   ```

   La déclaration anticipée d’une énumération non délimitée est une extension Microsoft. Pour résoudre ce problème, compilez les fichiers qui incluent cellularapi_oem. h sans l' **`/permissive-`** option, ou utilisez l' [**`/wd`**](compiler-option-warning-level.md) option pour émettre un message d’avertissement C4471.

- Problème dans um/omscript. h

   Dans C++ 03, la conversion d’un littéral de chaîne en BSTR (qui est un typedef en’wchar_t * ') est déconseillée, mais autorisée. En C++ 11, la conversion n’est plus autorisée.

   ```cpp
   virtual /* [id] */ HRESULT STDMETHODCALLTYPE setExpression(
       /* [in] */ __RPC__in BSTR propname,
       /* [in] */ __RPC__in BSTR expression,
       /* [in][defaultvalue] */ __RPC__in BSTR language = L"") = 0; // C2440
   ```

   Pour résoudre ce problème, compilez les fichiers qui incluent omscript. h sans l' **`/permissive-`** option, ou utilisez à la **`/Zc:strictStrings-`** place.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

Dans Visual Studio 2017 version 15,5 et versions ultérieures, utilisez la procédure suivante :

1. Ouvrez la boîte de dialogue **pages de propriétés** de votre projet.

1. Sélectionnez la page de propriétés de la propriété de **configuration**  >  **C/C++**  >  **Language** .

1. Modifiez la valeur de la propriété **mode de conformité** sur **Oui (/permissive-)**. Cliquez sur **OK** ou sur **appliquer** pour enregistrer vos modifications.

Dans les versions antérieures à Visual Studio 2017 version 15,5, utilisez la procédure suivante :

1. Ouvrez la boîte de dialogue **pages de propriétés** de votre projet.

1. Sélectionnez la page de propriétés ligne de commande des **Propriétés de configuration**  >  **C/C++**  >  **Command Line** .

1. Entrez l’option du compilateur **/permissive-** dans la zone **options supplémentaires** . Cliquez sur **OK** ou sur **appliquer** pour enregistrer vos modifications.

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Voir aussi

[Options du compilateur MSVC](compiler-options.md)\
[Syntaxe de la ligne de commande du compilateur MSVC](compiler-command-line-syntax.md)
