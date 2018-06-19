---
title: Erreur LNK1104 des outils Éditeur de liens | Documents Microsoft
ms.custom: ''
ms.date: 05/17/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1104
dev_langs:
- C++
helpviewer_keywords:
- LNK1104
ms.assetid: 9ca6f929-0efc-4055-8354-3cf5b4e636dc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d2b832d4bceab88fbf3fbe8325a414669d11073c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33302810"
---
# <a name="linker-tools-error-lnk1104"></a>Erreur des outils Éditeur de liens LNK1104

> Impossible d’ouvrir le fichier '*nom de fichier*'

L’éditeur de liens n’a pas pu ouvrir le fichier spécifié. Les causes les plus courantes de ce problème sont que le fichier est en cours d’utilisation ou verrouillé par un autre processus, n’existe pas, ne figure pas dans un des répertoires de recherche de l’éditeur de liens, ou vous n’êtes peut-être pas des autorisations suffisantes pour accéder au fichier. Moins fréquemment, vous avez pouvez manquer d’espace disque, le fichier est peut-être trop grand ou le chemin d’accès au fichier est trop long.

## <a name="possible-causes-and-solutions"></a>Causes et solutions possibles

Cette erreur peut se produire lorsque l’éditeur de liens tente d’ouvrir un fichier en lecture ou en écriture. Pour limiter les causes possibles, vérifiez le type de fichier, il est et utilisez les sections suivantes pour aider à identifier et résoudre le problème spécifique.

### <a name="cannot-open-your-app-or-its-pdb-file"></a>Impossible d’ouvrir votre application ou son fichier .pdb

Si le nom de fichier est l’exécutable de votre projet est généré, ou un fichier .pdb associé, la cause la plus courante est que votre application s’exécute déjà lorsque vous essayez de régénérer ou il est chargé dans un débogueur. Pour résoudre ce problème, arrêtez le programme et le déchargement du débogueur avant de réexécuter la génération. Si l’application est ouverte dans un autre programme, comme un éditeur de ressources, fermez-la. Dans les cas extrêmes, vous devrez peut-être utiliser le Gestionnaire des tâches pour mettre fin au processus, ou arrêter et redémarrer Visual Studio.

Les programmes antivirus souvent temporairement bloquent l’accès aux fichiers nouvellement créé, particulièrement .exe et .dll fichiers exécutables. Pour résoudre ce problème, essayez d’excluant les répertoires de génération de projet à partir de l’antivirus.

### <a name="cannot-open-a-microsoft-library-file"></a>Impossible d’ouvrir un fichier Microsoft Library

Si le fichier ne peut pas être ouvert est l’un des fichiers de bibliothèque standard fournis par Microsoft, tels que kernel32.lib, vous avez peut-être une erreur de configuration de projet ou une erreur d’installation. Vérifiez que le Kit de développement logiciel Windows a été installé et si votre projet nécessite d’autres bibliothèques de Microsoft, tels que MFC, assurez-vous que les composants MFC étaient également installés par le programme d’installation de Visual Studio. Vous pouvez exécuter le programme d’installation à nouveau pour ajouter des composants facultatifs à tout moment. Pour plus d’informations, consultez [modifier Visual Studio](/visualstudio/install/modify-visual-studio). Utilisez l’onglet composants individuels dans le programme d’installation pour choisir des bibliothèques spécifiques et les kits de développement logiciel.

Si vous générez un projet qui a été créé à l’aide d’une version antérieure de Visual Studio, les outils de plateforme et les bibliothèques de cette version ne peuvent pas être installés. Si le message d’erreur se produit pour un contrôle de version du nom de la bibliothèque comme msvcr100.lib, c’est probablement la cause. Pour résoudre ce problème, vous avez deux options : vous pouvez mettre à niveau le projet pour utiliser l’ensemble d’outils de plateforme actuelle que vous avez installé, ou vous pouvez installer l’ensemble d’outils plus anciens et générez le projet sans modification. Pour plus d’informations, consultez [la mise à niveau des projets à partir de Versions antérieures de Visual C++](../../porting/upgrading-projects-from-earlier-versions-of-visual-cpp.md) et [utiliser multi-ciblage natif dans Visual Studio pour générer des projets ancien](../../porting/use-native-multi-targeting.md).

Si vous recevez cette erreur lorsque vous générez pour une configuration ou une nouvelle plateforme cible, les bibliothèques pour cet ensemble d’outils plateforme ou la configuration de projet n’est peut-être pas installés. Vérifiez que le **ensemble d’outils de plateforme** et **Version du Kit de développement logiciel Windows** spécifié dans le [page de propriétés général](../../ide/general-property-page-project.md) pour votre projet sont installés et vérifiez que requis bibliothèques sont disponibles dans le **répertoires de bibliothèques** spécifié dans le [Page de propriétés répertoires VC ++](../../ide/vcpp-directories-property-page.md) pour vos paramètres de configuration. Il existe des paramètres distincts pour le débogage et les configurations de vente au détail, ainsi que les configurations de 32 bits et 64 bits, par conséquent, si une build fonctionne, mais une autre provoque une erreur, assurez-vous que les paramètres sont corrects et que les bibliothèques et les outils requis sont installés pour chaque vous générez la configuration.

Si vous utilisez l’IDE de Visual Studio pour générer un projet qui a été copié à partir d’un autre ordinateur, les emplacements d’installation pour les bibliothèques peuvent être différents. Vérifiez le **répertoires de bibliothèques** propriété sur le [Page de propriétés répertoires VC ++](../../ide/vcpp-directories-property-page.md) pour le projet et modifiez-le si nécessaire. Pour afficher et modifier les chemins d’accès de bibliothèque actuel dans l’environnement IDE, choisissez le contrôle de liste déroulante pour le **répertoires de bibliothèques** propriété et choisissez **modifier**. Le **évaluée valeur** section de la **répertoires de bibliothèques** boîte de dialogue répertorie les chemins d’accès actuels, recherchées les fichiers de bibliothèque.

Cette erreur peut également se produire lorsque le chemin d’accès au Kit de développement est obsolète. Si vous avez installé une version du Kit de développement qui est plus récente que la version de Visual Studio, assurez-vous que les chemins d’accès spécifié dans le [Page de propriétés répertoires VC ++](../../ide/vcpp-directories-property-page.md) sont mis à jour le nouveau SDK. Si vous utilisez l’invite de commandes développeur, assurez-vous que le fichier de commandes qui initialise les variables d’environnement est mis à jour pour les nouveaux chemins de kit de développement logiciel. Ce problème peut être évité en utilisant le programme d’installation de Visual Studio pour installer les kits de développement logiciel mis à jour.

### <a name="cannot-open-a-third-party-library-file"></a>Impossible d’ouvrir un fichier de bibliothèque tierce

Il existe plusieurs causes courantes pour résoudre ce problème :

- Le chemin d’accès à votre fichier de bibliothèque est peut-être incorrect, ou vous n’a pas spécifié elle à l’éditeur de liens.

- Vous avez peut-être installé une version 32 bits de la bibliothèque, mais que vous créez pour 64 bits, ou vice versa.

- La bibliothèque peut-être avoir des dépendances sur d’autres bibliothèques qui ne sont pas installés.

Pour résoudre un problème de chemin d’accès, vérifiez que la variable d’environnement LIB est définie et qu’il contient tous les répertoires pour les bibliothèques que vous utilisez, pour chaque configuration que vous générez. Dans l’IDE, la variable LIB est définie par le **répertoires de bibliothèques** propriété sur le [Page de propriétés répertoires VC ++](../../ide/vcpp-directories-property-page.md). Assurez-vous que tous les répertoires qui contiennent les bibliothèques que vous avez besoin sont répertoriés ici, pour chaque configuration que vous générez.

Si vous avez besoin fournir un répertoire de la bibliothèque qui substitue un répertoire de la bibliothèque standard, vous pouvez utiliser la [/LIBPATH](../../build/reference/libpath-additional-libpath.md) option sur la ligne de commande ou dans l’IDE, vous pouvez utiliser la **répertoires de bibliothèques supplémentaires** propriété dans le **propriétés de Configuration > Éditeur de liens > Général** page de propriétés pour votre projet.

Assurez-vous que vous avez installé chaque version de la bibliothèque que vous avez besoin pour les configurations que vous générez. Envisagez d’utiliser le [vcpkg](../../vcpkg.md) utilitaire de gestion pour automatiser l’installation et le programme d’installation pour de nombreuses bibliothèques courantes du package. Si possible, il est préférable de créer vos propres copies des bibliothèques tierces, pour être certain d’avoir toutes les dépendances locales qui les bibliothèques, et ils sont générés pour la même configuration que votre projet.

### <a name="cannot-open-a-file-built-by-your-project"></a>Impossible d’ouvrir un fichier généré par votre projet.

Cette erreur peut s’afficher si le fichier *nom de fichier* est généré par votre solution, mais n’existe pas lorsque l’éditeur de liens tente d’y accéder. Cela peut se produire quand un projet dépend d’un autre projet, mais les projets ne sont pas générés dans l’ordre approprié. Pour résoudre ce problème, assurez-vous que vos références de projet sont définies dans le projet qui utilise le fichier pour le fichier manquant est généré avant qu’il soit nécessaire. Pour plus d’informations, consultez [ajouter des références de projets Visual C++](../../ide/adding-references-in-visual-cpp-projects.md) et [gestion des références dans un projet](/visualstudio/ide/managing-references-in-a-project).

### <a name="cannot-open-file-cprogramobj"></a>Impossible d’ouvrir le fichier ' C:\\Program.obj'

Si vous voyez cette erreur, ou une erreur similaire impliquant un fichier .obj inattendue à la racine de votre lecteur, le problème est certainement un chemin d’accès de bibliothèque qui n’est pas encapsulée dans des guillemets doubles.

Pour résoudre ce problème pour les versions de ligne de commande, vérifiez le [/LIBPATH](../../build/reference/libpath-additional-libpath.md) option des paramètres, les chemins d’accès spécifiés dans la variable d’environnement LIB et les chemins d’accès spécifiés sur la ligne de commande et assurez-vous que vous utilisez des guillemets autour des chemins d’accès qui incluent des espaces.

Pour résoudre ce problème dans l’IDE, vérifiez le **répertoires de bibliothèques** propriété sur le [propriétés de Configuration > répertoires VC ++](../../ide/vcpp-directories-property-page.md) page de propriétés, la **répertoires de bibliothèques supplémentaires** propriété dans le **propriétés de Configuration > Éditeur de liens > Général** page de propriétés et le **dépendances supplémentaires** propriété dans le **Configuration Propriétés > Éditeur de liens > entrée** page de propriétés pour votre projet. Assurez-vous que tous les chemins d’accès qui contiennent les bibliothèques que vous avez besoin sont encapsulées dans des guillemets doubles si nécessaire.

### <a name="other-common-issues"></a>Autres problèmes courants

Cette erreur peut se produire lorsque le nom de fichier de bibliothèque ou le chemin d’accès spécifié pour l’éditeur de liens sur la ligne de commande ou dans un [#pragma comment (lib, « nom_bibliothèque »)](../../preprocessor/comment-c-cpp.md) la directive est incorrecte ou le chemin d’accès a une spécification de lecteur non valide. Vérifiez l’orthographe et l’extension de fichier et vérifiez que le fichier existe à l’emplacement spécifié.

Un autre programme a peut-être ouvert le fichier et l’éditeur de liens ne peut pas y accéder en écriture. Les programmes antivirus souvent bloquent temporairement l’accès aux fichiers qui vient d’être créés. Pour résoudre ce problème, essayez d’excluant les répertoires de génération de projet à partir de l’antivirus.

Si vous utilisez une option de génération en parallèle, il est possible que Visual Studio a verrouillé le fichier sur un autre thread. Pour résoudre ce problème, vérifiez que vous ne créez pas le même objet de code ou de la bibliothèque dans plusieurs projets, et utiliser les dépendances de génération ou de références de projet pour prendre les binaires générés dans votre projet.

Lorsque vous spécifiez des bibliothèques dans le **dépendances supplémentaires** propriété utiliser directement, des espaces pour séparer les noms de bibliothèques, pas des virgules ou des points-virgules. Si vous utilisez la **modifier** élément de menu pour ouvrir la **dépendances supplémentaires** boîte de dialogue, utilisez des sauts de ligne pour séparer les noms, non par des virgules, des points-virgules ou des espaces. Également utiliser les nouvelles lignes lorsque vous spécifiez des chemins d’accès de bibliothèque dans le **répertoires de bibliothèques** et **répertoires de bibliothèques supplémentaires** boîtes de dialogue.

Vous pouvez voir cette erreur lorsque le chemin d’accès pour *nom de fichier* s’étend sur plus de 260 caractères. Modifier les noms ou réorganiser votre structure de répertoires si nécessaire pour raccourcir les chemins d’accès aux fichiers requis.

Cette erreur peut se produire, car le fichier est trop volumineux. Objet ou bibliothèques les fichiers plus un gigaoctet taille peut provoquer des problèmes pour l’éditeur de liens 32 bits. Un correctif pour résoudre ce problème est d’utiliser l’ensemble d’outils 64 bits. Pour plus d’informations sur la façon de procéder à la ligne de commande, consultez [Comment : activer un 64 bits Visual C++ ensemble d’outils de la ligne de commande](../../build/how-to-enable-a-64-bit-visual-cpp-toolset-on-the-command-line.md). Pour plus d’informations sur la façon de procéder dans l’IDE, consultez [à l’aide de MSBuild avec le compilateur et outils 64 bits](../../build/walkthrough-using-msbuild-to-create-a-visual-cpp-project.md#using-msbuild-to-build-your-project) et ce billet de débordement de pile : [comment Visual Studio utiliser la chaîne d’outils native amd64](http://stackoverflow.com/questions/19820718/how-to-make-visual-studio-use-the-native-amd64-toolchain/23793055).

Cette erreur peut se produire si vous disposez des autorisations de fichier est insuffisante pour accéder à *nom de fichier*. Cela peut se produire si vous utilisez un compte d’utilisateur ordinaire et une tentative d’accéder aux fichiers de bibliothèque dans des répertoires protégés du système ou utilisez les fichiers copiés à partir d’autres utilisateurs qui ont leurs autorisations d’origine définie. Pour résoudre ce problème, déplacez le fichier vers un répertoire de projet accessible en écriture. Si le fichier se trouve dans un répertoire accessible en écriture, mais il possède des autorisations inaccessibles, vous pouvez utiliser une invite de commandes administrateur et exécutez la commande takeown.exe de prendre possession du fichier.

L’erreur peut se produire lorsque vous n’avez pas suffisamment d’espace disque. L’éditeur de liens utilise des fichiers temporaires dans plusieurs cas. Même si vous disposez de suffisamment d’espace disque, un lien très volumineux peut épuiser ou fragmenter l’espace disque disponible. Envisagez d’utiliser le [/OPT (optimisations)](../../build/reference/opt-optimizations.md) option ; effectuant lectures d’élimination COMDAT transitives tous les fichiers objets plusieurs fois.

Si le *nom de fichier* est nommé LNK*nnn*, qui est un nom de fichier généré par l’éditeur de liens pour un fichier temporaire, le répertoire spécifié dans la variable d’environnement TMP n’existe pas, ou plusieurs répertoires peut être spécifiée pour la variable d’environnement TMP. Chemin d’accès d’un seul répertoire doit être spécifié pour la variable d’environnement TMP.
