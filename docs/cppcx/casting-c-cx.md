---
description: 'En savoir plus sur : casting (C++/CX)'
title: Effectuer un cast (C++/CX)
ms.date: 06/19/2018
ms.assetid: 5247f6c7-6a0a-4021-97c9-21c868bd9455
ms.openlocfilehash: 90b9e90833acc14bcf76287b44f70fb914c7604a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97190274"
---
# <a name="casting-ccx"></a>Effectuer un cast (C++/CX)

Quatre opérateurs de cast différents s’appliquent aux types de Windows Runtime : opérateur [static_cast](../cpp/static-cast-operator.md), opérateur [dynamic_cast](../cpp/dynamic-cast-operator.md), opérateur **safe_cast** et [opérateur reinterpret_cast](../cpp/reinterpret-cast-operator.md). **safe_cast** et **`static_cast`** lèvent une exception lorsque la conversion ne peut pas être effectuée ; [Static_cast opérateur](../cpp/static-cast-operator.md) effectue également une vérification de type au moment de la compilation. **`dynamic_cast`** retourne **`nullptr`** s’il ne parvient pas à convertir le type. Bien que **`reinterpret_cast`** retourne une valeur non null, il est possible qu’il ne soit pas valide. Pour cette raison, nous vous recommandons de ne pas utiliser, **`reinterpret_cast`** sauf si vous savez que le cast est concluant. En outre, nous vous recommandons de ne pas utiliser de casts de style C dans votre code C++/CX, car ils sont identiques à **`reinterpret_cast`** .

Le compilateur et le runtime exécutent également des casts implicites, par exemple, dans les opérations de boxing lorsqu'un type valeur ou un type intégré sont passés en tant qu'arguments à une méthode dont le type de paramètre est `Object^`. En théorie, un cast implicite ne doit jamais générer une exception au moment de l'exécution. Si le compilateur ne peut pas effectuer une conversion implicite, il déclenche une erreur au moment de la compilation.

Windows Runtime est une abstraction sur COM, qui utilise les codes d’erreur HRESULT au lieu des exceptions. En général, [Platform::InvalidCastException](../cppcx/platform-invalidcastexception-class.md) indique une erreur COM de bas niveau d'E_NOINTERFACE.

## <a name="static_cast"></a>static_cast

Un **`static_cast`** est vérifié au moment de la compilation pour déterminer s’il existe une relation d’héritage entre les deux types. Le cast provoque une erreur de compilation si les types ne sont pas liés.

Un **`static_cast`** sur une classe ref entraîne également l’exécution d’un contrôle au moment de l’exécution. Un **`static_cast`** sur une classe ref peut passer la vérification au moment de la compilation mais échoue toujours au moment de l’exécution. dans ce cas, une `Platform::InvalidCastException` est levée. En général, vous n'avez pas à gérer ces exceptions, car elles indiquent presque toujours des erreurs de programmation que vous pouvez éliminer au cours du développement et des tests.

Utilisez **`static_cast`** si le code déclare explicitement une relation entre les deux types, et que vous êtes par conséquent sûr que le cast doit fonctionner.

```cpp
    interface class A{};
    public ref class Class1 sealed : A { };
    // ...
    A^ obj = ref new Class1(); // Class1 is an A
    // You know obj is a Class1. The compiler verifies that this is possible, and in C++/CX a run-time check is also performed.
    Class1^ c = static_cast<Class1^>(obj);
```

## <a name="safe_cast"></a>safe_cast

L’opérateur **safe_cast** fait partie de Windows Runtime. Il effectue une vérification de type au moment de l'exécution et lève une `Platform::InvalidCastException` si la conversion échoue. Utilisez **safe_cast** lorsqu’un échec au moment de l’exécution indique une condition exceptionnelle. L’objectif principal de **safe_cast** est d’aider à identifier les erreurs de programmation au cours des phases de développement et de test au point où elles se produisent. Vous ne devez pas gérer l'exception, car l'exception non gérée elle-même identifie le point de défaillance.

Utilisez safe_cast si le code ne déclare pas la relation mais que vous avez la certitude que le cast doit fonctionner.

```cpp
    // A and B are not related
    interface class A{};
    interface class B{};
    public ref class Class1 sealed : A, B { };
    // ...
    A^ obj = ref new Class1();

    // You know that obj’s backing type implements A and B, but
    // the compiler can’t tell this by comparing A and B. The run-time type check succeeds.
    B^ obj2 = safe_cast<B^>(obj);
```

## <a name="dynamic_cast"></a>dynamic_cast

Utilisez **`dynamic_cast`** lorsque vous effectuez un cast d’un objet (plus spécifiquement, un chapeau **^** ) en un type plus dérivé, vous vous attendez à ce que l’objet cible soit parfois **`nullptr`** ou que le cast puisse échouer, et vous souhaitez gérer cette condition comme un chemin de code normal au lieu d’une exception. Par exemple, dans le modèle de projet **application vide (Windows universel)** , la `OnLaunched` méthode dans App. XAMP. cpp utilise **`dynamic_cast`** pour tester si la fenêtre d’application possède du contenu. Ce n'est pas une erreur si elle ne possède pas de contenu mais une condition attendue. `Windows::Current::Content` est un `Windows::UI::XAML::UIElement` et est converti en un `Windows::UI.XAML::Controls::Frame`, qui est un type plus dérivé dans la hiérarchie d'héritage.

```cpp
void App::OnLaunched(Windows::ApplicationModel::Activation::LaunchActivatedEventArgs^ args)
{
    auto rootFrame = dynamic_cast<Frame^>(Window::Current->Content);

    // Do not repeat app initialization when the window already has content,
    // just ensure that the window is active
    if (rootFrame == nullptr)
    {
        // Create a Frame to act as the navigation context and associate it with
        // a SuspensionManager key
        rootFrame = ref new Frame();
        // ...
    }
}
```

Une autre utilisation de **`dynamic_cast`** est de sonder un `Object^` pour déterminer s’il contient un type valeur boxed. Dans ce cas, vous tentez une `dynamic_cast<Platform::Box>` ou une `dynamic_cast<Platform::IBox>`.

## <a name="dynamic_cast-and-tracking-references-"></a>dynamic_cast et références de suivi (%)

Vous pouvez également appliquer un **`dynamic_cast`** à une référence de suivi, mais dans ce cas, le cast se comporte comme **safe_cast**. Elle lève une exception `Platform::InvalidCastException` en cas d’échec, car une référence de suivi ne peut pas avoir la valeur **`nullptr`** .

## <a name="reinterpret_cast"></a>reinterpret_cast

Nous vous recommandons de ne pas utiliser [reinterpret_cast](../cpp/reinterpret-cast-operator.md) , car aucune vérification n'est effectuée, que ce soit au moment de la compilation ou de l'exécution. Dans le pire des cas, un **`reinterpret_cast`** permet aux erreurs de programmation de ne pas être détectées au moment du développement et peut entraîner des erreurs subtiles ou catastrophiques dans le comportement de votre programme. Par conséquent, nous vous recommandons **`reinterpret_cast`** d’utiliser uniquement dans les rares cas où vous devez effectuer un cast entre des types non liés et vous savez que le cast va être concluant. Un exemple d’utilisation rare consiste à convertir un type de Windows Runtime en son type ABI sous-jacent, ce qui signifie que vous prenez le contrôle du décompte de références pour l’objet. C'est la raison pour laquelle nous vous recommandons d'utiliser le pointeur intelligent [ComPtr Class](../cpp/com-ptr-t-class.md) . Sinon, vous devez appeler spécifiquement Release sur l'interface. L'exemple suivant montre comment une classe de référence peut faire l'objet d'un cast en une `IInspectable*`.

```cpp
#include <wrl.h>
using namespace Microsoft::WRL;
auto winRtObject = ref new SomeWinRTType();
ComPtr<IInspectable> inspectable = reinterpret_cast<IInspectable*>(winRtObject);
// ...
```

Si vous utilisez **`reinterpret_cast`** pour effectuer une conversion à partir d’une interface d’exécution oneWindows vers une autre, vous provoquez la libération de l’objet deux fois. Par conséquent, utilisez uniquement ce Cast lorsque vous effectuez une conversion vers une interface d’extensions de composant non C + +.

## <a name="abi-types"></a>Types ABI.

- Les types ABI se trouvent dans les en-têtes du Kit de développement logiciel (SDK) Windows. Pour des raisons de commodité, les en-têtes sont nommés d'après le nom des espaces de noms, par exemple, `windows.storage.h`.

- Les types ABI se trouvent dans une ABI d'espace de noms spéciale, par exemple, `ABI::Windows::Storage::Streams::IBuffer*`.

- Les conversions entre un type d’interface Windows Runtime et son type ABI équivalent sont toujours sécurisées, c’est-à-dire, `IBuffer^` à `ABI::IBuffer*` .

- Une classe de Runtime Windows Runtime doit toujours être convertie en `IInspectable*` ou en son interface par défaut, si cela est connu.

- Après la conversion en types ABI, vous possédez la durée de vie du type et vous devez suivre les règles COM. Nous vous recommandons d'utiliser `WRL::ComPtr` pour simplifier la gestion de la durée de vie des pointeurs ABI.

Le tableau suivant récapitule les cas dans lesquels il est possible d’utiliser en toute sécurité **`reinterpret_cast`** . Dans tous les cas, le cast est sécurisé dans les deux sens.

| Cast de, casté en | Cast en, Cast à partir de |
|--|--|
| `HSTRING` | `String^` |
| `HSTRING*` | `String^*` |
| `IInspectable*` | `Object^` |
| `IInspectable**` | `Object^*` |
| `IInspectable-derived-type*` | `same-interface-from-winmd^` |
| `IInspectable-derived-type**` | `same-interface-from-winmd^*` |
| `IDefault-interface-of-RuntimeClass*` | `same-RefClass-from-winmd^` |
| `IDefault-interface-of-RuntimeClass**` | `same-RefClass-from-winmd^*` |

## <a name="see-also"></a>Voir aussi

- [Système de types](../cppcx/type-system-c-cx.md)
- [Informations de référence sur le langage C++/CX](../cppcx/visual-c-language-reference-c-cx.md)
- [Référence des espaces de noms](../cppcx/namespaces-reference-c-cx.md)
