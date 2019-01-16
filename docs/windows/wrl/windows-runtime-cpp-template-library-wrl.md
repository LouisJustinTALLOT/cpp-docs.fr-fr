---
title: Bibliothèque de modèles Windows Runtime C++ (WRL)
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: b915afce-553b-44a7-b8dc-0ab601758eb0
ms.openlocfilehash: 5c1a4e7df424499f400dbd70d675956deef6bc5d
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54336023"
---
# <a name="windows-runtime-c-template-library-wrl"></a>Bibliothèque de modèles Windows Runtime C++ (WRL)

La bibliothèque de modèles C++ Windows Runtime (WRL) est une bibliothèque de modèles qui fournit un moyen de bas niveau de créer et d’utiliser des composants Windows Runtime.

> [!NOTE]
> WRL est désormais remplacée par C / c++ / WinRT, une standard C ++ 17 projection de langage pour Windows Runtime APIs. C++ / c++ / WinRT est disponible dans le SDK Windows 10 à partir de la version 1803 qui interviennent. C++ / c++ / WinRT est entièrement implémentée dans les fichiers d’en-tête et conçu pour vous permettre d’accès idéal à l’API Windows moderne.
>
> Avec C / c++ / WinRT, vous pouvez consommer et créer le Windows Runtime APIs à l’aide de n’importe quel conformes aux normes C ++ 17 du compilateur. C++ / c++ / WinRT généralement plus performant et produit des binaires plus petits que toute autre option de langage pour le Windows Runtime. Nous continuerons à prendre en charge de C++ / c++ / CX et WRL, mais vous recommandons vivement que les nouvelles applications utiliser C++ / c++ / WinRT. Pour plus d’informations, consultez [C++ / c++ / WinRT](https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/index).

## <a name="benefits"></a>Avantages

La bibliothèque de modèles Windows Runtime C++ vous permet plus facilement implémenter et consommer des composants de composant COM (Object Model). Il fournit des techniques de gestion interne comme comptage de références pour gérer la durée de vie des objets et de tester des valeurs HRESULT pour déterminer si une opération a réussi ou échoué. Pour pouvoir utiliser la bibliothèque de modèles Windows Runtime C++, vous devez respecter soigneusement ces règles et techniques.

C++ / c++ / CX est un moyen de haut niveau, en fonction de langage à utiliser des composants Windows Runtime. À la fois la bibliothèque de modèles Windows Runtime C++ et C++ / c++ / CX simplifient l’écriture de code pour le Windows Runtime en exécutant automatiquement les tâches de gestion interne à votre place.

La bibliothèque de modèles Windows Runtime C++ et C / c++ / CX offrent des avantages différents. Voici quelques raisons pour lesquelles vous souhaiterez peut-être utiliser la bibliothèque de modèles Windows Runtime C++ au lieu de C++ / c++ / CX :

- Bibliothèque de modèles Windows Runtime C++ ajoute peu d’abstraction sur le Windows Runtime binaire Interface Application (ABI), ce qui vous donne la possibilité de contrôler le code sous-jacent pour mieux créer ou consommer Windows APIs Runtime.

- C++ / c++ / CX représente les valeurs HRESULT de COM en tant qu’exceptions. Si vous avez hérité d’une base de code qui utilise COM, ou qui n’utilise pas les exceptions, vous constaterez peut-être que la bibliothèque de modèles C++ Windows Runtime est une façon plus naturelle pour travailler avec le Runtime de Windows, car vous n’êtes pas obligé d’utiliser des exceptions.

   > [!NOTE]
   > La bibliothèque de modèles Windows Runtime C++ utilise les valeurs HRESULT et ne lève pas d’exceptions. En outre, la bibliothèque de modèles Windows Runtime C++ utilise des pointeurs intelligents et le modèle RAII pour contribuer à garantir que les objets sont détruits correctement lorsque votre code d’application lève une exception. Pour plus d’informations sur les pointeurs intelligents et le modèle RAII, consultez [pointeurs intelligents](../../cpp/smart-pointers-modern-cpp.md) et [ressources propre des objets (RAII)](../../cpp/objects-own-resources-raii.md).

- L’objectif et la conception de la bibliothèque de modèles C++ Windows Runtime est inspirée par la bibliothèque ATL (Active Template), qui est un ensemble de classes C++ basées sur modèle qui simplifie la programmation d’objets COM. Étant donné que la bibliothèque de modèles Windows Runtime C++ utilise C++ standard pour encapsuler le Runtime de Windows, vous pouvez plus facilement le port et interagir avec de nombreux composants COM existants écrits en ATL à l’exécution de Windows. Si vous connaissez déjà ATL, vous constaterez peut-être que la programmation de la bibliothèque de modèles C++ Windows Runtime est plus facile.

## <a name="getting-started"></a>Prise en main

Voici quelques ressources qui peuvent vous aider à commencer à travailler avec la bibliothèque de modèles Windows Runtime C++ tout de suite.

[Le Windows Runtime Library (WRL)](https://channel9.msdn.com/Events/Windows-Camp/Developing-Windows-8-Metro-style-apps-in-Cpp/The-Windows-Runtime-Library-WRL-)<br/>
Dans cette vidéo de Channel 9, en savoir plus sur comment la bibliothèque de modèles Windows Runtime C++ vous aide à que écrire des applications Universal Windows Platform (UWP) et comment créer et consommer des composants Windows Runtime.

[Guide pratique pour Activer et utiliser un composant d’exécution de Windows](how-to-activate-and-use-a-windows-runtime-component-using-wrl.md)<br/>
Montre comment utiliser la bibliothèque de modèles Windows Runtime C++ pour initialiser le Runtime Windows et activer et utiliser un composant Windows Runtime.

[Guide pratique pour Terminer une opération asynchrone](how-to-complete-asynchronous-operations-using-wrl.md)<br/>
Montre comment utiliser la bibliothèque de modèles Windows Runtime C++ pour démarrer des opérations asynchrones et effectuer des actions lorsque les opérations se terminent.

[Guide pratique pour Gérer les événements](how-to-handle-events-using-wrl.md)<br/>
Montre comment utiliser la bibliothèque de modèles Windows Runtime C++ pour vous abonner à et gérer les événements d’un objet Windows Runtime.

[Procédure pas à pas : Création d’une application UWP à l’aide de WRL et Media Foundation](walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation.md)<br/>
Découvrez comment créer une application UWP qui utilise [Microsoft Media Foundation](/windows/desktop/medfound/microsoft-media-foundation-sdk).

[Guide pratique pour Créer un composant COM classique](how-to-create-a-classic-com-component-using-wrl.md)<br/>
Montre comment utiliser la bibliothèque de modèles Windows Runtime C++ pour créer un composant COM de base et une méthode simple pour vous inscrire et utiliser le composant COM à partir d’une application de bureau.

[Guide pratique pour Instancier directement les composants WRL](how-to-instantiate-wrl-components-directly.md)<br/>
Découvrez comment utiliser les fonctions [Microsoft::WRL::Make](make-function.md) et [Microsoft::WRL::Details::MakeAndInitialize](makeandinitialize-function.md) pour instancier un composant à partir du module qui le définit.

[Guide pratique pour Utiliser winmdidl.exe et midlrt.exe pour créer des fichiers .h à partir de métadonnées windows](use-winmdidl-and-midlrt-to-create-h-files-from-windows-metadata.md)<br/>
Montre comment consommer des composants Windows Runtime personnalisées à partir de WRL en créant un fichier IDL à partir des métadonnées .winmd.

[Procédure pas à pas : connexion à l’aide de tâches et de requêtes HTTP XML](../../parallel/concrt/walkthrough-connecting-using-tasks-and-xml-http-requests.md)<br/>
Montre comment utiliser le [IXMLHTTPRequest2](/windows/desktop/api/msxml6/nn-msxml6-ixmlhttprequest2) et [IXMLHTTPRequest2Callback](/windows/desktop/api/msxml6/nn-msxml6-ixmlhttprequest2callback) interfaces avec des tâches pour envoyer des demandes HTTP GET et POST à un service web dans une application UWP.

[Exemple optimiseur de voyage Bing Maps](https://code.msdn.microsoft.com/Bing-Maps-trip-optimizer-c4e037f7)<br/>
Utilise le `HttpRequest` classe qui est définie dans [procédure pas à pas : Connexion à l’aide des tâches et des requêtes HTTP XML](../../parallel/concrt/walkthrough-connecting-using-tasks-and-xml-http-requests.md) dans le contexte d’une application UWP complète.

[Création d’un composant Windows DLL d’exécution avec l’exemple C++](https://code.msdn.microsoft.com/windowsapps/Creating-a-Windows-Runtime-6c399797)<br/>
Montre comment utiliser la bibliothèque de modèles Windows Runtime C++ pour créer un composant DLL in-process et le consommer à partir de C++ / c++ / CX, JavaScript et c#.

[Exemple de jeu marble maze DirectX](https://code.msdn.microsoft.com/windowsapps/DirectX-Marble-Maze-Game-e4806345)<br/>
Montre comment utiliser la bibliothèque de modèles C++ Windows Runtime pour gérer la durée de vie des composants COM tels que DirectX et Media Foundation dans le contexte d’un jeu 3D complet.

[Envoi de notifications toast à partir d’exemples d’applications de bureau](https://code.msdn.microsoft.com/windowsdesktop/Sending-toast-notifications-71e230a2)<br/>
Montre comment utiliser la bibliothèque de modèles Windows Runtime C++ pour travailler avec des notifications de toast à partir d’une application de bureau.

## <a name="windows-runtime-c-template-library-compared-to-atl"></a>Windows Runtime bibliothèque de modèles C++ comparé à ATL

Bibliothèque de modèles Windows Runtime C++ ressemble à la bibliothèque ATL (Active Template), car vous pouvez l’utiliser pour créer des objets COM rapides de petites. Bibliothèque de modèles Windows Runtime C++ et ATL partagent également des concepts tels que la définition d’objets dans des modules, l’inscription explicite d’interfaces et la création d’objets à l’aide de fabriques. Vous pouvez être à l’aise avec la bibliothèque de modèles Windows Runtime C++ si vous êtes familiarisé avec ATL.

Bibliothèque de modèles Windows Runtime C++ prend en charge la fonctionnalité COM requise pour les applications UWP. Par conséquent, elle diffère de la bibliothèque ATL car elle omet la prise en charge directe des fonctionnalités COM telles que :

- agrégation ;

- implémentations stock ;

- interfaces doubles (`IDispatch`) ;

- interfaces d'énumérateur standard ;

- points de connexion ;

- interfaces détachables ;

- incorporation OLE ;

- contrôles ActiveX ;

- COM+.

## <a name="concepts"></a>Concepts

Bibliothèque de modèles Windows Runtime C++ fournit des types représentant quelques concepts de base. Les sections suivantes décrivent ces types.

### <a name="comptr"></a>ComPtr

[ComPtr](comptr-class.md) est un type de *pointeur intelligent* qui représente l'interface spécifiée par le paramètre de modèle. Utilisez `ComPtr` pour déclarer une variable pouvant accéder aux membres d'un objet dérivé de l'interface. `ComPtr` met à jour automatiquement un décompte de références pour le pointeur d'interface sous-jacent et libère l'interface lorsque le décompte de références atteint zéro.

### <a name="runtimeclass"></a>RuntimeClass

[RuntimeClass](runtimeclass-class.md) représente une classe instanciée qui hérite d'un ensemble d'interfaces spécifiées. Un `RuntimeClass` objet peut fournir une combinaison de prise en charge pour une ou plusieurs interfaces Windows Runtime COM, ou une référence faible à un composant.

### <a name="module"></a>Module

[Module](module-class.md) représente une collection d'objets connexes. Un objet `Module` gère les fabriques de classe, qui créent des objets, et l'inscription, qui permet à d'autres applications d'utiliser un objet.

### <a name="callback"></a>Rappel

La fonction [Callback](callback-function-wrl.md) crée un objet dont la fonction membre est un gestionnaire d'événements (une méthode de rappel). Utilisez la fonction `Callback` pour écrire des opérations asynchrones.

### <a name="eventsource"></a>EventSource

[EventSource](eventsource-class.md) sert à gérer des gestionnaires d'événements *délégués* . Utiliser la bibliothèque de modèles Windows Runtime C++ pour implémenter un délégué et utilisez `EventSource` pour ajouter, supprimer et appeler des délégués.

### <a name="asyncbase"></a>AsyncBase

[AsyncBase](asyncbase-class.md) fournit des méthodes virtuelles qui représentent le modèle de programmation asynchrone Windows Runtime. Redéfinissez les membres de cette classe pour créer une classe personnalisée capable de démarrer, arrêter ou contrôler la progression d'une opération asynchrone.

### <a name="ftmbase"></a>FtmBase

[FtmBase](ftmbase-class.md) représente un objet marshaler libre de threads. `FtmBase` crée un tableau global d'interface (GIT) et vous permet de gérer le marshaling et les objets proxy.

### <a name="weakref"></a>WeakRef

[WeakRef](weakref-class.md) est un type de pointeur intelligent qui représente une *référence faible*, qui fait référence à un objet qui peut être accessible ou non. Un `WeakRef` objet peut être utilisé uniquement par le Windows Runtime et non par le COM classique.

Un objet `WeakRef` représente généralement un objet dont l'existence est contrôlée par un thread ou une application externe. Par exemple, un objet `WeakRef` peut faire référence à un objet fichier. Lorsque le fichier est ouvert, `WeakRef` est valide et le fichier référencé est accessible. En revanche, quand le fichier est fermé, `WeakRef` est incorrect et le fichier n'est pas accessible.

## <a name="related-topics"></a>Rubriques connexes

|||
|-|-|
|[API principales par catégorie](key-wrl-apis-by-category.md)|Met en évidence la principale bibliothèque de modèles Windows Runtime C++ types, fonctions et les macros.|
|[Référence](wrl-reference.md)|Contient des informations de référence pour la bibliothèque de modèles C++ Windows Runtime.|
|[Référence rapide (Windows Runtime et Visual C++)](../../cppcx/quick-reference-c-cx.md)|Décrit brièvement le C + c++ / fonctionnalités CX qui prennent en charge l’exécution de Windows.|
|[À l’aide de composants Windows Runtime en Visual C++](/windows/uwp/winrt-components/walkthrough-creating-a-basic-windows-runtime-component-in-cpp-and-calling-it-from-javascript-or-csharp)|Montre comment utiliser C++ / c++ / CX pour créer un composant Windows Runtime de base.|
