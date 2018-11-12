---
title: 'Comment : organiser des fichiers de sortie de projet pour les générations'
ms.date: 11/04/2016
helpviewer_keywords:
- Visual C++, output files
- output files, organizing
ms.assetid: 521d95ea-2dcc-4da0-b5eb-ac3e57941446
ms.openlocfilehash: 9dd70f52c79d00282122f935b19770b973901103
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50575966"
---
# <a name="how-to-organize-project-output-files-for-builds"></a>Comment : organiser des fichiers de sortie de projet pour les générations

Cette rubrique décrit les bonnes pratiques relatives à l’organisation de fichiers de sortie de projet. Des erreurs de build peuvent se produire si vous ne configurez pas correctement les fichiers de sortie de projet. Cette rubrique décrit également les avantages et les inconvénients de chaque méthode d’organisation de vos fichiers de sortie de projet.

## <a name="referencing-clr-assemblies"></a>Référencement d’assemblys CLR

#### <a name="to-reference-assemblies-with-using"></a>Pour référencer des assemblys avec #using

1. Vous pouvez référencer un assembly directement à partir de votre code à l’aide de la directive #using, par exemple `#using <System.Data.dll>`. Pour plus d’informations, consultez [#using, directive](../preprocessor/hash-using-directive-cpp.md).

   Le fichier spécifié peut être un fichier .dll, .exe, .netmodule ou .obj, à condition qu’il soit en MSIL. Le composant référencé peut être généré dans n’importe quel langage. Cette option vous permet d’accéder à IntelliSense puisque les métadonnées sont extraites de MSIL. Le fichier en question doit être dans le chemin du projet. Sinon, ce dernier ne peut pas être compilé et IntelliSense n’est pas disponible. Pour déterminer facilement si le fichier est dans le chemin, cliquez avec le bouton droit sur la ligne #using et choisissez la commande **Ouvrir le document**. Vous êtes averti si le fichier est introuvable.

   Si vous ne souhaitez pas indiquer le chemin complet du fichier, utilisez l’option de compilateur **/AI** pour modifier le chemin de recherche pour les références #using. Pour plus d’informations, consultez l’article [/AI (Spécifier les répertoires des métadonnées)](../build/reference/ai-specify-metadata-directories.md).

#### <a name="to-reference-assemblies-with-fu"></a>Pour référencer des assemblys avec /FU

1. Au lieu de référencer un assembly directement à partir d’un fichier de code comme décrit ci-dessus, vous pouvez utiliser l’option de compilateur **/FU**. L’avantage de cette méthode, c’est que vous n’êtes pas obligé d’ajouter une instruction #using séparée à chaque fichier faisant référence à un assembly donné.

   Pour définir cette option, ouvrez les **Pages de propriétés** du projet. Développez les nœuds **Propriétés de configuration** et **C/C++**, puis sélectionnez **Avancé**. Ajoutez les assemblys désirés en regard de **Fichiers #using forcés**. Pour plus d’informations, consultez l’article [/FU (Nom du fichier #using imposé)](../build/reference/fu-name-forced-hash-using-file.md).

#### <a name="to-reference-assemblies-with-add-new-reference"></a>Pour référencer des assemblys avec Ajouter une nouvelle référence

1. C’est le moyen le plus simple d’utiliser des assemblys CLR. Veillez d’abord à compiler le projet avec l’option de compilateur **/clr**. Cliquez ensuite avec le bouton droit sur le projet dans **l’Explorateur de solutions**, puis sélectionnez **Ajouter**, **Références**. La boîte de dialogue **Pages de propriétés** s’affiche.

1. Dans la boîte de dialogue **Pages de propriétés**, sélectionnez **Ajouter une nouvelle référence**. La boîte de dialogue qui s’affiche répertorie tous les assemblys (.NET, COM, etc.) disponibles dans le projet actif. Sélectionnez l’assembly désiré, puis cliquez sur **OK**.

   Une fois qu’une référence de projet est définie, les dépendances correspondantes sont gérées automatiquement. Par ailleurs, étant donné que les métadonnées font partie d’un assembly, vous n’êtes pas obligé d’ajouter un fichier d’en-tête ni de prototyper les éléments utilisés à partir d’assemblys managés.

## <a name="referencing-native-dlls-or-static-libraries"></a>Référencement de DLL natives ou de bibliothèques statiques

#### <a name="to-reference-native-dlls-or-static-libraries"></a>Pour référencer des DLL natives ou des bibliothèques statiques

1. Référencez le fichier d’en-tête approprié dans votre code à l’aide de la directive #include. Le fichier d’en-tête doit être dans le chemin include ou doit faire partie du projet actif. Pour plus d’informations, consultez [#include, directive (C/C++)](../preprocessor/hash-include-directive-c-cpp.md).

1. Vous pouvez également définir des dépendances de projet. La définition de dépendances de projet garantit deux choses. Premièrement, comme les projets sont générés dans le bon ordre, ils peuvent toujours trouver les fichiers dépendants dont ils ont besoin. Deuxièmement, le répertoire de sortie du projet dépendant est ajouté implicitement au chemin, ce qui facilite la recherche des fichiers durant l’édition de liens.

1. Pour déployer l’application, vous devez placer la DLL dans un emplacement approprié. Vous avez le choix entre les options suivantes :

   1. Chemin identique à celui de l’exécutable.

   1. N’importe où dans le chemin système (variable d’environnement **path**).

   1. Dans l’assembly côte à côte. Pour plus d’informations, consultez [Génération d’assemblys côte à côte C/C++](../build/building-c-cpp-side-by-side-assemblies.md).

## <a name="working-with-multiple-projects"></a>Utilisation de plusieurs fichiers

Par défaut, quand les projets sont générés, tous les fichiers de sortie sont créés dans un sous-répertoire du répertoire du projet. Le répertoire est nommé en fonction de la configuration de build (par exemple, Debug ou Release). Pour que les projets frères se référencent entre eux, chaque projet doit ajouter explicitement à son chemin les répertoires de sortie de l’autre projet (assurant ainsi la réussite de la liaison). Cette opération est effectuée automatiquement quand vous définissez les dépendances du projet. Mais si vous n’utilisez pas de dépendances, vous devez gérer ceci avec soin car les builds peuvent devenir très difficiles à gérer. Par exemple, lorsqu’un projet a des configurations Debug et Release et qu’il comprend une bibliothèque externe d’un projet frère, il doit utiliser un fichier de bibliothèque différent en fonction de la configuration générée. Le codage de ces chemins de manière irréversible peut donc s’avérer difficile.

Tous les fichiers de sortie essentiels (exécutables, fichiers d’éditeur de liens incrémentiels, fichiers PDB, etc.) sont copiés dans un répertoire de solution commun. Quand vous travaillez avec une solution contenant plusieurs projets C++ avec des configurations équivalentes, tous les fichiers de sortie sont centralisés pour simplifier la liaison et le déploiement. Vous avez donc l’assurance que leur application/bibliothèque fonctionnera comme prévu puisque ces fichiers sont conservés ensemble (leur présence dans le chemin est garantie).

L’emplacement des fichiers de sortie peut être un problème majeur en cas de déploiement sur un environnement de production. Durant l’exécution de projets dans l’IDE, les chemins aux bibliothèques incluses ne sont pas nécessairement les mêmes que dans l’environnement de production. Par exemple, si vous avez `#using "../../lib/debug/mylib.dll"` dans votre code et que vous déployez ensuite mylib.dll à une position relative différente, l’application échoue au moment de l’exécution. Pour que ce problème ne se produise pas, évitez d’utiliser des chemins relatifs dans les instructions #include de votre code. Il est préférable de veiller à ce que les fichiers nécessaires figurent dans le chemin de build du projet et que les fichiers de production correspondants soient bien placés.

#### <a name="how-to-specify-where-output-files-go"></a>Comment spécifier la destination des fichiers de sortie

1. L’emplacement des paramètres de sortie du projet est indiqué dans les **Pages de propriétés** du projet. Développez le nœud en regard de **Propriétés de Configuration** et sélectionnez **Général**. L’emplacement de sortie est spécifié en regard de **Répertoire de sortie**. Pour plus d'informations, consultez [Général, page de propriétés (Projet)](../ide/general-property-page-project.md).

## <a name="see-also"></a>Voir aussi

[Types de projets Visual C++](../ide/visual-cpp-project-types.md)