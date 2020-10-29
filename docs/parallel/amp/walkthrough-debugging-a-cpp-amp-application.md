---
title: 'Procédure pas-à-pas : débogage d’une application C++ AMP'
ms.date: 04/23/2019
helpviewer_keywords:
- debugging, C++ Accelerated Massive Parallelism
- C++ AMP, debugging
- C++ Accelerated Massive Parallelism, debugging
- debugging, C++ AMP
ms.assetid: 40e92ecc-f6ba-411c-960c-b3047b854fb5
ms.openlocfilehash: 21ce276af9317c06f3b717b41685f419d2362d70
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92921683"
---
# <a name="walkthrough-debugging-a-c-amp-application"></a>Procédure pas-à-pas : débogage d’une application C++ AMP

Cette rubrique montre comment déboguer une application qui utilise C++ Accelerated Massive Parallelism (C++ AMP) pour tirer parti de l’unité de traitement graphique (GPU). Il utilise un programme de réduction parallèle qui additionne un grand tableau d’entiers. Cette procédure pas à pas décrit les tâches suivantes :

- Lancement du débogueur GPU.

- Inspection des threads GPU dans la fenêtre threads GPU.

- Utilisation de la fenêtre **Piles parallèles** pour observer simultanément les piles d’appels de plusieurs threads GPU.

- Utilisation de la fenêtre **Espion parallèle** pour inspecter les valeurs d’une expression unique sur plusieurs threads en même temps.

- Marquage, gel, décongélation et regroupement des threads GPU.

- Exécution de tous les threads d’une vignette à un emplacement spécifique dans le code.

## <a name="prerequisites"></a>Conditions préalables requises

Avant de commencer cette procédure pas à pas :

- Lisez [C++ amp vue d’ensemble](../../parallel/amp/cpp-amp-overview.md).

- Assurez-vous que les numéros de ligne sont affichés dans l’éditeur de texte. Pour plus d’informations, consultez [Comment : afficher les numéros de ligne dans l’éditeur](/visualstudio/ide/reference/how-to-display-line-numbers-in-the-editor).

- Assurez-vous que vous exécutez au moins Windows 8 ou Windows Server 2012 pour prendre en charge le débogage sur l’émulateur de logiciel.

[!INCLUDE[note_settings_general](../../mfc/includes/note_settings_general_md.md)]

### <a name="to-create-the-sample-project"></a>Pour créer l'exemple de projet

Les instructions de création d’un projet varient en fonction de la version de Visual Studio que vous utilisez. Assurez-vous que la version correcte est sélectionnée en haut à gauche de cette page.

::: moniker range="msvc-160"

### <a name="to-create-the-sample-project-in-visual-studio-2019"></a>Pour créer l’exemple de projet dans Visual Studio 2019

1. Dans la barre de menus, choisissez **Fichier** > **Nouveau** > **Projet** pour ouvrir la boîte de dialogue **Créer un projet** .

1. En haut de la boîte de dialogue, définissez **Langage** sur **C++** , **Plateforme** sur **Windows** et **Type de projet** sur **Console** .

1. À partir de la liste des types de projets, choisissez **Application console** , puis choisissez **Suivant** . Dans la page suivante, entrez `AMPMapReduce` dans la zone de texte **nom** pour donner un nom au projet et indiquer son emplacement si vous le souhaitez.

   ![Nommer le projet](../../build/media/mathclient-project-name-2019.png "Nommer le projet")

1. Choisissez le bouton **Créer** pour créer le projet client.

::: moniker-end

::: moniker range="<=msvc-150"

### <a name="to-create-the-sample-project-in-visual-studio-2017-or-visual-studio-2015"></a>Pour créer l’exemple de projet dans Visual Studio 2017 ou Visual Studio 2015

1. Démarrez Visual Studio.

1. Dans la barre de menus, choisissez **fichier** > **nouveau** > **projet** .

1. Sous **installé** dans le volet modèles, choisissez **Visual C++** .

1. Choisissez **application console Win32** , tapez `AMPMapReduce` dans la zone **nom** , puis choisissez le bouton **OK** .

1. Choisissez le bouton **Suivant** .

1. Désactivez la case à cocher **en-tête précompilé** , puis choisissez le bouton **Terminer** .

1. Dans **Explorateur de solutions** , supprimez *stdafx. h* , *targetver. h* et *stdafx. cpp* du projet.

::: moniker-end

Étapes suivantes :

1. Ouvrez AMPMapReduce. cpp et remplacez son contenu par le code suivant.

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

1. Dans la barre de menus, choisissez **fichier**  >  **enregistrer tout** .

1. Dans **Explorateur de solutions** , ouvrez le menu contextuel de **AMPMapReduce** , puis choisissez **Propriétés** .

1. Dans la boîte de dialogue **pages de propriétés** , sous **Propriétés de configuration** , choisissez en-têtes précompilés **C/C++**  >  **Precompiled Headers** .

1. Pour la propriété **en-tête précompilé** , sélectionnez **ne pas utiliser les en-têtes précompilés** , puis choisissez le bouton **OK** .

1. Dans la barre de menus, choisissez **générer**  >  **générer la solution** .

## <a name="debugging-the-cpu-code"></a>Débogage du code UC

Dans cette procédure, vous allez utiliser le débogueur Windows local pour vous assurer que le code de l’UC dans cette application est correct. Le segment du code UC de cette application qui est particulièrement intéressant est la **`for`** boucle dans la `reduction_sum_gpu_kernel` fonction. Il contrôle la réduction parallèle basée sur l’arborescence qui est exécutée sur le GPU.

### <a name="to-debug-the-cpu-code"></a>Pour déboguer le code UC

1. Dans **Explorateur de solutions** , ouvrez le menu contextuel de **AMPMapReduce** , puis choisissez **Propriétés** .

2. Dans la boîte de dialogue **pages de propriétés** , sous **Propriétés de configuration** , choisissez **débogage** . Vérifiez que **débogueur Windows local** est sélectionné dans la liste **débogueur à lancer** .

3. Revenez à l' **éditeur de code** .

4. Définissez des points d’arrêt sur les lignes de code présentées dans l’illustration suivante (environ lignes 67 ligne 70).

   ![Points d'arrêt d'UC](../../parallel/amp/media/campcpubreakpoints.png "Points d'arrêt d'UC") <br/>
   Points d'arrêt d'UC

5. Dans la barre de menus, choisissez **Déboguer**  >  **Démarrer le débogage** .

6. Dans la fenêtre **variables locales** , observez la valeur de `stride_size` jusqu’à ce que le point d’arrêt à la ligne 70 soit atteint.

7. Dans la barre de menus, choisissez **Déboguer**  >  **arrêter le débogage** .

## <a name="debugging-the-gpu-code"></a>Débogage du code GPU

Cette section montre comment déboguer le code GPU, qui est le code contenu dans la `sum_kernel_tiled` fonction. Le code GPU calcule la somme des entiers pour chaque « bloc » en parallèle.

### <a name="to-debug-the-gpu-code"></a>Pour déboguer le code GPU

1. Dans **Explorateur de solutions** , ouvrez le menu contextuel de **AMPMapReduce** , puis choisissez **Propriétés** .

2. Dans la boîte de dialogue **pages de propriétés** , sous **Propriétés de configuration** , choisissez **débogage** .

3. Dans la liste **Débogueur à lancer** , sélectionnez **Débogueur Windows local** .

4. Dans la liste **type de débogueur** , vérifiez que **auto** est sélectionné.

    **Auto** est la valeur par défaut. Avant Windows 10, le **GPU uniquement** est la valeur requise au lieu de **auto** .

5. Choisissez le bouton **OK** .

6. Définissez un point d’arrêt à la ligne 30, comme indiqué dans l’illustration suivante.

   ![Points d'arrêt GPU](../../parallel/amp/media/campgpubreakpoints.png "Points d'arrêt GPU") <br/>
   Point d’arrêt GPU

7. Dans la barre de menus, choisissez **Déboguer**  >  **Démarrer le débogage** . Les points d’arrêt dans le code UC des lignes 67 et 70 ne sont pas exécutés pendant le débogage GPU, car ces lignes de code sont exécutées sur le processeur.

### <a name="to-use-the-gpu-threads-window"></a>Pour utiliser la fenêtre threads GPU

1. Pour ouvrir la fenêtre **Threads GPU** , dans la barre de menus, choisissez **Déboguer** des  >  **Windows**  >  **Threads GPU** Windows.

   Vous pouvez inspecter l’état des threads GPU dans la fenêtre **Threads GPU** qui s’affiche.

2. Ancrez la fenêtre **Threads GPU** au bas de Visual Studio. Choisissez le bouton **développer le commutateur de thread** pour afficher les zones de texte de la vignette et du thread. La fenêtre **Threads GPU** affiche le nombre total de threads GPU actifs et bloqués, comme indiqué dans l’illustration suivante.

   ![Fenêtre Threads GPU avec 4 threads actifs](../../parallel/amp/media/campc.png "Fenêtre Threads GPU avec 4 threads actifs") <br/>
   Fenêtre Threads GPU

   313 vignettes sont allouées pour ce calcul. Chaque vignette contient 32 threads. Étant donné que le débogage GPU local se produit sur un émulateur de logiciel, il existe quatre threads GPU actifs. Les quatre threads exécutent les instructions simultanément, puis passent à l’instruction suivante.

   Dans la fenêtre **Threads GPU** , quatre threads GPU sont actifs et 28 threads GPU sont bloqués au niveau de l’instruction [tile_barrier :: wait](reference/tile-barrier-class.md#wait) définie à à propos de la ligne 21 ( `t_idx.barrier.wait();` ). Tous les threads GPU 32 appartiennent à la première vignette, `tile[0]` . Une flèche pointe vers la ligne qui contient le thread actuel. Pour basculer vers un autre thread, utilisez l’une des méthodes suivantes :

    - Dans la ligne du thread vers lequel basculer dans la fenêtre **Threads GPU** , ouvrez le menu contextuel et choisissez **basculer vers le thread** . Si la ligne représente plusieurs threads, vous allez basculer vers le premier thread en fonction des coordonnées du thread.

    - Entrez les valeurs de la vignette et du thread du thread dans les zones de texte correspondantes, puis choisissez le bouton **basculer le thread** .

   La fenêtre **pile des appels** affiche la pile des appels du thread GPU actuel.

### <a name="to-use-the-parallel-stacks-window"></a>Pour utiliser la fenêtre piles parallèles

1. Pour ouvrir la fenêtre **Piles parallèles** , dans la barre de menus, choisissez **Déboguer**  >  **Windows**  >  **Piles parallèles** Windows.

   Vous pouvez utiliser la fenêtre **Piles parallèles** pour inspecter simultanément les frames de pile de plusieurs threads GPU.

2. Ancrez la fenêtre **Piles parallèles** au bas de Visual Studio.

3. Assurez-vous que **Threads** est sélectionné dans la liste dans l’angle supérieur gauche. Dans l’illustration suivante, la fenêtre **Piles parallèles** affiche une vue axée sur la pile des appels des threads GPU que vous avez vues dans la fenêtre **Threads GPU** .

   ![Fenêtre Piles parallèles avec 4 threads actifs](../../parallel/amp/media/campd.png "Fenêtre Piles parallèles avec 4 threads actifs") <br/>
   Fenêtre Piles parallèles

   32 threads passés de `_kernel_stub` à l’instruction lambda dans l' `parallel_for_each` appel de fonction, puis à la `sum_kernel_tiled` fonction, où la réduction parallèle se produit. 28 des 32 threads ont progressé jusqu’à l’instruction [tile_barrier :: wait](reference/tile-barrier-class.md#wait) et restent bloqués à la ligne 22, tandis que les 4 autres threads restent actifs dans la `sum_kernel_tiled` fonction à la ligne 30.

   Vous pouvez inspecter les propriétés d’un thread GPU qui sont disponibles dans la fenêtre **Threads GPU** dans le volet enrichi de la fenêtre **Piles parallèles** . Pour ce faire, placez le pointeur de la souris sur le frame de pile de **sum_kernel_tiled** . L’illustration suivante montre le DataTip.

   ![DataTip pour la fenêtre Piles parallèles](../../parallel/amp/media/campe.png "DataTip pour la fenêtre Piles parallèles") <br/>
   DataTip de thread GPU

   Pour plus d’informations sur la fenêtre **Piles parallèles** , consultez [utilisation de la fenêtre piles parallèles](/visualstudio/debugger/using-the-parallel-stacks-window).

### <a name="to-use-the-parallel-watch-window"></a>Pour utiliser les Fenêtre Espion parallèles

1. Pour ouvrir la fenêtre **Espion parallèle** , dans la barre de menus, choisissez **Déboguer** la surveillance  >  **Windows**  >  **Parallel Watch**  >  **parallèle 1** de la surveillance parallèle Windows.

   Vous pouvez utiliser la fenêtre **Espion parallèle** pour inspecter les valeurs d’une expression sur plusieurs threads.

2. Ancrez la fenêtre **Espion parallèle 1** au bas de Visual Studio. Il y a 32 lignes dans la table de la fenêtre **Espion parallèle** . Chaque correspond à un thread GPU qui apparaissait à la fois dans la fenêtre threads GPU et dans la fenêtre **Piles parallèles** . À présent, vous pouvez entrer des expressions dont vous souhaitez inspecter les valeurs sur tous les threads GPU 32.

3. Sélectionnez l’en-tête de colonne **Ajouter un espion** , entrez `localIdx` , puis appuyez sur la touche **entrée** .

4. Sélectionnez à nouveau l’en-tête de colonne **Ajouter un espion** , tapez `globalIdx` , puis appuyez sur la touche **entrée** .

5. Sélectionnez à nouveau l’en-tête de colonne **Ajouter un espion** , tapez `localA[localIdx[0]]` , puis appuyez sur la touche **entrée** .

   Vous pouvez effectuer un tri selon une expression spécifiée en sélectionnant son en-tête de colonne correspondant.

   Sélectionnez l’en-tête de colonne **locala [localIdx [0]]** pour trier la colonne. L’illustration suivante montre les résultats du tri par **locala [localIdx [0]]** .

   ![Fenêtre Espion parallèle avec les résultats triés](../../parallel/amp/media/campf.png "Fenêtre Espion parallèle avec les résultats triés") <br/>
   Résultats du tri

   Vous pouvez exporter le contenu de la fenêtre **Espion parallèle** vers Excel en choisissant le bouton **Excel** , puis en choisissant **ouvrir dans Excel** . Si Excel est installé sur votre ordinateur de développement, une feuille de calcul Excel contenant le contenu s’ouvre.

6. Dans le coin supérieur droit de la fenêtre **Espion parallèle** , vous pouvez utiliser un contrôle de filtre pour filtrer le contenu à l’aide d’expressions booléennes. Entrez `localA[localIdx[0]] > 20000` dans la zone de texte contrôle de filtre, puis appuyez sur la touche **entrée** .

   La fenêtre contient désormais uniquement les threads sur lesquels la `localA[localIdx[0]]` valeur est supérieure à 20000. Le contenu est toujours trié par la `localA[localIdx[0]]` colonne, qui est l’action de tri effectuée précédemment.

## <a name="flagging-gpu-threads"></a>Marquage de threads GPU

Vous pouvez marquer des threads GPU spécifiques en les marquant dans la fenêtre **Threads GPU** , la fenêtre **Espion parallèle** ou le DataTip dans la fenêtre **Piles parallèles** . Si une ligne de la fenêtre threads GPU contient plusieurs threads, le marquage de cette ligne marque tous les threads contenus dans la ligne.

### <a name="to-flag-gpu-threads"></a>Pour signaler des threads GPU

1. Sélectionnez l’en-tête de colonne **[thread]** dans la fenêtre **Espion parallèle 1** pour trier par index de vignettes et index de thread.

2. Dans la barre de menus, choisissez **Déboguer**  >  **Continuer** , ce qui entraîne l’avancement des quatre threads qui étaient actifs jusqu’au cloisonnement suivant (défini à la ligne 32 de AMPMapReduce. cpp).

3. Choisissez le symbole de l’indicateur sur le côté gauche de la ligne qui contient les quatre threads qui sont désormais actifs.

   L’illustration suivante montre les quatre threads avec indicateur actif dans la fenêtre **Threads GPU** .

   ![Fenêtre Threads GPU avec threads avec indicateur](../../parallel/amp/media/campg.png "Fenêtre Threads GPU avec threads avec indicateur") <br/>
   Threads actifs dans la fenêtre Threads GPU

   La fenêtre **Espion parallèle** et le DataTip de la fenêtre **Piles parallèles** indiquent les threads avec indicateur.

4. Si vous souhaitez vous concentrer sur les quatre threads que vous avez signalés, vous pouvez choisir d’afficher, dans les fenêtres **Threads GPU** , **Espion parallèle** et **Piles parallèles** , uniquement les threads avec indicateur.

   Choisissez le bouton **afficher les indicateurs uniquement** sur l’une ou l’autre des fenêtres ou dans la barre d’outils **emplacement de débogage** . L’illustration suivante montre le bouton **afficher uniquement** les éléments marqués d’un indicateur dans la barre d’outils **emplacement de débogage** .

   ![Barre d'outils Emplacement de débogage avec icône Afficher uniquement avec indicateur](../../parallel/amp/media/camph.png "Barre d'outils Emplacement de débogage avec icône Afficher uniquement avec indicateur") <br/>
   Bouton **afficher uniquement les indicateurs**

   Désormais, les fenêtres **Threads GPU** , **Espion parallèle** et **Piles parallèles** affichent uniquement les threads avec indicateur.

## <a name="freezing-and-thawing-gpu-threads"></a>Gel et libération des threads GPU

Vous pouvez geler (suspendre) et libérer (reprendre) les threads GPU à partir de la fenêtre **Threads GPU** ou de la fenêtre **Espion parallèle** . Vous pouvez figer et libérer les threads de l’UC de la même façon ; Pour plus d’informations, consultez [Comment : utiliser la fenêtre threads](/visualstudio/debugger/how-to-use-the-threads-window).

### <a name="to-freeze-and-thaw-gpu-threads"></a>Pour figer et libérer des threads GPU

1. Choisissez le bouton **afficher uniquement** les threads avec indicateur pour afficher tous les threads.

2. Dans la barre de menus, choisissez **Déboguer**  >  **Continuer** .

3. Ouvrez le menu contextuel de la ligne active, puis choisissez **figer** .

   L’illustration suivante de la fenêtre **Threads GPU** montre que les quatre threads sont figés.

   ![Fenêtres Threads GPU indiquant les threads figés](../../parallel/amp/media/campk.png "Fenêtres Threads GPU indiquant les threads figés") <br/>
   Threads figés dans la fenêtre **Threads GPU**

   De même, la fenêtre **Espion parallèle** indique que les quatre threads sont figés.

4. Dans la barre de menus, choisissez **Déboguer**  >  **Continuer** pour permettre aux quatre prochains threads GPU de progresser au-delà du cloisonnement à la ligne 22 et d’atteindre le point d’arrêt à la ligne 30. La fenêtre **Threads GPU** indique que les quatre threads précédemment figés restent figés et à l’état actif.

5. Dans la barre de menus, choisissez **Déboguer** , **Continuer** .

6. Dans la fenêtre **Espion parallèle** , vous pouvez également libérer un ou plusieurs threads GPU.

### <a name="to-group-gpu-threads"></a>Pour regrouper les threads GPU

1. Dans le menu contextuel de l’un des threads de la fenêtre **Threads GPU** , choisissez **Grouper par** , **adresse** .

   Les threads de la fenêtre **Threads GPU** sont regroupés par adresse. L’adresse correspond à l’instruction dans le code machine où se trouvent chaque groupe de threads. 24 threads se trouvent à la ligne 22 où la [méthode tile_barrier :: wait](reference/tile-barrier-class.md#wait) est exécutée. 12 threads sont au niveau de l’instruction du cloisonnement à la ligne 32. Quatre de ces threads sont marqués d’un indicateur. Huit threads se trouvent au point d’arrêt à la ligne 30. Quatre de ces threads sont figés. L’illustration suivante montre les threads groupés dans la fenêtre **Threads GPU** .

   ![Fenêtre Threads GPU avec threads groupés par adresse](../../parallel/amp/media/campl.png "Fenêtre Threads GPU avec threads groupés par adresse") <br/>
   Threads groupés dans la fenêtre **Threads GPU**

2. Vous pouvez également effectuer l’opération **regrouper par** en ouvrant le menu contextuel de la grille de données de la fenêtre **Espion parallèle** , en choisissant **Grouper par** , puis en choisissant l’élément de menu qui correspond à la façon dont vous souhaitez regrouper les threads.

## <a name="running-all-threads-to-a-specific-location-in-code"></a>Exécution de tous les threads à un emplacement spécifique dans le code

Vous exécutez tous les threads d’une vignette donnée sur la ligne qui contient le curseur à l’aide de l' **exécution de la vignette actuelle jusqu’au curseur** .

### <a name="to-run-all-threads-to-the-location-marked-by-the-cursor"></a>Pour exécuter tous les threads à l’emplacement marqué par le curseur

1. Dans le menu contextuel pour les threads figés, choisissez **libérer** .

2. Dans l' **éditeur de code** , placez le curseur à la ligne 30.

3. Dans le menu contextuel de l' **éditeur de code** , choisissez exécuter la **vignette actuelle jusqu’au curseur** .

   Les 24 threads précédemment bloqués au niveau du cloisonnement à la ligne 21 ont progressé jusqu’à la ligne 32. Cela s’affiche dans la fenêtre **Threads GPU** .

## <a name="see-also"></a>Voir aussi

[Présentation de C++ AMP](../../parallel/amp/cpp-amp-overview.md)<br/>
[Débogage du code GPU](/visualstudio/debugger/debugging-gpu-code)<br/>
[Comment : utiliser la fenêtre threads GPU](/visualstudio/debugger/how-to-use-the-gpu-threads-window)<br/>
[Comment : utiliser la fenêtre Espion parallèle](/visualstudio/debugger/how-to-use-the-parallel-watch-window)<br/>
[Analyse du code C++ AMP avec le visualiseur concurrentiel](/archive/blogs/nativeconcurrency/analyzing-c-amp-code-with-the-concurrency-visualizer)
