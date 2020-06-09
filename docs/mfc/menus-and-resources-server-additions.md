---
title: 'Menus et ressources : ajouts de serveurs'
ms.date: 11/04/2016
helpviewer_keywords:
- OLE visual editing servers [MFC]
- accelerator tables [MFC], server applications
- visual editing [MFC], application menus and resources
- server applications [MFC], accelerator table
- string tables [MFC], visual editing applications
- servers [MFC], menu additions
- resources [MFC], server applications
- OLE server applications [MFC], menus and resources
- string editing [MFC], visual editing applications
- IDP_OLE_INIT_FAILED macro [MFC]
- server applications [MFC], OLE menus and resources
- OLE initialization failure [MFC]
ms.assetid: 56ce9e8d-8f41-4db8-8dee-e8b0702d057c
ms.openlocfilehash: f67212dc7d4e2ab90421c7b2eee48acae4745940
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84626184"
---
# <a name="menus-and-resources-server-additions"></a>Menus et ressources : ajouts de serveurs

Cet article explique les modifications qui doivent être apportées aux menus et autres ressources dans une application serveur d’édition visuelle (composant). Une application serveur requiert de nombreux ajouts à la structure de menu et à d’autres ressources, car elle peut être démarrée dans l’un des trois modes : autonome, incorporé ou en place. Comme décrit dans l’article [menus et ressources (OLE)](menus-and-resources-ole.md) , il existe un maximum de quatre jeux de menus. Les quatre sont utilisés pour une application de serveur complet MDI, tandis que seules trois sont utilisées pour un mini-serveur. L’Assistant application crée la disposition de menu nécessaire pour le type de serveur souhaité. Certaines personnalisations peuvent être nécessaires.

Si vous n’utilisez pas l’Assistant Application, vous souhaiterez peut-être consulter HIERSVR. RC, le script de ressources de l’exemple d’application MFC [HIERSVR](../overview/visual-cpp-samples.md), pour voir comment ces modifications sont implémentées.

Les sujets abordés dans cet article sont les suivants :

- [Ajouts au menu serveur](#_core_server_menu_additions)

- [Ajouts de tables d’accélérateurs](#_core_server_application_accelerator_table_additions)

- [Ajouts de tables de chaînes](menus-and-resources-container-additions.md)

- [Ajouts de mini-port](#_core_mini.2d.server_additions)

## <a name="server-menu-additions"></a><a name="_core_server_menu_additions"></a>Ajouts au menu serveur

Des ressources de menu doivent être ajoutées aux applications serveur (composant) pour prendre en charge la modification visuelle OLE. Les menus utilisés lorsque l’application est exécutée en mode autonome n’ont pas besoin d’être modifiés, mais vous devez ajouter deux nouvelles ressources de menu avant de générer l’application : une pour prendre en charge l’activation sur place et une autre pour prendre en charge le serveur en cours d’ouverture complète. Les deux ressources de menu sont utilisées par les applications complètes et mini-mini.

- Pour prendre en charge l’activation sur place, vous devez créer une ressource de menu qui est très similaire à la ressource de menu utilisée lorsqu’elle est exécutée en mode autonome. La différence dans ce menu est que les éléments de fichier et de fenêtre (et tous les autres éléments de menu qui traitent l’application, et non les données) sont manquants. L’application conteneur fournit ces éléments de menu. Pour plus d’informations sur et pour obtenir un exemple de cette technique de fusion de menus, consultez l’article [menus et ressources : fusion de menus](menus-and-resources-menu-merging.md).

- Pour prendre en charge l’activation entièrement ouverte, vous devez créer une ressource de menu presque identique à la ressource de menu utilisée lorsqu’elle est exécutée en mode autonome. La seule modification de cette ressource de menu est que certains éléments sont reformulés pour refléter le fait que le serveur fonctionne sur un élément incorporé dans un document composé.

Outre les modifications mentionnées dans cet article, votre fichier de ressources doit inclure AFXOLESV. RC, qui est requis pour l’implémentation de bibliothèque MFC (Microsoft Foundation Class). Ce fichier se trouve dans le sous-répertoire MFC\Include

## <a name="server-application-accelerator-table-additions"></a><a name="_core_server_application_accelerator_table_additions"></a>Ajouts de tables d’accélérateurs d’application serveur

Deux nouvelles ressources de table d’accélérateurs doivent être ajoutées aux applications serveur ; ils correspondent directement aux nouvelles ressources de menu décrites précédemment. La première table d’accélérateurs est utilisée lorsque l’application serveur est activée sur place. Il se compose de toutes les entrées de la table d’accélérateurs de la vue, à l’exception de celles qui sont liées aux menus fichier et fenêtre.

La deuxième table est presque une copie exacte de la table d’accélérateurs de la vue. Toutes les différences entre les modifications parallèles effectuées dans le menu complet mentionné dans [ajouts au menu serveur](#_core_server_menu_additions).

Pour obtenir un exemple de ces modifications dans la table d’accélérateurs, comparez les tables d’accélérateurs IDR_HIERSVRTYPE_SRVR_IP et IDR_HIERSVRTYPE_SRVR_EMB avec les IDR_MAINFRAME dans HIERSVR. Fichier RC inclus dans l’exemple [HIERSVR](../overview/visual-cpp-samples.md)OLE MFC. Les accélérateurs de fichier et de fenêtre sont absents de la table sur place et les copies exactes de ceux-ci se trouvent dans la table incorporée.

## <a name="string-table-additions-for-server-applications"></a><a name="_core_string_table_additions_for_server_applications"></a>Ajouts de tables de chaînes pour les applications serveur

Un seul ajout de table de chaînes est nécessaire dans une application serveur (chaîne pour signifier que l’initialisation d’OLE a échoué). À titre d’exemple, voici l’entrée de table de chaînes générée par l’Assistant Application :

|id|String|
|--------|------------|
|IDP_OLE_INIT_FAILED|Échec de l’initialisation OLE. Assurez-vous que la version des bibliothèques OLE est correcte.|

## <a name="miniserver-additions"></a><a name="_core_mini.2d.server_additions"></a>Ajouts de mini-port

Les mêmes ajouts s’appliquent à miniservers comme indiqué ci-dessus pour les serveurs complets. Comme un mini-ordinateur ne peut pas être exécuté en mode autonome, son menu principal est bien plus petit. Le menu principal créé par l’Assistant application n’a qu’un menu fichier, qui contient uniquement les éléments quitter et à propos de. Les menus et les accélérateurs intégrés et sur place pour miniservers sont les mêmes que ceux des serveurs complets.

## <a name="see-also"></a>Voir aussi

[Menus et ressources (OLE)](menus-and-resources-ole.md)<br/>
[Menus et ressource : fusion de menus](menus-and-resources-menu-merging.md)
