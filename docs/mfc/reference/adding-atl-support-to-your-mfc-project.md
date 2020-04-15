---
title: Ajout de la prise en charge ATL à votre projet MFC
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.adding.atl.mfc
helpviewer_keywords:
- MFC, ATL support
- ATL, MFC projects
ms.assetid: b5fe15d6-7752-4818-b9f9-62482ad35c95
ms.openlocfilehash: 05c4e8ba54d9a573b422f136c9e8cf69e48d1c9a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371680"
---
# <a name="adding-atl-support-to-your-mfc-project"></a>Ajout de la prise en charge ATL à votre projet MFC

Si vous avez déjà créé une application basée sur MFC, vous pouvez ajouter facilement un support pour la bibliothèque Active Template (ATL) en utilisant l’IDE.

> [!NOTE]
> Cette prise en charge s’applique uniquement aux objets simples COM ajoutés à un fichier exécutable MFC ou à un projet DLL. Vous pouvez ajouter d’autres objets COM (y compris les commandes ActiveX) aux projets MFC, mais les objets pourraient ne pas fonctionner comme prévu.

::: moniker range=">=vs-2019"

1. Dans Solution Explorer, cliquez à droite sur le nœud du projet.

1. Dans le menu contextuel, cliquez sur **Ajouter**, puis sur **Nouvel élément**.

1. Choisissez **ATL** dans la vitre gauche, puis choisissez **ATL Support** dans la vitre centrale.

::: moniker-end

::: moniker range="<=vs-2017"

### <a name="to-add-atl-support-to-your-mfc-project"></a>Pour ajouter le support ATL à votre projet MFC

1. Dans Solution Explorer, cliquez à droite sur le nœud du projet.

1. Dans le menu contextuel, cliquez sur **Ajouter**, puis cliquez sur **Ajouter une classe**.

1. Sélectionnez **ATL** dans la vitre gauche, puis choisissez **Ajouter ATL Support au projet MFC** dans la vitre centrale.

::: moniker-end

Pour plus d’informations sur la façon dont l’ajout d’un support ATL modifie le code de votre projet MFC, voir [Détails du support ATL ajouté par l’assistant ATL](../../mfc/reference/details-of-atl-support-added-by-the-atl-wizard.md)

## <a name="see-also"></a>Voir aussi

[Ajout d’une classe](../../ide/adding-a-class-visual-cpp.md)<br/>
[Ajout de fonctionnalités à l’aide des Assistants Code](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[Ajout d’une fonction membre](../../ide/adding-a-member-function-visual-cpp.md)<br/>
[Ajout d’une variable membre](../../ide/adding-a-member-variable-visual-cpp.md)<br/>
[Substitution d’une fonction virtuelle](../../ide/overriding-a-virtual-function-visual-cpp.md)<br/>
[Gestionnaire de messages MFC](../../mfc/reference/adding-an-mfc-message-handler.md)<br/>
[Parcours de la structure de classe](../../ide/navigate-code-cpp.md)
