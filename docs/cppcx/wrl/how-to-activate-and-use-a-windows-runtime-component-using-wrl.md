---
description: 'En savoir plus sur : Comment : activer et utiliser un composant Windows Runtime à l’aide de WRL'
title: "Comment : activer et utiliser un composant Windows Runtime Component à l'aide de WRL"
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 54828f02-6af3-45d1-b965-d0104442f8d5
ms.openlocfilehash: 1f66565956b1f7c3a0232e9271131e4ae8d53101
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97249943"
---
# <a name="how-to-activate-and-use-a-windows-runtime-component-using-wrl"></a>Comment : activer et utiliser un composant Windows Runtime Component à l'aide de WRL

Ce document montre comment utiliser le Windows Runtime C++ Template Library (WRL) pour initialiser le Windows Runtime et comment activer et utiliser un composant Windows Runtime.

Pour utiliser un composant, vous devez acquérir un pointeur d’interface vers le type implémenté par le composant. Et étant donné que la technologie sous-jacente du Windows Runtime est le modèle COM (Component Object Model), vous devez suivre les règles COM pour maintenir une instance du type. Par exemple, vous devez conserver le *nombre de références* qui détermine le moment où le type est supprimé de la mémoire.

Pour simplifier l’utilisation de la Windows Runtime, Windows Runtime bibliothèque de modèles C++ fournit le modèle de pointeur intelligent, [ComPtr \<T> ](comptr-class.md), qui effectue automatiquement le décompte de références. Lorsque vous déclarez une variable, spécifiez l' `ComPtr<` *identificateur de nom d’interface* `>` . Pour accéder à un membre d’interface, appliquez l’opérateur d’accès aux membres Arrow ( `->` ) à l’identificateur.

> [!IMPORTANT]
> Quand vous appelez une fonction d’interface, testez toujours la valeur de retour HRESULT.

## <a name="activating-and-using-a-windows-runtime-component"></a>Activation et utilisation d’un composant Windows Runtime

Les étapes suivantes utilisent l' `Windows::Foundation::IUriRuntimeClass` interface pour montrer comment créer une fabrique d’activation pour un composant Windows Runtime, créer une instance de ce composant et récupérer une valeur de propriété. Ils montrent également comment initialiser le Windows Runtime. L’exemple complet suit.

> [!IMPORTANT]
> Bien que vous utilisiez généralement le Windows Runtime bibliothèque de modèles C++ dans une application plateforme Windows universelle (UWP), cet exemple utilise une application console comme illustration. Les fonctions telles que `wprintf_s` ne sont pas disponibles à partir d’une application UWP. Pour plus d’informations sur les types et les fonctions que vous pouvez utiliser dans une application UWP, consultez [fonctions CRT non prises en charge dans les applications plateforme Windows universelle](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) et [Win32 et com pour les applications UWP](/uwp/win32-and-com/win32-and-com-for-uwp-apps).

#### <a name="to-activate-and-use-a-windows-runtime-component"></a>Pour activer et utiliser un composant Windows Runtime

1. Include ( `#include` ) tout Windows Runtime requis, Windows Runtime bibliothèque de modèles c++ ou les en-têtes de la bibliothèque C++ standard.

   [!code-cpp[wrl-consume-component#2](../codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_1.cpp)]

   Nous vous recommandons d'utiliser la directive `using namespace` dans votre fichier .cpp pour rendre le code plus lisible.

2. Initialisez le thread dans lequel l’application s’exécute. Chaque application doit initialiser son thread et son modèle de thread. Cet exemple utilise la classe [Microsoft :: WRL :: wrappers :: RoInitializeWrapper](roinitializewrapper-class.md) pour initialiser le Windows Runtime et spécifie [RO_INIT_MULTITHREADED](/windows/win32/api/roapi/ne-roapi-ro_init_type) comme modèle de thread. La `RoInitializeWrapper` classe appelle `Windows::Foundation::Initialize` à la construction et `Windows::Foundation::Uninitialize` lorsqu’elle est détruite.

   [!code-cpp[wrl-consume-component#3](../codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_2.cpp)]

   Dans la deuxième instruction, l’opérateur [RoInitializeWrapper :: HRESULT](roinitializewrapper-class.md#hresult) retourne le `HRESULT` à partir de l’appel à `Windows::Foundation::Initialize` .

3. Créez une *fabrique d’activation* pour l' `ABI::Windows::Foundation::IUriRuntimeClassFactory` interface.

   [!code-cpp[wrl-consume-component#4](../codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_3.cpp)]

   Le Windows Runtime utilise des noms qualifiés complets pour identifier les types. Le `RuntimeClass_Windows_Foundation_Uri` paramètre est une chaîne fournie par le Windows Runtime et contient le nom de classe d’exécution requis.

4. Initialisez une variable [Microsoft :: WRL :: wrappers :: HString](hstring-class.md) qui représente l’URI `"https://www.microsoft.com"` .

   [!code-cpp[wrl-consume-component#6](../codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_4.cpp)]

   Dans le Windows Runtime, vous n’allouez pas de mémoire pour une chaîne que le Windows Runtime utilisera. Au lieu de cela, le Windows Runtime crée une copie de votre chaîne dans une mémoire tampon qu’il conserve et utilise pour les opérations, puis retourne un handle vers la mémoire tampon qu’il a créée.

5. Utilisez la `IUriRuntimeClassFactory::CreateUri` méthode de fabrique pour créer un `ABI::Windows::Foundation::IUriRuntimeClass` objet.

   [!code-cpp[wrl-consume-component#7](../codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_5.cpp)]

6. Appelez la `IUriRuntimeClass::get_Domain` méthode pour récupérer la valeur de la `Domain` propriété.

   [!code-cpp[wrl-consume-component#8](../codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_6.cpp)]

7. Imprimez le nom de domaine dans la console et revenez. Tous les objets `ComPtr` et RAII quittent la portée et sont libérés automatiquement.

   [!code-cpp[wrl-consume-component#9](../codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_7.cpp)]

   La fonction [WindowsGetStringRawBuffer](/windows/win32/api/winstring/nf-winstring-windowsgetstringrawbuffer) récupère le formulaire Unicode sous-jacent de la chaîne d’URI.

Voici l’exemple complet :

[!code-cpp[wrl-consume-component#1](../codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_8.cpp)]

## <a name="compiling-the-code"></a>Compilation du code

Pour compiler le code, copiez-le, puis collez-le dans un projet Visual Studio, ou collez-le dans un fichier nommé `wrl-consume-component.cpp` , puis exécutez la commande suivante dans une fenêtre d’invite de commandes Visual Studio.

`cl.exe wrl-consume-component.cpp runtimeobject.lib`

## <a name="see-also"></a>Voir aussi

[Bibliothèque de modèles Windows Runtime C++ (WRL)](windows-runtime-cpp-template-library-wrl.md)
