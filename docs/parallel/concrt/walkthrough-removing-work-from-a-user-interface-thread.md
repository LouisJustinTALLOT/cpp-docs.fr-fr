---
description: 'En savoir plus sur : procédure pas à pas : suppression de travail d’un thread de User-Interface'
title: "Procédure pas à pas : suppression de travail d'un thread d'interface utilisateur"
ms.date: 08/19/2019
helpviewer_keywords:
- user-interface threads, removing work from [Concurrency Runtime]
- removing work from user-interface threads [Concurrency Runtime]
ms.assetid: a4a65cc2-b3bc-4216-8fa8-90529491de02
ms.openlocfilehash: 816e8446771cda907397f43386c33476cf3665b8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97340916"
---
# <a name="walkthrough-removing-work-from-a-user-interface-thread"></a>Procédure pas à pas : suppression de travail d'un thread d'interface utilisateur

Ce document montre comment utiliser l’runtime d’accès concurrentiel pour déplacer le travail effectué par le thread d’interface utilisateur dans une application Microsoft Foundation Classes (MFC) vers un thread de travail. Ce document montre également comment améliorer les performances d’une longue opération de dessin.

La suppression du travail du thread d’interface utilisateur par déchargement des opérations bloquantes, par exemple, le dessin, sur des threads de travail peut améliorer la réactivité de votre application. Cette procédure pas à pas utilise une routine de dessin qui génère la fractale de Mandelbrot pour illustrer une longue opération de blocage. La génération de la fractale Mandelbrot est également un bon candidat à la parallélisation, car le calcul de chaque pixel est indépendant de tous les autres calculs.

## <a name="prerequisites"></a>Prérequis

Lisez les rubriques suivantes avant de commencer cette procédure pas à pas :

- [Parallélisme des tâches](../../parallel/concrt/task-parallelism-concurrency-runtime.md)

- [Blocs de messages asynchrones](../../parallel/concrt/asynchronous-message-blocks.md)

- [Fonctions de passage de messages](../../parallel/concrt/message-passing-functions.md)

- [Algorithmes parallèles](../../parallel/concrt/parallel-algorithms.md)

- [Annulation dans la bibliothèque de modèles parallèles](cancellation-in-the-ppl.md)

Nous vous recommandons également de comprendre les principes de base du développement d’applications MFC et de GDI+ avant de commencer cette procédure pas à pas. Pour plus d’informations sur MFC, consultez [applications de bureau MFC](../../mfc/mfc-desktop-applications.md). Pour plus d’informations sur GDI+, consultez [GDI+](/windows/win32/gdiplus/-gdiplus-gdi-start).

## <a name="sections"></a><a name="top"></a> Sections

Cette procédure pas à pas contient les sections suivantes :

- [Création de l’application MFC](#application)

- [Implémentation de la version série de l’application Mandelbrot](#serial)

- [Suppression du travail du thread User-Interface](#removing-work)

- [Amélioration des performances de dessin](#performance)

- [Ajout de la prise en charge de l’annulation](#cancellation)

## <a name="creating-the-mfc-application"></a><a name="application"></a> Création de l’application MFC

Cette section décrit comment créer l’application MFC de base.

### <a name="to-create-a-visual-c-mfc-application"></a>Pour créer une Visual C++ application MFC

1. Utilisez l' **Assistant Application MFC** pour créer une application MFC avec tous les paramètres par défaut. Consultez [procédure pas à pas : utilisation des nouveaux contrôles de l’interpréteur de commandes MFC](../../mfc/walkthrough-using-the-new-mfc-shell-controls.md) pour obtenir des instructions sur l’ouverture de l’Assistant pour votre version de Visual Studio.

1. Tapez un nom pour le projet, par exemple, `Mandelbrot` , puis cliquez sur **OK** pour afficher l **'Assistant Application MFC**.

1. Dans le volet **type d’application** , sélectionnez **document unique**. Vérifiez que la case à cocher **prise en charge de l’architecture document/vue** est désactivée.

1. Cliquez sur **Terminer** pour créer le projet et fermer l' **Assistant Application MFC**.

   Vérifiez que l’application a été créée avec succès en la générant et en l’exécutant. Pour générer l’application, dans le menu **générer** , cliquez sur **générer la solution**. Si l’application est générée avec succès, exécutez l’application en cliquant sur **Démarrer le débogage** dans le menu **Déboguer** .

## <a name="implementing-the-serial-version-of-the-mandelbrot-application"></a><a name="serial"></a> Implémentation de la version série de l’application Mandelbrot

Cette section décrit comment dessiner une fractale de Mandelbrot. Cette version dessine la fractale de Mandelbrot dans un objet [bitmap](/windows/win32/api/gdiplusheaders/nl-gdiplusheaders-bitmap) GDI+, puis copie le contenu de cette image bitmap dans la fenêtre cliente.

#### <a name="to-implement-the-serial-version-of-the-mandelbrot-application"></a>Pour implémenter la version série de l’application Mandelbrot

1. Dans *pch. h* (*stdafx. h* dans Visual Studio 2017 et versions antérieures), ajoutez la `#include` directive suivante :

   [!code-cpp[concrt-mandelbrot#1](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_1.h)]

1. Dans ChildView. h, après la `pragma` directive, définissez le `BitmapPtr` type. Le `BitmapPtr` type permet à un pointeur vers un `Bitmap` objet d’être partagé par plusieurs composants. L' `Bitmap` objet est supprimé lorsqu’il n’est plus référencé par aucun composant.

   [!code-cpp[concrt-mandelbrot#2](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_2.h)]

1. Dans ChildView. h, ajoutez le code suivant à la **`protected`** section de la `CChildView` classe :

   [!code-cpp[concrt-mandelbrot#3](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_3.h)]

1. Dans ChildView. cpp, commentez ou supprimez les lignes suivantes.

   [!code-cpp[concrt-mandelbrot#4](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_4.cpp)]

   Dans les versions Debug, cette étape empêche l’application d’utiliser l' `DEBUG_NEW` allocateur, qui est incompatible avec GDI+.

1. Dans ChildView. cpp, ajoutez une **`using`** directive à l' `Gdiplus` espace de noms.

   [!code-cpp[concrt-mandelbrot#5](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_5.cpp)]

1. Ajoutez le code suivant au constructeur et au destructeur de la `CChildView` classe pour initialiser et arrêter GDI+.

   [!code-cpp[concrt-mandelbrot#6](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_6.cpp)]

1. Implémentez la méthode `CChildView::DrawMandelbrot`. Cette méthode dessine la fractale de Mandelbrot sur l' `Bitmap` objet spécifié.

   [!code-cpp[concrt-mandelbrot#7](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_7.cpp)]

1. Implémentez la méthode `CChildView::OnPaint`. Cette méthode appelle `CChildView::DrawMandelbrot` , puis copie le contenu de l' `Bitmap` objet dans la fenêtre.

   [!code-cpp[concrt-mandelbrot#8](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_8.cpp)]

1. Vérifiez que l’application a été correctement mise à jour en la générant et en l’exécutant.

L’illustration suivante montre les résultats de l’application Mandelbrot.

![L'application Mandelbrot](../../parallel/concrt/media/mandelbrot.png "L'application Mandelbrot")

Étant donné que le calcul pour chaque pixel est coûteux en termes de calcul, le thread d’interface utilisateur ne peut pas traiter des messages supplémentaires tant que le calcul global n’est pas terminé. Cela peut nuire à la réactivité de l’application. Toutefois, vous pouvez soulager ce problème en supprimant le travail du thread d’interface utilisateur.

[[Haut](#top)]

## <a name="removing-work-from-the-ui-thread"></a><a name="removing-work"></a> Suppression du travail du thread d’interface utilisateur

Cette section montre comment supprimer le travail de dessin du thread d’interface utilisateur dans l’application Mandelbrot. En déplaçant le travail de dessin du thread d’interface utilisateur vers un thread de travail, le thread d’interface utilisateur peut traiter les messages lorsque le thread de travail génère l’image en arrière-plan.

L’runtime d’accès concurrentiel offre trois façons d’exécuter des tâches : des [groupes de tâches](../../parallel/concrt/task-parallelism-concurrency-runtime.md), des [agents asynchrones](../../parallel/concrt/asynchronous-agents.md)et des [tâches légères](../../parallel/concrt/task-scheduler-concurrency-runtime.md). Bien que vous puissiez utiliser l’un de ces mécanismes pour supprimer le travail du thread d’interface utilisateur, cet exemple utilise un objet [Concurrency :: task_group](reference/task-group-class.md) , car les groupes de tâches prennent en charge l’annulation. Cette procédure pas à pas utilise ultérieurement l’annulation pour réduire la quantité de travail effectuée lorsque la fenêtre cliente est redimensionnée et pour effectuer un nettoyage lorsque la fenêtre est détruite.

Cet exemple utilise également un objet [Concurrency :: unbounded_buffer](reference/unbounded-buffer-class.md) pour permettre au thread d’interface utilisateur et au thread de travail de communiquer entre eux. Une fois que le thread de travail a produit l’image, il envoie un pointeur vers l' `Bitmap` objet à l’objet, puis `unbounded_buffer` publie un message de peinture sur le thread d’interface utilisateur. Le thread d’interface utilisateur reçoit ensuite de l’objet `unbounded_buffer` l' `Bitmap` objet et le dessine dans la fenêtre cliente.

#### <a name="to-remove-the-drawing-work-from-the-ui-thread"></a>Pour supprimer le travail de dessin du thread d’interface utilisateur

1. Dans *pch. h* (*stdafx. h* dans Visual Studio 2017 et versions antérieures), ajoutez les `#include` directives suivantes :

   [!code-cpp[concrt-mandelbrot#101](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_9.h)]

1. Dans ChildView. h, ajoutez `task_group` `unbounded_buffer` les variables membres et à la **`protected`** section de la `CChildView` classe. L' `task_group` objet contient les tâches qui effectuent le dessin ; l' `unbounded_buffer` objet contient l’image Mandelbrot terminée.

   [!code-cpp[concrt-mandelbrot#102](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_10.h)]

1. Dans ChildView. cpp, ajoutez une **`using`** directive à l' `concurrency` espace de noms.

   [!code-cpp[concrt-mandelbrot#103](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_11.cpp)]

1. Dans la `CChildView::DrawMandelbrot` méthode, après l’appel à `Bitmap::UnlockBits` , appelez la fonction [Concurrency :: Send](reference/concurrency-namespace-functions.md#send) pour passer l' `Bitmap` objet au thread d’interface utilisateur. Publiez ensuite un message de peinture dans le thread d’interface utilisateur et invalidez la zone cliente.

   [!code-cpp[concrt-mandelbrot#104](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_12.cpp)]

1. Mettez à jour la `CChildView::OnPaint` méthode pour recevoir l’objet mis à jour `Bitmap` et dessiner l’image dans la fenêtre cliente.

   [!code-cpp[concrt-mandelbrot#105](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_13.cpp)]

   La `CChildView::OnPaint` méthode crée une tâche pour générer l’image Mandelbrot si elle n’existe pas dans la mémoire tampon des messages. La mémoire tampon des messages ne contient pas d' `Bitmap` objet dans les cas tels que le message de peinture initial et lorsqu’une autre fenêtre est déplacée devant la fenêtre du client.

1. Vérifiez que l’application a été correctement mise à jour en la générant et en l’exécutant.

L’interface utilisateur est maintenant plus réactive car le travail de dessin est effectué en arrière-plan.

[[Haut](#top)]

## <a name="improving-drawing-performance"></a><a name="performance"></a> Amélioration des performances de dessin

La génération de la fractale Mandelbrot est un bon candidat à la parallélisation, car le calcul de chaque pixel est indépendant de tous les autres calculs. Pour paralléliser la procédure de dessin, convertissez la **`for`** boucle externe de la `CChildView::DrawMandelbrot` méthode en un appel à l’algorithme d' [arallel_for d’accès concurrentiel ::p](reference/concurrency-namespace-functions.md#parallel_for) , comme suit.

[!code-cpp[concrt-mandelbrot#301](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_14.cpp)]

Étant donné que le calcul de chaque élément bitmap est indépendant, vous n’avez pas à synchroniser les opérations de dessin qui accèdent à la mémoire bitmap. Cela permet de mettre à l’échelle les performances à mesure que le nombre de processeurs disponibles augmente.

[[Haut](#top)]

## <a name="adding-support-for-cancellation"></a><a name="cancellation"></a> Ajout de la prise en charge de l’annulation

Cette section décrit comment gérer le redimensionnement de fenêtre et comment annuler des tâches de dessin actives lorsque la fenêtre est détruite.

L' [annulation de document dans la bibliothèque de modèles parallèles](cancellation-in-the-ppl.md) explique le fonctionnement de l’annulation dans le Runtime. L’annulation est coopérative. par conséquent, il ne se produit pas immédiatement. Pour arrêter une tâche annulée, le runtime lève une exception interne pendant un appel ultérieur de la tâche dans le Runtime. La section précédente montre comment utiliser l' `parallel_for` algorithme pour améliorer les performances de la tâche de dessin. L’appel à `parallel_for` permet au runtime d’arrêter la tâche et, par conséquent, d’autoriser le fonctionnement de l’annulation.

### <a name="cancelling-active-tasks"></a>Annulation des tâches actives

L’application Mandelbrot crée `Bitmap` des objets dont les dimensions correspondent à la taille de la fenêtre du client. Chaque fois que la fenêtre cliente est redimensionnée, l’application crée une tâche en arrière-plan supplémentaire pour générer une image pour la nouvelle taille de fenêtre. L’application ne nécessite pas ces images intermédiaires. elle nécessite uniquement l’image pour la taille finale de la fenêtre. Pour empêcher l’application d’effectuer ce travail supplémentaire, vous pouvez annuler toutes les tâches de dessin actives dans les gestionnaires de messages pour les `WM_SIZE` messages et, puis `WM_SIZING` replanifier le travail de dessin une fois que la fenêtre est redimensionnée.

Pour annuler les tâches de dessin actives quand la fenêtre est redimensionnée, l’application appelle la méthode [Concurrency :: task_group :: Cancel](reference/task-group-class.md#cancel) dans les gestionnaires pour `WM_SIZING` les `WM_SIZE` messages et. Le gestionnaire du `WM_SIZE` message appelle également la méthode [Concurrency :: task_group :: wait](reference/task-group-class.md#wait) pour attendre que toutes les tâches actives se terminent, puis replanifie la tâche de dessin pour la taille de fenêtre mise à jour.

Lorsque la fenêtre cliente est détruite, il est conseillé d’annuler toutes les tâches de dessin actives. L’annulation d’une tâche de dessin active permet de s’assurer que les threads de travail ne publient pas de messages dans le thread d’interface utilisateur après la destruction de la fenêtre du client. L’application annule toutes les tâches de dessin actives dans le gestionnaire pour le `WM_DESTROY` message.

### <a name="responding-to-cancellation"></a>Réponse à l’annulation

La `CChildView::DrawMandelbrot` méthode, qui exécute la tâche de dessin, doit répondre à l’annulation. Étant donné que le runtime utilise la gestion des exceptions pour annuler des tâches, la `CChildView::DrawMandelbrot` méthode doit utiliser un mécanisme sécurisé pour garantir que toutes les ressources sont correctement nettoyées. Cet exemple utilise le modèle RAII ( *Resource Acquisition Is Initialization* ) pour garantir que les bits de la bitmap sont déverrouillés lorsque la tâche est annulée.

##### <a name="to-add-support-for-cancellation-in-the-mandelbrot-application"></a>Pour ajouter la prise en charge de l’annulation dans l’application Mandelbrot

1. Dans ChildView. h, dans la **`protected`** section de la `CChildView` classe, ajoutez des déclarations pour `OnSize` les `OnSizing` fonctions de `OnDestroy` table des messages, et.

   [!code-cpp[concrt-mandelbrot#201](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_15.h)]

1. Dans ChildView. cpp, modifiez la table des messages pour qu’elle contienne des gestionnaires pour les `WM_SIZE` `WM_SIZING` messages, et `WM_DESTROY` .

   [!code-cpp[concrt-mandelbrot#202](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_16.cpp)]

1. Implémentez la méthode `CChildView::OnSizing`. Cette méthode annule toutes les tâches de dessin existantes.

   [!code-cpp[concrt-mandelbrot#203](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_17.cpp)]

1. Implémentez la méthode `CChildView::OnSize`. Cette méthode annule toutes les tâches de dessin existantes et crée une tâche de dessin pour la taille de la fenêtre cliente mise à jour.

   [!code-cpp[concrt-mandelbrot#204](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_18.cpp)]

1. Implémentez la méthode `CChildView::OnDestroy`. Cette méthode annule toutes les tâches de dessin existantes.

   [!code-cpp[concrt-mandelbrot#205](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_19.cpp)]

1. Dans ChildView. cpp, définissez la `scope_guard` classe, qui implémente le modèle RAII.

   [!code-cpp[concrt-mandelbrot#206](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_20.cpp)]

1. Ajoutez le code suivant à la `CChildView::DrawMandelbrot` méthode après l’appel à `Bitmap::LockBits` :

   [!code-cpp[concrt-mandelbrot#207](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_21.cpp)]

   Ce code gère l’annulation en créant un `scope_guard` objet. Lorsque l’objet quitte l’étendue, il déverrouille les bits de la bitmap.

1. Modifiez la fin de la `CChildView::DrawMandelbrot` méthode pour ignorer l' `scope_guard` objet une fois que les bits de la bitmap sont déverrouillés, mais avant l’envoi des messages au thread d’interface utilisateur. Cela permet de s’assurer que le thread d’interface utilisateur n’est pas mis à jour avant le déverrouillage des bits de la bitmap.

   [!code-cpp[concrt-mandelbrot#208](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_22.cpp)]

1. Vérifiez que l’application a été correctement mise à jour en la générant et en l’exécutant.

Lorsque vous redimensionnez la fenêtre, le travail de dessin est effectué uniquement pour la taille finale de la fenêtre. Toutes les tâches de dessin actives sont également annulées lorsque la fenêtre est détruite.

[[Haut](#top)]

## <a name="see-also"></a>Voir aussi

[Procédures pas à pas runtime d’accès concurrentiel](../../parallel/concrt/concurrency-runtime-walkthroughs.md)<br/>
[Parallélisme des tâches](../../parallel/concrt/task-parallelism-concurrency-runtime.md)<br/>
[Blocs de messages asynchrones](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[Fonctions de passage de messages](../../parallel/concrt/message-passing-functions.md)<br/>
[Algorithmes parallèles](../../parallel/concrt/parallel-algorithms.md)<br/>
[Annulation dans la bibliothèque de modèles parallèles](cancellation-in-the-ppl.md)<br/>
[Applications de bureau MFC](../../mfc/mfc-desktop-applications.md)
