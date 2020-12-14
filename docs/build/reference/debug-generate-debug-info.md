---
description: En savoir plus sur:/DEBUG (générer les informations de débogage)
title: /DEBUG (Générer les informations de débogage)
ms.date: 05/16/2019
f1_keywords:
- VC.Project.VCLinkerTool.GenerateDebugInformation
- /debug
helpviewer_keywords:
- DEBUG linker option
- /DEBUG linker option
- -DEBUG linker option
- PDB files
- debugging [C++], debug information files
- generate debug info linker option
- pdb files, generating debug info
- .pdb files, generating debug info
- debugging [C++], linker option
- program databases [C++]
ms.assetid: 1af389ae-3f8b-4d76-a087-1cdf861e9103
ms.openlocfilehash: b0ef30fe7cb5eb5af0c46d6f6a8f3533d2e7d6ea
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97201818"
---
# <a name="debug-generate-debug-info"></a>/DEBUG (Générer les informations de débogage)

```
/DEBUG[:{FASTLINK|FULL|NONE}]
```

## <a name="remarks"></a>Notes

L’option **/DEBUG** permet de créer des informations de débogage pour le fichier exécutable.

L’éditeur de liens place les informations de débogage dans un fichier de base de données du programme (PDB). Il met à jour le fichier PDB lors des générations suivantes du programme.

Un exécutable (fichier .exe ou DLL) créé pour le débogage contient le nom et le chemin du fichier PDB correspondant. Le débogueur lit le nom incorporé et utilise le fichier PDB lorsque vous déboguez le programme. L’éditeur de liens utilise le nom de base du programme et l’extension .pdb pour nommer la base de données du programme et incorpore le chemin où il a été créé. Pour remplacer cette valeur par défaut, définissez [/PDB](pdb-use-program-database.md) et spécifiez un autre nom de fichier.

L’option **/DEBUG:FASTLINK** est disponible dans Visual Studio 2017 et ultérieur. Cette option laisse les informations de symboles privés dans les produits individuels de compilation utilisés pour générer le fichier exécutable. Elle génère un fichier PDB limité qui indexe dans les informations de débogage des fichiers objet et bibliothèques utilisés pour générer l’exécutable au lieu d’effectuer une copie complète. Cette option peut lier de deux à quatre fois plus vite que la génération de fichiers PDB complets et est recommandée quand vous déboguez localement et que vous disposez des produits de génération. Ce fichier PDB limité ne peut pas être utilisé pour le débogage lorsque les produits de build nécessaires ne sont pas disponibles, par exemple quand le fichier exécutable est déployé sur un autre ordinateur. Dans une invite de commandes développeur, vous pouvez utiliser l’outil mspdbcmf.exe pour générer un fichier PDB complet à partir de ce fichier PDB limité. Dans Visual Studio, utilisez les éléments de menu Projet ou Générer pour générer un fichier PDB complet afin de créer un fichier PDB complet pour le projet ou la solution.

L’option **/DEBUG:FULL** déplace toutes les informations de symboles privés à partir des produits individuels de compilation (fichiers objet et bibliothèques) dans un fichier PDB unique et peut représenter la partie la plus longue du lien. Toutefois, le fichier PDB complet peut permettre de déboguer le fichier exécutable quand aucun autre produit de build n’est disponible, par exemple quand le fichier exécutable est déployé.

L’option **/DEBUG:NONE** ne génère pas de fichier PDB.

Lorsque vous spécifiez **/DEBUG** sans aucune option supplémentaire, l’éditeur de liens utilise par défaut **/DEBUG:FULL** pour la ligne de commande et les générations Makefile pour les versions Release dans l’IDE Visual Studio et pour les versions Debug et Release dans Visual Studio 2015 et antérieur. À compter de Visual Studio 2017, le système de build dans l’IDE utilise par défaut **/DEBUG:FASTLINK** lorsque vous spécifiez l’option **/DEBUG** pour les versions Debug. Les autres valeurs par défaut restent inchangées pour assurer la compatibilité descendante.

L’option [Compatible C7](z7-zi-zi-debug-information-format.md) (/Z7) du compilateur indique au compilateur de laisser les informations de débogage dans les fichiers .obj. Vous pouvez également utiliser l’option du compilateur [Base de données du programme](z7-zi-zi-debug-information-format.md) (/Zi) pour stocker les informations de débogage dans un fichier PDB pour le fichier .obj. L’éditeur de liens recherche d’abord le fichier PDB de l’objet dans le chemin absolu écrit dans le fichier .obj, puis dans le répertoire qui contient le fichier .obj. Vous ne pouvez pas indiquer le nom ni l’emplacement du fichier PDB d’un objet à l’éditeur de liens.

[/INCREMENTAL](incremental-link-incrementally.md) est implicite lorsque /DEBUG est spécifié.

Comme /DEBUG remplace les valeurs par défaut REF par NOREF et ICF par NOICF pour l’option [/OPT](opt-optimizations.md), si vous voulez les valeurs par défaut d’origine, vous devez spécifier explicitement /OPT:REF ou /OPT:ICF.

Il n’est pas possible de créer un fichier .exe ni .dll qui contient des informations de débogage. Les informations de débogage sont toujours placées dans un fichier .obj ou .pdb.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Cliquez sur le dossier **Éditeur de liens**.

1. Cliquez sur la page de propriétés **Débogage**.

1. Modifiez la propriété **Générer des infos de débogage** pour activer la génération de fichiers PDB. Vous activez ainsi /DEBUG:FASTLINK par défaut dans Visual Studio 2017 et ultérieur.

1. Modifiez la propriété **Générer un fichier de base de données du programme complet** afin d’activer DEBUG:FULL pour la génération de fichiers PDB complets pour chaque build incrémentielle.

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

1. Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.GenerateDebugInformation%2A>.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur l’éditeur de liens MSVC](linking.md)<br/>
[Options de l’éditeur de liens MSVC](linker-options.md)
