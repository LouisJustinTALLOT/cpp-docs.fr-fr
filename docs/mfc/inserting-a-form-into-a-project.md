---
description: 'En savoir plus sur : insertion d’un formulaire dans un projet'
title: Insertion d'un formulaire dans un projet
ms.date: 11/04/2016
helpviewer_keywords:
- inserting forms [MFC]
- Insert New dialog box [MFC]
- forms, adding to projects
ms.assetid: f3bd2998-3ce2-496d-ac5c-57ca70eec7cb
ms.openlocfilehash: d0c67532261e4c5a5740f4ff07543f141b34d7a7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97220485"
---
# <a name="inserting-a-form-into-a-project"></a>Insertion d'un formulaire dans un projet

Les formulaires fournissent un conteneur pratique pour les contrôles. Vous pouvez facilement insérer un formulaire MFC dans votre application, à condition que l’application prenne en charge les bibliothèques MFC.

### <a name="to-insert-a-form-into-your-project"></a>Pour insérer un formulaire dans votre projet

1. Dans Affichage de classes, sélectionnez le projet auquel vous souhaitez ajouter le formulaire, puis cliquez avec le bouton droit de la souris.

1. Dans le menu contextuel, cliquez sur **Ajouter**, puis sur **Ajouter une classe**.

   Si la commande **nouveau formulaire** n’est pas disponible, votre projet peut être basé sur le Active Template Library (ATL). Pour ajouter un formulaire à un projet ATL, vous devez [spécifier certains paramètres](../atl/reference/application-settings-atl-project-wizard.md) lors de la création initiale du projet.

1. Dans le dossier **MFC** , cliquez sur **classe MFC**.

1. À l’aide de l’Assistant classe MFC, faites en sorte que la nouvelle classe dérive de [CFormView](reference/cformview-class.md).

Visual C++ ajoute le formulaire à votre application, en l’ouvrant à l’intérieur de l’éditeur de boîtes de dialogue pour vous permettre de commencer à ajouter des contrôles et à travailler sur sa conception globale.

Vous souhaiterez peut-être effectuer les étapes supplémentaires suivantes (non applicables pour les applications basées sur des boîtes de dialogue) :

1. Substituez la `OnUpdate` fonction membre.

1. Implémentez une fonction membre pour déplacer des données de votre vue vers votre document.

1. Créer une `OnPrint` fonction membre.

## <a name="see-also"></a>Voir aussi

[Mode Formulaire](form-views-mfc.md)
