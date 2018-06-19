---
title: 'Comment : activer et utiliser un composant Windows Runtime à l’aide de WRL | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
ms.assetid: 54828f02-6af3-45d1-b965-d0104442f8d5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 50c37438bf3a840f57119245b845d0b94f1873db
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33880768"
---
# <a name="how-to-activate-and-use-a-windows-runtime-component-using-wrl"></a>Comment : activer et utiliser un composant Windows Runtime Component à l'aide de WRL
Ce document montre comment utiliser la bibliothèque de modèles C++ (WRL) de Windows Runtime pour initialiser le Runtime Windows et comment activer et utiliser un composant Windows Runtime.  
  
 Pour utiliser un composant, vous devez obtenir un pointeur d’interface vers le type qui est implémenté par le composant. Et, étant donné que la technologie sous-jacente de l’exécution de Windows est le modèle COM (Component Object), vous devez suivre les règles de COM pour conserver une instance du type. Par exemple, vous devez mettre à jour le *le décompte de références* qui détermine quand le type est supprimé de la mémoire.  
  
 Pour simplifier l’utilisation de Windows Runtime, bibliothèque de modèles Windows Runtime C++ fournit le modèle de pointeur intelligent, [ComPtr\<T >](../windows/comptr-class.md), qui effectue automatiquement un comptage de références. Quand vous déclarez une variable, spécifiez `ComPtr<` *-nom de l’interface* `>` *identificateur*. Pour accéder à un membre d’interface, appliquer l’opérateur d’accès aux membres flèche (`->`) à l’identificateur.  
  
> [!IMPORTANT]
>  Lorsque vous appelez une fonction d’interface, testez toujours les `HRESULT` valeur de retour.  
  
## <a name="activating-and-using-a-windows-runtime-component"></a>Activation et l’utilisation d’un composant Windows Runtime  
 Les étapes suivantes utilisent le `Windows::Foundation::IUriRuntimeClass` interface pour montrer comment créer une fabrique d’activation pour un composant Windows Runtime, créez une instance de ce composant et récupérer une valeur de propriété. Ils montrent également comment initialiser le Windows Runtime. L’exemple complet suit.  
  
> [!IMPORTANT]
>  Bien que vous utilisez généralement la bibliothèque de modèles Windows Runtime C++ dans une application de plateforme Windows universelle (UWP), cet exemple utilise une application console à titre d’illustration. Les fonctions telles que `wprintf_s` ne sont pas disponibles à partir d’une application UWP. Pour plus d’informations sur les types et les fonctions que vous pouvez utiliser dans une application UWP, consultez [fonctions CRT non prises en charge dans les applications de plateforme Windows universelle](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) et [Win32 et COM pour applications UWP](/uwp/win32-and-com/win32-and-com-for-uwp-apps).  
  
#### <a name="to-activate-and-use-a-windows-runtime-component"></a>Pour activer et utiliser un composant Windows Runtime  
  
1.  Inclure (`#include`) les requis Windows Runtime, bibliothèque de modèles Windows Runtime C++ ou les en-têtes de la bibliothèque C++ Standard.  
  
     [!code-cpp[wrl-consume-component#2](../windows/codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_1.cpp)]  
  
     Nous vous recommandons d'utiliser la directive `using namespace` dans votre fichier .cpp pour rendre le code plus lisible.  
  
2.  Initialiser le thread dans lequel l’application s’exécute. Chaque application doit initialiser son thread et le modèle de thread. Cet exemple utilise le [Microsoft::WRL::Wrappers::RoInitializeWrapper](../windows/roinitializewrapper-class.md) classe pour initialiser le Windows Runtime et spécifie [RO_INIT_MULTITHREADED](http://msdn.microsoft.com/library/windows/apps/br224661.aspx) comme modèle de thread. Le `RoInitializeWrapper` classe appelle `Windows::Foundation::Initialize` lors de la construction, et `Windows::Foundation::Uninitialize` quand il est détruit.  
  
     [!code-cpp[wrl-consume-component#3](../windows/codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_2.cpp)]  
  
     Dans la deuxième instruction, le [RoInitializeWrapper::HRESULT](../windows/roinitializewrapper-hresult-parens-operator.md) opérateur retourne le `HRESULT` à partir de l’appel à `Windows::Foundation::Initialize`.  
  
3.  Créer un *fabrique d’activation* pour la `ABI::Windows::Foundation::IUriRuntimeClassFactory` interface.  
  
     [!code-cpp[wrl-consume-component#4](../windows/codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_3.cpp)]  
  
     Le Windows Runtime utilise des noms complets pour identifier les types. Le `RuntimeClass_Windows_Foundation_Uri` paramètre est une chaîne qui est fournie par le Windows Runtime et qui contient le nom de classe runtime requis.  
  
4.  Initialiser un [Microsoft::WRL::Wrappers::HString](../windows/hstring-class.md) variable qui représente l’URI `"http://www.microsoft.com"`.  
  
     [!code-cpp[wrl-consume-component#6](../windows/codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_4.cpp)]  
  
     Dans le Windows Runtime, vous ne pas allouer de la mémoire d’une chaîne qui utilise le Windows Runtime. Au lieu de cela, le Windows Runtime crée une copie de la chaîne dans une mémoire tampon qu’il gère et utilise pour les opérations et puis retourne un handle vers la mémoire tampon qu’il est créé.  
  
5.  Utilisez le `IUriRuntimeClassFactory::CreateUri` méthode de fabrique pour créer un `ABI::Windows::Foundation::IUriRuntimeClass` objet.  
  
     [!code-cpp[wrl-consume-component#7](../windows/codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_5.cpp)]  
  
6.  Appelez le `IUriRuntimeClass::get_Domain` pour récupérer la valeur de la `Domain` propriété.  
  
     [!code-cpp[wrl-consume-component#8](../windows/codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_6.cpp)]  
  
7.  Imprimer le nom de domaine dans la console et de retour. Tous les objets `ComPtr` et RAII quittent la portée et sont libérés automatiquement.  
  
     [!code-cpp[wrl-consume-component#9](../windows/codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_7.cpp)]  
  
     Le [WindowsGetStringRawBuffer](http://msdn.microsoft.com/library/windows/apps/br224636.aspx) fonction récupère le formulaire Unicode sous-jacente de la chaîne d’URI.  
  
 Voici un exemple complet :  
  
 [!code-cpp[wrl-consume-component#1](../windows/codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_8.cpp)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Pour compiler le code, copiez-le et collez-le dans un projet Visual Studio ou collez-le dans un fichier nommé `wrl-consume-component.cpp` , puis exécutez la commande suivante dans une fenêtre d’invite de commandes Visual Studio.  
  
 **CL.exe wrl consommer component.cpp runtimeobject.lib**  
  
## <a name="see-also"></a>Voir aussi  
 [Bibliothèque de modèles Windows Runtime C++ (WRL)](../windows/windows-runtime-cpp-template-library-wrl.md)