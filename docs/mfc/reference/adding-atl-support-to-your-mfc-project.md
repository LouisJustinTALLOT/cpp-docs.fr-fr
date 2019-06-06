---
title: Ajout de la prise en charge ATL à votre projet MFC
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.adding.atl.mfc
helpviewer_keywords:
- MFC, ATL support
- ATL, MFC projects
ms.assetid: b5fe15d6-7752-4818-b9f9-62482ad35c95
ms.openlocfilehash: 0f75ffd09da1502e5f1488dbce0d8d2b9623d396
ms.sourcegitcommit: 65ed563a8a1d4d90f872a2a6edcb086f84ec9f77
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2019
ms.locfileid: "66741727"
---
# <a name="adding-atl-support-to-your-mfc-project"></a>Ajout de la prise en charge ATL à votre projet MFC

Si vous avez déjà créé une application basée sur MFC, puis vous pouvez ajouter la prise en charge pour la bibliothèque ATL (Active Template) facilement en exécutant l’ajouter prise en charge ATL à l’Assistant de projet MFC.

> [!NOTE]
>  ATL et MFC ne sont généralement pas pris en charge dans les éditions Express de Visual Studio.

> [!NOTE]
>  Cette prise en charge s’applique uniquement aux objets simples COM ajoutés à un fichier exécutable MFC ou à un projet DLL. Vous pouvez ajouter des autres objets COM (y compris les contrôles ActiveX) à des projets MFC, mais les objets risque de ne pas fonctionner comme prévu.

### <a name="to-add-atl-support-to-your-mfc-project"></a>Pour ajouter la prise en charge ATL à votre projet MFC

1. Dans l’Explorateur de solutions, cliquez sur le projet auquel vous souhaitez ajouter la prise en charge ATL.

1. Dans le menu contextuel, cliquez sur **Ajouter**, puis cliquez sur **Ajouter une classe**.

1. Sélectionnez le **ajouter la prise en charge ATL au projet MFC** icône.

    > [!NOTE]
    >  Cette icône se trouve dans le dossier ATL le **catégories** volet.

1. Lorsque vous y êtes invité, cliquez sur **Oui** pour ajouter la prise en charge ATL.

Pour plus d’informations sur la façon dont l’ajout de prise en charge ATL modifie le code de votre projet MFC, consultez [détails de la prise en charge ATL ajoutée par l’Assistant ATL](../../mfc/reference/details-of-atl-support-added-by-the-atl-wizard.md)

## <a name="see-also"></a>Voir aussi

[Ajout d’une classe](../../ide/adding-a-class-visual-cpp.md)<br/>
[Ajout de fonctionnalités à l’aide des Assistants Code](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[Ajout d’une fonction membre](../../ide/adding-a-member-function-visual-cpp.md)<br/>
[Ajout d’une variable membre](../../ide/adding-a-member-variable-visual-cpp.md)<br/>
[Substitution d’une fonction virtuelle](../../ide/overriding-a-virtual-function-visual-cpp.md)<br/>
[Gestionnaire de messages MFC](../../mfc/reference/adding-an-mfc-message-handler.md)<br/>
[Parcours de la structure de classe](../../ide/navigate-code-cpp.md)
