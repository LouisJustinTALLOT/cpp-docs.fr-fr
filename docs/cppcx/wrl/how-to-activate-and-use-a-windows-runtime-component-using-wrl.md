---
title: 'Procédure : Activer et utiliser un composant d’exécution de Windows à l’aide de WRL'
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 54828f02-6af3-45d1-b965-d0104442f8d5
ms.openlocfilehash: 8c0bed825f76fdf0f2c5cc1fa095e54f08bb8a67
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59037210"
---
# <a name="how-to-activate-and-use-a-windows-runtime-component-using-wrl"></a>Procédure : Activer et utiliser un composant d’exécution de Windows à l’aide de WRL

Ce document montre comment utiliser la bibliothèque de modèles C++ (WRL) de Windows Runtime pour initialiser le Runtime Windows et comment activer et utiliser un composant Windows Runtime.

Pour utiliser un composant, vous devez obtenir un pointeur d’interface vers le type qui est implémenté par le composant. Et étant donné que la technologie sous-jacente du Runtime Windows est le composant COM (Object Model), vous devez suivre les règles de COM pour maintenir une instance du type. Par exemple, vous devez maintenir la *le décompte de références* qui détermine quand le type est supprimé de la mémoire.

Pour simplifier l’utilisation du Runtime Windows, bibliothèque de modèles Windows Runtime C++ fournit le modèle de pointeur intelligent, [ComPtr\<T >](comptr-class.md), qui effectue automatiquement de comptage de références. Quand vous déclarez une variable, spécifiez `ComPtr<` *nom de l’interface* `>` *identificateur*. Pour accéder à un membre d’interface, appliquer l’opérateur member-access flèche (`->`) à l’identificateur.

> [!IMPORTANT]
> Lorsque vous appelez une fonction d’interface, testez toujours la valeur de retour HRESULT.

## <a name="activating-and-using-a-windows-runtime-component"></a>Activation et l’utilisation d’un composant d’exécution de Windows

Les étapes suivantes utilisent le `Windows::Foundation::IUriRuntimeClass` interface pour montrer comment créer une fabrique d’activation pour un composant Windows Runtime, créez une instance de ce composant et récupérer une valeur de propriété. Ils indiquent également comment initialiser le Runtime de Windows. L’exemple complet suit.

> [!IMPORTANT]
> Bien que vous utilisez généralement la bibliothèque de modèles Windows Runtime C++ dans une application de plateforme universelle Windows (UWP), cet exemple utilise une application console à titre d’illustration. Les fonctions telles que `wprintf_s` ne sont pas disponibles à partir d’une application UWP. Pour plus d’informations sur les types et les fonctions que vous pouvez utiliser dans une application UWP, consultez [fonctions CRT non prises en charge dans les applications de plateforme Windows universelle](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) et [Win32 et COM pour les applications UWP](/uwp/win32-and-com/win32-and-com-for-uwp-apps).

#### <a name="to-activate-and-use-a-windows-runtime-component"></a>Pour activer et utiliser un composant Windows Runtime

1. Inclure (`#include`) toute requise Windows Runtime, bibliothèque de modèles C++ Windows Runtime ou les en-têtes de bibliothèque C++ Standard.

   [!code-cpp[wrl-consume-component#2](../codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_1.cpp)]

   Nous vous recommandons d'utiliser la directive `using namespace` dans votre fichier .cpp pour rendre le code plus lisible.

2. Initialiser le thread dans lequel l’application s’exécute. Chaque application doit s’initialiser son thread et le modèle de thread. Cet exemple utilise le [Microsoft::WRL::Wrappers::RoInitializeWrapper](roinitializewrapper-class.md) classe pour initialiser le Runtime Windows et spécifie [RO_INIT_MULTITHREADED](/windows/desktop/api/roapi/ne-roapi-ro_init_type) en tant que le modèle de thread. Le `RoInitializeWrapper` classe appels `Windows::Foundation::Initialize` lors de la construction, et `Windows::Foundation::Uninitialize` quand il est détruit.

   [!code-cpp[wrl-consume-component#3](../codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_2.cpp)]

   Dans la deuxième instruction, le [RoInitializeWrapper::HRESULT](roinitializewrapper-class.md#hresult) opérateur retourne le `HRESULT` à partir de l’appel à `Windows::Foundation::Initialize`.

3. Créer un *fabrique d’activation* pour le `ABI::Windows::Foundation::IUriRuntimeClassFactory` interface.

   [!code-cpp[wrl-consume-component#4](../codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_3.cpp)]

   Le Runtime Windows utilise des noms qualifiés complets pour identifier les types. Le `RuntimeClass_Windows_Foundation_Uri` paramètre est une chaîne qui est fournie par le Runtime Windows et contient le nom de classe runtime requis.

4. Initialiser un [Microsoft::WRL::Wrappers::HString](hstring-class.md) variable qui représente l’URI `"http://www.microsoft.com"`.

   [!code-cpp[wrl-consume-component#6](../codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_4.cpp)]

   Dans le Windows Runtime, vous ne pas allouer de mémoire pour une chaîne qui utilise le Runtime de Windows. Au lieu de cela, le Runtime de Windows crée une copie de votre chaîne dans une mémoire tampon qu’il gère et utilise pour les opérations et puis retourne un handle vers la mémoire tampon qu’il créé.

5. Utilisez le `IUriRuntimeClassFactory::CreateUri` méthode de fabrique pour créer un `ABI::Windows::Foundation::IUriRuntimeClass` objet.

   [!code-cpp[wrl-consume-component#7](../codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_5.cpp)]

6. Appelez le `IUriRuntimeClass::get_Domain` méthode pour récupérer la valeur de la `Domain` propriété.

   [!code-cpp[wrl-consume-component#8](../codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_6.cpp)]

7. Imprimer le nom de domaine dans la console et retourner. Tous les objets `ComPtr` et RAII quittent la portée et sont libérés automatiquement.

   [!code-cpp[wrl-consume-component#9](../codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_7.cpp)]

   Le [WindowsGetStringRawBuffer](/windows/desktop/api/winstring/nf-winstring-windowsgetstringrawbuffer) fonction récupère le formulaire Unicode sous-jacente de la chaîne d’URI.

Voici un exemple complet :

[!code-cpp[wrl-consume-component#1](../codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_8.cpp)]

## <a name="compiling-the-code"></a>Compilation du code

Pour compiler le code, copiez-le et collez-le dans un projet Visual Studio ou collez-le dans un fichier nommé `wrl-consume-component.cpp` , puis exécutez la commande suivante dans une fenêtre d’invite de commandes Visual Studio.

`cl.exe wrl-consume-component.cpp runtimeobject.lib`

## <a name="see-also"></a>Voir aussi

[Bibliothèque de modèles Windows Runtime C++ (WRL)](windows-runtime-cpp-template-library-wrl.md)