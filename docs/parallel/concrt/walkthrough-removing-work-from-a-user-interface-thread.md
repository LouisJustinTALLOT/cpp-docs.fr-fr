---
title: 'Procédure pas à pas : Suppression de travail d’un Thread d’Interface utilisateur | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- user-interface threads, removing work from [Concurrency Runtime]
- removing work from user-interface threads [Concurrency Runtime]
ms.assetid: a4a65cc2-b3bc-4216-8fa8-90529491de02
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0502ce728c35b08d927cea48ee5b82756980aec5
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33694285"
---
# <a name="walkthrough-removing-work-from-a-user-interface-thread"></a>Procédure pas à pas : suppression de travail d'un thread d'interface utilisateur
Ce document montre comment utiliser le Runtime d’accès concurrentiel pour déplacer le travail effectué par le thread d’interface utilisateur (IU) dans une application Microsoft Foundation Classes (MFC) vers un thread de travail. Ce document montre également comment améliorer les performances d’une longue opération de dessin.  
  
 Suppression de travail à partir du thread d’interface utilisateur en déchargeant les opérations de blocage, par exemple, le dessin, threads de travail peut améliorer la réactivité de votre application. Cette procédure pas à pas utilise une routine de dessin qui génère une fractale de Mandelbrot pour illustrer une longue opération de blocage. La génération d’une fractale de Mandelbrot est également un bon candidat pour la parallélisation car le calcul de chaque pixel est indépendant de tous les autres calculs.  
  
## <a name="prerequisites"></a>Prérequis  
 Lisez les rubriques suivantes avant de commencer cette procédure pas à pas :  
  
-   [Parallélisme des tâches](../../parallel/concrt/task-parallelism-concurrency-runtime.md)  
  
-   [Blocs de messages asynchrones](../../parallel/concrt/asynchronous-message-blocks.md)  
  
-   [Fonctions de passage de messages](../../parallel/concrt/message-passing-functions.md)  
  
-   [Algorithmes parallèles](../../parallel/concrt/parallel-algorithms.md)  
  
-   [Annulation dans la bibliothèque de modèles parallèles](cancellation-in-the-ppl.md)  
  
 Nous vous recommandons également de que vous comprenez les notions de base du développement d’applications MFC et [!INCLUDE[ndptecgdiplus](../../parallel/concrt/includes/ndptecgdiplus_md.md)] avant de commencer cette procédure pas à pas. Pour plus d’informations à propos de MFC, consultez [Applications de bureau MFC](../../mfc/mfc-desktop-applications.md). Pour plus d’informations sur [!INCLUDE[ndptecgdiplus](../../parallel/concrt/includes/ndptecgdiplus_md.md)], consultez [GDI +](https://msdn.microsoft.com/en-us/library/windows/desktop/ms533798).  
  
##  <a name="top"></a> Sections  
 Cette procédure pas à pas contient les sections suivantes :  
  
-   [Création d’une Application MFC](#application)  
  
-   [Implémentation de la Version de l’Application Mandelbrot](#serial)  
  
-   [Suppression de travail à partir du Thread d’Interface utilisateur](#removing-work)  
  
-   [Amélioration des performances de dessin](#performance)  
  
-   [Ajout de la prise en charge l’annulation](#cancellation)  
  
##  <a name="application"></a> Création d’une Application MFC  
 Cette section décrit comment créer l’application MFC de base.  
  
### <a name="to-create-a-visual-c-mfc-application"></a>Pour créer une application MFC Visual C++  
  
1.  Dans le menu **Fichier** , cliquez sur **Nouveau**, puis sur **Projet**.  
  
2.  Dans le **nouveau projet** boîte de dialogue le **modèles installés** volet, sélectionnez **Visual C++**, puis, dans le **modèles** volet, sélectionnez **Application MFC**. Tapez un nom pour le projet, par exemple, `Mandelbrot`, puis cliquez sur **OK** pour afficher les **Assistant Application MFC**.  
  
3.  Dans le **Type d’Application** volet, sélectionnez **document unique**. Vérifiez que le **prise en charge d’architecture Document/vue** case à cocher est désactivée.  
  
4.  Cliquez sur **Terminer** pour créer le projet et fermer la **Assistant Application MFC**.  
  
     Vérifiez que l’application a été créée avec succès en générant et en l’exécutant. Pour générer l’application, dans le **générer** menu, cliquez sur **générer la Solution**. Si l’application est générée avec succès, exécutez-la en cliquant sur **démarrer le débogage** sur la **déboguer** menu.  
  
##  <a name="serial"></a> Implémentation de la Version de l’Application Mandelbrot  
 Cette section décrit comment dessiner une fractale de Mandelbrot. Cette version dessine la fractale de Mandelbrot dans un [!INCLUDE[ndptecgdiplus](../../parallel/concrt/includes/ndptecgdiplus_md.md)] [Bitmap](https://msdn.microsoft.com/library/ms534420.aspx) de l’objet, puis copie le contenu de cette bitmap dans la fenêtre cliente.  
  
#### <a name="to-implement-the-serial-version-of-the-mandelbrot-application"></a>Pour implémenter la version sérialisée de l’application Mandelbrot  
  
1.  Dans le fichier stdafx.h, ajoutez le code suivant `#include` directive :  
  
     [!code-cpp[concrt-mandelbrot#1](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_1.h)]  
  
2.  Dans ChildView.h, après la `pragma` directive, définir le `BitmapPtr` type. Le `BitmapPtr` type permet à un pointeur vers un `Bitmap` objet à être partagé par plusieurs composants. Le `Bitmap` objet est supprimé lorsqu’il n’est plus référencé par aucun composant.  
  
     [!code-cpp[concrt-mandelbrot#2](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_2.h)]  
  
3.  Dans ChildView.h, ajoutez le code suivant à la `protected` section de la `CChildView` classe :  
  
     [!code-cpp[concrt-mandelbrot#3](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_3.h)]  
  
4.  Dans ChildView.cpp, commentez ou supprimez les lignes suivantes.  
  
     [!code-cpp[concrt-mandelbrot#4](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_4.cpp)]  
  
     Dans les versions Debug, cette étape empêche l’application d’utiliser la `DEBUG_NEW` allocateur, qui n’est pas compatible avec [!INCLUDE[ndptecgdiplus](../../parallel/concrt/includes/ndptecgdiplus_md.md)].  
  
5.  Dans ChildView.cpp, ajoutez une `using` directive pour le `Gdiplus` espace de noms.  
  
     [!code-cpp[concrt-mandelbrot#5](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_5.cpp)]  
  
6.  Ajoutez le code suivant au constructeur et destructeur de la `CChildView` classe pour initialiser et arrêter [!INCLUDE[ndptecgdiplus](../../parallel/concrt/includes/ndptecgdiplus_md.md)].  
  
     [!code-cpp[concrt-mandelbrot#6](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_6.cpp)]  
  
7.  Implémentez la méthode `CChildView::DrawMandelbrot`. Cette méthode dessine la fractale de Mandelbrot spécifié `Bitmap` objet.  
  
     [!code-cpp[concrt-mandelbrot#7](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_7.cpp)]  
  
8.  Implémentez la méthode `CChildView::OnPaint`. Cette méthode appelle `CChildView::DrawMandelbrot` , puis copie le contenu de la `Bitmap` objet dans la fenêtre.  
  
     [!code-cpp[concrt-mandelbrot#8](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_8.cpp)]  
  
9. Vérifiez que l’application a été mis à jour avec succès en générant et en l’exécutant.  
  
 L’illustration suivante montre les résultats de l’application Mandelbrot.  
  
 ![L’Application Mandelbrot](../../parallel/concrt/media/mandelbrot.png "mandelbrot")  
  
 Étant donné que le calcul de chaque pixel est gourmand, le thread d’interface utilisateur ne peut pas traiter les messages supplémentaires jusqu'à ce que le calcul global se termine. Cela peut réduire les temps de réponse dans l’application. Toutefois, vous pouvez atténuer ce problème en supprimant du travail à partir du thread d’interface utilisateur.  
  
 [[Haut](#top)]  
  
##  <a name="removing-work"></a> Suppression de travail à partir du Thread d’interface utilisateur  
 Cette section montre comment supprimer le travail de dessin à partir du thread d’interface utilisateur dans l’application Mandelbrot. En déplaçant le travail de dessin à partir du thread d’interface utilisateur à un thread de travail, le thread d’interface utilisateur peut traiter les messages que le thread de travail génère l’image en arrière-plan.  
  
 Le Runtime d’accès concurrentiel fournit trois méthodes pour exécuter des tâches : [groupes de tâches](../../parallel/concrt/task-parallelism-concurrency-runtime.md), [agents asynchrones](../../parallel/concrt/asynchronous-agents.md), et [tâches légères](../../parallel/concrt/task-scheduler-concurrency-runtime.md). Vous pouvez utiliser l’un de ces mécanismes pour supprimer du travail à partir du thread d’interface utilisateur, cet exemple utilise un [concurrency::task_group](reference/task-group-class.md) , car les groupes de tâches prennent en charge l’annulation de l’objet. Cette procédure pas à pas utilise ensuite l’annulation pour réduire la quantité de travail qui est effectuée lors du redimensionnement de la fenêtre du client et effectuer un nettoyage lorsque la fenêtre est détruite.  
  
 Cet exemple utilise également un [concurrency::unbounded_buffer](reference/unbounded-buffer-class.md) objet afin de permettre le thread d’interface utilisateur et le thread de travail pour communiquer entre eux. Une fois que le thread de travail génère l’image, il envoie un pointeur vers le `Bitmap` de l’objet à le `unbounded_buffer` de l’objet et puis envoie un message de peinture au thread d’interface utilisateur. Le thread d’interface utilisateur reçoit le `unbounded_buffer` objet la `Bitmap` de l’objet et dessine dans la fenêtre du client.  
  
#### <a name="to-remove-the-drawing-work-from-the-ui-thread"></a>Pour supprimer du travail de dessin à partir du thread d’interface utilisateur  
  
1.  Dans le fichier stdafx.h, ajoutez le code suivant `#include` directives :  
  
     [!code-cpp[concrt-mandelbrot#101](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_9.h)]  
  
2.  Dans ChildView.h, ajoutez `task_group` et `unbounded_buffer` variables membres pour le `protected` section de la `CChildView` classe. Le `task_group` objet conserve les tâches qui exécutent le dessin ; le `unbounded_buffer` objet contient l’image Mandelbrot terminée.  
  
     [!code-cpp[concrt-mandelbrot#102](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_10.h)]  
  
3.  Dans ChildView.cpp, ajoutez une `using` directive pour le `concurrency` espace de noms.  
  
     [!code-cpp[concrt-mandelbrot#103](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_11.cpp)]  
  

4.  Dans le `CChildView::DrawMandelbrot` (méthode), après l’appel à `Bitmap::UnlockBits`, appeler le [concurrency::send](reference/concurrency-namespace-functions.md#send) fonction pour passer le `Bitmap` objet pour le thread d’interface utilisateur. Publier un message de peinture au thread d’interface utilisateur, puis invalide la zone cliente.  

  
     [!code-cpp[concrt-mandelbrot#104](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_12.cpp)]  
  
5.  Mise à jour la `CChildView::OnPaint` méthode pour recevoir les mises à jour `Bitmap` de l’objet et dessiner l’image dans la fenêtre du client.  
  
     [!code-cpp[concrt-mandelbrot#105](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_13.cpp)]  
  
     Le `CChildView::OnPaint` méthode crée une tâche pour générer l’image Mandelbrot si une n’existe pas dans le tampon de messages. Le tampon de messages ne contient pas un `Bitmap` objet dans les cas tels que le message de peinture initial et lorsqu’une autre fenêtre est déplacée devant la fenêtre du client.  
  
6.  Vérifiez que l’application a été mis à jour avec succès en générant et en l’exécutant.  
  
 L’interface utilisateur est maintenant plus réactive, car le travail de dessin est effectué en arrière-plan.  
  
 [[Haut](#top)]  
  
##  <a name="performance"></a> Amélioration des performances de dessin  

 La génération d’une fractale de Mandelbrot est un bon candidat pour la parallélisation car le calcul de chaque pixel est indépendant de tous les autres calculs. Pour paralléliser la procédure de dessin, convertir externe `for` boucle dans le `CChildView::DrawMandelbrot` (méthode) à un appel à la [concurrency::parallel_for](reference/concurrency-namespace-functions.md#parallel_for) algorithme, comme suit.  

  
 [!code-cpp[concrt-mandelbrot#301](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_14.cpp)]  
  
 Étant donné que le calcul de chaque élément de bitmap est indépendant, il est inutile synchroniser les opérations de dessin qui accèdent à la mémoire de l’image bitmap. Cela permet aux performances à l’échelle en tant que le nombre de processeurs disponibles augmente.  
  
 [[Haut](#top)]  
  
##  <a name="cancellation"></a> Ajout de la prise en charge l’annulation  
 Cette section décrit comment gérer le redimensionnement de fenêtre et comment annuler toutes les tâches de dessin actives lorsque la fenêtre est détruite.  
  
 Le document [l’annulation dans la bibliothèque PPL](cancellation-in-the-ppl.md) explique le fonctionne de l’annulation dans le runtime. L’annulation est coopérative ; Par conséquent, il ne se produit pas immédiatement. Pour arrêter une tâche annulée, le runtime lève une exception interne pendant un appel ultérieur à partir de la tâche dans le runtime. La section précédente montre comment utiliser le `parallel_for` algorithme pour améliorer les performances de la tâche de dessin. L’appel à `parallel_for` permet à l’exécution d’arrêter la tâche et par conséquent, l’annulation de fonctionner.  
  
### <a name="cancelling-active-tasks"></a>L’annulation de tâches actives  
 L’application Mandelbrot crée `Bitmap` objets dont les dimensions correspondent à la taille de la fenêtre du client. Chaque fois que la fenêtre cliente est redimensionnée, l’application crée une tâche supplémentaire en arrière-plan pour générer une image pour la nouvelle taille de fenêtre. L’application ne requiert pas ces images intermédiaires ; Il nécessite uniquement l’image pour la taille de fenêtre finale. Pour empêcher l’application d’exécuter ce travail supplémentaire, vous pouvez annuler toutes les tâches de dessin actives dans les gestionnaires de messages pour le `WM_SIZE` et `WM_SIZING` puis replanifiez dessin et les messages de travail une fois que la fenêtre est redimensionnée.  
  
 Pour annuler les tâches de dessin actives lorsque la fenêtre est redimensionnée, l’application appelle la [Concurrency::task_group :: Cancel](reference/task-group-class.md#cancel) méthode dans les gestionnaires pour les `WM_SIZING` et `WM_SIZE` messages. Le gestionnaire pour le `WM_SIZE` message également les appels le [Concurrency::task_group :: wait](reference/task-group-class.md#wait) méthode pour attendre que toutes les tâches à effectuer et puis replanifie la tâche de dessin pour la taille de la fenêtre mise à jour.  
  
 Lorsque la fenêtre du client est détruite, il est conseillé d’annuler toutes les tâches de dessin actives. L’annulation de toutes les tâches de dessin actives permet de s’assurer que les threads de travail ne validez pas de messages vers le thread d’interface utilisateur après la destruction de la fenêtre du client. L’application annule toutes les tâches de dessin actives dans le Gestionnaire de la `WM_DESTROY` message.  
  
### <a name="responding-to-cancellation"></a>Répondre à l’annulation  
 Le `CChildView::DrawMandelbrot` (méthode), qui effectue la tâche de dessin, doit répondre à l’annulation. Étant donné que le runtime utilise la gestion des exceptions pour annuler des tâches, le `CChildView::DrawMandelbrot` méthode doit utiliser un mécanisme sécurisé de l’exception afin de garantir que toutes les ressources sont correctement nettoyées. Cet exemple utilise le *Resource Acquisition Is Initialization* modèle (RAII) pour garantir que les bits de la bitmap soient déverrouillés lorsque la tâche est annulée.  
  
##### <a name="to-add-support-for-cancellation-in-the-mandelbrot-application"></a>Pour ajouter la prise en charge l’annulation de l’application Mandelbrot  
  
1.  Dans ChildView.h, dans le `protected` section de la `CChildView` de classe, ajoutez des déclarations pour les `OnSize`, `OnSizing`, et `OnDestroy` des fonctions de mappage de message.  
  
     [!code-cpp[concrt-mandelbrot#201](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_15.h)]  
  
2.  Dans ChildView.cpp, modifiez la table des messages pour qu’il contienne des gestionnaires pour les `WM_SIZE`, `WM_SIZING`, et `WM_DESTROY` messages.  
  
     [!code-cpp[concrt-mandelbrot#202](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_16.cpp)]  
  
3.  Implémentez la méthode `CChildView::OnSizing`. Cette méthode annule toutes les tâches de dessin existantes.  
  
     [!code-cpp[concrt-mandelbrot#203](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_17.cpp)]  
  
4.  Implémentez la méthode `CChildView::OnSize`. Cette méthode annule toutes les tâches de dessin existantes et crée une nouvelle tâche de dessin pour la taille de fenêtre du client mis à jour.  
  
     [!code-cpp[concrt-mandelbrot#204](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_18.cpp)]  
  
5.  Implémentez la méthode `CChildView::OnDestroy`. Cette méthode annule toutes les tâches de dessin existantes.  
  
     [!code-cpp[concrt-mandelbrot#205](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_19.cpp)]  
  
6.  Dans ChildView.cpp, définissez la `scope_guard` classe qui implémente le modèle RAII.  
  
     [!code-cpp[concrt-mandelbrot#206](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_20.cpp)]  
  
7.  Ajoutez le code suivant à la `CChildView::DrawMandelbrot` méthode après l’appel à `Bitmap::LockBits`:  
  
     [!code-cpp[concrt-mandelbrot#207](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_21.cpp)]  
  
     Ce code gère l’annulation en créant un `scope_guard` objet. Lorsque l’objet hors de portée, il déverrouille les bits de la bitmap.  
  
8.  Modifiez la fin de la `CChildView::DrawMandelbrot` méthode pour fermer le `scope_guard` une fois les bits de la bitmap déverrouillés, mais avant que tous les messages sont envoyés vers le thread d’interface utilisateur de l’objet. Cela garantit que le thread d’interface utilisateur n’est pas mis à jour avant que les bits du bitmap sont déverrouillées.  
  
     [!code-cpp[concrt-mandelbrot#208](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_22.cpp)]  
  
9. Vérifiez que l’application a été mis à jour avec succès en générant et en l’exécutant.  
  
 Lorsque vous redimensionnez la fenêtre, travail de dessin est effectué uniquement pour la taille de fenêtre finale. Toutes les tâches de dessin actives sont également annulées lorsque la fenêtre est détruite.  
  
 [[Haut](#top)]  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures pas à pas Runtime d’accès concurrentiel](../../parallel/concrt/concurrency-runtime-walkthroughs.md)   
 [Parallélisme des tâches](../../parallel/concrt/task-parallelism-concurrency-runtime.md)   
 [Blocs de messages asynchrones](../../parallel/concrt/asynchronous-message-blocks.md)   
 [Fonctions de passage de messages](../../parallel/concrt/message-passing-functions.md)   
 [Algorithmes parallèles](../../parallel/concrt/parallel-algorithms.md)   
 [Annulation dans la bibliothèque de modèles parallèles](cancellation-in-the-ppl.md)   
 [MFC, applications de bureau](../../mfc/mfc-desktop-applications.md)
