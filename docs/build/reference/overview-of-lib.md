---
title: Vue d'ensemble de LIB
description: Vue d’ensemble de l’utilisation et des options de l’outil bibliothèque, lib. exe.
ms.date: 02/09/2020
f1_keywords:
- Lib
helpviewer_keywords:
- LIB [C++], modes
ms.assetid: e997d423-f574-434f-8b56-25585d137ee0
ms.openlocfilehash: 5829a65ab0dc4ef193236c9ae480856a17c5874c
ms.sourcegitcommit: 8414cd91297dea88c480e208c7b5301db9972f19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77257610"
---
# <a name="overview-of-lib"></a>Vue d'ensemble de LIB

LIB (lib. exe) crée des bibliothèques standard, des bibliothèques d’importation et des fichiers d’exportation que vous pouvez utiliser avec [Link](linker-options.md) lors de la génération d’un programme. LIB s’exécute à partir d’une invite de commandes.

Vous pouvez utiliser LIB dans les modes suivants :

- [Création ou modification d’une bibliothèque COFF](managing-a-library.md)

- [Extraction d’un objet membre dans un fichier](extracting-a-library-member.md)

- [Création d’un fichier d’exportation et d’une bibliothèque d’importation](working-with-import-libraries-and-export-files.md)

Ces modes s’excluent mutuellement ; vous pouvez utiliser LIB dans un seul mode à la fois.

## <a name="lib-options"></a>Options de LIB

Le tableau suivant répertorie les options de lib. exe, ainsi qu’un lien vers des informations supplémentaires.

|Option|Description|
|-|-|
|**/DEF**|Créer une bibliothèque d’importation et un fichier d’exportation.<br/><br/>Pour plus d’informations, consultez [génération d’une bibliothèque d’importation et d’un fichier d’exportation](building-an-import-library-and-export-file.md).|
|**/ERRORREPORT**| Action déconseillée. Pour plus d’informations, consultez [Exécution de LIB](running-lib.md).|
|**/EXPORT**|   Exporte une fonction à partir de votre programme.<br/><br/>Pour plus d’informations, consultez [génération d’une bibliothèque d’importation et d’un fichier d’exportation](building-an-import-library-and-export-file.md).|
|**/EXTRACT**|   Créez un fichier objet (. obj) qui contient une copie d’un membre d’une bibliothèque existante.<br/><br/>Pour plus d’informations, consultez [extraction d’un membre de bibliothèque](extracting-a-library-member.md).|
|**/INCLUDE**|   Ajoute un symbole à la table de symboles.<br/><br/>Pour plus d’informations, consultez [génération d’une bibliothèque d’importation et d’un fichier d’exportation](building-an-import-library-and-export-file.md).|
|**/LIBPATH**|   Substitue le chemin d’accès de la bibliothèque d’environnement.<br/><br/>Pour plus d’informations, consultez [gestion d’une bibliothèque](managing-a-library.md).|
|**/LINKREPRO**|   Crée des artefacts nécessaires pour reproduire un incident lib. exe ou une erreur interne.<br/><br/>Pour plus d’informations, consultez [Exécution de LIB](running-lib.md).|
|**/LINKREPROTARGET**|   Génère uniquement les artefacts **/LINKREPRO** lorsque lib. exe est utilisé avec un fichier spécifié.<br/><br/>Pour plus d’informations, consultez [Exécution de LIB](running-lib.md).|
|**/LIST**|   Affiche des informations sur la bibliothèque de sortie à la sortie standard.<br/><br/>Pour plus d’informations, consultez [gestion d’une bibliothèque](managing-a-library.md).|
|**/LTCG**|   Provoque la génération de la bibliothèque à l’aide de la génération de code durant l’édition de liens.<br/><br/>Pour plus d’informations, consultez [Exécution de LIB](running-lib.md).|
|**/MACHINE**|   Spécifie la plateforme cible pour le programme.<br/><br/>Pour plus d’informations, consultez [Exécution de LIB](running-lib.md).|
|**/NAME**|   Lors de la création d’une bibliothèque d’importation, spécifie le nom de la DLL pour laquelle la bibliothèque d’importation est générée.<br/><br/>Pour plus d’informations, consultez [gestion d’une bibliothèque](managing-a-library.md).|
|**/NODEFAULTLIB**|   Supprime une ou plusieurs bibliothèques par défaut de la liste des bibliothèques qu’elle recherche lors de la résolution des références externes.<br/><br/>Pour plus d’informations, consultez [gestion d’une bibliothèque](managing-a-library.md).|
|**/NOLOGO**|   Supprime l’affichage du message de copyright et du numéro de version LIB et empêche l’écho des fichiers de commandes.<br/><br/>Pour plus d’informations, consultez [Exécution de LIB](running-lib.md).|
|**/OUT**|   Remplace le nom de fichier de sortie par défaut.<br/><br/>Pour plus d’informations, consultez [gestion d’une bibliothèque](managing-a-library.md).|
|**/REMOVE**|   Omet un objet de la bibliothèque de sortie.<br/><br/>Pour plus d’informations, consultez [gestion d’une bibliothèque](managing-a-library.md).|
|**/SUBSYSTEM**|   Indique au système d’exploitation comment exécuter un programme créé en établissant un lien vers la bibliothèque de sortie.<br/><br/>Pour plus d’informations, consultez [gestion d’une bibliothèque](managing-a-library.md).|
|**/VERBOSE**|   Affiche des détails sur la progression de la session, y compris les noms des fichiers. obj en cours d’ajout.<br/><br/>Pour plus d’informations, consultez [Exécution de LIB](running-lib.md).|
|**/WX**|   Considérer les avertissements comme des erreurs.<br/><br/>Pour plus d’informations, consultez [Exécution de LIB](running-lib.md).|

## <a name="see-also"></a>Voir aussi

\ de [référence lib](lib-reference.md)
[Fichiers d’entrée LIB](lib-input-files.md)\
[Fichiers de sortie LIB](lib-output-files.md)\
[Autre\ de sortie lib](other-lib-output.md)
[Structure d’une bibliothèque](structure-of-a-library.md)
