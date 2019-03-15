---
title: Vue d'ensemble de LIB
ms.date: 11/04/2016
f1_keywords:
- Lib
helpviewer_keywords:
- LIB [C++], modes
ms.assetid: e997d423-f574-434f-8b56-25585d137ee0
ms.openlocfilehash: 97d7b8892574fbe485a8d6c5e344e4a77aaf8519
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57820219"
---
# <a name="overview-of-lib"></a>Vue d'ensemble de LIB

LIB crée des bibliothèques standard, des bibliothèques d’importation et exportation de fichiers, vous pouvez utiliser avec [lien](linker-options.md) lors de la création d’un programme. LIB s’exécute à partir d’une invite de commandes.

Vous pouvez utiliser LIB dans les modes suivants :

- [Création ou modification d’une bibliothèque COFF](managing-a-library.md)

- [Extraction d’un objet membre vers un fichier](extracting-a-library-member.md)

- [Création d’un fichier d’exportation et d’une bibliothèque d’importation](working-with-import-libraries-and-export-files.md)

Ces modes sont mutuellement exclusives ; Vous pouvez utiliser LIB dans un seul mode à la fois.

## <a name="lib-options"></a>Options de lib

Le tableau suivant répertorie les options de lib.exe, avec un lien vers plus d’informations.

|Option|Description|
|-|-|
|**/DEF**|Créer une bibliothèque d’importation et d’un fichier d’exportation.<br/><br/>Pour plus d’informations, consultez [génération d’une bibliothèque d’importation et d’un fichier d’exportation](building-an-import-library-and-export-file.md).|
|**/ERRORREPORT**|   Envoyer des informations à Microsoft sur les erreurs internes avec lib.exe.<br/><br/>Pour plus d’informations, consultez [en cours d’exécution de LIB](running-lib.md).|
|**/EXPORT**|   Exporte une fonction à partir de votre programme.<br/><br/>Pour plus d’informations, consultez [génération d’une bibliothèque d’importation et d’un fichier d’exportation](building-an-import-library-and-export-file.md).|
|**/EXTRACT**|   Créez un fichier objet (.obj) qui contient une copie d’un membre d’une bibliothèque existante.<br/><br/>Pour plus d’informations, consultez [extraction d’un membre de bibliothèque](extracting-a-library-member.md).|
|**/INCLUDE**|   Ajoute un symbole à la table de symboles.<br/><br/>Pour plus d’informations, consultez [génération d’une bibliothèque d’importation et d’un fichier d’exportation](building-an-import-library-and-export-file.md).|
|**/LIBPATH**|   Substitue le chemin d’accès de la bibliothèque d’environnement.<br/><br/>Pour plus d’informations, consultez [gestion d’une bibliothèque](managing-a-library.md).|
|**/LIST**|   Affiche des informations sur la bibliothèque de sortie vers la sortie standard.<br/><br/>Pour plus d’informations, consultez [gestion d’une bibliothèque](managing-a-library.md).|
|**/LTCG**|   Provoque la bibliothèque à l’aide de la génération de code du moment de la liaison.<br/><br/>Pour plus d’informations, consultez [en cours d’exécution de LIB](running-lib.md).|
|**/MACHINE**|   Spécifie la plateforme cible pour le programme.<br/><br/>Pour plus d’informations, consultez [en cours d’exécution de LIB](running-lib.md).|
|**/NAME**|   Lorsque vous créez une bibliothèque d’importation, spécifie le nom de la DLL pour laquelle la bibliothèque d’importation est générée.<br/><br/>Pour plus d’informations, consultez [gestion d’une bibliothèque](managing-a-library.md).|
|**/NODEFAULTLIB**|   Supprime une ou plusieurs bibliothèques par défaut de la liste des bibliothèques qu’elle parcourt lors de la résolution des références externes.<br/><br/>Pour plus d’informations, consultez [gestion d’une bibliothèque](managing-a-library.md).|
|**/NOLOGO**|   Supprime l’affichage de la LIB copyright message et numéro de version et empêche la répercussion des fichiers de commandes.<br/><br/>Pour plus d’informations, consultez [en cours d’exécution de LIB](running-lib.md).|
|**/OUT**|   Remplace le nom de fichier de sortie par défaut.<br/><br/>Pour plus d’informations, consultez [gestion d’une bibliothèque](managing-a-library.md).|
|**/ SUPPRIMER**|   Omet un objet à partir de la bibliothèque de sortie.<br/><br/>Pour plus d’informations, consultez [gestion d’une bibliothèque](managing-a-library.md).|
|**/SUBSYSTEM**|   Indique le système d’exploitation comment exécuter un programme créé par la liaison à la bibliothèque de sortie.<br/><br/>Pour plus d’informations, consultez [gestion d’une bibliothèque](managing-a-library.md).|
|**/VERBOSE**|   Affiche des détails sur la progression de la session, y compris les noms des fichiers .obj en cours d’ajout.<br/><br/>Pour plus d’informations, consultez [en cours d’exécution de LIB](running-lib.md).|
|**/WX**|   Considérer les avertissements comme des erreurs.<br/><br/>Pour plus d’informations, consultez [en cours d’exécution de LIB](running-lib.md).|

## <a name="see-also"></a>Voir aussi

[Référence LIB](lib-reference.md)<br/>
[Fichiers d’entrée LIB](lib-input-files.md)<br/>
[Fichiers de sortie LIB](lib-output-files.md)<br/>
[Autre sortie LIB](other-lib-output.md)<br/>
[Structure d’une bibliothèque](structure-of-a-library.md)
