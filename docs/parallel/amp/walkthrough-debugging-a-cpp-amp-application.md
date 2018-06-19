---
title: 'Procédure pas à pas : Débogage d’une Application C++ AMP | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-amp
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- debugging, C++ Accelerated Massive Parallelism
- C++ AMP, debugging
- C++ Accelerated Massive Parallelism, debugging
- debugging, C++ AMP
ms.assetid: 40e92ecc-f6ba-411c-960c-b3047b854fb5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1bf80276b5434804651bcc4507397e9479f6e494
ms.sourcegitcommit: da7b7533d1a4dc141cc0f09149e4e4196f2fe329
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2018
ms.locfileid: "34463090"
---
# <a name="walkthrough-debugging-a-c-amp-application"></a>Procédure pas-à-pas : débogage d’une application C++ AMP
Cette rubrique montre comment déboguer une application qui utilise C++ Accelerated les Massive Parallelism (C++ AMP) pour tirer parti de l’unité de traitement graphique (GPU). Il utilise un programme de réduction parallèle qui additionne un grand tableau d’entiers. Cette procédure pas à pas décrit les tâches suivantes :  
  
-   Lancer le débogueur GPU.  
  
-   Inspection des threads GPU dans la fenêtre Threads GPU.  
  
-   À l’aide de la fenêtre Piles parallèles pour simultanément observer les piles d’appels de plusieurs threads GPU.  
  
-   À l’aide de la fenêtre Espion parallèle pour inspecter des valeurs d’une expression unique entre plusieurs threads en même temps.  
  
-   Marquage, gel, libération et regroupement des threads GPU.  
  
-   L’exécution de tous les threads d’une vignette à un emplacement spécifique dans le code.  
  
## <a name="prerequisites"></a>Prérequis  
 Avant de commencer cette procédure pas à pas :  
  
-   Lecture [présentation de C++ AMP](../../parallel/amp/cpp-amp-overview.md).  
  
-   Assurez-vous que cette ligne de nombres sont affichés dans l’éditeur de texte. Pour plus d’informations, consultez [Comment : afficher les numéros de ligne dans l’éditeur](/visualstudio/ide/reference/how-to-display-line-numbers-in-the-editor).  
  
-   Assurez-vous que vous exécutez [!INCLUDE[win8](../../build/reference/includes/win8_md.md)] ou [!INCLUDE[winserver8](../../build/reference/includes/winserver8_md.md)] pour prendre en charge le débogage sur l’émulateur de logiciel.  
  
 [!INCLUDE[note_settings_general](../../mfc/includes/note_settings_general_md.md)]  
  
### <a name="to-create-the-sample-project"></a>Pour créer l'exemple de projet  
  
1.  Démarrez Visual Studio.  
  
2.  Dans la barre de menus, sélectionnez **Fichier**, **Nouveau**, **Projet**.  
  
3.  Sous **installé** dans le volet Modèles, choisissez **Visual C++**.  
  
4.  Choisissez **Application Console Win32**, type `AMPMapReduce` dans les **nom** zone, puis choisissez le **OK** bouton.  
  
5.  Choisissez le bouton **Suivant**.  
  
6.  Désactivez le **d’en-tête précompilé** case à cocher, puis choisissez le **Terminer** bouton.  
  
7.  Dans **l’Explorateur de solutions**, supprimer stdafx.h, targetver.h et stdafx.cpp à partir du projet.  
  
8.  Ouvrez AMPMapReduce.cpp et remplacer son contenu par le code suivant.  
  
 ```cpp  
    // AMPMapReduce.cpp defines the entry point for the program.  
    // The program performs a parallel-sum reduction that computes the sum of an array of integers.   
  
    #include <stdio.h>  
    #include <tchar.h>  
    #include <amp.h>  
  
    const int BLOCK_DIM = 32;  
  
    using namespace concurrency;  
  
    void sum_kernel_tiled(tiled_index<BLOCK_DIM> t_idx, array<int, 1> &A, int stride_size) restrict(amp)  
    {  
        tile_static int localA[BLOCK_DIM];  
  
        index<1> globalIdx = t_idx.global * stride_size;  
        index<1> localIdx = t_idx.local;  
  
        localA[localIdx[0]] =  A[globalIdx];  
  
        t_idx.barrier.wait();  
  
        // Aggregate all elements in one tile into the first element.  
        for (int i = BLOCK_DIM / 2; i > 0; i /= 2)   
        {  
            if (localIdx[0] < i)   
            {  
  
                localA[localIdx[0]] += localA[localIdx[0] + i];  
            }  
  
            t_idx.barrier.wait();  
        }  
  
        if (localIdx[0] == 0)  
        {  
            A[globalIdx] = localA[0];  
        }  
    }  
  
    int size_after_padding(int n)  
    {  
        // The extent might have to be slightly bigger than num_stride to   
        // be evenly divisible by BLOCK_DIM. You can do this by padding with zeros.  
        // The calculation to do this is BLOCK_DIM * ceil(n / BLOCK_DIM)  
        return ((n - 1) / BLOCK_DIM + 1) * BLOCK_DIM;  
    }  
  
    int reduction_sum_gpu_kernel(array<int, 1> input)   
    {  
        int len = input.extent[0];  
  
        //Tree-based reduction control that uses the CPU.  
        for (int stride_size = 1; stride_size < len; stride_size *= BLOCK_DIM)   
        {  
            // Number of useful values in the array, given the current  
            // stride size.  
            int num_strides = len / stride_size;    
  
            extent<1> e(size_after_padding(num_strides));  
  
            // The sum kernel that uses the GPU.  
            parallel_for_each(extent<1>(e).tile<BLOCK_DIM>(), [&input, stride_size] (tiled_index<BLOCK_DIM> idx) restrict(amp)  
            {  
                sum_kernel_tiled(idx, input, stride_size);  
            });  
        }  
  
        array_view<int, 1> output = input.section(extent<1>(1));  
        return output[0];  
    }  
  
    int cpu_sum(const std::vector<int> &arr) {  
        int sum = 0;  
        for (size_t i = 0; i < arr.size(); i++) {  
            sum += arr[i];  
        }  
        return sum;  
    }  
  
    std::vector<int> rand_vector(unsigned int size) {  
        srand(2011);  
  
        std::vector<int> vec(size);  
        for (size_t i = 0; i < size; i++) {  
            vec[i] = rand();  
        }  
        return vec;  
    }  
  
    array<int, 1> vector_to_array(const std::vector<int> &vec) {  
        array<int, 1> arr(vec.size());  
        copy(vec.begin(), vec.end(), arr);  
        return arr;  
    }  
  
    int _tmain(int argc, _TCHAR* argv[])  
    {  
        std::vector<int> vec = rand_vector(10000);  
        array<int, 1> arr = vector_to_array(vec);  
  
        int expected = cpu_sum(vec);  
        int actual = reduction_sum_gpu_kernel(arr);  
  
        bool passed = (expected == actual);  
        if (!passed) {  
            printf("Actual (GPU): %d, Expected (CPU): %d", actual, expected);  
        }  
        printf("sum: %s\n", passed  "Passed!" : "Failed!");   
  
        getchar();  
  
        return 0;  
    }  
  
 ```  
  
9. Dans la barre de menus, sélectionnez **Fichier**, **Enregistrer tout**.  
  
10. Dans **l’Explorateur de solutions**, ouvrez le menu contextuel pour **AMPMapReduce**, puis choisissez **propriétés**.  
  
11. Dans le **Pages de propriétés** boîte de dialogue **propriétés de Configuration**, choisissez **C/C++**, **les en-têtes précompilés**.  
  
12. Pour le **d’un en-tête précompilé** propriété, sélectionnez **pas utiliser les en-têtes précompilés**, puis choisissez le **OK** bouton.  
  
13. Dans la barre de menus, choisissez **Générer**, puis **Générer la solution**.  
  
## <a name="debugging-the-cpu-code"></a>Débogage du Code de l’UC  
 Dans cette procédure, vous utiliserez le débogueur Windows Local pour vous assurer que le code de l’UC dans cette application est correct. Le segment du code de l’UC dans cette application est particulièrement intéressant est la `for` boucle dans le `reduction_sum_gpu_kernel` (fonction). Elle contrôle la réduction parallèle basé sur l’arborescence qui est exécutée sur le GPU.  
  
### <a name="to-debug-the-cpu-code"></a>Pour déboguer le code de l’UC  
  
1.  Dans **l’Explorateur de solutions**, ouvrez le menu contextuel pour **AMPMapReduce**, puis choisissez **propriétés**.  
  
2.  Dans le **Pages de propriétés** boîte de dialogue **propriétés de Configuration**, choisissez **débogage**. Vérifiez que **débogueur Windows Local** est sélectionné dans le **débogueur à lancer** liste.  
  
3.  Revenir à l’éditeur de Code.  
  
4.  Définir des points d’arrêt sur les lignes de code indiqué dans l’illustration suivante (environ lignes 67 de ligne 70).  
  
     ![Points d’arrêt de l’UC](../../parallel/amp/media/campcpubreakpoints.png "campcpubreakpoints")  
Points d'arrêt d'UC  
  
5.  Dans la barre de menus, choisissez **Débogage**, puis **Démarrer le débogage**.  
  
6.  Dans le **variables locales** fenêtre, observez la valeur de `stride_size` jusqu'à ce que le point d’arrêt à la ligne 70 est atteint.  
  
7.  Dans la barre de menus, choisissez **Débogage**, **Arrêter le débogage**.  
  
## <a name="debugging-the-gpu-code"></a>Débogage du Code GPU  
 Cette section montre comment déboguer le code GPU, qui est le code contenu dans le `sum_kernel_tiled` (fonction). Le code GPU calcule la somme des entiers pour chaque « bloc » en parallèle.  
  
### <a name="to-debug-the-gpu-code"></a>Pour déboguer le code GPU  
  
1.  Dans **l’Explorateur de solutions**, ouvrez le menu contextuel pour **AMPMapReduce**, puis choisissez **propriétés**.  
  
2.  Dans le **Pages de propriétés** boîte de dialogue **propriétés de Configuration**, choisissez **débogage**.  
  
3.  Dans le **débogueur à lancer** liste, sélectionnez **débogueur Windows Local**.  
  
4.  Dans le **Type de débogueur** liste, vérifiez que **automatique** est sélectionnée.

    **Auto** est la valeur par défaut. Avant Windows 10, **GPU uniquement** est la valeur requise à la place de **automatique**.
  
5.  Sélectionnez le bouton **OK** .  
  
6.  Définissez un point d’arrêt à la ligne 30, comme indiqué dans l’illustration suivante.  
  
     ![Points d’arrêt GPU](../../parallel/amp/media/campgpubreakpoints.png "campgpubreakpoints")  
Point d’arrêt GPU  
  
7.  Dans la barre de menus, choisissez **Débogage**, puis **Démarrer le débogage**. Les points d’arrêt dans le code de l’UC au niveau des lignes 67 et 70 ne sont pas exécutées au cours de débogage, car ces lignes de code sont exécutées sur le processeur GPU.  
  
### <a name="to-use-the-gpu-threads-window"></a>Pour utiliser la fenêtre Threads GPU  
  
1.  Pour ouvrir la fenêtre Threads GPU, dans la barre de menus, choisissez **déboguer**, **Windows**, **Threads GPU**.  
  
     Vous pouvez examiner l’état de threads GPU dans la fenêtre Threads GPU qui s’affiche.  
  
2.  Ancrez la fenêtre Threads GPU en bas de Visual Studio. Choisissez le **développer une commutation de threads** bouton pour afficher les zones de texte de mosaïque et un thread. La fenêtre Threads GPU affiche le nombre total de threads GPU actifs et bloqués, comme indiqué dans l’illustration suivante.  
  
     ![Fenêtre Threads GPU avec 4 threads actifs](../../parallel/amp/media/campc.png "campc")  
Fenêtre Threads GPU  
  
     Il existe des 313 vignettes alloués pour ce calcul. Chaque mosaïque contient 32 threads. Étant donné que le débogage GPU local se produit sur un émulateur de logiciel, il existe quatre threads GPU actifs. Les quatre threads exécutent les instructions simultanément et passez conjointement à l’instruction suivante.  
  
     Dans la fenêtre threads GPU, il existe quatre threads GPU active et 28 threads GPU bloquée au niveau du [tile_barrier::wait](reference/tile-barrier-class.md#wait) instruction définie à sur ligne 21 (`t_idx.barrier.wait();`). Tous les threads GPU 32 appartiennent à la première vignette `tile[0]`. Une flèche pointe vers la ligne qui inclut le thread actuel. Pour basculer vers un autre thread, utilisez une des méthodes suivantes :  

  
    -   Dans la ligne pour le thread de basculer dans la fenêtre Threads GPU, ouvrez le menu contextuel et choisissez **basculer vers le Thread**. Si la ligne représente plusieurs threads, vous allez utiliser le premier thread selon les coordonnées du thread.  
  
    -   Entrez les valeurs de mosaïque et un thread du thread dans les zones de texte correspondante, puis choisissez le **commutateur Thread** bouton.  
  
     La fenêtre Pile des appels affiche la pile des appels du thread GPU actuel.  
  
### <a name="to-use-the-parallel-stacks-window"></a>Pour utiliser la fenêtre Piles parallèles  
  
1.  Pour ouvrir la fenêtre Piles parallèles, dans la barre de menus, choisissez **déboguer**, **Windows**, **piles parallèles**.  
  
     Vous pouvez utiliser la fenêtre Piles parallèles simultanément inspecter les frames de pile de plusieurs threads GPU.  
  
2.  Ancrez la fenêtre Piles parallèles en bas de Visual Studio.  
  
3.  Assurez-vous que **Threads** est sélectionné dans la liste dans le coin supérieur gauche. Dans l’illustration suivante, la fenêtre Piles parallèles affiche une vue de la pile des appels axée sur des threads GPU que vous avez vu dans la fenêtre Threads GPU.  
  
     ![Fenêtre Piles parallèles avec 4 threads actifs](../../parallel/amp/media/campd.png "campd")  
Fenêtre Piles parallèles  
  
     32 threads est passé de `_kernel_stub` à l’instruction d’expression lambda dans le `parallel_for_each` l’appel de fonction et, en le `sum_kernel_tiled` fonction, où se produit la réduction en parallèle. 28 hors 32 threads ont depuis progressé à la [tile_barrier::wait](reference/tile-barrier-class.md#wait) instruction et reste bloqué à la ligne 22, tandis que les autres 4 threads restent actifs dans le `sum_kernel_tiled` fonction à la ligne 30.  

  
     Vous pouvez examiner les propriétés d’un thread GPU qui sont disponibles dans la fenêtre Threads GPU dans le DataTip riche de la fenêtre Piles parallèles. Pour ce faire, placez le pointeur de la souris sur le frame de pile **sum_kernel_tiled**. L’illustration suivante montre le DataTip.  
  
     ![DataTip pour la fenêtre Piles parallèles](../../parallel/amp/media/campe.png "campe")  
Thread GPU DataTip  
  
     Pour plus d’informations sur la fenêtre Piles parallèles, consultez [à l’aide de la fenêtre Piles parallèles](/visualstudio/debugger/using-the-parallel-stacks-window).  
  
### <a name="to-use-the-parallel-watch-window"></a>Pour utiliser la fenêtre Espion parallèle  
  
1.  Pour ouvrir la fenêtre Espion parallèle, sur la barre de menus, choisissez **déboguer**, **Windows**, **espion parallèle**, **espion parallèle 1**.  
  
     Vous pouvez utiliser la fenêtre Espion parallèle pour inspecter les valeurs d’une expression entre plusieurs threads.  
  
2.  Ancrer la fenêtre Espion parallèle 1 vers le bas de Visual Studio. Il existe 32 lignes dans la table de la fenêtre Espion parallèle. Chacun correspond à un thread GPU qui apparaît dans la fenêtre Threads GPU et de la fenêtre Piles parallèles. Maintenant, vous pouvez entrer des expressions dont les valeurs à inspecter sur tous les threads GPU 32.  
  
3.  Sélectionnez le **ajouter un espion** en-tête de colonne, entrez `localIdx`, puis appuyez sur ENTRÉE.  
  
4.  Sélectionnez le **ajouter un espion** à nouveau les en-tête de colonne, tapez `globalIdx`, puis appuyez sur ENTRÉE.  
  
5.  Sélectionnez le **ajouter un espion** à nouveau les en-tête de colonne, tapez `localA[localIdx[0]]`, puis appuyez sur ENTRÉE.  
  
     Vous pouvez trier par une expression spécifiée en sélectionnant l’en-tête de colonne correspondant.  
  
     Sélectionnez le **localA [localIdx [0]]** en-tête de colonne pour trier la colonne. L’illustration suivante montre les résultats sont triés par **localA [localIdx [0]]**.  
  
     ![Fenêtre Espion parallèle avec les résultats triés](../../parallel/amp/media/campf.png "campf")  
 Résultats du tri  
  
     Vous pouvez exporter le contenu de la fenêtre Espion parallèle vers Excel en cliquant sur le bouton Excel, puis en choisissant **ouvrir dans Excel**. Si vous avez installé Excel sur votre ordinateur de développement, une feuille de calcul Excel qui contient le contenu s’ouvre.  
  
6.  Dans le coin supérieur droit de la fenêtre Espion parallèle, il existe un contrôle de filtre que vous pouvez utiliser pour filtrer le contenu à l’aide d’expressions booléennes. Entrée `localA[localIdx[0]] > 20000` dans le texte du contrôle filtre zone, puis choisissez la touche ENTRÉE.  
  
     La fenêtre contient désormais uniquement les threads sur lesquels le `localA[localIdx[0]]` valeur est supérieure à 20000. Le contenu est toujours trié par la `localA[localIdx[0]]` colonne, qui est l’action de tri que vous avez déjà effectué.  
  
## <a name="flagging-gpu-threads"></a>Marquage des Threads GPU  
 Vous pouvez marquer des threads GPU spécifiques en leur attribuant un indicateur dans la fenêtre Threads GPU, la fenêtre Espion parallèle ou le DataTip dans la fenêtre Piles parallèles. Si une ligne dans la fenêtre Threads GPU contient plusieurs threads, marquer cette ligne signale tous les threads sont contenus dans la ligne.  
  
### <a name="to-flag-gpu-threads"></a>Pour signaler des threads GPU  
  
1.  Sélectionnez le **[Thread]** en-tête de colonne dans la fenêtre Espion parallèle 1 pour trier par index de mosaïque et de l’index de thread.  
  
2.  Dans la barre de menus, choisissez **déboguer**, **continuer**, ce qui entraîne les quatre threads qui étaient actives à la progression de la barrière suivante (définie à la ligne 32 du AMPMapReduce.cpp).  
  
3.  Sur le côté gauche de la ligne qui contient les quatre threads sont actifs, sélectionnez l’indicateur.  
  
     L’illustration suivante montre les quatre threads avec indicateur actives dans la fenêtre Threads GPU.  
  
     ![Fenêtre Threads GPU avec threads avec indicateur](../../parallel/amp/media/campg.png "campg")  
Threads actifs dans la fenêtre Threads GPU  
  
     La fenêtre Espion parallèle et le DataTip de la fenêtre Piles parallèles à la fois indiquent les threads avec indicateur.  
  
4.  Si vous souhaitez vous concentrer sur les quatre threads avec indicateur, vous pouvez choisir d’afficher, dans les Threads GPU, Espion parallèle et piles parallèles windows, uniquement les threads avec indicateur.  
  
     Choisissez l’afficher uniquement avec indicateur bouton sur n’importe quel de windows ou sur le **emplacement de débogage** barre d’outils. L’illustration suivante montre le bouton Afficher uniquement avec indicateur sur le **emplacement de débogage** barre d’outils.  
  
     ![Barre d’outils emplacement avec une icône d’afficher uniquement avec indicateur débogage](../../parallel/amp/media/camph.png "camph")  
Bouton Afficher uniquement les threads avec indicateur  
  
     Maintenant, les fenêtres Threads GPU, Espion parallèles et piles parallèles affichent uniquement les threads avec indicateur.  
  
## <a name="freezing-and-thawing-gpu-threads"></a>Gel et libération des Threads GPU  
 Vous pouvez figer (suspendre) et libérer (reprendre) les threads GPU à partir de la fenêtre Threads GPU ou la fenêtre Espion parallèle. Vous pouvez figer et libérer les threads de l’UC de la même façon ; Pour plus d’informations, consultez [Comment : utiliser la fenêtre Threads](/visualstudio/debugger/how-to-use-the-threads-window).  
  
### <a name="to-freeze-and-thaw-gpu-threads"></a>Pour figer et dégeler les threads GPU  
  
1.  Choisissez le **afficher uniquement avec indicateur** bouton pour afficher tous les threads.  
  
2.  Dans la barre de menus, choisissez **déboguer**, **continuer**.  
  
3.  Ouvrez le menu contextuel pour la ligne active, puis sélectionnez **Figer**.  
  
     L’illustration suivante de la fenêtre Threads GPU indique que toutes les quatre threads sont figés.  
  
     ![Fenêtres Threads GPU indiquant les threads figés](../../parallel/amp/media/campk.png "campk")  
Threads figés dans la fenêtre Threads GPU  
  
     De même, la fenêtre Espion parallèle indique que toutes les quatre threads sont figés.  
  
4.  Dans la barre de menus, choisissez **déboguer**, **continuer** pour autoriser les quatre threads GPU progression après le cloisonnement à la ligne 22 et d’atteindre le point d’arrêt à la ligne 30. La fenêtre Threads GPU indique que les quatre threads précédemment figées restent figé et dans l’état actif.  
  
5.  Dans la barre de menus, choisissez **déboguer**, **continuer**.  
  
6.  Dans la fenêtre Espion parallèle, vous pouvez également libérer individuels ou plusieurs threads GPU.  
  
### <a name="to-group-gpu-threads"></a>Pour regrouper des threads GPU  
  
1.  Dans le menu contextuel pour un des threads dans le **Threads GPU** fenêtre, choisissez **Group By**, **adresse**.  
  
     Les threads dans la fenêtre Threads GPU sont regroupées par adresse. L’adresse correspond à l’instruction dans le code machine où chaque groupe de threads est localisé. 24 threads sont à la ligne 22 où le [tile_barrier::wait, méthode](reference/tile-barrier-class.md#wait) est exécutée. 12 threads sont à l’instruction de la barrière à la ligne 32. Quatre de ces threads sont signalées. Huit threads sont sur le point d’arrêt à la ligne 30. Quatre de ces threads sont figés. L’illustration suivante montre les threads groupés dans la fenêtre Threads GPU.  

  
     ![Fenêtre Threads GPU avec threads groupés par adresse](../../parallel/amp/media/campl.png "campl")  
Threads regroupés dans la fenêtre Threads GPU  
  
2.  Vous pouvez également effectuer la **Group By** opération en ouvrant le menu contextuel de la grille de données de la fenêtre Espion parallèle, en choisissant **Group By**, puis en choisissant l’élément de menu qui correspond à la façon dont vous souhaitez que pour regrouper les threads.  
  
## <a name="running-all-threads-to-a-specific-location-in-code"></a>Tous les Threads en cours d’exécution à un emplacement spécifique dans le Code  
 Vous exécutez tous les threads dans une vignette donnée à la ligne qui contient le curseur à l’aide de **exécuter actuel vignette jusqu’au curseur**.  
  
### <a name="to-run-all-threads-to-the-location-marked-by-the-cursor"></a>Pour exécuter tous les threads à l’emplacement marqué par le curseur  
  
1.  Dans le menu contextuel pour les threads figés, choisissez **libérer**.  
  
2.  Dans l’éditeur de Code, placez le curseur dans la ligne 30.  
  
3.  Dans le menu contextuel de l’éditeur de Code, choisissez **exécuter la Tile actuel au curseur**.  
  
     Les 24 threads précédemment bloqués au cloisonnement à la ligne 21 ont depuis progressé à ligne 32. Ceci est illustré dans le **Threads GPU** fenêtre.  
  
## <a name="see-also"></a>Voir aussi  
 [Présentation de C++ AMP](../../parallel/amp/cpp-amp-overview.md)   
 [Débogage du Code GPU](/visualstudio/debugger/debugging-gpu-code)   
 [Comment : utiliser la fenêtre Threads GPU](/visualstudio/debugger/how-to-use-the-gpu-threads-window)   
 [Comment : utiliser la fenêtre Espion parallèle](/visualstudio/debugger/how-to-use-the-parallel-watch-window)   
 [Analyse du Code C++ AMP avec le visualiseur concurrentiel](http://go.microsoft.com/fwlink/p/?linkid=253987&clcid=0x409)

