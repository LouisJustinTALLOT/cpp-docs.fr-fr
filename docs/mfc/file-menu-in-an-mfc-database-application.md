---
title: Menu Fichier dans une application de base de données MFC
ms.date: 11/04/2016
helpviewer_keywords:
- File menu
- database applications [MFC], File menu commands
ms.assetid: 92dafb75-c1b3-4860-80a0-87a83bfc36f2
ms.openlocfilehash: fbbb4382749278708e8e758f79a618d5cad0549e
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84615698"
---
# <a name="file-menu-in-an-mfc-database-application"></a>Menu Fichier dans une application de base de données MFC

Si vous créez une application de base de données MFC et que vous n’utilisez pas la sérialisation, comment interpréter les commandes ouvrir, fermer, enregistrer et enregistrer sous du menu fichier alors qu’il n’existe aucune instruction de style pour cette question, voici quelques suggestions :

- Éliminez entièrement la commande Open du menu fichier.

- Interprétez la commande Open en tant que « Open Database » et affichez l’utilisateur une liste des sources de données que votre application reconnaît.

- Interpréter la commande Open comme, par exemple, « Open Profile ». Conservez l’ouverture d’un fichier sérialisé, mais utilisez le fichier pour stocker un document sérialisé contenant des informations de « profil utilisateur », telles que les préférences de l’utilisateur, y compris son ID de connexion (éventuellement excluant le mot de passe) et la source de données avec laquelle il a récemment travaillé.

L’Assistant Application MFC prend en charge la création d’une application sans commandes de menu fichier associées à un document. Sélectionnez l’option **vue de base de données sans prise en charge des fichiers** sur la page **prise en charge des bases de données** .

Pour interpréter une commande de menu fichier d’une manière spéciale, vous devez substituer un ou plusieurs gestionnaires de commandes, principalement dans votre `CWinApp` classe dérivée de. Par exemple, si vous remplacez complètement `OnFileOpen` (qui implémente la `ID_FILE_OPEN` commande) pour signifier « Open Database : »

- N’appelez pas la version de la classe de base de `OnFileOpen` , car vous remplacez complètement l’implémentation par défaut de la commande de l’infrastructure.

- Utilisez le gestionnaire à la place pour afficher une boîte de dialogue qui répertorie les sources de données. Vous pouvez afficher une telle boîte de dialogue en appelant `CDatabase::OpenEx` ou `CDatabase::Open` avec le paramètre **null**. Cela ouvre une boîte de dialogue ODBC qui affiche toutes les sources de données disponibles sur l’ordinateur de l’utilisateur.

- Étant donné que les applications de base de données n’enregistrent généralement pas l’intégralité d’un document, vous souhaiterez sans doute supprimer les implémentations Save et Save As, sauf si vous utilisez un document sérialisé pour stocker les informations de profil. Dans le cas contraire, vous pouvez implémenter la commande Save comme, par exemple, « Commit Transaction ». Consultez la [note technique 22](tn022-standard-commands-implementation.md) pour plus d’informations sur le remplacement de ces commandes.

## <a name="see-also"></a>Voir aussi

[Sérialisation : sérialisation et entrées/sorties de base de données](serialization-serialization-vs-database-input-output.md)
