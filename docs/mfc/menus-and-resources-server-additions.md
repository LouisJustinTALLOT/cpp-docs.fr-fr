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
ms.openlocfilehash: 8366cd8b0376766b7914c94a24cef6598761a805
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375987"
---
# <a name="menus-and-resources-server-additions"></a>Menus et ressources : ajouts de serveurs

Cet article explique les modifications qui doivent être apportées aux menus et autres ressources dans une application serveur d’édition visuelle (composant). Une application serveur nécessite de nombreux ajouts à la structure du menu et d’autres ressources, car elle peut être commencée dans l’un des trois modes : se tenir seul, intégré ou en place. Tel que décrit dans l’article [Menus and Resources (OLE),](../mfc/menus-and-resources-ole.md) il y a un maximum de quatre ensembles de menus. Tous les quatre sont utilisés pour une application MDI plein serveur, tandis que seulement trois sont utilisés pour un mini-serveur. L’assistant d’application créera la disposition du menu nécessaire pour le type de serveur que vous voulez. Une certaine personnalisation peut être nécessaire.

Si vous n’utilisez pas l’assistant d’application, vous pouvez regarder HIERSVR. RC, le script de ressources de l’application d’échantillon MFC [HIERSVR](../overview/visual-cpp-samples.md), pour voir comment ces changements sont mis en œuvre.

Les sujets abordés dans cet article sont les suivants :

- [Ajouts de menu serveur](#_core_server_menu_additions)

- [Ajouts de tables d’accélérateur](#_core_server_application_accelerator_table_additions)

- [Ajouts de table à cordes](../mfc/menus-and-resources-container-additions.md)

- [Ajouts de miniserveurs](#_core_mini.2d.server_additions)

## <a name="server-menu-additions"></a><a name="_core_server_menu_additions"></a>Ajouts de menu serveur

Les applications serveur (composant) doivent avoir des ressources de menu ajoutées pour prendre en charge l’édition visuelle OLE. Les menus utilisés lorsque l’application est exécuté en mode autonome n’ont pas besoin d’être modifiés, mais vous devez ajouter deux nouvelles ressources de menu avant de construire l’application: l’une pour soutenir l’activation sur place et l’autre pour soutenir le serveur étant entièrement ouvert. Les deux ressources de menu sont utilisées par des applications complètes et mini-servateurs.

- Pour soutenir l’activation sur place, vous devez créer une ressource de menu qui est très similaire à la ressource de menu utilisée lorsqu’elle est exécutée en mode autonome. La différence dans ce menu est que les éléments de fichier et de fenêtre (et tous les autres éléments de menu qui traitent de l’application, et non les données) sont manquants. L’application de conteneur fournira ces éléments de menu. Pour plus d’informations sur, et un exemple de, cette technique de fusion de menu, voir l’article [Menus et Ressources: Menu Fusion .](../mfc/menus-and-resources-menu-merging.md)

- Pour prendre en charge l’activation entièrement ouverte, vous devez créer une ressource de menu presque identique à la ressource de menu utilisée lorsqu’elle est exécutée en mode autonome. La seule modification à cette ressource de menu est que certains éléments sont reformulés pour refléter le fait que le serveur fonctionne sur un élément intégré dans un document composé.

En plus des modifications énumérées dans cet article, votre fichier de ressources doit inclure AFXOLESV. RC, qui est nécessaire pour la mise en œuvre de la Microsoft Foundation Class Library. Ce fichier est dans la sous-directionnelle MFC-Inclure.

## <a name="server-application-accelerator-table-additions"></a><a name="_core_server_application_accelerator_table_additions"></a>Ajouts de table d’accélérateur d’applications de serveur

Deux nouvelles ressources de table d’accélérateur doivent être ajoutées aux applications de serveur ; elles correspondent directement aux nouvelles ressources de menu décrites précédemment. La première table d’accélérateur est utilisée lorsque l’application du serveur est activée en place. Il se compose de toutes les entrées dans la table d’accélérateur de la vue, sauf celles liées aux menus de fichier et de fenêtre.

La deuxième table est presque une copie exacte de la table d’accélérateur de la vue. Toutes les différences de modifications parallèles apportées dans le menu entièrement ouvert mentionné dans [les ajouts de menu serveur](#_core_server_menu_additions).

Par exemple, ces changements de table d’accélérateur, comparez les tables d’accélérateur IDR_HIERSVRTYPE_SRVR_IP et IDR_HIERSVRTYPE_SRVR_EMB avec IDR_MAINFRAME dans l’HIERSVR. Fichier RC inclus dans l’échantillon MFC OLE [HIERSVR](../overview/visual-cpp-samples.md). Les accélérateurs de fichiers et de fenêtre sont absents de la table sur place et des copies exactes d’entre eux sont dans la table intégrée.

## <a name="string-table-additions-for-server-applications"></a><a name="_core_string_table_additions_for_server_applications"></a>Ajouts de table de chaîne pour les applications de serveur

Un seul ajout de table de chaîne est nécessaire dans une application serveur — une chaîne pour signifier que l’initialisation OLE a échoué. À titre d’exemple, voici l’entrée de la table à cordes que l’assistant d’application génère :

|id|String|
|--------|------------|
|IDP_OLE_INIT_FAILED|La initialisation d’OLE a échoué. Assurez-vous que les bibliothèques OLE sont la bonne version.|

## <a name="miniserver-additions"></a><a name="_core_mini.2d.server_additions"></a>Ajouts de miniserveurs

Les mêmes ajouts s’appliquent aux miniservateurs que ceux énumérés ci-dessus pour les serveurs complets. Parce qu’un mini-serveur ne peut pas être exécuté en mode autonome, son menu principal est beaucoup plus petit. Le menu principal créé par l’assistant d’application n’a qu’un menu Fichier, contenant uniquement les éléments Exit and About. Les menus et accélérateurs intégrés et sur place pour les miniservateurs sont les mêmes que ceux des serveurs complets.

## <a name="see-also"></a>Voir aussi

[Menus et ressources (OLE)](../mfc/menus-and-resources-ole.md)<br/>
[Menus et ressource : fusion de menus](../mfc/menus-and-resources-menu-merging.md)
