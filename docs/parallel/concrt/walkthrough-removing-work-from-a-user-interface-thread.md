---
title: 'Procédure pas à pas : Suppression de travail d’un Thread d’Interface utilisateur'
ms.date: 11/19/2018
helpviewer_keywords:
- user-interface threads, removing work from [Concurrency Runtime]
- removing work from user-interface threads [Concurrency Runtime]
ms.assetid: a4a65cc2-b3bc-4216-8fa8-90529491de02
ms.openlocfilehash: 1838ad0d6adb146adacb8b3a395f44f76e2a8d3f
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57304715"
---
# <a name="walkthrough-removing-work-from-a-user-interface-thread"></a>Procédure pas à pas : Suppression de travail d’un Thread d’Interface utilisateur

Ce document montre comment utiliser le Runtime d’accès concurrentiel pour déplacer le travail effectué par le thread d’interface utilisateur (IU) dans une application Microsoft Foundation Classes (MFC) à un thread de travail. Ce document montre également comment améliorer les performances d’une longue opération de dessin.

Suppression de travail à partir du thread d’interface utilisateur en déchargeant les opérations bloquantes, par exemple, le dessin, aux threads de travail peut améliorer la réactivité de votre application. Cette procédure pas à pas utilise une routine de dessin qui génère une fractale de Mandelbrot pour illustrer une longue opération de blocage. La génération de la fractale de Mandelbrot est également un bon candidat pour la parallélisation car le calcul de chaque pixel est indépendant de tous les autres calculs.

## <a name="prerequisites"></a>Prérequis

Lisez les rubriques suivantes avant de commencer cette procédure pas à pas :

- [Parallélisme des tâches](../../parallel/concrt/task-parallelism-concurrency-runtime.md)

- [Blocs de messages asynchrones](../../parallel/concrt/asynchronous-message-blocks.md)

- [Fonctions de passage de messages](../../parallel/concrt/message-passing-functions.md)

- [Algorithmes parallèles](../../parallel/concrt/parallel-algorithms.md)

- [Annulation dans la bibliothèque de modèles parallèles](cancellation-in-the-ppl.md)

Nous vous recommandons également de comprendre les principes fondamentaux du développement d’applications MFC et GDI + avant de commencer cette procédure pas à pas. Pour plus d’informations à propos de MFC, consultez [MFC Desktop Applications](../../mfc/mfc-desktop-applications.md). Pour plus d’informations sur GDI +, consultez [GDI +](https://msdn.microsoft.com/library/windows/desktop/ms533798).

##  <a name="top"></a> Sections

Cette procédure pas à pas contient les sections suivantes :

- [Création de l’Application MFC](#application)

- [Implémentation de la Version sérialisée de l’Application Mandelbrot](#serial)

- [Suppression de travail à partir du Thread d’Interface utilisateur](#removing-work)

- [Amélioration des performances de dessin](#performance)

- [Ajout de prise en charge de l’annulation](#cancellation)

##  <a name="application"></a> Création de l’Application MFC

Cette section décrit comment créer l’application MFC de base.

### <a name="to-create-a-visual-c-mfc-application"></a>Pour créer une application MFC Visual C++

1. Dans le menu **Fichier** , cliquez sur **Nouveau**, puis sur **Projet**.

1. Dans le **nouveau projet** boîte de dialogue le **modèles installés** volet, sélectionnez **Visual C++**, puis, dans le **modèles** volet, sélectionnez **Application MFC**. Tapez un nom pour le projet, par exemple, `Mandelbrot`, puis cliquez sur **OK** pour afficher le **Assistant Application MFC**.

1. Dans le **Type d’Application** volet, sélectionnez **monodocument**. Vérifiez que le **support de l’architecture Document/vue** case à cocher est désactivée.

1. Cliquez sur **Terminer** pour créer le projet et fermer la **Assistant Application MFC**.

   Vérifiez que l’application a été créée avec succès en créant et son exécution. Pour générer l’application, dans le **Build** menu, cliquez sur **générer la Solution**. Si l’application est générée avec succès, exécutez l’application en cliquant sur **démarrer le débogage** sur le **déboguer** menu.

##  <a name="serial"></a> Implémentation de la Version sérialisée de l’Application Mandelbrot

Cette section décrit comment créer la fractale de Mandelbrot. Cette version dessine la fractale de Mandelbrot dans GDI + [Bitmap](/windows/desktop/api/gdiplusheaders/nl-gdiplusheaders-bitmap) de l’objet et puis copie le contenu de cette bitmap dans la fenêtre du client.

#### <a name="to-implement-the-serial-version-of-the-mandelbrot-application"></a>Pour implémenter la version sérialisée de l’application Mandelbrot

1. Dans stdafx.h, ajoutez le code suivant `#include` directive :

   [!code-cpp[concrt-mandelbrot#1](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_1.h)]

1. Dans ChildView.h, après le `pragma` directive, définir le `BitmapPtr` type. Le `BitmapPtr` type permet à un pointeur vers un `Bitmap` objet devant être partagé par plusieurs composants. Le `Bitmap` objet est supprimé lorsqu’il n’est plus référencé par aucun composant.

   [!code-cpp[concrt-mandelbrot#2](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_2.h)]

1. Dans ChildView.h, ajoutez le code suivant à la `protected` section de la `CChildView` classe :

   [!code-cpp[concrt-mandelbrot#3](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_3.h)]

1. Dans ChildView.cpp, commentez ou supprimez les lignes suivantes.

   [!code-cpp[concrt-mandelbrot#4](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_4.cpp)]

   Dans les versions Debug, cette étape empêche l’application d’utiliser le `DEBUG_NEW` allocateur, qui n’est pas compatible avec GDI +.

1. Dans ChildView.cpp, ajoutez un `using` directive pour le `Gdiplus` espace de noms.

   [!code-cpp[concrt-mandelbrot#5](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_5.cpp)]

1. Ajoutez le code suivant au constructeur et destructeur de la `CChildView` classe pour initialiser et arrêter GDI +.

   [!code-cpp[concrt-mandelbrot#6](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_6.cpp)]

1. Implémentez la méthode `CChildView::DrawMandelbrot`. Cette méthode dessine une fractale de Mandelbrot spécifié `Bitmap` objet.

   [!code-cpp[concrt-mandelbrot#7](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_7.cpp)]

1. Implémentez la méthode `CChildView::OnPaint`. Cette méthode appelle `CChildView::DrawMandelbrot` , puis copie le contenu de la `Bitmap` objet dans la fenêtre.

   [!code-cpp[concrt-mandelbrot#8](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_8.cpp)]

1. Vérifiez que l’application a été mises à jour en créant et son exécution.

L’illustration suivante montre les résultats de l’application Mandelbrot.

![L’Application Mandelbrot](../../parallel/concrt/media/mandelbrot.png "l’Application Mandelbrot")

Étant donné que le calcul de chaque pixel est gourmand en ressources, le thread d’interface utilisateur ne peut pas traiter les messages supplémentaires jusqu'à ce que le calcul total se termine. Cela peut réduire la réactivité de l’application. Toutefois, vous pouvez atténuer ce problème en supprimant le travail à partir du thread d’interface utilisateur.

[[Haut](#top)]

##  <a name="removing-work"></a> Suppression de travail à partir du Thread d’interface utilisateur

Cette section montre comment supprimer le travail de dessin à partir du thread d’interface utilisateur dans l’application Mandelbrot. En déplaçant le travail de dessin à partir du thread d’interface utilisateur à un thread de travail, le thread d’interface utilisateur peut traiter les messages que le thread de travail génère l’image en arrière-plan.

Le Runtime d’accès concurrentiel fournit trois méthodes pour exécuter des tâches : [groupes de tâches](../../parallel/concrt/task-parallelism-concurrency-runtime.md), [agents asynchrones](../../parallel/concrt/asynchronous-agents.md), et [tâches légères](../../parallel/concrt/task-scheduler-concurrency-runtime.md). Bien que vous pouvez utiliser l’un de ces mécanismes pour supprimer du travail à partir du thread d’interface utilisateur, cet exemple utilise un [concurrency::task_group](reference/task-group-class.md) , car les groupes de tâches prennent en charge l’annulation de l’objet. Cette procédure pas à pas utilise plus tard d’annulation afin de réduire la quantité de travail qui est effectuée lorsque la fenêtre du client est redimensionnée et effectuer un nettoyage lorsque la fenêtre est détruite.

Cet exemple utilise également un [concurrency::unbounded_buffer](reference/unbounded-buffer-class.md) objet afin de permettre le thread d’interface utilisateur et le thread de travail pour communiquer entre eux. Une fois que le thread de travail génère l’image, il envoie un pointeur vers le `Bitmap` de l’objet à le `unbounded_buffer` de l’objet, puis publie un message de peinture au thread d’interface utilisateur. Le thread d’interface utilisateur reçoit le `unbounded_buffer` objet le `Bitmap` de l’objet et dessine dans la fenêtre du client.

#### <a name="to-remove-the-drawing-work-from-the-ui-thread"></a>Pour supprimer le travail de dessin à partir du thread d’interface utilisateur

1. Dans stdafx.h, ajoutez le code suivant `#include` directives :

   [!code-cpp[concrt-mandelbrot#101](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_9.h)]

1. Dans ChildView.h, ajoutez `task_group` et `unbounded_buffer` les variables de membre à la `protected` section de la `CChildView` classe. Le `task_group` objet conserve les tâches qui exécutent le dessin ; le `unbounded_buffer` objet conserve l’image de Mandelbrot terminée.

   [!code-cpp[concrt-mandelbrot#102](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_10.h)]

1. Dans ChildView.cpp, ajoutez un `using` directive pour le `concurrency` espace de noms.

   [!code-cpp[concrt-mandelbrot#103](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_11.cpp)]

1. Dans le `CChildView::DrawMandelbrot` (méthode), après l’appel à `Bitmap::UnlockBits`, appelez le [concurrency::send](reference/concurrency-namespace-functions.md#send) (fonction) pour passer le `Bitmap` objet pour le thread d’interface utilisateur. Publier un message de peinture au thread d’interface utilisateur, puis invalide la zone cliente.

   [!code-cpp[concrt-mandelbrot#104](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_12.cpp)]

1. Mise à jour le `CChildView::OnPaint` méthode pour recevoir les mises à jour `Bitmap` de l’objet et dessiner l’image dans la fenêtre du client.

   [!code-cpp[concrt-mandelbrot#105](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_13.cpp)]

   Le `CChildView::OnPaint` méthode crée une tâche pour générer l’image Mandelbrot si il n’existe pas dans le tampon de messages. Le tampon de messages ne contiendra pas un `Bitmap` objet dans les cas tels que le message de peinture initial et lorsqu’une autre fenêtre est déplacée devant la fenêtre du client.

1. Vérifiez que l’application a été mises à jour en créant et son exécution.

L’interface utilisateur est maintenant plus réactive, car le travail de dessin est effectué en arrière-plan.

[[Haut](#top)]

##  <a name="performance"></a> Amélioration des performances de dessin

La génération de la fractale de Mandelbrot est un bon candidat pour la parallélisation car le calcul de chaque pixel est indépendant de tous les autres calculs. Pour paralléliser la procédure de dessin, convertissez externe `for` boucle dans le `CChildView::DrawMandelbrot` méthode à un appel à la [concurrency::parallel_for](reference/concurrency-namespace-functions.md#parallel_for) algorithme, comme suit.

[!code-cpp[concrt-mandelbrot#301](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_14.cpp)]

Étant donné que le calcul de chaque élément de bitmap est indépendant, il est inutile synchroniser les opérations de dessin qui accèdent à la mémoire bitmap. Ainsi, les performances à l’échelle en tant que le nombre de processeurs disponibles augmente.

[[Haut](#top)]

##  <a name="cancellation"></a> Ajout de prise en charge de l’annulation

Cette section décrit comment gérer le redimensionnement des fenêtres et comment annuler des tâches de dessins actives lorsque la fenêtre est détruite.

Le document [l’annulation dans la bibliothèque PPL](cancellation-in-the-ppl.md) explique le fonctionne de l’annulation dans le runtime. L’annulation est coopérative ; Par conséquent, il ne se produit pas immédiatement. Pour arrêter une tâche annulée, le runtime lève une exception interne pendant un appel ultérieur à partir de la tâche dans le runtime. La section précédente montre comment utiliser le `parallel_for` algorithme pour améliorer les performances de la tâche de dessin. L’appel à `parallel_for` permet à l’exécution d’arrêter la tâche et par conséquent, l’annulation de fonctionner.

### <a name="cancelling-active-tasks"></a>L’annulation de tâches actives

Crée l’application Mandelbrot `Bitmap` objets dont les dimensions correspondent à la taille de la fenêtre du client. Chaque fois que la fenêtre du client est redimensionnée, l’application crée une tâche supplémentaire en arrière-plan pour générer une image pour la nouvelle taille de fenêtre. L’application ne nécessite pas ces images intermédiaires ; Il nécessite uniquement l’image pour la taille de fenêtre finale. Pour empêcher l’application d’exécuter ce travail supplémentaire, vous pouvez annuler toutes les tâches dessins actives dans les gestionnaires de messages pour le `WM_SIZE` et `WM_SIZING` messages et puis replanifiez dessin fonctionneront une fois la fenêtre est redimensionnée.

Pour annuler les tâches de dessins actives lorsque la fenêtre est redimensionnée, l’application appelle le [Concurrency::task_group :: Cancel](reference/task-group-class.md#cancel) méthode dans les gestionnaires pour le `WM_SIZING` et `WM_SIZE` messages. Le gestionnaire pour le `WM_SIZE` message également appels le [Concurrency::task_group :: wait](reference/task-group-class.md#wait) méthode pour attendre que toutes les tâches à effectuer et puis replanifie la tâche de dessin pour la taille de fenêtre de mise à jour.

Lorsque la fenêtre du client est détruite, il est conseillé d’annuler toutes les tâches actives dessins. Annulation de toutes les tâches actives dessins permet de s’assurer que les threads de travail ne les publiez pas les messages vers le thread d’interface utilisateur après la destruction de la fenêtre du client. L’application annule toutes les tâches actives dessins dans le gestionnaire pour le `WM_DESTROY` message.

### <a name="responding-to-cancellation"></a>Répondre à l’annulation

Le `CChildView::DrawMandelbrot` (méthode), qui exécute la tâche de dessin, doit répondre à l’annulation. Étant donné que le runtime utilise la gestion des exceptions pour annuler des tâches, le `CChildView::DrawMandelbrot` méthode doit utiliser un mécanisme sécurisé de l’exception afin de garantir que toutes les ressources sont correctement nettoyées. Cet exemple utilise le *Resource Acquisition Is Initialization* modèle (RAII) pour garantir que les bits du bitmap sont déverrouillés lorsque la tâche est annulée.

##### <a name="to-add-support-for-cancellation-in-the-mandelbrot-application"></a>Pour ajouter la prise en charge de l’annulation dans l’application Mandelbrot

1. Dans ChildView.h, dans le `protected` section de la `CChildView` de classe, ajoutez des déclarations pour les `OnSize`, `OnSizing`, et `OnDestroy` des fonctions de mappage de message.

   [!code-cpp[concrt-mandelbrot#201](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_15.h)]

1. Dans ChildView.cpp, modifiez la table des messages pour qu’il contienne des gestionnaires pour les `WM_SIZE`, `WM_SIZING`, et `WM_DESTROY` messages.

   [!code-cpp[concrt-mandelbrot#202](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_16.cpp)]

1. Implémentez la méthode `CChildView::OnSizing`. Cette méthode annule toutes les tâches dessins existants.

   [!code-cpp[concrt-mandelbrot#203](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_17.cpp)]

1. Implémentez la méthode `CChildView::OnSize`. Cette méthode annule toutes les tâches dessins existants et crée une nouvelle tâche de dessin pour la taille de fenêtre du client mis à jour.

   [!code-cpp[concrt-mandelbrot#204](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_18.cpp)]

1. Implémentez la méthode `CChildView::OnDestroy`. Cette méthode annule toutes les tâches dessins existants.

   [!code-cpp[concrt-mandelbrot#205](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_19.cpp)]

1. Dans ChildView.cpp, définissez la `scope_guard` classe qui implémente le modèle RAII.

   [!code-cpp[concrt-mandelbrot#206](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_20.cpp)]

1. Ajoutez le code suivant à la `CChildView::DrawMandelbrot` méthode après l’appel à `Bitmap::LockBits`:

   [!code-cpp[concrt-mandelbrot#207](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_21.cpp)]

   Ce code gère l’annulation en créant un `scope_guard` objet. Lorsque l’objet quitte la portée, il déverrouille les bits du bitmap.

1. Modifiez la fin de la `CChildView::DrawMandelbrot` méthode pour faire disparaître le `scope_guard` une fois les bits du bitmap déverrouillés, mais avant que tous les messages sont envoyés au thread d’interface utilisateur de l’objet. Cela garantit que le thread d’interface utilisateur n’est pas mis à jour avant que les bits du bitmap sont déverrouillées.

   [!code-cpp[concrt-mandelbrot#208](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_22.cpp)]

9. Vérifiez que l’application a été mises à jour en créant et son exécution.

Quand vous redimensionnez la fenêtre, le travail de dessin est effectuée uniquement pour la taille de fenêtre finale. Les tâches de dessins actives sont également annulées lorsque la fenêtre est détruite.

[[Haut](#top)]

## <a name="see-also"></a>Voir aussi

[Procédures pas à pas relatives au runtime d’accès concurrentiel](../../parallel/concrt/concurrency-runtime-walkthroughs.md)<br/>
[Parallélisme des tâches](../../parallel/concrt/task-parallelism-concurrency-runtime.md)<br/>
[Blocs de messages asynchrones](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[Fonctions de passage de messages](../../parallel/concrt/message-passing-functions.md)<br/>
[Algorithmes parallèles](../../parallel/concrt/parallel-algorithms.md)<br/>
[Annulation dans la bibliothèque de modèles parallèles](cancellation-in-the-ppl.md)<br/>
[MFC, applications de bureau](../../mfc/mfc-desktop-applications.md)
