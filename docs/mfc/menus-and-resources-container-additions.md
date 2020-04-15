---
title: 'Menus et ressources : ajouts de conteneurs'
ms.date: 11/04/2016
f1_keywords:
- IDP_OLE_INIT_FAILED
- IDP_FAILED_TO_CREATE
- VK_ESCAPE
helpviewer_keywords:
- application accelerator table [MFC]
- VK_ESCAPE key [MFC]
- IDP_FAILED_TO_CREATE macro [MFC]
- visual editing, application menus and resources
- OLE containers [MFC], menus and resources
- accelerator tables [MFC], container applications
- IDP_OLE_INIT_FAILED macro [MFC]
- CONTAIN tutorial [MFC]
- Links menu item [MFC]
ms.assetid: 425448be-8ca0-412e-909a-a3a9ce845288
ms.openlocfilehash: c8da58316f471f7b7d26e142cc1dd1ccaa6ad8b5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364790"
---
# <a name="menus-and-resources-container-additions"></a>Menus et ressources : ajouts de conteneurs

Cet article explique les modifications qui doivent être apportées aux menus et autres ressources dans une application de conteneur d’édition visuelle.

Dans les applications de conteneurs, deux types de modifications doivent être apportées : des modifications aux ressources existantes pour soutenir l’édition visuelle OLE et l’ajout de nouvelles ressources utilisées pour l’activation sur place. Si vous utilisez l’assistant d’application pour créer votre application de conteneur, ces étapes seront faites pour vous, mais elles peuvent nécessiter une personnalisation.

Si vous n’utilisez pas l’assistant d’application, vous pouvez regarder OCLIENT. RC, le script de ressources de l’application de l’échantillon OCLIENT, pour voir comment ces changements sont mis en œuvre. Voir l’échantillon MFC OLE [OCLIENT](../overview/visual-cpp-samples.md).

Les sujets abordés dans cet article sont les suivants :

- [Ajouts de menu de conteneurs](#_core_container_menu_additions)

- [Ajouts de tables d’accélérateur](#_core_container_application_accelerator_table_additions)

- [Ajouts de table à cordes](#_core_string_table_additions_for_container_applications)

## <a name="container-menu-additions"></a><a name="_core_container_menu_additions"></a>Ajouts de menu de conteneurs

Vous devez ajouter les éléments suivants au menu Edit :

|Élément|Objectif|
|----------|-------------|
|**Insérer un nouvel objet**|Ouvre la boîte de dialogue OLE Insert Object pour insérer un élément lié ou intégré dans le document.|
|**Lien pâte**|Colle un lien vers l’élément sur le Clipboard dans le document.|
|**Verbe OLE**|Appelle le verbe principal de l’élément sélectionné. Le texte de cet élément de menu change pour refléter le verbe principal de l’élément sélectionné.|
|**Liens**|Ouvre la boîte de dialogue OLE Edit Links pour modifier les éléments liés existants.|

En plus des modifications énumérées dans cet article, votre fichier source doit inclure AFXOLECL. RC, qui est nécessaire pour la mise en œuvre de la Microsoft Foundation Class Library. Insérer New Object est le seul ajout de menu requis. D’autres éléments peuvent être ajoutés, mais ceux énumérés ici sont les plus communs.

Vous devez créer un nouveau menu pour votre application de conteneurs si vous souhaitez prendre en charge l’activation sur place d’éléments contenus. Ce menu se compose du même menu Fichier et des menus pop-up fenêtre utilisés lorsque les fichiers sont ouverts, mais il a deux séparateurs placés entre eux. Ces séparateurs sont utilisés pour indiquer où l’élément serveur (composant) (application) doit placer ses menus lorsqu’il est activé. Pour plus d’informations sur cette technique de fusion de menu, voir [Menus et Ressources: Menu Fusion](../mfc/menus-and-resources-menu-merging.md).

## <a name="container-application-accelerator-table-additions"></a><a name="_core_container_application_accelerator_table_additions"></a>Ajouts de table d’accélérateur d’applications de conteneurs

De petites modifications aux ressources de table d’accélérateur d’une application de conteneurs sont nécessaires si vous soutenez l’activation sur place. Le premier changement permet à l’utilisateur d’appuyer sur la clé d’évacuation (ESC) pour annuler le mode d’édition sur place. Ajouter l’entrée suivante à la table d’accélérateur principal :

|id|Clé|Type|
|--------|---------|----------|
|ID_CANCEL_EDIT_CNTR|VK_ESCAPE|**VIRTKEY**|

Le deuxième changement consiste à créer une nouvelle table d’accélérateur qui correspond à la nouvelle ressource de menu créée pour l’activation sur place. Ce tableau a des entrées pour les menus de fichier et de fenêtre en plus de l’entrée VK_ESCAPE ci-dessus. L’exemple suivant est le tableau d’accélérateur créé pour l’activation place dans l’échantillon MFC [CONTAINER](../overview/visual-cpp-samples.md):

|id|Clé|Type|
|--------|---------|----------|
|ID_FILE_NEW|Ctrl+N|**VIRTKEY**|
|ID_FILE_OPEN|Ctrl+O|**VIRTKEY**|
|ID_FILE_SAVE|Ctrl+S|**VIRTKEY**|
|ID_FILE_PRINT|Ctrl+P|**VIRTKEY**|
|ID_NEXT_PANE|VK_F6|**VIRTKEY**|
|ID_PREV_PANE|SHIFT-VK_F6|**VIRTKEY**|
|ID_CANCEL_EDIT_CNTR|VK_ESCAPE|**VIRTKEY**|

## <a name="string-table-additions-for-container-applications"></a><a name="_core_string_table_additions_for_container_applications"></a>Ajouts de table de chaîne pour les applications de conteneurs

La plupart des modifications apportées aux tables à chaîne pour les applications de conteneurs correspondent aux éléments de menu supplémentaires mentionnés dans [les ajouts de menu de conteneurs.](#_core_container_menu_additions) Ils fournissent le texte affiché dans la barre d’état lorsque chaque élément de menu est affiché. À titre d’exemple, voici les entrées de table à cordes générées par l’assistant de l’application :

|id|String|
|--------|------------|
|IDP_OLE_INIT_FAILED|La initialisation d’OLE a échoué. Assurez-vous que les bibliothèques OLE sont la bonne version.|
|IDP_FAILED_TO_CREATE|N’a pas réussi à créer l’objet. Assurez-vous que l’objet est entré dans le registre du système.|

## <a name="see-also"></a>Voir aussi

[Menus et ressources (OLE)](../mfc/menus-and-resources-ole.md)<br/>
[Menus et ressources : ajouts de serveurs](../mfc/menus-and-resources-server-additions.md)
