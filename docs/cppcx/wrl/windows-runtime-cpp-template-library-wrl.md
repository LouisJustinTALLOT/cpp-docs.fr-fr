---
description: 'En savoir plus sur : Windows Runtime C++ Template Library (WRL)'
title: Bibliothèque de modèles Windows Runtime C++ (WRL)
ms.date: 11/04/2016
ms.topic: overview
ms.assetid: b915afce-553b-44a7-b8dc-0ab601758eb0
ms.openlocfilehash: cc94f907964efdf4bf93e8d92922f69373740d85
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97333917"
---
# <a name="windows-runtime-c-template-library-wrl"></a>Bibliothèque de modèles Windows Runtime C++ (WRL)

La bibliothèque de modèles C++ Windows Runtime (WRL) est une bibliothèque de modèles qui fournit un moyen de bas niveau de créer et d’utiliser des composants Windows Runtime.

> [!NOTE]
> WRL est désormais remplacé par C++/WinRT, une projection de langage C++ 17 standard pour les API Windows Runtime. C++/WinRT est disponible dans le kit de développement logiciel (SDK) Windows 10 à partir de la version 1803. C++/WinRT est entièrement implémenté dans les fichiers d’en-tête et conçu pour vous fournir un accès de première classe à l’API Windows moderne.
>
> Avec C++/WinRT, vous pouvez utiliser et créer Windows Runtime API à l’aide de n’importe quel compilateur C++ 17 conforme aux normes. C++/WinRT fonctionne généralement mieux et produit des binaires plus petits que n’importe quelle autre option de langage pour le Windows Runtime. Nous continuerons de prendre en charge les langages C++/CX et WRL, mais recommandons vivement l’utilisation du langage C++/WinRT avec des nouvelles applications. Pour plus d’informations, consultez [C++/WinRT](/windows/uwp/cpp-and-winrt-apis/index).

## <a name="benefits"></a>Avantages

La bibliothèque de modèles C++ Windows Runtime vous permet d’implémenter et d’utiliser plus facilement des composants COM (Component Object Model). Il fournit des techniques de maintenance telles que le comptage des références pour gérer la durée de vie des objets et tester des valeurs HRESULT pour déterminer si une opération a réussi ou échoué. Pour utiliser avec succès la bibliothèque de modèles Windows Runtime C++, vous devez suivre avec soin ces règles et techniques.

Le/CX C++ est un moyen de haut niveau basé sur le langage d’utiliser Windows Runtime composants. La bibliothèque de modèles C++ Windows Runtime et C++/CX simplifient l’écriture de code pour le Windows Runtime en effectuant automatiquement des tâches de maintenance à votre place.

La bibliothèque de modèles C++ Windows Runtime et C++/CX offrent des avantages différents. Voici quelques raisons pour lesquelles vous voudrez peut-être utiliser la bibliothèque de modèles C++ Windows Runtime au lieu de C++/CX :

- Windows Runtime bibliothèque de modèles C++ ajoute peu d’abstraction sur l’interface ABI (application binary interface) Windows Runtime, ce qui vous donne la possibilité de contrôler le code sous-jacent pour mieux créer ou consommer des API Windows Runtime.

- C++/CX représente les valeurs COM HRESULT comme des exceptions. Si vous avez hérité d’une base de code qui utilise COM ou qui n’utilise pas d’exceptions, vous pouvez constater que la bibliothèque de modèles C++ Windows Runtime est un moyen plus naturel de travailler avec le Windows Runtime, car vous n’êtes pas obligé d’utiliser des exceptions.

   > [!NOTE]
   > La bibliothèque de modèles C++ Windows Runtime utilise des valeurs HRESULT et ne lève pas d’exceptions. En outre, la bibliothèque de modèles C++ Windows Runtime utilise des pointeurs intelligents et le modèle RAII pour garantir que les objets sont détruits correctement lorsque votre code d’application lève une exception. Pour plus d’informations sur les pointeurs intelligents et RAII, consultez la page [pointeurs intelligents](../../cpp/smart-pointers-modern-cpp.md) et [ressources propres (RAII)](../../cpp/object-lifetime-and-resource-management-modern-cpp.md).

- L’objectif et la conception de la bibliothèque de modèles Windows Runtime C++ sont inspirés par le Active Template Library (ATL), qui est un ensemble de classes C++ basées sur des modèles qui simplifient la programmation des objets COM. Étant donné que Windows Runtime C++ Template Library utilise le C++ standard pour encapsuler les Windows Runtime, vous pouvez plus facilement porter et interagir avec de nombreux composants COM existants écrits en ATL dans le Windows Runtime. Si vous connaissez déjà ATL, vous constaterez peut-être que Windows Runtime la programmation de la bibliothèque de modèles C++ est plus facile.

## <a name="getting-started"></a>Mise en route

Voici quelques ressources qui peuvent vous aider à travailler immédiatement avec la bibliothèque de modèles C++ Windows Runtime.

[Windows Runtime Library (WRL)](https://channel9.msdn.com/Events/Windows-Camp/Developing-Windows-8-Metro-style-apps-in-Cpp/The-Windows-Runtime-Library-WRL-)<br/>
Dans cette vidéo Channel 9, Découvrez comment la bibliothèque de modèles C++ Windows Runtime vous aide à écrire des applications plateforme Windows universelle (UWP) et comment créer et utiliser des composants Windows Runtime.

[Comment : activer et utiliser un composant Windows Runtime Component](how-to-activate-and-use-a-windows-runtime-component-using-wrl.md)<br/>
Montre comment utiliser la bibliothèque de modèles Windows Runtime C++ pour initialiser le Windows Runtime et activer et utiliser un composant Windows Runtime.

[Comment : terminer une opération asynchrone](how-to-complete-asynchronous-operations-using-wrl.md)<br/>
Montre comment utiliser la bibliothèque de modèles Windows Runtime C++ pour démarrer des opérations asynchrones et effectuer un travail lorsque les opérations se terminent.

[Comment : gérer les événements](how-to-handle-events-using-wrl.md)<br/>
Montre comment utiliser la bibliothèque de modèles Windows Runtime C++ pour s’abonner aux événements d’un objet Windows Runtime et les gérer.

[Procédure pas à pas : Création d’une application UWP à l’aide de WRL et Media Foundation](walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation.md)<br/>
Découvrez comment créer une application UWP qui utilise [Microsoft Media Foundation](/windows/win32/medfound/microsoft-media-foundation-sdk).

[Comment : créer un composant COM classique](how-to-create-a-classic-com-component-using-wrl.md)<br/>
Montre comment utiliser la bibliothèque de modèles Windows Runtime C++ pour créer un composant COM de base et une méthode de base pour inscrire et consommer le composant COM à partir d’une application de bureau.

[Comment : instancier directement des composants WRL](how-to-instantiate-wrl-components-directly.md)<br/>
Découvrez comment utiliser les fonctions [Microsoft::WRL::Make](make-function.md) et [Microsoft::WRL::Details::MakeAndInitialize](makeandinitialize-function.md) pour instancier un composant à partir du module qui le définit.

[Procédure : Utiliser winmdidl.exe et midlrt.exe pour créer les fichiers .h à partir des métadonnées Windows](use-winmdidl-and-midlrt-to-create-h-files-from-windows-metadata.md)<br/>
Montre comment consommer des composants Windows Runtime personnalisées à partir de WRL en créant un fichier IDL à partir des métadonnées .winmd.

[Procédure pas à pas : connexion à l’aide de tâches et de requêtes HTTP XML](../../parallel/concrt/walkthrough-connecting-using-tasks-and-xml-http-requests.md)<br/>
Montre comment utiliser les interfaces [IXMLHTTPRequest2](/windows/win32/api/msxml6/nn-msxml6-ixmlhttprequest2) et [IXMLHTTPRequest2Callback](/windows/win32/api/msxml6/nn-msxml6-ixmlhttprequest2callback) avec des tâches pour envoyer des requêtes http et de publication à un service Web dans une application UWP.

[Exemple d’optimiseur de voyage Bing Maps](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples)<br/>
Utilise la `HttpRequest` classe définie dans [procédure pas à pas : connexion à l’aide de tâches et de requêtes http XML](../../parallel/concrt/walkthrough-connecting-using-tasks-and-xml-http-requests.md) dans le contexte d’une application UWP complète.

[Exemple de création d’un composant DLL Windows Runtime avec C++](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples)<br/>
Montre comment utiliser la bibliothèque de modèles Windows Runtime C++ pour créer un composant DLL in-process et le consommer à partir de C++/CX, JavaScript et C#.

[Exemple de jeu Marble Maze DirectX](/samples/microsoft/windows-appsample-marble-maze/directx-marble-maze-game-sample/)<br/>
Montre comment utiliser la bibliothèque de modèles Windows Runtime C++ pour gérer la durée de vie des composants COM tels que DirectX et Media Foundation dans le contexte d’un jeu 3D complet.

[Notifications toast à partir d’applications de bureau](/windows/uwp/design/shell/tiles-and-notifications/toast-desktop-apps)<br/>
Montre comment envoyer des notifications toast à partir d’une application de bureau.

## <a name="windows-runtime-c-template-library-compared-to-atl"></a>Bibliothèque de modèles C++ Windows Runtime comparaison avec ATL

Windows Runtime bibliothèque de modèles C++ ressemble à la Active Template Library (ATL), car vous pouvez l’utiliser pour créer des objets COM petits et rapides. Windows Runtime bibliothèque de modèles C++ et ATL partagent également des concepts tels que la définition d’objets dans des modules, l’inscription explicite d’interfaces et la création d’objets à l’aide de fabriques. Vous pouvez vous familiariser avec Windows Runtime bibliothèque de modèles C++ si vous êtes familiarisé avec ATL.

La bibliothèque de modèles C++ Windows Runtime prend en charge la fonctionnalité COM requise pour les applications UWP. Par conséquent, elle diffère de la bibliothèque ATL car elle omet la prise en charge directe des fonctionnalités COM telles que :

- aggregation

- implémentations stock ;

- interfaces doubles (`IDispatch`) ;

- interfaces d'énumérateur standard ;

- points de connexion ;

- interfaces détachables ;

- incorporation OLE ;

- contrôles ActiveX ;

- COM+.

## <a name="concepts"></a>Concepts

Windows Runtime bibliothèque de modèles C++ fournit des types qui représentent quelques concepts de base. Les sections suivantes décrivent ces types.

### <a name="comptr"></a>ComPtr

[ComPtr](comptr-class.md) est un type de *pointeur intelligent* qui représente l'interface spécifiée par le paramètre de modèle. Utilisez `ComPtr` pour déclarer une variable pouvant accéder aux membres d'un objet dérivé de l'interface. `ComPtr` met à jour automatiquement un décompte de références pour le pointeur d'interface sous-jacent et libère l'interface lorsque le décompte de références atteint zéro.

### <a name="runtimeclass"></a>RuntimeClass

[RuntimeClass](runtimeclass-class.md) représente une classe instanciée qui hérite d'un ensemble d'interfaces spécifiées. Un `RuntimeClass` objet peut fournir une combinaison de prise en charge pour une ou plusieurs interfaces COM Windows Runtime, ou une référence faible à un composant.

### <a name="module"></a>Module

[Module](module-class.md) représente une collection d'objets connexes. Un objet `Module` gère les fabriques de classe, qui créent des objets, et l'inscription, qui permet à d'autres applications d'utiliser un objet.

### <a name="callback"></a>Rappel

La fonction [Callback](callback-function-wrl.md) crée un objet dont la fonction membre est un gestionnaire d'événements (une méthode de rappel). Utilisez la fonction `Callback` pour écrire des opérations asynchrones.

### <a name="eventsource"></a>EventSource

[EventSource](eventsource-class.md) sert à gérer des gestionnaires d'événements *délégués* . Utilisez Windows Runtime bibliothèque de modèles C++ pour implémenter un délégué et utilisez `EventSource` pour ajouter, supprimer et appeler des délégués.

### <a name="asyncbase"></a>AsyncBase

[AsyncBase](asyncbase-class.md) fournit des méthodes virtuelles qui représentent le modèle de programmation asynchrone Windows Runtime. Redéfinissez les membres de cette classe pour créer une classe personnalisée capable de démarrer, arrêter ou contrôler la progression d'une opération asynchrone.

### <a name="ftmbase"></a>FtmBase

[FtmBase](ftmbase-class.md) représente un objet marshaler libre de threads. `FtmBase` crée un tableau global d'interface (GIT) et vous permet de gérer le marshaling et les objets proxy.

### <a name="weakref"></a>WeakRef

[WeakRef](weakref-class.md) est un type de pointeur intelligent qui représente une *référence faible*, qui fait référence à un objet qui peut être accessible ou non. Un `WeakRef` objet peut être utilisé uniquement par le Windows Runtime, et non par le com classique.

Un objet `WeakRef` représente généralement un objet dont l'existence est contrôlée par un thread ou une application externe. Par exemple, un objet `WeakRef` peut faire référence à un objet fichier. Lorsque le fichier est ouvert, `WeakRef` est valide et le fichier référencé est accessible. En revanche, quand le fichier est fermé, `WeakRef` est incorrect et le fichier n'est pas accessible.

## <a name="related-topics"></a>Rubriques connexes

[API clés par catégorie](key-wrl-apis-by-category.md)\
Met en surbrillance les types, les fonctions et les macros principales de la bibliothèque de modèles C++ Windows Runtime.

[Faire](wrl-reference.md)\
Contient des informations de référence pour la bibliothèque de modèles C++ Windows Runtime.

[Aide-mémoire (C++/CX)](../../cppcx/quick-reference-c-cx.md)\
Décrit brièvement les fonctionnalités C++/CX qui prennent en charge l’Windows Runtime.

[Utilisation des composants de Windows Runtime dans Visual C++](/windows/uwp/winrt-components/walkthrough-creating-a-basic-windows-runtime-component-in-cpp-and-calling-it-from-javascript-or-csharp)\
Montre comment utiliser C++/CX pour créer un composant de base Windows Runtime.
