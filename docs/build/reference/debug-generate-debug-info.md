---
title: -DEBUG (générer les informations de débogage) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.GenerateDebugInformation
- /debug
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f93c47a0f96cf0b75b453bcea97212d4ab2fd6d3
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32375725"
---
# <a name="debug-generate-debug-info"></a>/DEBUG (Générer les informations de débogage)
```  
/DEBUG[:{FASTLINK|FULL|NONE}]  
```  
  
## <a name="remarks"></a>Notes  

Le **/DEBUG** option permet de créer des informations de débogage pour le fichier exécutable.    
  
L’éditeur de liens place les informations de débogage dans un fichier du programme (PDB) de la base de données. Il met à jour le fichier PDB lors des générations suivantes du programme.  
  
Un exécutable créé pour le débogage (fichier .exe ou DLL) contient le nom et le chemin d’accès du fichier PDB correspondant. Le débogueur lit le nom incorporé et utilise le fichier PDB lors du débogage du programme. L’éditeur de liens utilise le nom de base du programme et l’extension .pdb pour nommer la base de données du programme et incorpore le chemin d’accès où il a été créé. Pour substituer cette valeur par défaut, définissez [/PDB](../../build/reference/pdb-use-program-database.md) et spécifiez un nom de fichier différent.  

Le **/Debug : Fastlink** option laisse les informations de symboles privés dans les produits individuels compilation utilisés pour générer le fichier exécutable. Il génère un fichier PDB limité qui indexe dans les informations de débogage dans les fichiers objets et les bibliothèques utilisées pour générer le fichier exécutable au lieu d’effectuer une copie complète. Cette option peut lier deux à quatre fois plus rapidement que la génération PDB complet et est recommandée quand vous effectuez un débogage localement et que vous avez les produits de build disponibles. Ce fichier PDB limité ne peut pas être utilisé pour le débogage lorsque les produits de build requis ne sont pas disponibles, par exemple lorsque le fichier exécutable est déployé sur un autre ordinateur. Dans une invite de commandes développeur, vous pouvez utiliser l’outil mspdbcmf.exe pour générer un fichier PDB complet à partir de ce fichier PDB limité. Dans Visual Studio, utilisez les éléments de menu projet ou de Build pour générer un fichier PDB complet pour créer un fichier PDB complet pour le projet ou la solution.  
  
Le **/Debug : Full** option déplace toutes les informations de symbole privé à partir des produits individuels de compilation (fichiers objets et bibliothèques) dans un fichier PDB unique et peut être la partie la plus longue du lien. Toutefois, le fichier PDB complet permet de déboguer le fichier exécutable lorsque aucun autre produit de build n’est disponibles, telles que lorsque le fichier exécutable est déployé.  
  
Le **/DEBUG : aucun** option ne génère pas un fichier PDB.  
  
Lorsque vous spécifiez **/DEBUG** avec aucune des options supplémentaires, l’éditeur de liens par défaut est **/Debug : Full** pour la ligne de commande et les builds de makefile pour les versions release de l’IDE de Visual Studio et debug et release versions de Visual Studio 2015 et versions antérieures. À compter de Visual Studio 2017, le système de génération dans l’IDE par défaut est **/Debug : Fastlink** lorsque vous spécifiez la **/DEBUG** option pour les versions debug. Autres valeurs par défaut ne sont pas modifiés pour assurer la compatibilité descendante.  
  
Du compilateur [Compatible C7](../../build/reference/z7-zi-zi-debug-information-format.md) (/ Z7) option indique au compilateur de laisser les informations de débogage dans les fichiers .obj. Vous pouvez également utiliser le [base de données du programme](../../build/reference/z7-zi-zi-debug-information-format.md) (/ Zi) du compilateur permet de stocker les informations de débogage dans un fichier PDB pour le fichier .obj. L’éditeur de liens recherche PDB de l’objet dans le chemin d’accès absolu écrit dans le fichier .obj, puis dans le répertoire qui contient le fichier .obj. Vous ne pouvez pas spécifier de nom de fichier PDB d’un objet ou l’emplacement de l’éditeur de liens.  
  
[/INCREMENTAL](../../build/reference/incremental-link-incrementally.md) est implicite lorsque /DEBUG est spécifié.  
  
/Debug modifie les valeurs par défaut pour le [/OPT](../../build/reference/opt-optimizations.md) dans l’option REF par NOREF et ICF NOICF, donc si vous souhaitez que les valeurs par défaut d’origine, vous devez spécifier explicitement/OPT : REF ou/OPT : ICF.  
  
Il n’est pas possible de créer un .exe ou .dll qui contient les informations de débogage. Déboguer des informations sont toujours placées dans un fichier .obj ou .pdb.  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio  
  
1.  Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [définition des propriétés de projet Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Cliquez sur le **l’éditeur de liens** dossier.  
  
3.  Cliquez sur le **débogage** page de propriétés.  
  
4.  Modifier la **générer des infos de débogage** propriété pour activer la génération du fichier PDB. Ainsi, / Debug : Fastlink par défaut dans Visual Studio 2017.  
  
4.  Modifier la **générer fichier de base de données de programme complet** propriété pour activer/Debug : Full pour la génération PDB complet pour chaque build incrémentielle.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation  
  
1.  Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.GenerateDebugInformation%2A>.  
  
## <a name="see-also"></a>Voir aussi  
 [Définition des Options de l’éditeur de liens](../../build/reference/setting-linker-options.md)   
 [Options de l’éditeur de liens](../../build/reference/linker-options.md)
