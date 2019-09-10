---
title: Erreur des outils Éditeur de liens LNK1104
ms.date: 09/06/2019
f1_keywords:
- LNK1104
helpviewer_keywords:
- LNK1104
ms.assetid: 9ca6f929-0efc-4055-8354-3cf5b4e636dc
ms.openlocfilehash: f3effd9054954a90f69c5b18d8f099e6d705d9a3
ms.sourcegitcommit: 7babce70714242cf498ca811eec3695fad3abd03
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/09/2019
ms.locfileid: "70808836"
---
# <a name="linker-tools-error-lnk1104"></a>Erreur des outils Éditeur de liens LNK1104

> Impossible d’ouvrir le fichier'*nom_fichier*'

L’éditeur de liens n’a pas pu ouvrir le fichier spécifié. Les causes les plus courantes de ce problème sont que le fichier est en cours d’utilisation ou verrouillé par un autre processus. Il est également possible que le fichier n’existe pas ou qu’il ne se trouve pas dans l’un des répertoires que l’éditeur de liens recherche. Ou vous ne disposez peut-être pas des autorisations suffisantes pour accéder au fichier. Moins souvent, vous n’avez peut-être pas suffisamment d’espace disque, le fichier est trop volumineux ou le chemin d’accès au fichier est trop long.

## <a name="possible-causes-and-solutions"></a>Causes et solutions possibles

Cette erreur peut se produire lorsque l’éditeur de liens tente d’ouvrir un fichier pour la lecture ou l’écriture. Pour limiter les causes possibles, commencez par vérifier le type de fichier. Ensuite, utilisez les sections suivantes pour vous aider à identifier et à résoudre le problème spécifique.

### <a name="cant-open-your-app-or-its-pdb-file"></a>Impossible d’ouvrir votre application ou son fichier. pdb

Si le nom de fichier est l’exécutable que votre projet génère, ou un fichier. pdb associé, la cause la plus courante est que votre application est déjà en cours d’exécution lorsque vous essayez de la régénérer ou qu’elle est chargée dans un débogueur. Pour résoudre ce problème, arrêtez le programme et déchargez-le du débogueur avant de le régénérer. Si l’application est ouverte dans un autre programme, tel qu’un éditeur de ressources, fermez-la. Dans les cas extrêmes, vous devrez peut-être utiliser le gestionnaire des tâches pour mettre fin au processus, ou arrêter et redémarrer Visual Studio.

Les programmes antivirus bloquent souvent temporairement l’accès aux fichiers créés récemment, en particulier les fichiers exécutables. exe et. dll. Pour résoudre ce problème, essayez d’exclure les répertoires de build de votre projet du scanneur antivirus.

### <a name="cant-open-a-microsoft-library-file"></a>Impossible d’ouvrir un fichier de bibliothèque Microsoft

Si le fichier qui ne peut pas être ouvert est l’un des fichiers de bibliothèque standard fournis par Microsoft, par exemple Kernel32. lib, il se peut que vous ayez une erreur de configuration de projet ou une erreur d’installation. Vérifiez que le SDK Windows a été installé et, si votre projet requiert d’autres bibliothèques Microsoft telles que MFC, assurez-vous que les composants MFC ont également été installés par le programme d’installation de Visual Studio. Vous pouvez réexécuter le programme d’installation pour ajouter des composants facultatifs à tout moment. Pour plus d’informations, consultez [modifier Visual Studio](/visualstudio/install/modify-visual-studio). Utilisez l’onglet composants individuels dans le programme d’installation pour choisir des bibliothèques et des kits de développement logiciel (SDK) spécifiques.

Il n’existe aucune bibliothèque atténuée spectre pour les applications ou les composants de Windows universel (UWP). Si le rapport d’erreurs mentionne le fichier *vccorlib. lib* , vous avez peut-être activé [/Qspectre](../../build/reference/qspectre.md) dans un projet UWP. Désactivez l’option de compilateur **/Qspectre** pour résoudre ce problème. Dans Visual Studio, modifiez la propriété d' **atténuation spectre** , qui se trouve dans la page de > génération de**code** **C++/C**de la boîte de dialogue **pages de propriétés** du projet.

Si vous générez un projet qui a été créé à l’aide d’une version antérieure de Visual Studio, l’ensemble d’outils de plateforme et les bibliothèques pour cette version ne sont peut-être pas installés. Si le message d’erreur s’affiche pour un nom de bibliothèque avec version, tel que msvcr100. lib, il s’agit probablement de la cause. Pour résoudre ce problème, vous avez deux options : vous pouvez mettre à niveau le projet pour utiliser l’ensemble d’outils de plateforme actuel que vous avez installé, ou vous pouvez installer l’ensemble d’outils antérieur et générer le projet sans le modifier. Pour plus d’informations, consultez [mise à niveau de projets à partir C++ de versions antérieures de Visual](../../porting/upgrading-projects-from-earlier-versions-of-visual-cpp.md) et [utiliser le multi-ciblage natif dans Visual Studio pour générer des projets anciens](../../porting/use-native-multi-targeting.md).

Si vous voyez cette erreur lorsque vous générez pour une nouvelle plateforme ou configuration cible, les bibliothèques pour cette configuration de projet ou cet ensemble d’outils de plateforme peuvent ne pas être installées. Vérifiez que l' **ensemble d’outils de plateforme** et la **version de SDK Windows** spécifiés dans la [page de propriétés général](../../build/reference/general-property-page-project.md) pour votre projet sont installés, puis vérifiez que les bibliothèques requises sont disponibles dans les **répertoires de bibliothèque** spécifiés dans la [page de propriétés Répertoires VC + +](../../build/reference/vcpp-directories-property-page.md) de vos paramètres de configuration. Il existe des paramètres distincts pour les configurations de débogage et de vente au détail, ainsi que pour les configurations 32 bits et 64 bits, donc si une build fonctionne, mais qu’une autre génère une erreur, assurez-vous que les paramètres sont corrects et que les outils et bibliothèques requis sont installés pour chaque configuration que vous générez.

Si vous utilisez l’IDE de Visual Studio pour générer un projet qui a été copié à partir d’un autre ordinateur, les emplacements d’installation des bibliothèques peuvent être différents. Vérifiez la propriété **répertoires** de la bibliothèque sur la [page de propriétés Répertoires VC + +](../../build/reference/vcpp-directories-property-page.md) pour le projet et mettez-la à jour si nécessaire. Pour afficher et modifier le jeu de chemins d’accès de bibliothèque actuel dans l’IDE, choisissez le contrôle de liste déroulante de la propriété **répertoires de bibliothèque** , puis choisissez **modifier**. La section **valeur évaluée** de la boîte de dialogue **répertoires de bibliothèque** répertorie les chemins d’accès actuels recherchés pour les fichiers de bibliothèque.

Cette erreur peut également se produire lorsque le chemin d’accès au SDK Windows est obsolète. Si vous avez installé une version de la SDK Windows qui est plus récente que votre version de Visual Studio, assurez-vous que les chemins d’accès spécifiés dans la [page de propriétés Répertoires VC + +](../../build/reference/vcpp-directories-property-page.md) sont mis à jour pour correspondre au nouveau kit de développement logiciel (SDK). Si vous utilisez la Invite de commandes développeur, assurez-vous que le fichier de commandes qui initialise les variables d’environnement est mis à jour pour les nouveaux chemins d’accès du kit de développement logiciel (SDK). Ce problème peut être évité en utilisant le programme d’installation de Visual Studio pour installer les kits de développement logiciel (SDK) mis à jour.

### <a name="cannot-open-a-third-party-library-file"></a>Impossible d’ouvrir un fichier de bibliothèque tiers

Il existe plusieurs causes courantes à ce problème :

- Le chemin d’accès à votre fichier de bibliothèque est peut-être incorrect, ou vous n’avez peut-être pas spécifié l’éditeur de liens.

- Vous avez peut-être installé une version 32 bits de la bibliothèque, mais vous créez pour 64 bits, ou vice-versa.

- La bibliothèque peut avoir des dépendances avec d’autres bibliothèques qui ne sont pas installées.

Pour résoudre un problème de chemin d’accès, vérifiez que la variable d’environnement LIB est définie et contient tous les répertoires des bibliothèques que vous utilisez, pour chaque configuration que vous générez. Dans l’IDE, la variable LIB est définie par la propriété **répertoires** de la bibliothèque dans la [page de propriétés Répertoires VC + +](../../build/reference/vcpp-directories-property-page.md). Assurez-vous que tous les répertoires contenant les bibliothèques dont vous avez besoin sont répertoriés ici, pour chaque configuration que vous générez.

Si vous devez fournir un répertoire de bibliothèque qui remplace un répertoire de bibliothèque standard, vous pouvez utiliser l’option [/LIBPATH](../../build/reference/libpath-additional-libpath.md) sur la ligne de commande ou dans l’IDE, vous pouvez utiliser la propriété **répertoires de bibliothèques supplémentaires** dans les **Propriétés de configuration. > Éditeur de liens >** page de propriétés général pour votre projet.

Vérifiez que vous avez installé toutes les versions de la bibliothèque dont vous avez besoin pour les configurations que vous créez. Envisagez d’utiliser l’utilitaire de gestion des packages [vcpkg](../../vcpkg.md) pour automatiser l’installation et la configuration de nombreuses bibliothèques courantes. Dans la mesure du possible, il est préférable de créer vos propres copies des bibliothèques tierces. vous devez donc vous assurer que vous disposez de toutes les dépendances locales requises par les bibliothèques et qu’elles sont générées pour les mêmes configurations que votre projet.

### <a name="cannot-open-a-file-built-by-your-project"></a>Impossible d’ouvrir un fichier généré par votre projet

Cette erreur peut s’afficher si le *nom* de fichier est généré par votre solution, mais n’existe pas encore lorsque l’éditeur de liens tente d’y accéder. Cela peut se produire lorsqu’un projet dépend d’un autre projet, mais que les projets ne sont pas générés dans le bon ordre. Pour résoudre ce problème, assurez-vous que vos références de projet sont définies dans le projet qui utilise le fichier, de sorte que le fichier manquant est généré avant qu’il ne soit requis. Pour plus d’informations, consultez [Ajout de références dans C++ les projets Visual Studio](../../build/adding-references-in-visual-cpp-projects.md) et [gestion des références dans un projet](/visualstudio/ide/managing-references-in-a-project).

### <a name="cannot-open-file-cprogramobj"></a>Impossible d’ouvrir le fichier'\\C : Program. obj'

Si vous voyez cette erreur ou une erreur similaire impliquant un fichier. obj inattendu à la racine de votre lecteur, le problème est certainement un chemin d’accès de bibliothèque qui n’est pas placé entre guillemets doubles.

Pour résoudre ce problème pour les générations à partir de la ligne de commande, vérifiez les paramètres de l’option [/LIBPATH](../../build/reference/libpath-additional-libpath.md) , les chemins d’accès spécifiés dans la variable d’environnement lib et les chemins d’accès spécifiés sur la ligne de commande, et veillez à utiliser des guillemets doubles autour des chemins d’accès qui incluent des espaces.

Pour résoudre ce problème dans l’IDE, vérifiez la propriété **répertoires** de la bibliothèque sur la page [propriétés de configuration > Répertoires VC + +](../../build/reference/vcpp-directories-property-page.md) , la propriété **répertoires de bibliothèques supplémentaires** dans les **Propriétés de configuration > l’éditeur de liens. >** Page de propriétés général, et la propriété **dépendances supplémentaires** dans l' **éditeur de liens propriétés de configuration > >** page de propriétés d’entrée pour votre projet. Assurez-vous que tous les chemins d’accès aux répertoires contenant les bibliothèques dont vous avez besoin sont enveloppés par des guillemets doubles, si nécessaire.

### <a name="other-common-issues"></a>Autres problèmes courants

Cette erreur peut se produire lorsque le chemin d’accès ou le nom de fichier de bibliothèque spécifié pour l’éditeur de liens sur la ligne de commande ou dans une directive [#pragma comment (lib, « library_name »)](../../preprocessor/comment-c-cpp.md) est incorrect ou que le chemin d’accès a une spécification de lecteur non valide. Vérifiez l’orthographe et l’extension de fichier et vérifiez que le fichier existe à l’emplacement spécifié.

Un autre programme a peut-être ouvert le fichier et l’éditeur de liens ne peut pas y accéder en écriture. Les programmes antivirus bloquent souvent temporairement l’accès aux fichiers nouvellement créés. Pour résoudre ce problème, essayez d’exclure les répertoires de build de votre projet du scanneur antivirus.

Si vous utilisez une option de génération parallèle, il est possible que Visual Studio ait verrouillé le fichier sur un autre thread. Pour résoudre ce problème, vérifiez que vous ne générez pas le même objet de code ou la même bibliothèque dans plusieurs projets, et que vous utilisez des dépendances de génération ou des références de projet pour récupérer des fichiers binaires générés dans votre projet.

Lorsque vous spécifiez directement des bibliothèques individuelles dans la propriété **dépendances supplémentaires** , utilisez des espaces pour séparer les noms de bibliothèque, et non des virgules ou des points-virgules. Si vous utilisez l’élément de menu **modifier** pour ouvrir la boîte de dialogue **dépendances supplémentaires** , utilisez les nouvelles lignes pour séparer les noms, et non les virgules, les points-virgules ou les espaces. Utilisez également les nouvelles lignes lorsque vous spécifiez des chemins de bibliothèque dans les boîtes de dialogue **répertoires de bibliothèque** et **répertoires de bibliothèques supplémentaires** .

Cette erreur peut s’afficher lorsque le chemin d’accès au *nom de fichier* se développe en plus de 260 caractères. Modifiez les noms ou réorganisez votre structure de répertoires si nécessaire pour raccourcir les chemins d’accès aux fichiers requis.

Cette erreur peut se produire si le fichier est trop volumineux. Les bibliothèques ou les fichiers objets dont la taille est supérieure à 1 Go peuvent entraîner des problèmes pour l’éditeur de liens 32 bits. Pour résoudre ce problème, vous pouvez utiliser l’ensemble d’outils 64 bits. Pour plus d’informations sur la façon de procéder sur la ligne de commande [, consultez Procédure : Activez un ensemble d’outils visuels C++ 64 bits sur la ligne](../../build/how-to-enable-a-64-bit-visual-cpp-toolset-on-the-command-line.md)de commande. Pour plus d’informations sur la façon de procéder dans l’IDE, consultez [utilisation de MSBuild avec le compilateur et les outils 64 bits](../../build/walkthrough-using-msbuild-to-create-a-visual-cpp-project.md#using-msbuild-to-build-your-project) et ce Stack Overflow publication : [Comment faire en sorte que Visual Studio utilise le chaîne d’outils amd64 natif](https://stackoverflow.com/questions/19820718/how-to-make-visual-studio-use-the-native-amd64-toolchain/23793055).

Cette erreur peut se produire si vous disposez d’autorisations de fichiers insuffisantes pour accéder au *nom*de fichier. Cela peut se produire si vous utilisez un compte d’utilisateur ordinaire et tentez d’accéder aux fichiers de bibliothèque dans des répertoires système protégés, ou d’utiliser des fichiers copiés à partir d’autres utilisateurs dont les autorisations d’origine sont définies. Pour résoudre ce problème, déplacez le fichier vers un répertoire de projet accessible en écriture. Si le fichier se trouve dans un répertoire accessible en écriture mais a des autorisations inaccessibles, vous pouvez utiliser une invite de commandes d’administrateur et exécuter la commande takeown. exe pour prendre possession du fichier.

L’erreur peut se produire lorsque vous n’avez pas suffisamment d’espace disque. L’éditeur de liens utilise des fichiers temporaires dans plusieurs cas. Même si vous disposez d’un espace disque suffisant, un lien très volumineux peut épuiser ou fragmenter l’espace disque disponible. Envisagez d’utiliser l’option [/OPT (optimisations)](../../build/reference/opt-optimizations.md) ; l’élimination de COMDAT transitif lit tous les fichiers objets plusieurs fois.

Si le *nom* de fichier est nommé LNK*nnn*, qui est un nom de fichier généré par l’éditeur de liens pour un fichier temporaire, le répertoire spécifié dans la variable d’environnement TMP peut ne pas exister, ou plusieurs répertoires peuvent être spécifiés pour la variable d’environnement TMP. Un seul chemin d’accès au répertoire doit être spécifié pour la variable d’environnement TMP.
