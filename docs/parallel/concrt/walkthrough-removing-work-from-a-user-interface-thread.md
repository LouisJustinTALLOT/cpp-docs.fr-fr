---
title: "Procédure pas à pas : suppression de travail d'un thread d'interface utilisateur"
ms.date: 08/19/2019
helpviewer_keywords:
- user-interface threads, removing work from [Concurrency Runtime]
- removing work from user-interface threads [Concurrency Runtime]
ms.assetid: a4a65cc2-b3bc-4216-8fa8-90529491de02
ms.openlocfilehash: 52bc98ef339a19c6ec2a53697f532a9a94b6c9a6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377442"
---
# <a name="walkthrough-removing-work-from-a-user-interface-thread"></a>Procédure pas à pas : suppression de travail d'un thread d'interface utilisateur

Ce document montre comment utiliser le Temps d’exécution De concurrency pour déplacer le travail qui est effectué par le thread utilisateur-interface (interface utilisateur) dans une application Microsoft Foundation Classes (MFC) à un thread de travailleur. Ce document montre également comment améliorer les performances d’une longue opération de dessin.

Supprimer le travail du thread d’interface utilisateur en déchargeant les opérations de blocage, par exemple, le dessin, vers les fils des travailleurs peut améliorer la réactivité de votre application. Cette procédure pas à pas utilise une routine de dessin qui génère la fractale Mandelbrot pour démontrer une longue opération de blocage. La génération de la fractale Mandelbrot est également un bon candidat à la parallélisation car le calcul de chaque pixel est indépendant de tous les autres calculs.

## <a name="prerequisites"></a>Prérequis

Lisez les sujets suivants avant de commencer cette procédure pas à pas :

- [Parallélisme des tâches](../../parallel/concrt/task-parallelism-concurrency-runtime.md)

- [Blocs de messages asynchrones](../../parallel/concrt/asynchronous-message-blocks.md)

- [Fonctions de passage de message](../../parallel/concrt/message-passing-functions.md)

- [Algorithmes parallèles](../../parallel/concrt/parallel-algorithms.md)

- [Annulation dans la bibliothèque de modèles parallèles](cancellation-in-the-ppl.md)

Nous vous recommandons également de comprendre les bases du développement d’applications MFC et de GDIMD avant de commencer cette procédure pas à pas. Pour plus d’informations sur MFC, voir [MFC Desktop Applications](../../mfc/mfc-desktop-applications.md). Pour plus d’informations sur GDIMD, voir [GDIMD](/windows/win32/gdiplus/-gdiplus-gdi-start).

## <a name="sections"></a><a name="top"></a>Sections

Cette procédure pas à pas contient les sections suivantes :

- [Création de l’application MFC](#application)

- [Mise en œuvre de la version série de l’application Mandelbrot](#serial)

- [Suppression du travail du thread utilisateur-interface](#removing-work)

- [Améliorer les performances de dessin](#performance)

- [Ajout d’un support pour l’annulation](#cancellation)

## <a name="creating-the-mfc-application"></a><a name="application"></a>Création de l’application MFC

Cette section décrit comment créer l’application MFC de base.

### <a name="to-create-a-visual-c-mfc-application"></a>Pour créer une application Visual CMD MFC

1. Utilisez **l’assistant d’application MFC** pour créer une application MFC avec tous les paramètres par défaut. Voir [Procédure pas à pas : Utilisation des nouveaux contrôles de la coque MFC](../../mfc/walkthrough-using-the-new-mfc-shell-controls.md) pour obtenir des instructions sur la façon d’ouvrir l’assistant pour votre version de Visual Studio.

1. Tapez un nom pour le `Mandelbrot`projet, par exemple, , puis cliquez **sur OK** pour afficher le **MFC Application Wizard**.

1. Dans le volet **type d’application,** sélectionnez **le document unique**. Assurez-vous que la case à cocher **de support d’architecture Document/View** est effacée.

1. Cliquez sur **Finition** pour créer le projet et fermer le **MFC Application Wizard**.

   Vérifiez que l’application a été créée avec succès en la construisant et en l’exécutant. Pour construire l’application, sur le menu **Build,** cliquez sur **Build Solution**. Si l’application se construit avec succès, exécutez l’application en cliquant sur **Start Debugging** sur le menu **Debug.**

## <a name="implementing-the-serial-version-of-the-mandelbrot-application"></a><a name="serial"></a>Mise en œuvre de la version série de l’application Mandelbrot

Cette section décrit comment dessiner la fractale Mandelbrot. Cette version attire la fractale Mandelbrot sur un objet [GDI Bitmap,](/windows/win32/api/gdiplusheaders/nl-gdiplusheaders-bitmap) puis copie le contenu de cette bitmap à la fenêtre du client.

#### <a name="to-implement-the-serial-version-of-the-mandelbrot-application"></a>Pour implémenter la version série de l’application Mandelbrot

1. Dans *pch.h* (*stdafx.h* dans Visual Studio 2017 et plus tôt), ajoutez la directive suivante `#include` :

   [!code-cpp[concrt-mandelbrot#1](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_1.h)]

1. Dans ChildView.h, `pragma` après la `BitmapPtr` directive, définissez le type. Le `BitmapPtr` type permet de `Bitmap` partager un pointeur vers un objet par plusieurs composants. L’objet `Bitmap` est supprimé lorsqu’il n’est plus référencé par aucun composant.

   [!code-cpp[concrt-mandelbrot#2](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_2.h)]

1. Dans ChildView.h, ajoutez le `protected` code suivant `CChildView` à la section de la classe :

   [!code-cpp[concrt-mandelbrot#3](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_3.h)]

1. Dans ChildView.cpp, commentez ou supprimez les lignes suivantes.

   [!code-cpp[concrt-mandelbrot#4](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_4.cpp)]

   Dans Debug construit, cette étape empêche l’application d’utiliser l’alloueur, `DEBUG_NEW` ce qui est incompatible avec GDI.

1. Dans ChildView.cpp, `using` ajoutez une `Gdiplus` directive à l’espace nom.

   [!code-cpp[concrt-mandelbrot#5](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_5.cpp)]

1. Ajoutez le code suivant au constructeur et `CChildView` au destructeur de la classe pour initialiser et arrêter GDIMD.

   [!code-cpp[concrt-mandelbrot#6](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_6.cpp)]

1. Implémentez la méthode `CChildView::DrawMandelbrot`. Cette méthode attire la fractale Mandelbrot à l’objet spécifié. `Bitmap`

   [!code-cpp[concrt-mandelbrot#7](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_7.cpp)]

1. Implémentez la méthode `CChildView::OnPaint`. Cette méthode `CChildView::DrawMandelbrot` appelle puis copie `Bitmap` le contenu de l’objet à la fenêtre.

   [!code-cpp[concrt-mandelbrot#8](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_8.cpp)]

1. Vérifiez que l’application a été mise à jour avec succès en la construisant et en l’exécutant.

L’illustration suivante montre les résultats de l’application Mandelbrot.

![L'application Mandelbrot](../../parallel/concrt/media/mandelbrot.png "L'application Mandelbrot")

Parce que le calcul pour chaque pixel est computationnellement coûteux, le thread d’interface utilisateur ne peut pas traiter des messages supplémentaires jusqu’à ce que le calcul global se termine. Cela pourrait diminuer la réactivité dans l’application. Cependant, vous pouvez soulager ce problème en supprimant le travail du thread d’interface utilisateur.

[[Top](#top)]

## <a name="removing-work-from-the-ui-thread"></a><a name="removing-work"></a>Suppression du travail du fil d’assurance-chômage

Cette section montre comment supprimer le travail de dessin du fil d’interface utilisateur dans l’application Mandelbrot. En déplaçant le travail de dessin du fil d’interface utilisateur à un thread de travailleur, le thread d’interface utilisateur peut traiter des messages pendant que le thread de travail génère l’image en arrière-plan.

Le Concurrency Runtime offre trois façons d’exécuter des tâches: [les groupes de tâches](../../parallel/concrt/task-parallelism-concurrency-runtime.md), les agents [asynchrones](../../parallel/concrt/asynchronous-agents.md), et [les tâches légères](../../parallel/concrt/task-scheduler-concurrency-runtime.md). Bien que vous puissiez utiliser l’un de ces mécanismes pour supprimer le travail du thread d’interface utilisateur, cet exemple utilise une [concordance: ::task_group](reference/task-group-class.md) objet parce que les groupes de tâches prennent en charge l’annulation. Cette procédure pas à pas utilise plus tard l’annulation pour réduire la quantité de travail qui est effectuée lorsque la fenêtre du client est resized, et pour effectuer le nettoyage lorsque la fenêtre est détruite.

Cet exemple utilise également une [concordance : : unbounded_buffer](reference/unbounded-buffer-class.md) objet pour permettre au fil d’interface utilisateur et au fil de travail de communiquer entre eux. Après que le fil de travail produit `Bitmap` l’image, il envoie un pointeur à l’objet à l’objet, `unbounded_buffer` puis affiche un message de peinture sur le fil d’interface utilisateur. Le fil d’interface `unbounded_buffer` utilisateur `Bitmap` reçoit alors de l’objet l’objet et l’attire vers la fenêtre du client.

#### <a name="to-remove-the-drawing-work-from-the-ui-thread"></a>Pour supprimer le travail de dessin du fil d’interface utilisateur

1. Dans *pch.h* (*stdafx.h* dans Visual Studio 2017 et plus tôt), ajoutez les directives suivantes `#include` :

   [!code-cpp[concrt-mandelbrot#101](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_9.h)]

1. Dans ChildView.h, `task_group` `unbounded_buffer` ajoutez et `protected` ajoutez des `CChildView` variables de membre à la section de la classe. L’objet `task_group` détient les tâches qui effectuent le dessin; l’objet `unbounded_buffer` détient l’image mandelbrot terminée.

   [!code-cpp[concrt-mandelbrot#102](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_10.h)]

1. Dans ChildView.cpp, `using` ajoutez une `concurrency` directive à l’espace nom.

   [!code-cpp[concrt-mandelbrot#103](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_11.cpp)]

1. Dans `CChildView::DrawMandelbrot` la méthode, après `Bitmap::UnlockBits`l’appel à , appelez la [concurrence::envoyer](reference/concurrency-namespace-functions.md#send) la fonction pour passer l’objet `Bitmap` au thread d’interface utilisateur. Ensuite, affichez un message de peinture sur le thread d’interface utilisateur et invalidez la zone client.

   [!code-cpp[concrt-mandelbrot#104](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_12.cpp)]

1. Mettre `CChildView::OnPaint` à jour la `Bitmap` méthode pour recevoir l’objet mis à jour et dessiner l’image à la fenêtre du client.

   [!code-cpp[concrt-mandelbrot#105](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_13.cpp)]

   La `CChildView::OnPaint` méthode crée une tâche pour générer l’image Mandelbrot si l’on n’existe pas dans le tampon de message. Le tampon de message `Bitmap` ne contiendra pas un objet dans des cas tels que le message de peinture initial et quand une autre fenêtre est déplacée devant la fenêtre du client.

1. Vérifiez que l’application a été mise à jour avec succès en la construisant et en l’exécutant.

L’interface utilisateur est maintenant plus réactive car le travail de dessin est effectué en arrière-plan.

[[Top](#top)]

## <a name="improving-drawing-performance"></a><a name="performance"></a>Améliorer les performances de dessin

La génération de la fractale Mandelbrot est un bon candidat à la parallélisation car le calcul de chaque pixel est indépendant de tous les autres calculs. Pour paralliser la procédure `for` de dessin, convertir la boucle extérieure de la `CChildView::DrawMandelbrot` méthode en un appel à la [concurrence: :parallel pour l’algorithme,](reference/concurrency-namespace-functions.md#parallel_for) comme suit.

[!code-cpp[concrt-mandelbrot#301](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_14.cpp)]

Parce que le calcul de chaque élément bitmap est indépendant, vous n’avez pas à synchroniser les opérations de dessin qui accèdent à la mémoire de bitmap. Cela permet aux performances de s’étendre à mesure que le nombre de processeurs disponibles augmente.

[[Top](#top)]

## <a name="adding-support-for-cancellation"></a><a name="cancellation"></a>Ajout d’un support pour l’annulation

Cette section décrit comment gérer la resizing de fenêtre et comment annuler toutes les tâches de dessin actif lorsque la fenêtre est détruite.

Le document [Annulation dans la PPL](cancellation-in-the-ppl.md) explique comment fonctionne l’annulation dans le temps d’exécution. L’annulation est coopérative; par conséquent, il ne se produit pas immédiatement. Pour arrêter une tâche annulée, le temps d’exécution lance une exception interne au cours d’un appel ultérieur de la tâche dans le temps d’exécution. La section précédente montre `parallel_for` comment utiliser l’algorithme pour améliorer les performances de la tâche de dessin. L’appel `parallel_for` permet à l’heure d’exécution d’arrêter la tâche, et permet donc l’annulation de travailler.

### <a name="cancelling-active-tasks"></a>Annulation des tâches actives

L’application Mandelbrot crée des `Bitmap` objets dont les dimensions correspondent à la taille de la fenêtre client. Chaque fois que la fenêtre client est resized, l’application crée une tâche d’arrière-plan supplémentaire pour générer une image pour la nouvelle taille de fenêtre. L’application ne nécessite pas ces images intermédiaires; il ne nécessite que l’image pour la taille finale de la fenêtre. Pour empêcher l’application d’effectuer ce travail supplémentaire, vous pouvez annuler `WM_SIZE` `WM_SIZING` toutes les tâches de dessin actif dans les gestionnaires de messages pour les messages et puis reprogrammer le travail de dessin après la fenêtre est resized.

Pour annuler les tâches de dessin actif lorsque la fenêtre est resized, l’application appelle la [concordance::task_group::annuler](reference/task-group-class.md#cancel) la méthode dans les gestionnaires pour les `WM_SIZING` messages et les `WM_SIZE` messages. Le gestionnaire `WM_SIZE` du message appelle également la [concordance::task_group::méthode d’attente](reference/task-group-class.md#wait) pour attendre toutes les tâches actives pour terminer, puis reprogramme la tâche de dessin pour la taille de la fenêtre mise à jour.

Lorsque la fenêtre du client est détruite, il est de bonne pratique d’annuler toute tâche de dessin actif. L’annulation de toute tâche de dessin actif permet de s’assurer que les fils des travailleurs ne publient pas de messages sur le fil d’interface utilisateur après la destruction de la fenêtre du client. L’application annule toutes les tâches de `WM_DESTROY` dessin actif dans le gestionnaire pour le message.

### <a name="responding-to-cancellation"></a>Répondre à l’annulation

La `CChildView::DrawMandelbrot` méthode, qui effectue la tâche de dessin, doit répondre à l’annulation. Étant donné que le temps d’exécution utilise la manipulation des exceptions pour annuler les tâches, la `CChildView::DrawMandelbrot` méthode doit utiliser un mécanisme de sécurité d’exception pour garantir que toutes les ressources sont correctement nettoyées. Cet exemple utilise le modèle *d’acquisition de ressources est initialisation* (RAII) pour garantir que les bits de bitmap sont déverrouillés lorsque la tâche est annulée.

##### <a name="to-add-support-for-cancellation-in-the-mandelbrot-application"></a>Pour ajouter un support d’annulation dans l’application Mandelbrot

1. Dans ChildView.h, `protected` dans la `CChildView` section de la `OnSize`classe, ajouter des déclarations pour les fonctions de `OnSizing`carte de message et `OnDestroy` de message.

   [!code-cpp[concrt-mandelbrot#201](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_15.h)]

1. Dans ChildView.cpp, modifiez la carte de `WM_SIZE` `WM_SIZING`message `WM_DESTROY` pour contenir les gestionnaires pour le , , et les messages.

   [!code-cpp[concrt-mandelbrot#202](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_16.cpp)]

1. Implémentez la méthode `CChildView::OnSizing`. Cette méthode annule toutes les tâches de dessin existantes.

   [!code-cpp[concrt-mandelbrot#203](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_17.cpp)]

1. Implémentez la méthode `CChildView::OnSize`. Cette méthode annule toutes les tâches de dessin existantes et crée une nouvelle tâche de dessin pour la taille de fenêtre client mise à jour.

   [!code-cpp[concrt-mandelbrot#204](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_18.cpp)]

1. Implémentez la méthode `CChildView::OnDestroy`. Cette méthode annule toutes les tâches de dessin existantes.

   [!code-cpp[concrt-mandelbrot#205](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_19.cpp)]

1. Dans ChildView.cpp, `scope_guard` définissez la classe, qui met en œuvre le modèle RAII.

   [!code-cpp[concrt-mandelbrot#206](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_20.cpp)]

1. Ajoutez le code `CChildView::DrawMandelbrot` suivant à la `Bitmap::LockBits`méthode après l’appel à :

   [!code-cpp[concrt-mandelbrot#207](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_21.cpp)]

   Ce code gère l’annulation en créant un `scope_guard` objet. Lorsque l’objet quitte la portée, il déverrouille les bits de bitmap.

1. Modifier la fin `CChildView::DrawMandelbrot` de la `scope_guard` méthode pour rejeter l’objet après que les bits bitmap sont déverrouillés, mais avant que tous les messages sont envoyés au thread d’interface utilisateur. Cela garantit que le thread d’interface utilisateur n’est pas mis à jour avant que les bitmap bits sont déverrouillés.

   [!code-cpp[concrt-mandelbrot#208](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_22.cpp)]

1. Vérifiez que l’application a été mise à jour avec succès en la construisant et en l’exécutant.

Lorsque vous resize la fenêtre, le travail de dessin est effectué uniquement pour la taille finale de la fenêtre. Toutes les tâches de dessin actif sont également annulées lorsque la fenêtre est détruite.

[[Top](#top)]

## <a name="see-also"></a>Voir aussi

[Procédure pas à pas De Concurrency Runtime](../../parallel/concrt/concurrency-runtime-walkthroughs.md)<br/>
[Parallélisme des tâches](../../parallel/concrt/task-parallelism-concurrency-runtime.md)<br/>
[Blocs de messages asynchrones](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[Fonctions de passage de message](../../parallel/concrt/message-passing-functions.md)<br/>
[Algorithmes parallèles](../../parallel/concrt/parallel-algorithms.md)<br/>
[Annulation dans la bibliothèque de modèles parallèles](cancellation-in-the-ppl.md)<br/>
[MFC, applications de bureau](../../mfc/mfc-desktop-applications.md)
