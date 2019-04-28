---
title: Effectuer un cast (C++/CX)
ms.date: 06/19/2018
ms.assetid: 5247f6c7-6a0a-4021-97c9-21c868bd9455
ms.openlocfilehash: 65d489d14c91b462e5a2bbe8bd60fce2657904a7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62258211"
---
# <a name="casting-ccx"></a>Effectuer un cast (C++/CX)

Quatre opérateurs de cast différents s’appliquent aux types Windows Runtime : [opérateur static_cast](../cpp/static-cast-operator.md), [opérateur dynamic_cast](../cpp/dynamic-cast-operator.md), **opérateur safe_cast**, et [ reinterpret_cast, opérateur](../cpp/reinterpret-cast-operator.md). **safe_cast** et **static_cast** lève une exception lors de la conversion ne peut pas être exécutée. [opérateur static_cast](../cpp/static-cast-operator.md) effectue également une vérification de type au moment de la compilation. **dynamic_cast** retourne **nullptr** en cas d’échec convertir le type. Bien que **reinterpret_cast** retourne une valeur non null, il peut être non valide. Pour cette raison, nous vous conseillons pas **reinterpret_cast** , sauf si vous savez que le cast va réussir. En outre, nous vous recommandons de pas utiliser des casts de style C dans votre C++/CX de code, car elles sont identiques aux **reinterpret_cast**.

Le compilateur et le runtime exécutent également des casts implicites, par exemple, dans les opérations de boxing lorsqu'un type valeur ou un type intégré sont passés en tant qu'arguments à une méthode dont le type de paramètre est `Object^`. En théorie, un cast implicite ne doit jamais générer une exception au moment de l'exécution. Si le compilateur ne peut pas effectuer une conversion implicite, il déclenche une erreur au moment de la compilation.

Windows Runtime est une abstraction sur COM, qui utilise des codes d’erreur HRESULT au lieu d’exceptions. En général, [Platform::InvalidCastException](../cppcx/platform-invalidcastexception-class.md) indique une erreur COM de bas niveau d'E_NOINTERFACE.

## <a name="staticcast"></a>static_cast

Un **static_cast** est vérifié au moment de la compilation pour déterminer s’il existe une relation d’héritage entre les deux types. Le cast provoque une erreur de compilation si les types ne sont pas liés.

Un **static_cast** sur une variable de référence la classe entraîne également une vérification de l’exécution à effectuer. Un **static_cast** sur ref classe passe la vérification des temps de compilation mais encore échouer au moment de l’exécution ; dans ce cas un `Platform::InvalidCastException` est levée. En général, vous n'avez pas à gérer ces exceptions, car elles indiquent presque toujours des erreurs de programmation que vous pouvez éliminer au cours du développement et des tests.

Utilisez **static_cast** si le code déclare explicitement une relation entre les deux types, et vous êtes certain que le cast doit fonctionner.

```cpp
    interface class A{};
    public ref class Class1 sealed : A { };
    // ...
    A^ obj = ref new Class1(); // Class1 is an A
    // You know obj is a Class1. The compiler verifies that this is possible, and in C++/CX a run-time check is also performed.
    Class1^ c = static_cast<Class1^>(obj);
```

## <a name="safecast"></a>safe_cast

Le **safe_cast** opérateur fait partie de Windows Runtime. Il effectue une vérification de type au moment de l'exécution et lève une `Platform::InvalidCastException` si la conversion échoue. Utilisez **safe_cast** lorsqu’un échec d’exécution indique une condition exceptionnelle. L’objectif principal de **safe_cast** consiste à identifier les erreurs de programmation pendant le développement et le test des phases au point où elles se produisent. Vous ne devez pas gérer l'exception, car l'exception non gérée elle-même identifie le point de défaillance.

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

## <a name="dynamiccast"></a>dynamic_cast

Utilisez **dynamic_cast** lors de la conversion d’un objet (plus précisément, un chapeau **^**) à un type plus dérivé, vous attendez soit que la cible objet peut être parfois **nullptr** ou que le cast puisse échouer, et que vous souhaitez gérer cette condition comme un chemin d’accès du code normal au lieu d’une exception. Par exemple, dans le **application vide (Windows universel)** modèle de projet, le `OnLaunched` méthode dans les utilisations app.xamp.cpp **dynamic_cast** pour tester si la fenêtre d’application possède du contenu. Ce n'est pas une erreur si elle ne possède pas de contenu mais une condition attendue. `Windows::Current::Content` est un `Windows::UI::XAML::UIElement` et est converti en un `Windows::UI.XAML::Controls::Frame`, qui est un type plus dérivé dans la hiérarchie d'héritage.

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

Une autre utilisation de **dynamic_cast** est de détecter un `Object^` pour déterminer s’il contient un type valeur boxed. Dans ce cas, vous tentez une `dynamic_cast<Platform::Box>` ou une `dynamic_cast<Platform::IBox>`.

## <a name="dynamiccast-and-tracking-references-"></a>dynamic_cast et références de suivi (%)

Vous pouvez également appliquer un **dynamic_cast** à une référence de suivi, mais dans ce cas, le cast se comporte comme **safe_cast**. Elle lève une exception `Platform::InvalidCastException` en cas d’échec, car une référence de suivi ne peut pas avoir la valeur **nullptr**.

## <a name="reinterpretcast"></a>reinterpret_cast

Nous vous recommandons de ne pas utiliser [reinterpret_cast](../cpp/reinterpret-cast-operator.md) , car aucune vérification n'est effectuée, que ce soit au moment de la compilation ou de l'exécution. Dans le pire des cas, un **reinterpret_cast** rend possible pour la programmation des erreurs détectées au moment du développement et de provoquer des erreurs subtiles ou catastrophiques un comportement de votre programme. Par conséquent, nous vous recommandons d’utiliser **reinterpret_cast** uniquement dans les rares cas où vous devez effectuer un cast entre types non liés et que vous savez que le cast va réussir. Un exemple d’utilisation rare consiste à convertir un type Windows Runtime en son type ABI sous-jacent, cela signifie que vous prenez le contrôle du décompte de références pour l’objet. C'est la raison pour laquelle nous vous recommandons d'utiliser le pointeur intelligent [ComPtr Class](../cpp/com-ptr-t-class.md) . Sinon, vous devez appeler spécifiquement Release sur l'interface. L'exemple suivant montre comment une classe de référence peut faire l'objet d'un cast en une `IInspectable*`.

```cpp
#include <wrl.h>
using namespace Microsoft::WRL;
auto winRtObject = ref new SomeWinRTType();
ComPtr<IInspectable> inspectable = reinterpret_cast<IInspectable*>(winRtObject);
// ...
```

Si vous utilisez **reinterpret_cast** pour convertir à partir de l’interface de Runtime oneWindows vers un autre, vous conduisez l’objet doit être publié deux fois. Par conséquent, utilisez uniquement cette conversion lors de la conversion vers une interface d’extensions de composant Visual C++.

## <a name="abi-types"></a>Types ABI.

- Les types ABI se trouvent dans les en-têtes du Kit de développement logiciel (SDK) Windows. Pour des raisons de commodité, les en-têtes sont nommés d'après le nom des espaces de noms, par exemple, `windows.storage.h`.

- Les types ABI se trouvent dans une ABI d'espace de noms spéciale, par exemple, `ABI::Windows::Storage::Streams::IBuffer*`.

- Conversions entre un type d’interface Windows Runtime et son type ABI équivalent sont toujours sûres, autrement dit, `IBuffer^` à `ABI::IBuffer*`.

- Une classe d’exécution de Windows Runtime doit-elle toujours être convertie en `IInspectable*` ou son interface par défaut, si cela est connu.

- Après la conversion en types ABI, vous possédez la durée de vie du type et vous devez suivre les règles COM. Nous vous recommandons d'utiliser `WRL::ComPtr` pour simplifier la gestion de la durée de vie des pointeurs ABI.

Le tableau suivant récapitule les cas dans lesquels il est déconseillé d’utiliser **reinterpret_cast**. Dans tous les cas, le cast est sécurisé dans les deux sens.

|||
|-|-|
|`HSTRING`|`String^`|
|`HSTRING*`|`String^*`|
|`IInspectable*`|`Object^`|
|`IInspectable**`|`Object^*`|
|`IInspectable-derived-type*`|`same-interface-from-winmd^`|
|`IInspectable-derived-type**`|`same-interface-from-winmd^*`|
|`IDefault-interface-of-RuntimeClass*`|`same-RefClass-from-winmd^`|
|`IDefault-interface-of-RuntimeClass**`|`same-RefClass-from-winmd^*`|

## <a name="see-also"></a>Voir aussi

- [Système de type](../cppcx/type-system-c-cx.md)
- [Référence du langage Visual C++](../cppcx/visual-c-language-reference-c-cx.md)
- [Référence aux espaces de noms](../cppcx/namespaces-reference-c-cx.md)
