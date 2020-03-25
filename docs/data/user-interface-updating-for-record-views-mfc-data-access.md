---
title: Mise à jour de l'interface utilisateur pour les vues des enregistrements (Accès aux données MFC)
ms.date: 11/04/2016
helpviewer_keywords:
- user interfaces, updating
- menus, updating as context changes
- record views, user interface
ms.assetid: 2c7914b6-2dc3-40c3-b2f2-8371da2a4063
ms.openlocfilehash: 9bfb907d21c928c605b304c595acb834d0046e35
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80209051"
---
# <a name="user-interface-updating-for-record-views--mfc-data-access"></a>Mise à jour de l'interface utilisateur pour les vues des enregistrements (Accès aux données MFC)

`CRecordView` fournit des gestionnaires de mise à jour de l’interface utilisateur par défaut pour les commandes de navigation. Ces gestionnaires automatisent l'activation et la désactivation des objets d'interface utilisateur (éléments de menu et boutons de barre d'outils). L’Assistant application fournit des menus standard et, si vous choisissez l’option **barre d’outils ancrable** , un ensemble de boutons de barre d’outils pour les commandes. Si vous créez une classe de vue d'enregistrement à l'aide de `CRecordView`, vous pouvez ajouter des objets d'interface utilisateur similaires à votre application.

### <a name="to-create-menu-resources-with-the-menu-editor"></a>Pour créer des ressources de menu avec l'éditeur de menu

1. En vous référant aux informations sur l’utilisation de l' [éditeur de menus](../windows/menu-editor.md), créez votre propre menu avec les quatre mêmes commandes.

#### <a name="to-create-toolbar-buttons-with-the-graphics-editor"></a>Pour créer des boutons de barre d'outils avec l'éditeur de graphismes

1. En vous référant aux informations sur l’utilisation de l' [éditeur de barres d'](../windows/toolbar-editor.md)outils, modifiez la ressource de barre d’outils pour ajouter des boutons de barre d’outils à vos commandes de navigation dans les enregistrements.

## <a name="see-also"></a>Voir aussi

[Prise en charge de la navigation dans une vue d’enregistrement](../data/supporting-navigation-in-a-record-view-mfc-data-access.md)<br/>
[Utilisation d’une vue de l’enregistrement](../data/using-a-record-view-mfc-data-access.md)
