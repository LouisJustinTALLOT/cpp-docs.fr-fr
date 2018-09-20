---
title: Menu fichier dans une Application de base de données MFC | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- File menu
- database applications [MFC], File menu commands
ms.assetid: 92dafb75-c1b3-4860-80a0-87a83bfc36f2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5fe90e01ec53711f47418d4512262e2e05e62f26
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46425130"
---
# <a name="file-menu-in-an-mfc-database-application"></a>Menu Fichier dans une application de base de données MFC

Si vous créez une application de base de données MFC et ne pas utiliser la sérialisation, comment doit interpréter l’ouvrir, fermer, enregistrer et enregistrer en tant que commandes dans le menu fichier s’il n’existe aucun règles de style pour cette question, voici quelques suggestions :

- Éliminer entièrement commande Ouvrir du menu fichier.

- Interpréter la commande Ouvrir en tant que « base de données ouverte » et afficher la liste des sources de données que votre application reconnaît l’utilisateur.

- Interprétation de la commande Ouvrir comme, par exemple, « ouvrir de profil ». Conserver les ouvrir pour ouvrir un fichier sérialisé, utiliser, mais le fichier pour stocker un document sérialisé contenant des informations de « profil utilisateur », telles que les préférences de l’utilisateur, y compris son ou son ID de connexion (éventuellement sans le mot de passe) et les source de données il ou elle plus récemment travaillé avec.

L’Assistant Application MFC prend en charge la création d’une application avec aucune commande de menu fichier liées aux documents. Sélectionnez le **vue sans prise en charge du fichier de base de données** option sur le **prennent en charge de la base de données** page.

Pour interpréter une commande de menu fichier d’une façon particulière, vous devez substituer un ou plusieurs gestionnaires de commandes, principalement dans votre `CWinApp`-classe dérivée. Par exemple, si vous substituez complètement `OnFileOpen` (qui implémente le `ID_FILE_OPEN` commande) comme signifiant « base de données ouvert : »

- N’appelez pas la version de la classe de base de `OnFileOpen`, étant donné que vous remplacez complètement l’implémentation par défaut de la commande.

- Utilisez le gestionnaire à la place pour afficher une boîte de dialogue répertoriant les sources de données. Vous pouvez afficher cette boîte de dialogue en appelant `CDatabase::OpenEx` ou `CDatabase::Open` avec le paramètre **NULL**. Cela ouvre une boîte de dialogue ODBC qui affiche toutes les sources de données disponibles sur l’ordinateur de l’utilisateur.

- Étant donné que les applications de base de données en général, n’enregistrement pas un document entier, vous souhaiterez probablement supprimer l’enregistrement et l’enregistrer en tant que des implémentations, sauf si vous utilisez un document sérialisé pour stocker les informations de profil. Sinon, vous pouvez implémenter la commande Enregistrer sous, par exemple, « validation de transaction ». Consultez [Note technique 22](../mfc/tn022-standard-commands-implementation.md) pour plus d’informations sur la substitution de ces commandes.

## <a name="see-also"></a>Voir aussi

[Sérialisation : sérialisation et Base de données d’entrée/sortie](../mfc/serialization-serialization-vs-database-input-output.md)

