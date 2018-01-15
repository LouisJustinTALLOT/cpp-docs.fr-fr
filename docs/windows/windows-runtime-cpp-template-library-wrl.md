---
title: "Windows Runtime bibliothèque de modèles C++ (WRL) | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: C++
ms.assetid: b915afce-553b-44a7-b8dc-0ab601758eb0
caps.latest.revision: "32"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e742b5509fd9a7889321e5e8c576e4fa3c8401cd
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/03/2018
---
# <a name="windows-runtime-c-template-library-wrl"></a>Bibliothèque de modèles Windows Runtime C++ (WRL)
La bibliothèque de modèles C++ (WRL) de Windows Runtime est une bibliothèque de modèles qui fournit un moyen de bas niveau pour créer et utiliser des composants Windows Runtime.  
  
## <a name="benefits"></a>Avantages  
 La bibliothèque de modèles Windows Runtime C++ vous permet de mettre en œuvre et consommer des composants de modèle COM (Component Object) plus facilement. Elle fournit des techniques de gestion interne comme le décompte des références pour gérer la durée de vie des objets et tester des valeurs d' `HRESULT` afin de déterminer si une opération a réussi ou échoué. Pour pouvoir utiliser la bibliothèque de modèles Windows Runtime C++, vous devez respecter soigneusement ces règles et techniques.  
  
 C + c++ / CX est un moyen haut niveau basée sur le langage à utiliser les composants Windows Runtime. À la fois la bibliothèque de modèles Windows Runtime C++ et C + c++ / CX simplifient l’écriture de code pour le Windows Runtime en exécutant automatiquement les tâches de gestion interne à votre place.  
  
 La bibliothèque de modèles Windows Runtime C++ et C + c++ / CX offrent des avantages différents. Voici quelques raisons pour lesquelles vous souhaiterez peut-être utiliser la bibliothèque de modèles Windows Runtime C++ au lieu de C + c++ / CX :  
  
-   Bibliothèque de modèles Windows Runtime C++ ajoute peu d’abstraction sur le Windows Runtime Application Binary Interface (ABI), ce qui vous donne la possibilité de contrôler le code sous-jacent pour mieux créer ou consommer APIs Windows Runtime.  
  
-   C + c++ / CX représente COM `HRESULT` valeurs en tant qu’exceptions. Si vous avez hérité d’une base de code qui utilise COM ou un qui n’utilise pas d’exceptions, vous constaterez peut-être que la bibliothèque de modèles Windows Runtime C++ est un moyen plus naturel de travailler avec le Windows Runtime, car vous n’êtes pas obligé d’utiliser des exceptions.  
  
    > [!NOTE]
    >  La bibliothèque de modèles Windows Runtime C++ utilise `HRESULT` valeurs et de ne pas lever d’exceptions. En outre, la bibliothèque de modèles Windows Runtime C++ utilise des pointeurs intelligents et le modèle RAII afin de garantir que les objets sont détruits correctement lorsque votre code d’application lève une exception. Pour plus d’informations sur les pointeurs intelligents et le modèle RAII, consultez [pointeurs intelligents](../cpp/smart-pointers-modern-cpp.md) et [objets propres ressources (RAII)](../cpp/objects-own-resources-raii.md).  
  
-   L’objectif et la conception de la bibliothèque de modèles Windows Runtime C++ est inspirée par la bibliothèque ATL (Active Template), qui est un ensemble de classes C++ basées sur un modèle qui simplifient la programmation d’objets COM. Étant donné que la bibliothèque de modèles Windows Runtime C++ utilise du C++ standard pour encapsuler le Windows Runtime, vous pouvez plus facilement le port et interagir avec de nombreux composants COM existants écrits en ATL vers le Windows Runtime. Si vous connaissez déjà ATL, vous constaterez peut-être que la programmation de la bibliothèque de modèles Windows Runtime C++ est plus facile.  
  
## <a name="getting-started"></a>Prise en main  
 Voici quelques ressources qui peuvent vous aider à utiliser avec la bibliothèque de modèles Windows Runtime C++ immédiatement.  
  
 [La bibliothèque Windows Runtime (WRL)](http://channel9.msdn.com/Events/Windows-Camp/Developing-Windows-8-Metro-style-apps-in-Cpp/The-Windows-Runtime-Library-WRL-)  
 Dans cette vidéo de Channel 9, découvrez comment la bibliothèque de modèles Windows Runtime C++ vous aide à que écrire des applications de plateforme Windows universelle et comment créer et consommer des composants Windows Runtime.  
  
 [Comment : activer et utiliser un composant Windows Runtime](../windows/how-to-activate-and-use-a-windows-runtime-component-using-wrl.md)  
 Montre comment utiliser la bibliothèque de modèles Windows Runtime C++ pour initialiser le Windows Runtime et activer et utiliser un composant Windows Runtime.  
  
 [Comment : effectuer des opérations asynchrones](../windows/how-to-complete-asynchronous-operations-using-wrl.md)  
 Montre comment utiliser la bibliothèque de modèles Windows Runtime C++ pour démarrer des opérations asynchrones et effectuer des actions lorsque les opérations se terminent.  
  
 [Comment : gérer des événements](../windows/how-to-handle-events-using-wrl.md)  
 Montre comment utiliser la bibliothèque de modèles Windows Runtime C++ s’abonner à et gérer les événements d’un objet Windows Runtime.  
  
 [Procédure pas à pas : Création d’un composant Runtime de base de Windows](../windows/walkthrough-creating-a-basic-windows-runtime-component-using-wrl.md)  
 Montre comment utiliser la bibliothèque de modèles Windows Runtime C++ pour créer un composant Windows Runtime de base qui additionne deux nombres. Montre également comment déclencher des événements et utiliser le composant à partir d’une application de plateforme Windows universelle qui utilise JavaScript.  
  
 [Procédure pas à pas : création d’une application Windows Store à l’aide de WRL et Media Foundation](../windows/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation.md)  
 Découvrez comment créer une application de plateforme Windows universelle qui utilise [Microsoft Media Foundation](http://msdn.microsoft.com/library/windows/apps/ms694197).  
  
 [Comment : créer un composant COM classique](../windows/how-to-create-a-classic-com-component-using-wrl.md)  
 Montre comment utiliser la bibliothèque de modèles Windows Runtime C++ pour créer un composant COM de base et une méthode de base pour stocker et consommer le composant COM à partir d’une application de bureau.  
  
 [Guide pratique pour instancier directement les composants WRL](../windows/how-to-instantiate-wrl-components-directly.md)  
 Découvrez comment utiliser le [Microsoft::wrl :: Make](../windows/make-function.md) et [Microsoft::WRL::Details::MakeAndInitialize](../windows/makeandinitialize-function.md) pour instancier un composant à partir du module qui le définit.  
  
 [Guide pratique pour utiliser winmdidl.exe et midlrt.exe pour créer les fichiers .h à partir des métadonnées Windows](../windows/use-winmdidl-and-midlrt-to-create-h-files-from-windows-metadata.md)  
 Montre comment consommer des composants Windows Runtime personnalisées à partir de WRL en créant un fichier IDL à partir des métadonnées .winmd.  
  
 [Procédure pas à pas : connexion à l’aide de tâches et de requêtes HTTP XML](../parallel/concrt/walkthrough-connecting-using-tasks-and-xml-http-requests.md)  
 Montre comment utiliser le [IXMLHTTPRequest2](http://msdn.microsoft.com/en-us/bbc11c4a-aecf-4d6d-8275-3e852e309908) et [IXMLHTTPRequest2Callback](http://msdn.microsoft.com/en-us/aa4b3f4c-6e28-458b-be25-6cce8865fc71) interfaces avec des tâches pour envoyer des demandes HTTP GET et POST à un service web dans une application de plateforme Windows universelle.  
  
 [Exemple optimiseur de voyage Bing Maps](http://code.msdn.microsoft.com/Bing-Maps-trip-optimizer-c4e037f7)  
 Utilise le `HttpRequest` classe qui est définie dans [procédure pas à pas : connexion à l’aide de tâches et les requêtes HTTP XML](../parallel/concrt/walkthrough-connecting-using-tasks-and-xml-http-requests.md) dans le contexte d’une application complète de la plateforme Windows universelle.  
  
 [Création d’un composant DLL Windows Runtime avec C++, exemples](http://code.msdn.microsoft.com/windowsapps/Creating-a-Windows-Runtime-6c399797)  
 Montre comment utiliser la bibliothèque de modèles Windows Runtime C++ pour créer un composant DLL in-process et le consommer à partir de C + c++ / CX, JavaScript et c#.  
  
 [Exemple de jeu marble maze DirectX](http://code.msdn.microsoft.com/windowsapps/DirectX-Marble-Maze-Game-e4806345)  
 Montre comment utiliser la bibliothèque de modèles Windows Runtime C++ pour gérer la durée de vie des composants COM tels que DirectX et Media Foundation dans le contexte d’un jeu 3D complet.  
  
 [Envoi de notifications toast à partir des exemples d’applications de bureau](http://code.msdn.microsoft.com/windowsdesktop/Sending-toast-notifications-71e230a2)  
 Montre comment utiliser la bibliothèque de modèles Windows Runtime C++ pour manipuler des notifications toast à partir d’une application de bureau.  
  
## <a name="windows-runtime-c-template-library-compared-to-atl"></a>Windows Runtime bibliothèque de modèles C++ comparé à ATL  
 Bibliothèque de modèles Windows Runtime C++ ressemble à la bibliothèque ATL (Active Template), car vous pouvez l’utiliser pour créer des objets COM rapides de petites. Bibliothèque de modèles Windows Runtime C++ et ATL partagent également les concepts tels que la définition d’objets dans des modules, l’inscription explicite d’interfaces et la création d’objets à l’aide de fabriques. Vous pouvez être familiarisé avec la bibliothèque de modèles Windows Runtime C++ si vous êtes familiarisé avec ATL.  
  
 Bibliothèque de modèles Windows Runtime C++ prend en charge la fonctionnalité COM requise pour les applications de plateforme Windows universelle. Par conséquent, elle diffère de la bibliothèque ATL car elle omet la prise en charge directe des fonctionnalités COM telles que :  
  
-   agrégation ;  
  
-   implémentations stock ;  
  
-   interfaces doubles (`IDispatch`) ;  
  
-   interfaces d'énumérateur standard ;  
  
-   points de connexion ;  
  
-   interfaces détachables ;  
  
-   incorporation OLE ;  
  
-   contrôles ActiveX ;  
  
-   COM+.  
  
## <a name="concepts"></a>Concepts  
 Bibliothèque de modèles Windows Runtime C++ fournit des types représentant quelques concepts de base. Les sections suivantes décrivent ces types.  
  
### <a name="comptr"></a>ComPtr  
 [ComPtr](../windows/comptr-class.md) est un *pointeur intelligent* type qui représente l’interface spécifiée par le paramètre de modèle. Utilisez `ComPtr` pour déclarer une variable pouvant accéder aux membres d'un objet dérivé de l'interface. `ComPtr` met à jour automatiquement un décompte de références pour le pointeur d'interface sous-jacent et libère l'interface lorsque le décompte de références atteint zéro.  
  
### <a name="runtimeclass"></a>RuntimeClass  
 [RuntimeClass](../windows/runtimeclass-class.md) représente une classe instanciée qui hérite d’un ensemble d’interfaces spécifiées. A `RuntimeClass` objet peut fournir une combinaison de prise en charge pour une ou plusieurs interfaces COM de Windows Runtime, ou une référence faible à un composant.  
  
### <a name="module"></a>Module  
 [Module](../windows/module-class.md) représente une collection d’objets connexes. Un objet `Module` gère les fabriques de classe, qui créent des objets, et l'inscription, qui permet à d'autres applications d'utiliser un objet.  
  
### <a name="callback"></a>Rappel  
 Le [rappel](../windows/callback-function-windows-runtime-cpp-template-library.md) fonction crée un objet dont la fonction membre est un gestionnaire d’événements (une méthode de rappel). Utilisez la fonction `Callback` pour écrire des opérations asynchrones.  
  
### <a name="eventsource"></a>EventSource  
 [EventSource](../windows/eventsource-class.md) sert à gérer *déléguer* gestionnaires d’événements. Bibliothèque de modèles Windows Runtime C++ permet d’implémenter un délégué et utilisez `EventSource` pour ajouter, supprimer et appeler des délégués.  
  
### <a name="asyncbase"></a>AsyncBase  
 [AsyncBase](../windows/asyncbase-class.md) fournit des méthodes virtuelles qui représentent le modèle de programmation asynchrone Windows Runtime. Redéfinissez les membres de cette classe pour créer une classe personnalisée capable de démarrer, arrêter ou contrôler la progression d'une opération asynchrone.  
  
### <a name="ftmbase"></a>FtmBase  
 [FtmBase](../windows/ftmbase-class.md) représente un objet marshaler libre de threads. `FtmBase` crée un tableau global d'interface (GIT) et vous permet de gérer le marshaling et les objets proxy.  
  
### <a name="weakref"></a>WeakRef  
 [WeakRef](../windows/weakref-class.md) est un type de pointeur intelligent qui représente un *référence faible*, qui fait référence à un objet qui peut ou peut ne pas être accessible. A `WeakRef` objet peut être utilisé uniquement par le Windows Runtime et non par un COM classique.  
  
 Un objet `WeakRef` représente généralement un objet dont l'existence est contrôlée par un thread ou une application externe. Par exemple, un objet `WeakRef` peut faire référence à un objet fichier. Lorsque le fichier est ouvert, `WeakRef` est valide et le fichier référencé est accessible. En revanche, quand le fichier est fermé, `WeakRef` est incorrect et le fichier n'est pas accessible.  
  
## <a name="related-topics"></a>Rubriques connexes  
  
|||  
|-|-|  
|[Modèle de projet de bibliothèque de classes](../windows/wrl-class-library-project-template.md)|Décrit comment accéder au modèle de projet WRL Class Library. Ce modèle permet de simplifier la tâche de l’utilisation de Visual Studio pour créer des composants Windows Runtime.|  
|[API principales par catégorie](../windows/key-wrl-apis-by-category.md)|Met en surbrillance de la principale bibliothèque de modèles Windows Runtime C++ types, fonctions et les macros.|  
|[Référence](../windows/wrl-reference.md)|Contient des informations de référence pour la bibliothèque de modèles Windows Runtime C++.|  
|[Référence rapide (Windows Runtime et Visual C++)](http://go.microsoft.com/fwlink/p/?linkid=229180)|Décrit brièvement le C + c++ / fonctionnalités CX qui prennent en charge le Windows Runtime.|  
|[À l’aide de composants Windows Runtime en C++](http://go.microsoft.com/fwlink/p/?linkid=229155)|Montre comment utiliser c++ / CX pour créer un composant Windows Runtime de base.|