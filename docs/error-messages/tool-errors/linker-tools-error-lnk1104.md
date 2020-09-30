---
title: Erreur des outils Éditeur de liens LNK1104
description: Décrit l’erreur de l’éditeur de liens Microsoft C et C++ (MSVC) LNK1104, ses causes et les solutions possibles.
ms.date: 12/13/2019
f1_keywords:
- LNK1104
helpviewer_keywords:
- LNK1104
ms.assetid: 9ca6f929-0efc-4055-8354-3cf5b4e636dc
ms.openlocfilehash: aa7bcf34cddfa24956d807131b3c484e7d580e73
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91506034"
---
# <a name="linker-tools-error-lnk1104"></a>Erreur des outils Éditeur de liens LNK1104

> Impossible d’ouvrir le fichier'*nom_fichier*'

Cette erreur est signalée lorsque l’éditeur de liens ne parvient pas à ouvrir un fichier pour la lecture ou l’écriture. Les deux causes les plus courantes du problème sont les suivantes :

- votre programme est déjà en cours d’exécution ou est chargé dans le débogueur, et

- les chemins d’accès de la bibliothèque sont incorrects ou ne sont pas encapsulés dans des guillemets doubles.

Il existe de nombreuses autres causes possibles pour cette erreur. Pour les réduire, commencez par vérifier le type de *nom* de fichier. Ensuite, utilisez les sections suivantes pour vous aider à identifier et à résoudre le problème spécifique.

## <a name="cant-open-your-app-or-its-pdb-file"></a>Impossible d’ouvrir votre application ou son fichier. pdb

### <a name="your-app-is-running-or-its-loaded-in-the-debugger"></a>Votre application est en cours d’exécution, ou elle est chargée dans le débogueur

Lorsque *filename* est le nom de l’exécutable ou un fichier. pdb associé, vérifiez si votre application est déjà en cours d’exécution. Vérifiez ensuite s’il est chargé dans un débogueur. Pour résoudre ce problème, arrêtez le programme et déchargez-le du débogueur avant de le régénérer. Si l’application est ouverte dans un autre programme, tel qu’un éditeur de ressources, fermez-la. Si votre programme ne répond pas, vous devrez peut-être utiliser le gestionnaire des tâches pour mettre fin au processus. Vous devrez peut-être également fermer et redémarrer Visual Studio.

### <a name="your-app-is-locked-by-an-antivirus-scan"></a>Votre application est verrouillée par une analyse antivirus

Les programmes antivirus bloquent souvent temporairement l’accès aux fichiers créés récemment, en particulier les fichiers exécutables. exe et. dll. Pour résoudre ce problème, essayez d’exclure les répertoires de build de votre projet du scanneur antivirus.

## <a name="cant-open-a-microsoft-library-file"></a>Impossible d’ouvrir un fichier de bibliothèque Microsoft

### <a name="windows-libraries-such-as-kernel32lib"></a>Bibliothèques Windows, telles que kernel32. lib

Si le fichier qui ne peut pas être ouvert est l’un des fichiers de bibliothèque standard fournis par Microsoft, par exemple *Kernel32. lib*, il se peut que vous ayez une erreur de configuration de projet ou une erreur d’installation. Vérifiez que le SDK Windows a été installé. Si votre projet requiert d’autres bibliothèques Microsoft, telles que MFC, assurez-vous que les composants MFC ont également été installés par le programme d’installation de Visual Studio. Vous pouvez réexécuter le programme d’installation pour ajouter des composants facultatifs à tout moment. Pour plus d’informations, consultez [modifier Visual Studio](/visualstudio/install/modify-visual-studio). Utilisez l’onglet **composants individuels** dans le programme d’installation pour choisir des bibliothèques et des kits de développement logiciel (SDK) spécifiques.

### <a name="versioned-vcruntime-libraries"></a>Bibliothèques vcruntime avec version

Si le message d’erreur a une bibliothèque Microsoft, telle que *msvcr120. lib*, l’ensemble d’outils de plateforme de cette version de compilateur n’est peut-être pas installé. Pour résoudre ce problème, vous avez deux options : mettre à niveau le projet pour utiliser l’ensemble d’outils de plateforme actuel ou installer l’ensemble d’outils antérieur et générer le projet sans le modifier. Pour plus d’informations, consultez [mise à niveau de projets à partir de versions antérieures de Visual C++](../../porting/upgrading-projects-from-earlier-versions-of-visual-cpp.md) et [utiliser le multi-ciblage natif dans Visual Studio pour générer des projets anciens](../../porting/use-native-multi-targeting.md).

### <a name="retail-debug-or-platform-specific-libraries"></a>Bibliothèques de vente au détail, débogage ou spécifiques à la plateforme

L’erreur peut se produire lorsque vous créez pour la première fois une nouvelle plateforme ou une nouvelle configuration cible, comme Retail ou ARM64. Dans l’IDE, vérifiez que l' **ensemble d’outils de plateforme** et la Version de **SDK Windows** spécifiés dans la [page de propriétés général](../../build/reference/general-property-page-project.md) sont installés. Vérifiez également que les bibliothèques requises sont disponibles dans les **répertoires de bibliothèque** spécifiés dans la [page de propriétés Répertoires VC + +](../../build/reference/vcpp-directories-property-page.md). Vérifiez les propriétés de chaque configuration, telles que Debug, Retail, x86 ou ARM64. Si une build fonctionne, mais pas une autre, comparez les paramètres pour les deux. Installez tous les outils et bibliothèques requis manquants.

### <a name="the-vccorliblib-library"></a>Bibliothèque vccorlib. lib

Il n’existe aucune bibliothèque atténuée spectre pour les applications ou les composants de Windows universel (UWP). Si le message d’erreur comprend *vccorlib. lib*, vous avez peut-être activé [/Qspectre](../../build/reference/qspectre.md) dans un projet UWP. Désactivez l’option de compilateur **/Qspectre** pour résoudre ce problème. Dans Visual Studio, modifiez la propriété d' **atténuation spectre** . Elle est disponible dans la page génération de code **C/C++**  >  **Code Generation** de la boîte de dialogue **pages de propriétés** du projet.

### <a name="libraries-in-projects-from-online-or-other-sources"></a>Bibliothèques dans des projets en ligne ou dans d’autres sources

Si vous générez un projet copié à partir d’un autre ordinateur, les emplacements d’installation de la bibliothèque peuvent être différents. Pour les générations à partir de la ligne de commande, vérifiez que la variable d’environnement LIB et les chemins de bibliothèque sont définis correctement pour la Build. Dans Visual Studio, vous pouvez afficher et modifier les chemins d’accès de bibliothèque actuels définis dans les pages de propriétés de votre projet. Dans la page **Répertoires VC + +** , choisissez le contrôle de liste déroulante de la propriété **répertoires de bibliothèque** , puis choisissez **modifier**. La section **valeur évaluée** de la boîte de dialogue **répertoires de bibliothèque** répertorie les chemins d’accès actuels recherchés pour les fichiers de bibliothèque. Mettez à jour ces chemins d’accès pour pointer vers vos bibliothèques locales.

### <a name="updated-windows-sdk-libraries"></a>Bibliothèques de SDK Windows mises à jour

Cette erreur peut se produire lorsque le chemin d’accès Visual Studio vers le SDK Windows est obsolète. Cela peut se produire si vous installez un SDK Windows plus récent indépendamment du programme d’installation de Visual Studio. Pour le corriger dans l’IDE, mettez à jour les chemins d’accès spécifiés dans la [page de propriétés Répertoires VC + +](../../build/reference/vcpp-directories-property-page.md). Définissez la version dans le chemin d’accès pour qu’elle corresponde au nouveau kit de développement logiciel (SDK). Si vous utilisez la Invite de commandes développeur, mettez à jour le fichier de commandes qui initialise les variables d’environnement avec les nouveaux chemins d’accès du kit de développement logiciel (SDK). Ce problème peut être évité en utilisant le programme d’installation de Visual Studio pour installer les kits de développement logiciel (SDK) mis à jour.

## <a name="cant-open-a-third-party-library-file"></a>Impossible d’ouvrir un fichier de bibliothèque tiers

Il existe plusieurs causes courantes à ce problème :

- Le chemin d’accès à votre fichier de bibliothèque est peut-être incorrect ou n’est pas encapsulé dans des guillemets doubles. Ou, vous n’avez peut-être pas spécifié l’éditeur de liens.

- Vous avez peut-être installé une version 32 bits de la bibliothèque, mais vous générez pour 64 bits, ou d’une autre façon.

- La bibliothèque peut avoir des dépendances avec d’autres bibliothèques qui ne sont pas installées.

Pour résoudre un problème de chemin d’accès pour les générations à partir de la ligne de commande, vérifiez que la variable d’environnement LIB est définie. Assurez-vous qu’il comprend les chemins d’accès de toutes les bibliothèques que vous utilisez et pour chaque configuration que vous générez. Dans l’IDE, les chemins d’accès de bibliothèque sont définis par la propriété répertoires de la bibliothèque de **Répertoires VC + +**  >  **Library Directories** . Assurez-vous que tous les répertoires contenant les bibliothèques dont vous avez besoin sont répertoriés ici, pour chaque configuration que vous générez.

Vous devrez peut-être fournir un répertoire de bibliothèque qui remplace un répertoire de bibliothèque standard. Sur la ligne de commande, utilisez l’option [/LIBPATH](../../build/reference/libpath-additional-libpath.md) . Dans l’IDE, utilisez la propriété **répertoires de bibliothèques supplémentaires** dans les **propriétés de configuration > éditeur de liens >** page de propriétés général pour votre projet.

Veillez à installer toutes les versions de la bibliothèque dont vous avez besoin pour les configurations que vous créez. Envisagez d’utiliser l’utilitaire de gestion des packages [vcpkg](../../build/vcpkg.md) pour automatiser l’installation et la configuration de nombreuses bibliothèques courantes. Dans la mesure du possible, il est préférable de créer vos propres copies des bibliothèques tierces. Vous êtes alors sûr de disposer de toutes les dépendances locales des bibliothèques, créées pour les mêmes configurations que votre projet.

## <a name="cant-open-a-file-built-by-your-project"></a>Impossible d’ouvrir un fichier généré par votre projet

Cette erreur peut s’afficher si le *nom de fichier* n’existe pas encore lorsque l’éditeur de liens tente d’y accéder. Cela peut se produire lorsqu’un projet dépend d’un autre dans la solution, mais que les projets sont générés dans le mauvais ordre. Pour résoudre ce problème, assurez-vous que vos références de projet sont définies dans le projet qui utilise le fichier. Le fichier manquant est alors généré avant d’être requis. Pour plus d’informations, consultez [Ajout de références dans les projets Visual Studio C++](../../build/adding-references-in-visual-cpp-projects.md) et [gestion des références dans un projet](/visualstudio/ide/managing-references-in-a-project).

## <a name="cannot-open-file-cprogramobj"></a>Impossible d’ouvrir le fichier’C : \\ Program. obj'

Si vous voyez le nom de fichier *C : \\ Program. obj* dans le message d’erreur, encapsulez vos chemins de bibliothèque entre guillemets doubles. Cette erreur se produit lorsqu’un chemin d’accès non encapsulé qui commence par *C : \\ Program Files* est passé à l’éditeur de liens. Les chemins d’accès désencapsulés peuvent également provoquer des erreurs similaires. En règle générale, ils affichent un fichier. obj inattendu à la racine de votre lecteur.

Pour résoudre ce problème pour les générations à partir de la ligne de commande, vérifiez les paramètres de l’option [/LIBPATH](../../build/reference/libpath-additional-libpath.md) . Vérifiez également les chemins d’accès spécifiés dans la variable d’environnement LIB et les chemins d’accès spécifiés sur la ligne de commande. Veillez à utiliser des guillemets doubles autour de tous les chemins d’accès qui incluent des espaces.

Pour résoudre ce problème dans l’IDE, ajoutez des guillemets doubles, le cas échéant, aux propriétés suivantes de votre projet :

- La propriété **répertoires** de la bibliothèque dans les propriétés de configuration > page de propriétés [Répertoires VC + +](../../build/reference/vcpp-directories-property-page.md) ,

- La propriété **répertoires de bibliothèques supplémentaires** dans les **propriétés de configuration > éditeur de liens >** page de propriétés général,

- La propriété **dépendances supplémentaires** dans les **propriétés de configuration > éditeur de liens >** page de propriétés d’entrée.

## <a name="other-common-issues"></a>Autres problèmes courants

### <a name="path-or-filename-issues"></a>Problèmes de chemin d’accès ou de nom de fichier

Cette erreur peut se produire lorsque le nom de fichier ou le chemin d’accès de bibliothèque spécifié pour l’éditeur de liens est incorrect. Ou, lorsque le chemin d’accès a une spécification de lecteur non valide. Recherchez des problèmes dans la ligne de commande ou dans n’importe quel [#pragma commentaire (lib, "library_name")](../../preprocessor/comment-c-cpp.md) . Vérifiez l’orthographe et l’extension de fichier et vérifiez que le fichier existe à l’emplacement spécifié.

### <a name="parallel-build-synchronization"></a>Synchronisation des builds parallèles

Si vous utilisez une option de génération parallèle, Visual Studio peut avoir verrouillé le fichier sur un autre thread. Pour résoudre ce problème, vérifiez que le même objet ou la même bibliothèque de code n’est pas généré dans plusieurs projets. Utilisez des dépendances de build ou des références de projet pour récupérer des fichiers binaires générés dans votre projet.

### <a name="additional-dependencies-specified-in-the-ide"></a>Dépendances supplémentaires spécifiées dans l’IDE

Lorsque vous spécifiez directement des bibliothèques individuelles dans la propriété **dépendances supplémentaires** , utilisez des espaces pour séparer les noms de bibliothèque. N’utilisez pas de virgules ou de points-virgules. Si vous utilisez l’élément de menu **modifier** pour ouvrir la boîte de dialogue **dépendances supplémentaires** , utilisez les nouvelles lignes pour séparer les noms, et non les virgules, les points-virgules ou les espaces. Utilisez également les nouvelles lignes lorsque vous spécifiez des chemins de bibliothèque dans les boîtes de dialogue **répertoires de bibliothèque** et **répertoires de bibliothèques supplémentaires** .

### <a name="paths-that-are-too-long"></a>Chemins d’accès trop longs

Cette erreur peut s’afficher lorsque le chemin d’accès au *nom de fichier* se développe en plus de 260 caractères. Si nécessaire, réorganisez la structure de votre répertoire ou raccourcissez les noms des dossiers et des fichiers pour raccourcir les chemins.

### <a name="files-that-are-too-large"></a>Fichiers trop volumineux

Cette erreur peut se produire si le fichier est trop volumineux. Les bibliothèques ou les fichiers objets dont la taille est supérieure à 1 Go peuvent entraîner des problèmes pour l’éditeur de liens 32 bits. Pour résoudre ce problème, vous pouvez utiliser l’ensemble d’outils 64 bits. Pour plus d’informations sur l’utilisation de l’ensemble d’outils 64 bits sur la ligne de commande, consultez Guide pratique [pour activer un ensemble d’outils Visual C++ 64 bits sur la ligne de commande](../../build/how-to-enable-a-64-bit-visual-cpp-toolset-on-the-command-line.md). Pour plus d’informations sur l’utilisation de l’ensemble d’outils 64 bits dans l’IDE, consultez [utilisation de MSBuild avec le compilateur et les outils 64 bits](../../build/walkthrough-using-msbuild-to-create-a-visual-cpp-project.md#using-msbuild-to-build-your-project). Consultez également cette Stack Overflow publication : [Comment faire en sorte que Visual Studio utilise le chaîne d’outils amd64 natif](https://stackoverflow.com/questions/19820718/how-to-make-visual-studio-use-the-native-amd64-toolchain/23793055).

### <a name="incorrect-file-permissions"></a>Autorisations de fichier incorrectes

Cette erreur peut se produire si vous disposez d’autorisations de fichiers insuffisantes pour accéder au *nom*de fichier. Cela peut se produire si vous utilisez un compte d’utilisateur ordinaire pour accéder aux fichiers de bibliothèque dans les répertoires système protégés. Ou, si vous utilisez des fichiers copiés à partir d’autres utilisateurs dont les autorisations d’origine sont toujours définies. Pour résoudre ce problème, déplacez le fichier vers un répertoire de projet accessible en écriture. Si le fichier déplacé a des autorisations inaccessibles, exécutez la commande takeown.exe dans une fenêtre de commande d’administrateur pour prendre possession du fichier.

### <a name="insufficient-disk-space"></a>Espace disque insuffisant

L’erreur peut se produire lorsque vous n’avez pas suffisamment d’espace disque. L’éditeur de liens utilise des fichiers temporaires dans plusieurs cas. Même si vous disposez d’un espace disque suffisant, un grand lien peut épuiser ou fragmenter l’espace disque disponible. Envisagez d’utiliser l’option [/OPT (optimisations)](../../build/reference/opt-optimizations.md) ; l’élimination de COMDAT transitif lit tous les fichiers objets plusieurs fois.

### <a name="problems-in-the-tmp-environment-variable"></a>Problèmes dans la variable d’environnement TMP

Si le *nom* de fichier est nommé LNK*nnn*, il s’agit d’un nom de fichier généré par l’éditeur de liens pour un fichier temporaire. Le répertoire spécifié dans la variable d’environnement TMP n’existe peut-être pas. Ou bien, plusieurs répertoires peuvent être spécifiés pour la variable d’environnement TMP. Un seul chemin d’accès au répertoire doit être spécifié pour la variable d’environnement TMP.

## <a name="help-my-issue-isnt-listed-here"></a>Aide, mon problème n’est pas répertorié ici.

Si aucun des problèmes répertoriés ici ne s’applique, vous pouvez utiliser les outils de commentaires de Visual Studio pour obtenir de l’aide. Dans l’IDE, accédez à la barre de menus et choisissez **aide > envoyer des commentaires > signaler un problème**. Ou soumettez une suggestion en utilisant l' **aide > envoyer des commentaires > envoyer une suggestion**. Vous pouvez également utiliser le site Web de la [communauté de développeurs](https://developercommunity.visualstudio.com/spaces/62/index.html)Visual Studio C++). Utilisez-le pour rechercher des réponses aux questions et demander de l’aide. Pour plus d’informations, consultez [Guide pratique pour signaler un problème avec l’ensemble d’outils Visual C++ ou la documentation](../../overview/how-to-report-a-problem-with-the-visual-cpp-toolset.md).

Si vous avez découvert un nouveau moyen de résoudre ce problème, nous devons l’ajouter à cet article, faites-le nous savoir. Vous pouvez nous envoyer vos commentaires en utilisant le bouton ci-dessous pour **cette page**. Utilisez-le pour créer un nouveau problème dans notre [documentation C++ GitHub référentiel](https://github.com/MicrosoftDocs/cpp-docs/issues). Merci !
