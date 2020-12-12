---
description: 'En savoir plus sur les éléments suivants : mise à jour User-Interface pour les vues des enregistrements (accès aux données MFC)'
title: Mise à jour de l'interface utilisateur pour les vues des enregistrements (Accès aux données MFC)
ms.date: 11/04/2016
helpviewer_keywords:
- user interfaces, updating
- menus, updating as context changes
- record views, user interface
ms.assetid: 2c7914b6-2dc3-40c3-b2f2-8371da2a4063
ms.openlocfilehash: 3a199faa3e606260257ece0fff9a7d1de3095d18
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97116442"
---
# <a name="user-interface-updating-for-record-views--mfc-data-access"></a>Mise à jour de l'interface utilisateur pour les vues des enregistrements (Accès aux données MFC)

`CRecordView` fournit les gestionnaires de mise à jour de l’interface utilisateur par défaut pour les commandes de navigation. Ces gestionnaires automatisent l'activation et la désactivation des objets d'interface utilisateur (éléments de menu et boutons de barre d'outils). L’Assistant application fournit des menus standard et, si vous choisissez l’option **barre d’outils ancrable** , un ensemble de boutons de barre d’outils pour les commandes. Si vous créez une classe de vue d'enregistrement à l'aide de `CRecordView`, vous pouvez ajouter des objets d'interface utilisateur similaires à votre application.

### <a name="to-create-menu-resources-with-the-menu-editor"></a>Pour créer des ressources de menu avec l'éditeur de menu

1. En vous référant aux informations sur l’utilisation de l' [éditeur de menus](../windows/menu-editor.md), créez votre propre menu avec les quatre mêmes commandes.

#### <a name="to-create-toolbar-buttons-with-the-graphics-editor"></a>Pour créer des boutons de barre d'outils avec l'éditeur de graphismes

1. En vous référant aux informations sur l’utilisation de l' [éditeur de barres d'](../windows/toolbar-editor.md)outils, modifiez la ressource de barre d’outils pour ajouter des boutons de barre d’outils à vos commandes de navigation dans les enregistrements.

## <a name="see-also"></a>Voir aussi

[Prise en charge de la navigation dans une vue de l'enregistrement](../data/supporting-navigation-in-a-record-view-mfc-data-access.md)<br/>
[Utilisation d'une vue de l'enregistrement](../data/using-a-record-view-mfc-data-access.md)
