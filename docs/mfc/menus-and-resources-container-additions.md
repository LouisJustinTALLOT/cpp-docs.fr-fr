---
description: 'En savoir plus sur : menus et ressources : ajouts de conteneurs'
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
ms.openlocfilehash: e32167e66693587a32732c1c20fc6d85d3010ecb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97253362"
---
# <a name="menus-and-resources-container-additions"></a>Menus et ressources : ajouts de conteneurs

Cet article explique les modifications qui doivent être apportées aux menus et autres ressources dans une application de conteneur d’édition visuelle.

Dans les applications de conteneur, vous devez effectuer deux types de modifications : les modifications apportées aux ressources existantes pour prendre en charge l’édition visuelle OLE et l’ajout de nouvelles ressources utilisées pour l’activation sur place. Si vous utilisez l’Assistant application pour créer votre application conteneur, ces étapes sont effectuées pour vous, mais elles peuvent nécessiter une certaine personnalisation.

Si vous n’utilisez pas l’Assistant Application, vous souhaiterez peut-être consulter OCLIENT. RC, le script de ressources de l’exemple d’application OCLIENT, pour voir comment ces modifications sont implémentées. Consultez l’exemple MFC OLE [OCLIENT](../overview/visual-cpp-samples.md).

Les sujets abordés dans cet article sont les suivants :

- [Ajouts au menu conteneur](#_core_container_menu_additions)

- [Ajouts de tables d’accélérateurs](#_core_container_application_accelerator_table_additions)

- [Ajouts de tables de chaînes](#_core_string_table_additions_for_container_applications)

## <a name="container-menu-additions"></a><a name="_core_container_menu_additions"></a> Ajouts au menu conteneur

Vous devez ajouter les éléments suivants au menu Edition :

|Élément|Objectif|
|----------|-------------|
|**Insérer un nouvel objet**|Ouvre la boîte de dialogue Insérer un objet OLE pour insérer un élément lié ou incorporé dans le document.|
|**Coller le lien**|Colle un lien vers l’élément du presse-papiers dans le document.|
|**Verbe OLE**|Appelle le verbe principal de l’élément sélectionné. Le texte de cet élément de menu change pour refléter le verbe principal de l’élément sélectionné.|
|**Liens**|Ouvre la boîte de dialogue OLE modifier les liens pour modifier les éléments liés existants.|

En plus des modifications mentionnées dans cet article, votre fichier source doit inclure AFXOLECL. RC, qui est requis pour l’implémentation de bibliothèque MFC (Microsoft Foundation Class). Insert New Object est le seul ajout de menu requis. D’autres éléments peuvent être ajoutés, mais ceux répertoriés ici sont les plus courants.

Vous devez créer un nouveau menu pour votre application conteneur si vous souhaitez prendre en charge l’activation sur place des éléments contenus. Ce menu comprend les mêmes menus contextuels de menu de fichier et de fenêtre que ceux utilisés lorsque des fichiers sont ouverts, mais avec deux séparateurs placés entre eux. Ces séparateurs sont utilisés pour indiquer l’emplacement où l’élément de serveur (composant) (application) doit placer ses menus lorsqu’il est activé sur place. Pour plus d’informations sur cette technique de fusion de menus, consultez [menus et ressources : fusion de menus](menus-and-resources-menu-merging.md).

## <a name="container-application-accelerator-table-additions"></a><a name="_core_container_application_accelerator_table_additions"></a> Ajouts de tables d’accélérateurs d’application de conteneur

Les petites modifications apportées aux ressources de la table d’accélérateurs d’une application conteneur sont nécessaires si vous prenez en charge l’activation sur place. La première modification permet à l’utilisateur d’appuyer sur la touche ÉCHAP pour annuler le mode d’édition sur place. Ajoutez l’entrée suivante à la table d’accélérateurs principale :

|id|Clé|Type|
|--------|---------|----------|
|ID_CANCEL_EDIT_CNTR|VK_ESCAPE|**VIRTKEY**|

La deuxième modification consiste à créer une nouvelle table d’accélérateurs qui correspond à la nouvelle ressource de menu créée pour l’activation sur place. Ce tableau contient des entrées pour les menus fichier et fenêtre en plus de l’entrée VK_ESCAPE ci-dessus. L’exemple suivant est la table d’accélérateurs créée pour l’activation sur place dans le [conteneur](../overview/visual-cpp-samples.md)d’exemples MFC :

|id|Clé|Type|
|--------|---------|----------|
|ID_FILE_NEW|Ctrl+N|**VIRTKEY**|
|ID_FILE_OPEN|Ctrl+O|**VIRTKEY**|
|ID_FILE_SAVE|Ctrl+S|**VIRTKEY**|
|ID_FILE_PRINT|Ctrl+P|**VIRTKEY**|
|ID_NEXT_PANE|VK_F6|**VIRTKEY**|
|ID_PREV_PANE|MAJ + VK_F6|**VIRTKEY**|
|ID_CANCEL_EDIT_CNTR|VK_ESCAPE|**VIRTKEY**|

## <a name="string-table-additions-for-container-applications"></a><a name="_core_string_table_additions_for_container_applications"></a> Ajouts de tables de chaînes pour les applications de conteneur

La plupart des modifications apportées aux tables de chaînes pour les applications de conteneur correspondent aux éléments de menu supplémentaires mentionnés dans [ajouts de menu de conteneur](#_core_container_menu_additions). Ils fournissent le texte affiché dans la barre d’État lorsque chaque élément de menu est affiché. À titre d’exemple, Voici les entrées de table de chaînes générées par l’Assistant Application :

|id|String|
|--------|------------|
|IDP_OLE_INIT_FAILED|Échec de l’initialisation OLE. Assurez-vous que la version des bibliothèques OLE est correcte.|
|IDP_FAILED_TO_CREATE|Échec de la création de l’objet. Assurez-vous que l’objet est entré dans le registre système.|

## <a name="see-also"></a>Voir aussi

[Menus et ressources (OLE)](menus-and-resources-ole.md)<br/>
[Menus et ressources : ajouts de serveurs](menus-and-resources-server-additions.md)
