---
title: -permissive - (conformité aux normes) | Documents Microsoft
ms.date: 06/21/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /permissive
- VC.Project.VCCLCompilerTool.ConformanceMode
dev_langs:
- C++
helpviewer_keywords:
- /permissive compiler options [C++]
- -permissive compiler options [C++]
- Standards conformance compiler options
- permissive compiler options [C++]
ms.assetid: db1cc175-6e93-4a2e-9396-c3725d2d8f71
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3e1a9c407779b6bf441ea1375026af6ac04bb8c8
ms.sourcegitcommit: e013acba70aa29fed60ae7945162adee23e19c3b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/22/2018
ms.locfileid: "36322262"
---
# <a name="permissive--standards-conformance"></a>/ permissive-(conformité aux normes)

Spécifiez le mode de conformité aux normes pour le compilateur. Utilisez cette option pour vous aider à identifier et résoudre les problèmes de conformité dans votre code, pour le rendre plus correct et plus portables.

## <a name="syntax"></a>Syntaxe

> **/ permissive-**

## <a name="remarks"></a>Notes

Vous pouvez utiliser la **/ permissive-** option du compilateur pour spécifier le comportement de compilateur conforme aux normes. Cette option désactive les comportements permissive et définit les [/Zc](../../build/reference/zc-conformance.md) options du compilateur pour la conformité stricte. Dans l’IDE, cette option permet également le code non conforme de soulignement de moteur IntelliSense.

Par défaut, le **/ permissive-** option est définie dans les nouveaux projets créés par la version de Visual Studio 2017 15.5 et versions ultérieures. Il n’est pas défini par défaut dans les versions antérieures. Lorsque l’option est définie, le compilateur génère des erreurs de diagnostic ou des avertissements lors de constructions de langage non standard sont détectées dans votre code, y compris certains bogues courants dans pre-code C ++ 11.

Le **/ permissive-** option est compatible avec presque tous les fichiers d’en-tête dans les Kits de Windows plus récentes, telles que le Kit de développement logiciel (SDK) ou Windows Driver Kit (WDK), à partir de l’automne créateurs de kit de développement (10.0.16299.0). Les versions antérieures du Kit de développement peuvent ne pas compiler sous **/ permissive-** pour différentes raisons de conformité de code de la source. Le compilateur et la livraison de kits de développement logiciel sur des chronologies différentes, par conséquent, il existe d’autres problèmes. Pour les problèmes de fichier d’en-tête spécifique, voir [problèmes d’en-tête Windows](#windows-header-issues) ci-dessous.

Le **/ permissive-** option définit la [/Zc : strictstrings](../../build/reference/zc-conformance.md) et [/Zc : rvaluecast](../../build/reference/zc-conformance.md) options comportement conforme. Leur valeur par défaut non conforme de comportement. Vous pouvez passer spécifique **/Zc** options après **/ permissive-** sur la ligne de commande pour remplacer ce comportement.

Dans les versions du début du compilateur dans Visual Studio 2017 version 15.3, le **/ permissive-** option définit la [/Zc:ternary](../../build/reference/zc-ternary.md) option. Le compilateur implémente également plus de la configuration requise pour la recherche de nom en deux phases. Lorsque le **/ permissive-** option est définie, le compilateur analyse les définitions de modèle (fonction) et de la classe, identification des noms dépendants et indépendants utilisés dans les modèles. Dans cette version, l’analyse des dépendances uniquement nom est effectuée.

Les extensions spécifiques à l’environnement et des zones de langue que la norme laisse jusqu'à l’implémentation ne sont pas affectés par **/ permissive-**. Par exemple, spécifique à Microsoft `__declspec`, convention d’appel et la gestion des mots clés et les directives pragma de compilateur spécifiques ou les attributs gestion structurée des exceptions ne sont pas signalés par le compilateur dans **/ permissive-** mode.

Le **/ permissive-** option utilise la prise en charge de la conformité dans la version actuelle du compilateur pour déterminer les constructions de langage sont non conformes. L’option ne détermine pas si votre code est conforme à une version spécifique de la norme C++. Pour activer la prise en charge de tous les du compilateur implémenté pour le projet de norme plus récente, utilisez le [/std:latest](../../build/reference/std-specify-language-standard-version.md) option. Pour restreindre la prise en charge du compilateur pour la mise en œuvre en C ++ 17 standard, utilisez la [/std : c ++ 17](../../build/reference/std-specify-language-standard-version.md) option. Pour restreindre la prise en charge du compilateur pour mieux correspondre à la norme C ++ 14, utilisez le [/std : c ++ 14](../../build/reference/std-specify-language-standard-version.md) option, qui est la valeur par défaut.

Pas tous les C ++ 11, C ++ 14 ou C ++ 17 conforme aux normes code est pris en charge par le compilateur Visual C++ dans Visual Studio 2017. Selon la version de Visual Studio, le **/ permissive-** option peut ne pas détecte les problèmes concernant certains aspects de la recherche de nom en deux phases, liaison d’une référence non const à une valeur temporaire, traitement copie init comme init direct, ce qui permet plusieurs conversions définies par l’utilisateur dans l’initialisation ou de jetons de remplacement pour les opérateurs logiques et autres zones non pris en charge la mise en conformité. Pour plus d’informations sur les problèmes de conformité dans Visual C++, consultez [Nonstandard Behavior](../../cpp/nonstandard-behavior.md). Pour obtenir le meilleur parti de **/ permissive-**, mise à jour de Visual Studio vers la version la plus récente.

### <a name="how-to-fix-your-code"></a>Comment corriger votre code

Voici quelques exemples de code qui est détecté comme non conformes lorsque vous utilisez **/ permissive-**, ainsi que les méthodes suggérées pour résoudre les problèmes.

#### <a name="use-default-as-an-identifier-in-native-code"></a>Par défaut en tant qu’identificateur dans le code natif

```cpp
void func(int default); // Error C2321: 'default' is a keyword, and
                        // cannot be used in this context
```

#### <a name="lookup-members-in-dependent-base"></a>Membres de recherche de base dépendante

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

#### <a name="initialize-multiple-union-members-in-a-member-initializer"></a>Initialiser plusieurs membres d’union dans un initialiseur de membre

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

#### <a name="hidden-friend-name-lookup-rules"></a>Règles de recherche de nom masqué friend

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
    f(S); // Hidden friend now found via argument-dependent lookup.
}
```

#### <a name="use-scoped-enums-in-array-bounds"></a>Utilisez les enums délimités dans les limites du tableau

```cpp
enum class Color {
    Red, Green, Blue
};

int data[Color::Blue]; // error C3411: 'Color' is not valid as the size
                       // of an array as it is not an integer type.
                       // Cast to type size_t or int to fix.
```

#### <a name="use-for-each-in-native-code"></a>Utilisation pour chacune d’elles dans le code natif

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

#### <a name="ambiguous-conditional-operator-arguments"></a>Arguments de l’opérateur conditionnel ambiguë

Dans les versions du compilateur avant Visual Studio 2017 version 15.3, le compilateur a accepté les arguments pour l’opérateur conditionnel (ou un opérateur ternaire) `?:` qui sont considérés comme étant ambiguës par la norme. Dans **/ permissive-** mode, le compilateur émet désormais un ou plusieurs des diagnostics dans les cas compilé sans diagnostics dans les versions antérieures.

Les erreurs courantes qui peuvent résulter de cette modification sont les suivantes :

- erreur C2593 : 'opérateur' ? est ambigu

- erreur C2679 : binaire ' ?': aucun opérateur ne trouvé qui accepte un opérande de droite de type 'B' (ou il n’existe aucune conversion acceptable)

- l’erreur C2678 : binaire ' ?': aucun opérateur ne trouvé qui accepte un opérande de partie gauche de type 'A' (ou il n’existe aucune conversion acceptable)

- erreur C2446 : ' :': pas de conversion de « B » par « A »

Un modèle de code typique qui peut provoquer ce problème est une classe C fournit un constructeur non explicite d’un autre type T et un opérateur de conversion non explicite au type T. Dans ce cas, la conversion de l’argument 2 pour le type de la 3e et la conversion de l’argument 3 pour le type de la 2e sont des conversions valides, ce qui est ambigu conformément à la norme.

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

Il existe une exception importante à ce modèle commun lorsque T représente un des types de chaîne terminée par null (par exemple, `const char *`, `const char16_t *`, et ainsi de suite) et l’argument réel pour `?:` est une chaîne littérale de type correspondant. C ++ 17 est devenue la sémantique C ++ 14. Par conséquent, le code dans l’exemple 2 est accepté sous **/std : c ++ 14** et rejetés sous **/std : c ++ 17** lorsque **/Zc:ternary** ou **/permissive-** est utilisé.

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

Un autre cas où vous pouvez voir des erreurs est dans des opérateurs conditionnels avec un argument de type `void`. Ce cas peuvent être commun dans les macros d’assertion de type.

```cpp
// Example 3: void arguments
void myassert(const char* text, const char* file, int line);
// Accepted when /Zc:ternary or /permissive- is not used:
#define ASSERT_A(ex) (void)((ex) ? 1 : myassert(#ex, __FILE__, __LINE__))
// Accepted always:
#define ASSERT_B(ex) (void)((ex) ? void() : myassert(#ex, __FILE__, __LINE__))
```

Vous pouvez également voir les erreurs dans le modèle métaprogrammation, où les types de résultats d’opérateur conditionnel peuvent changer sous **/Zc:ternary** et **/ permissive-**. Pour résoudre ce problème consiste à utiliser [std::remove_reference](../../standard-library/remove-reference-class.md) sur le type résultant.

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

Lorsque le **/ permissive-** option est définie, le compilateur analyse les définitions de modèle (fonction) et de la classe, identification des noms dépendants et indépendants utilisés dans les modèles en fonction des besoins de la recherche de nom en deux phases. Dans Visual Studio 2017 une version 15.3, analyse de dépendance de nom est effectuée. En particulier, les noms non dépendants qui ne sont pas déclarés dans le contexte d’une définition de modèle provoquent un message de diagnostic comme requis par les normes ISO C++. Dans Visual Studio 2017 une version 15.7, liaison de noms non dépendants nécessiter argument dépendant de recherche dans le contexte de la définition est également assurée.

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

Si vous souhaitez le comportement hérité pour la recherche en deux phases, mais dans le cas contraire **/ permissive-** comportement, ajoutez le **/Zc:twoPhase-** option.

### <a name="windows-header-issues"></a>Problèmes d’en-tête Windows

Le **/ permissive-** option est trop stricte pour les versions des Kits Windows avant l’automne créateurs de mise à jour de kit de développement (10.0.16299.0), ou la version de Windows Driver Kit (WDK) 1709. Nous vous recommandons de mettre à jour avec les dernières versions des Kits Windows pour pouvoir utiliser **/ permissive-** dans votre code de pilote Windows ou un périphérique.

Certains fichiers d’en-tête en avril Windows SDK de mise à jour 2018 (10.0.17134.0), le SDK Windows automne créateurs de mise à jour (10.0.16299.0) ou Windows Driver Kit (WDK) 1709, persistent toujours des problèmes susceptibles de les rendre incompatibles avec l’utilisation de **/permissive-**. Pour contourner ces problèmes, nous vous recommandons de limiter l’utilisation de ces en-têtes pour uniquement ces fichiers de code source qui en ont besoin et supprimez le **/ permissive-** option lorsque vous compilez ces fichiers de code source spécifique.

Ces en-têtes WinRT WRL publiés dans les fenêtres avril 2018 Kit de développement logiciel mise à jour (10.0.17134.0) ne sont pas propres avec **/ permissive-**. Pour contourner ces problèmes, n’utilisez pas **/ permissive-**, ou utilisez **/ permissive-** avec **/Zc:twoPhase-** lorsque vous travaillez avec ces en-têtes :

- Problèmes de winrt/wrl/async.h

   ```Output
   C:\Program Files (x86)\Windows Kits\10\Include\10.0.17134.0\winrt\wrl\async.h(483): error C3861: 'TraceDelegateAssigned': identifier not found
   C:\Program Files (x86)\Windows Kits\10\Include\10.0.17134.0\winrt\wrl\async.h(491): error C3861: 'CheckValidStateForDelegateCall': identifier not found
   C:\Program Files (x86)\Windows Kits\10\Include\10.0.17134.0\winrt\wrl\async.h(509): error C3861: 'TraceProgressNotificationStart': identifier not found
   C:\Program Files (x86)\Windows Kits\10\Include\10.0.17134.0\winrt\wrl\async.h(513): error C3861: 'TraceProgressNotificationComplete': identifier not found
   ```

- Émettre dans winrt/wrl/implements.h

   ```Output
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\winrt\wrl\implements.h(2086): error C2039: 'SetStrongReference': is not a member of 'Microsoft::WRL::Details::WeakReferenceImpl'
   ```

Ces en-têtes en Mode utilisateur publiés dans les fenêtres avril 2018 Kit de développement logiciel mise à jour (10.0.17134.0) ne sont pas propres avec **/ permissive-**. Pour contourner ces problèmes, n’utilisez pas **/ permissive-** lorsque vous travaillez avec ces en-têtes :

- Problèmes de um/Tune.h

   ```Output
   C:\ProgramFiles(x86)\Windows Kits\10\include\10.0.17134.0\um\tune.h(139): error C3861: 'Release': identifier not found
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\tune.h(559): error C3861: 'Release': identifier not found
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\tune.h(1240): error C3861: 'Release': identifier not found
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\tune.h(1240): note: 'Release': function declaration must be available as none of the arguments depend on a template parameter
   ```

- Émettre dans um/spddkhlp.h

   ```Output
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\spddkhlp.h(759): error C3861: 'pNode': identifier not found
   ```

- Problèmes de um/refptrco.h

   ```Output
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\refptrco.h(179): error C2760: syntax error: unexpected token 'identifier', expected 'type specifier'
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\refptrco.h(342): error C2760: syntax error: unexpected token 'identifier', expected 'type specifier'
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\refptrco.h(395): error C2760: syntax error: unexpected token 'identifier', expected 'type specifier'
   ```

Ces problèmes sont spécifiques aux en-têtes de Mode utilisateur dans le SDK de mise à jour de créateurs font partie de Windows (10.0.16299.0) :

- Émettre dans um/Query.h

   Lorsque vous utilisez la **/ permissive-** commutateur de compilateur, le `tagRESTRICTION` structure ne se compile pas en raison du membre case(RTOr) 'ou'.

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

   Pour résoudre ce problème, compiler des fichiers qui incluent Query.h sans le **/ permissive-** option.

- Émettre dans um/cellularapi_oem.h

   Lorsque vous utilisez la **/ permissive-** commutateur du compilateur, la déclaration anticipée de `enum UICCDATASTOREACCESSMODE` génère un avertissement :

   ```cpp
   typedef enum UICCDATASTOREACCESSMODE UICCDATASTOREACCESSMODE; // C4471
   ```

   La déclaration anticipée d’enum non délimité est une extension Microsoft. Pour résoudre ce problème, compiler des fichiers qui incluent cellularapi_oem.h sans le **/ permissive-** option, ou utilisez le [/wd](../../build/reference/compiler-option-warning-level.md) option progressivement avertissement C4471.

- Émettre dans um/omscript.h

   Dans C ++ 03, une conversion à partir d’un littéral de chaîne BSTR (qui est un typedef pour ' wchar_t *') est déconseillée mais autorisée. Dans C ++ 11, la conversion n’est plus autorisée.

   ```cpp
   virtual /* [id] */ HRESULT STDMETHODCALLTYPE setExpression(
       /* [in] */ __RPC__in BSTR propname,
       /* [in] */ __RPC__in BSTR expression,
       /* [in][defaultvalue] */ __RPC__in BSTR language = L"") = 0; // C2440
   ```

   Pour résoudre ce problème, compiler des fichiers qui incluent omscript.h sans le **/ permissive-** option ou utilisez **/Zc:strictStrings-** à la place.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

Dans la version de Visual Studio 2017 15.5 et versions ultérieures, utilisez cette procédure :

1. Ouvrez votre projet **Pages de propriétés** boîte de dialogue.

1. Sélectionnez le **propriétés de Configuration** > **C/C++** > **langage** page de propriétés.

1. Modifier la **mode de conformité** valeur de propriété à **Oui (/ permissive-)**. Choisissez **OK** ou **appliquer** pour enregistrer vos modifications.

Dans les versions antérieures de Visual Studio 2017 version 15.5, utilisez cette procédure :

1. Ouvrez votre projet **Pages de propriétés** boîte de dialogue.

1. Sélectionnez le **propriétés de Configuration** > **C/C++** > **ligne de commande** page de propriétés.

1. Entrez le **/ permissive-** option du compilateur dans le **des Options supplémentaires** boîte. Choisissez **OK** ou **appliquer** pour enregistrer vos modifications.

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Voir aussi

- [Options du compilateur](../../build/reference/compiler-options.md)
- [Définition des options du compilateur](../../build/reference/setting-compiler-options.md)
