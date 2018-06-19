---
title: Exécuter LIB | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLibrarianTool.TargetMachine
- Lib
- VC.Project.VCLibrarianTool.PrintProgress
- VC.Project.VCLibrarianTool.SuppressStartupBanner
dev_langs:
- C++
helpviewer_keywords:
- -MACHINE target platform option
- command files, LIB
- MACHINE target platform option
- colon command files
- VERBOSE library manager option
- /NOLOGO library manager option
- dash option specifier
- /MACHINE target platform option
- forward slash option specifier
- -NOLOGO library manager option
- LIB [C++], running LIB
- -VERBOSE library manager option
- /VERBOSE library manager option
- command files
- NOLOGO library manager option
- slash (/)
- semicolon, command files
- / command files
ms.assetid: d54f5c81-7147-4b2c-a8db-68ce6eb1eabd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c306ba58bfef11f92d7e861272aad2aa605c8fde
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32377572"
---
# <a name="running-lib"></a>Exécution de LIB
Différentes options de ligne de commande peuvent être utilisé pour contrôler LIB.  
  
## <a name="lib-command-line"></a>Ligne de commande LIB  
 Pour exécuter LIB, tapez la commande `lib` suivi par les options et les noms de fichiers pour la tâche vous utilisez LIB à effectuer. LIB accepte également une entrée de ligne de commande dans des fichiers de commande, qui sont décrites dans la section suivante. LIB n’utilise pas une variable d’environnement.  
  
> [!NOTE]
>  Si vous êtes habitué à la LINK32.exe et LIB32.exe des outils fournis avec Microsoft Win32 logiciel Development Kit pour Windows NT, vous pouvez utilisez la commande `link32 -lib` ou de la commande `lib32` pour gérer les bibliothèques et création bibliothèques d’importation. Veillez à modifier les makefiles et batch pour utiliser le `lib` de commande à la place.  
  
## <a name="lib-command-files"></a>Fichiers de commandes LIB  
 Vous pouvez passer des arguments de ligne de commande à LIB dans un fichier de commandes à l’aide de la syntaxe suivante :  
  
```  
LIB @commandfile  
```  
  
 Le fichier `commandfile` est un fichier texte. Aucun espace ou une tabulation n’est autorisée entre le signe arobase (@) et le nom de fichier. Il n’existe aucune extension par défaut ; Vous devez spécifier le nom de fichier complet, y compris toute extension. Impossible d’utiliser des caractères génériques. Vous pouvez spécifier un chemin d’accès absolu ou relatif avec le nom de fichier.  
  
 Dans le fichier de commandes, les arguments peuvent être séparés par des espaces ou des onglets, comme la ligne de commande ; ils peuvent également être séparées par des caractères de saut de ligne. Utilisez un point-virgule ( ;) pour marquer un commentaire. LIB ignore tout le texte compris entre le point-virgule à la fin de la ligne.  
  
 Vous pouvez spécifier tout ou partie de la ligne de commande dans un fichier de commandes, et vous pouvez utiliser plusieurs fichiers de commandes dans une commande LIB. LIB accepte l’entrée de fichier de commandes comme si elle était spécifiée à cet emplacement sur la ligne de commande. Fichiers de commandes ne peuvent pas être imbriquées. LIB reproduit en écho le contenu des fichiers de commandes, sauf si l’option /NOLOGO est utilisée.  
  
## <a name="using-lib-options"></a>À l’aide des Options de LIB  
 Une option se compose d’un spécificateur d’option, qui peut être un tiret (-) ou une barre oblique (/), suivie du nom de l’option. Noms d’options ne peuvent pas être abrégés. Certaines options acceptent un argument spécifié après le signe deux-points ( :). Aucun des espaces ou des tabulations ne sont autorisées dans une spécification de l’option. Utilisez un ou plusieurs espaces ou des tabulations pour séparer les spécifications des options sur la ligne de commande. Noms des options et leurs arguments de nom de fichier ou le mot clé ne sont pas respecter la casse, mais les identificateurs utilisés comme arguments respectent la casse. LIB traite les options dans l’ordre spécifié sur la ligne de commande et dans les fichiers de commandes. Si une option est répétée avec différents arguments, le dernier traitement est prioritaire.  
  
 Les options suivantes s’appliquent à tous les modes de LIB :  
  
 / ERRORREPORT [NONE &AMP;#124; INVITE &AMP;#124; FILE D’ATTENTE &AMP;#124; ENVOI]  
 Si lib.exe échoue au moment de l’exécution, vous pouvez utiliser /ERRORREPORT pour envoyer des informations à Microsoft à propos de ces erreurs internes.  
  
 Pour plus d’informations sur/errorreport, consultez [/errorReport (signaler les erreurs du compilateur interne)](../../build/reference/errorreport-report-internal-compiler-errors.md).  
  
 /LTCG  
 Provoque la bibliothèque à l’aide de la génération de code de l’édition de liens.  Pour plus d’informations, consultez [LTCG](../../build/reference/ltcg-link-time-code-generation.md).  
  
 /MACHINE  
 Spécifie la plateforme cible pour le programme. En règle générale, vous n’avez pas besoin de spécifier/de l’ordinateur. LIB déduit le type d’ordinateur à partir des fichiers .obj. Toutefois, dans certaines circonstances, LIB ne peut pas déterminer le type d’ordinateur et émet un message d’erreur. Si une telle erreur se produit, spécifiez/de l’ordinateur. En mode/Extract, cette option est pour la vérification uniquement. Utilisez `lib /?` à la ligne de commande pour voir les types d’ordinateurs disponibles.  
  
 /NOLOGO  
 Supprime l’affichage de la LIB copyright message et numéro de version et empêche l’affichage des fichiers de commandes.  
  
 /VERBOSE  
 Affiche des détails sur la progression de la session, y compris les noms des fichiers .obj ajoutés. Les informations sont envoyées vers la sortie standard et peuvent être redirigées vers un fichier.  
  
 /WX [ : NO]  
 Considérer les avertissements comme des erreurs. Consultez [/WX (traiter les avertissements l’éditeur de liens comme des erreurs)](../../build/reference/wx-treat-linker-warnings-as-errors.md) pour plus d’informations.  
  
 Autres options s’appliquent uniquement aux modes spécifiques de LIB. Ces options sont décrites dans les sections décrivant chaque mode.  
  
## <a name="see-also"></a>Voir aussi  
 [Référence LIB](../../build/reference/lib-reference.md)