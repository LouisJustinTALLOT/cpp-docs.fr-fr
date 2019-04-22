---
title: 'Menus et ressources : Ajouts de conteneurs'
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
ms.openlocfilehash: b1a74fef743592d3d052226dac926fc7ddc58578
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58770341"
---
# <a name="menus-and-resources-container-additions"></a>Menus et ressources : Ajouts de conteneurs

Cet article décrit les modifications qui doivent être apportées aux menus et aux autres ressources dans une application conteneur d’édition visuelle.

Dans les applications de conteneur, deux types de modifications doivent être apportées : modifications apportées à des ressources existantes pour prendre en charge la modification visuelle OLE et l’ajout de nouvelles ressources permettant l’activation sur place. Si vous utilisez l’Assistant application pour créer votre application de conteneur, ces étapes seront effectuées pour vous, mais ils peuvent nécessitent une personnalisation.

Si vous n’utilisez pas l’Assistant application, vous souhaiterez examiner OCLIENT. RC, le script de ressources pour l’exemple d’application OCLIENT, pour voir comment ces modifications sont implémentées. Consultez l’exemple OLE MFC [OCLIENT](../overview/visual-cpp-samples.md).

Les sujets abordés dans cet article sont les suivantes :

- [Ajouts au Menu du conteneur](#_core_container_menu_additions)

- [Ajouts de Table d’accélérateurs](#_core_container_application_accelerator_table_additions)

- [Ajouts de Table de chaînes](#_core_string_table_additions_for_container_applications)

##  <a name="_core_container_menu_additions"></a> Ajouts au Menu du conteneur

Vous devez ajouter les éléments suivants au menu Edition :

|Élément|Objectif|
|----------|-------------|
|**Insérer le nouvel objet**|Ouvre la boîte de dialogue OLE insérer un objet pour insérer un élément lié ou incorporé dans le document.|
|**Coller la liaison**|Colle un lien vers l’élément dans le Presse-papiers dans le document.|
|**Verbe OLE**|Appelle le verbe principal de l’élément sélectionné. Le texte de cet élément de menu change pour refléter le verbe principal de l’élément sélectionné.|
|**Links**|Ouvre la boîte de dialogue OLE modifier les liens pour modifier les éléments liés existants.|

Outre les modifications répertoriées dans cet article, votre fichier source doit inclure AFXOLECL. RC, qui est requis pour l’implémentation de la bibliothèque Microsoft Foundation Class. Insérer un nouvel objet est l’ajout de menu requis uniquement. Autres éléments peuvent être ajoutés, mais ceux répertoriés ici sont les plus courantes.

Si vous souhaitez prendre en charge l’activation sur place d’éléments de relation contenant-contenus, vous devez créer un nouveau menu pour votre application conteneur. Ce menu comprend les même menu fichier et les menus contextuels de fenêtre utilisés lorsque les fichiers sont ouverts, mais il comporte deux séparateurs placés entre eux. Ces séparateurs sont utilisés pour indiquer où l’élément du serveur (composant) (application) doit placer ses menus lorsqu’activé sur place. Pour plus d’informations sur cette technique de fusion de menus, consultez [Menus et ressources : Fusion de menus](../mfc/menus-and-resources-menu-merging.md).

##  <a name="_core_container_application_accelerator_table_additions"></a> Ajouts à la Table conteneur Application Accelerator

Petites modifications apportées aux ressources de table d’accélérateurs d’une application de conteneur sont nécessaires si vous prenez en charge l’activation sur place. La première modification permet à l’utilisateur d’appuyer sur la touche ÉCHAP pour annuler le mode d’édition sur place. Ajoutez l’entrée suivante à la table d’accélérateurs principale :

|Id|Touche|Type|
|--------|---------|----------|
|ID_CANCEL_EDIT_CNTR|VK_ESCAPE|**VIRTKEY**|

La deuxième modification consiste à créer une nouvelle table d’accélérateurs qui correspond à la nouvelle ressource de menu créée pour l’activation sur place. Cette table comporte des entrées pour les menus fichier et fenêtre en plus de l’entrée VK_ESCAPE. L’exemple suivant est la table d’accélérateurs créée pour l’activation sur place dans l’exemple MFC [conteneur](../overview/visual-cpp-samples.md):

|Id|Touche|Type|
|--------|---------|----------|
|ID_FILE_NEW|CTRL+N|**VIRTKEY**|
|ID_FILE_OPEN|CTRL+O|**VIRTKEY**|
|ID_FILE_SAVE|CTRL+S|**VIRTKEY**|
|ID_FILE_PRINT|CTRL+P|**VIRTKEY**|
|ID_NEXT_PANE|VK_F6|**VIRTKEY**|
|ID_PREV_PANE|MAJ + VK_F6|**VIRTKEY**|
|ID_CANCEL_EDIT_CNTR|VK_ESCAPE|**VIRTKEY**|

##  <a name="_core_string_table_additions_for_container_applications"></a> Ajouts de Table de chaînes pour les Applications de conteneur

La plupart des modifications aux tables de chaînes pour les applications de conteneur correspondent aux éléments de menu supplémentaires mentionnés dans [ajouts au Menu du conteneur](#_core_container_menu_additions). Qu’ils vendent le texte affiché dans la barre d’état lorsque chaque élément de menu est affiché. Par exemple, voici les entrées de table de chaînes que l’Assistant application génère :

|Id|Chaîne|
|--------|------------|
|IDP_OLE_INIT_FAILED|Échec de l’initialisation d’OLE. Assurez-vous que vous avez la version correcte des bibliothèques OLE.|
|IDP_FAILED_TO_CREATE|Échec de création d’objet. Assurez-vous que l’objet est entré dans le Registre système.|

## <a name="see-also"></a>Voir aussi

[Menus et ressources (OLE)](../mfc/menus-and-resources-ole.md)<br/>
[Menus et ressources : Ajouts de serveurs](../mfc/menus-and-resources-server-additions.md)
