---
title: Spécification des outils de génération personnalisée
ms.date: 06/05/2018
f1_keywords:
- VC.Project.VCCustomBuildTool.CustomBuildToolBeforeTargets
- VC.Project.VCCustomBuildTool.Outputs
- VC.Project.VCCustomBuildTool.Command
- VC.Project.VCCustomBuildTool.CommandLine
- VC.Project.VCCustomBuildTool.AdditionalDependencies
- VC.Project.VCCustomBuildTool.Message
- VC.Project.VCCustomBuildTool.CustomBuildToolAfterTargets
- VC.Project.VCCustomBuildTool.Description
- VC.Project.VCCustomBuildTool.AdditionalInputs
helpviewer_keywords:
- build tools (C++), specifying
- custom build tools (C++), specifying
- builds (C++), custom build tools
ms.openlocfilehash: dbce226b34503a9e8e70b6f19d9aa0c68ef487f3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62314752"
---
# <a name="specify-custom-build-tools"></a>Spécifier des outils de génération personnalisée

Un *outil de génération personnalisée* fournit au système de génération les informations nécessaires pour générer des fichiers d’entrée spécifiques. Un outil de génération personnalisée spécifie une commande à exécuter, une liste de fichiers d’entrée, une liste des fichiers de sortie générés par la commande, ainsi qu’une description facultative de l’outil.

Pour obtenir des informations générales sur les outils de génération personnalisée et les étapes de la génération personnalisée, consultez [Présentation des étapes de génération personnalisée et des événements de build](understanding-custom-build-steps-and-build-events.md).

### <a name="to-specify-a-custom-build-tool"></a>Pour spécifier un outil de génération personnalisée

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [propriétés de compilateur et de build C++ définie dans Visual Studio](working-with-project-properties.md).

1. Choisissez **Propriétés de configuration** pour activer la zone **Configuration**. Dans la zone **Configuration**, sélectionnez la configuration pour laquelle vous souhaitez spécifier un outil de génération personnalisée.

1. Dans **l’Explorateur de solutions**, sélectionnez le fichier d’entrée pour l’outil de génération personnalisée.

   Si le dossier **Outil de génération personnalisée** n’apparaît pas, l’extension du fichier que vous avez sélectionné est associée à un outil par défaut. Par exemple, l’outil par défaut pour les fichiers .c et .cpp est le compilateur. Pour remplacer un paramètre d’outil par défaut, accédez au nœud **Propriétés de configuration**, au dossier **Général**, puis dans la propriété **Type d’élément**, choisissez **Outil de génération personnalisée**. Choisissez **Appliquer** pour afficher le nœud **Outil de génération personnalisée**.

1. Dans le nœud **Outil de génération personnalisée**, dans le dossier **Général**, spécifiez les propriétés associées à l’outil de génération personnalisée :

   - Dans **Dépendances supplémentaires**, spécifiez tout autre fichier en plus de celui pour lequel l’outil de génération personnalisée est défini (le fichier associé à l’outil de génération personnalisée est implicitement considéré comme entrée de l’outil). La présence de fichiers d’entrée supplémentaires dans un outil de génération personnalisée n’est pas obligatoire. Si vous avez plusieurs entrées supplémentaires, séparez-les par des points-virgules.

      Si la date d’un fichier **Dépendances supplémentaires** est ultérieure à celle du fichier d’entrée, l’outil de génération personnalisée est exécuté. Si tous les fichiers **Dépendances supplémentaires** sont plus anciens que le fichier d’entrée et que ce dernier est plus ancien que le fichier de propriétés **Sorties**, l’outil de génération personnalisée n’est pas exécuté.

      Prenons l’exemple d’un outil de génération personnalisée qui utilise MyInput.x comme entrée et qui génère MyInput.cpp. MyInput.x inclut le fichier d’en-tête MyHeader.h. Vous pouvez spécifier MyHeader.h comme dépendance d’entrée pour MyInput.x. Le système de génération génère alors MyInput.cpp quand il est obsolète par rapport à MyInput.x ou MyHeader.h.

      Les dépendances d’entrée permettent aussi de garantir que vos outils de génération personnalisée s’exécutent dans l’ordre souhaité. Dans l’exemple précédent, supposons que MyHeader.h soit en fait la sortie d’un outil de génération personnalisée. MyHeader.h étant une dépendance de MyInput.x, le système de génération génère d’abord Myheader.h avant d’exécuter l’outil de génération personnalisée sur MyInput.x.

   - Dans **Ligne de commande**, spécifiez une commande comme vous le feriez à une invite de commandes. Spécifiez une commande ou un fichier de commandes valide, ainsi que les fichiers d’entrée ou de sortie requis. Spécifiez la commande batch **call** avant le nom d’un fichier de commandes pour garantir l’exécution de toutes les commandes suivantes.

      Il est possible de spécifier plusieurs fichiers d’entrée et de sortie symboliquement à l’aide de macros MSBuild. Pour plus d’informations sur la façon de spécifier l’emplacement des fichiers ou les noms des groupes de fichiers, consultez [macros courantes pour générer des propriétés et les commandes](reference/common-macros-for-build-commands-and-properties.md).

      Dans la mesure où le caractère « % » est réservé à MSBuild, quand vous spécifiez une variable d’environnement, il convient de remplacer chaque caractère d’échappement **%** par la séquence d’échappement hexadécimale **%25**. Par exemple, remplacez **%WINDIR%** par **%25WINDIR%25**. MSBuild remplace chaque séquence **%25** par le caractère **%** avant d’accéder à la variable d’environnement.

   - Dans **Description**, entrez un message descriptif sur cet outil de génération personnalisée. Le message est imprimé dans la fenêtre **Sortie** quand le système de génération traite cet outil.

   - Dans **Sorties**, spécifiez le nom du fichier de sortie. Cette entrée est obligatoire. Si aucune valeur n’est spécifiée pour cette propriété, l’outil de génération personnalisée ne s’exécute pas. Si un outil de génération personnalisée a plusieurs sorties, séparez les noms de fichiers par un point-virgule.

      Le nom du fichier de sortie doit être identique à celui spécifié dans la propriété **Ligne de commande**. Le système de génération de projet recherche le fichier et examine sa date. Si le fichier de sortie est plus ancien que le fichier d’entrée ou si le fichier de sortie est introuvable, l’outil de génération personnalisée est exécuté. Si tous les fichiers **Dépendances supplémentaires** sont plus anciens que le fichier d’entrée et que ce dernier est plus ancien que le fichier spécifié dans la propriété **Sorties**, l’outil de génération personnalisée n’est pas exécuté.

Si vous souhaitez que le système de génération fonctionne sur un fichier de sortie généré par l’outil de génération personnalisée, vous devez l’ajouter manuellement au projet. L’outil de génération personnalisée met à jour le fichier durant la génération.

## <a name="example"></a>Exemple

Imaginons que vous souhaitiez inclure un fichier nommé parser.l dans votre projet. Vous avez un analyseur lexical, **lexer.exe**, sur votre chemin exécutable. Vous souhaitez l’utiliser pour traiter parser.l afin de produire un fichier .c portant le même nom de base (parser.c).

Pour commencer, ajoutez parser.l et parser.c au projet. Si les fichiers n’existent pas encore, ajoutez une référence aux fichiers. Créez un outil de génération personnalisée pour parser.l et entrez ce qui suit dans la propriété **Commandes** :

> **lexer %(FullPath) .\%(Filename).c**

Cette commande exécute l’analyseur lexical sur parser.l et génère en sortie parser.c dans le répertoire du projet.

Dans la propriété **Sorties**, entrez ce qui suit :

> **.\%(Filename).c**

Quand vous générez le projet, le système de génération compare les horodatages de parser.l et de parser.c. Si parser.l est plus récent, ou si parser.c n’existe pas, le système de génération exécute la valeur de la propriété **Ligne de commande** pour mettre à jour parser.c. Dans la mesure où parser.c a également été ajouté au projet, le système de génération compile parser.c.

## <a name="see-also"></a>Voir aussi

[Macros courantes pour les propriétés et les commandes de build](reference/common-macros-for-build-commands-and-properties.md)<br>
[Dépannage des personnalisations de génération](troubleshooting-build-customizations.md)
