---
title: Ajout de la prise en charge ATL à votre projet MFC
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.adding.atl.mfc
helpviewer_keywords:
- MFC, ATL support
- ATL, MFC projects
ms.assetid: b5fe15d6-7752-4818-b9f9-62482ad35c95
ms.openlocfilehash: 94303d1dfc7c06171def1224982f5e0aa5716ce4
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92924462"
---
# <a name="adding-atl-support-to-your-mfc-project"></a>Ajout de la prise en charge ATL à votre projet MFC

Si vous avez déjà créé une application MFC, vous pouvez facilement ajouter la prise en charge de l’Active Template Library (ATL) à l’aide de l’IDE.

> [!NOTE]
> Cette prise en charge s’applique uniquement aux objets simples COM ajoutés à un fichier exécutable MFC ou à un projet DLL. Vous pouvez ajouter d’autres objets COM (y compris des contrôles ActiveX) aux projets MFC, mais les objets peuvent ne pas fonctionner comme prévu.

::: moniker range=">=msvc-160"

1. Dans Explorateur de solutions, cliquez avec le bouton droit sur le nœud du projet.

1. Dans le menu contextuel, cliquez sur **Ajouter** , puis sur **Nouvel élément** .

1. Dans le volet gauche, choisissez **ATL** , puis **prise en charge ATL** dans le volet central.

::: moniker-end

::: moniker range="<=msvc-150"

### <a name="to-add-atl-support-to-your-mfc-project"></a>Pour ajouter la prise en charge ATL à votre projet MFC

1. Dans Explorateur de solutions, cliquez avec le bouton droit sur le nœud du projet.

1. Dans le menu contextuel, cliquez sur **Ajouter** , puis cliquez sur **Ajouter une classe** .

1. Sélectionnez **ATL** dans le volet gauche, puis choisissez **Ajouter la prise en charge ATL au projet MFC** dans le volet central.

::: moniker-end

Pour plus d’informations sur la façon dont l’ajout de la prise en charge ATL modifie le code de votre projet MFC, consultez [Détails de la prise en charge ATL ajoutée par l’Assistant ATL](../../mfc/reference/details-of-atl-support-added-by-the-atl-wizard.md)

## <a name="see-also"></a>Voir aussi

[Ajout d’une classe](../../ide/adding-a-class-visual-cpp.md)<br/>
[Ajout de fonctionnalités à l’aide des Assistants Code](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[Ajout d’une fonction membre](../../ide/adding-a-member-function-visual-cpp.md)<br/>
[Ajout d’une variable membre](../../ide/adding-a-member-variable-visual-cpp.md)<br/>
[Substitution d’une fonction virtuelle](../../ide/overriding-a-virtual-function-visual-cpp.md)<br/>
[Gestionnaire de messages MFC](../../mfc/reference/adding-an-mfc-message-handler.md)<br/>
[Parcours de la structure de classe](../../ide/navigate-code-cpp.md)
