---
title: Ajout d’un objet Simple ATL | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- vc.codewiz.classes.adding.atl
dev_langs:
- C++
helpviewer_keywords:
- ATL projects, adding objects
- objects [ATL]
- ATL, simple objects
ms.assetid: 9c57d2ef-0447-4c84-8982-3304b8e49847
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d1347fcebc6a3793cbe63ae356f7f9d2e03742cd
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46109767"
---
# <a name="adding-an-atl-simple-object"></a>Ajout d’un objet Simple ATL

Pour ajouter un objet ATL (Active Template Library) à votre projet, votre projet doit avoir été créé comme une application ATL ou comme une application MFC qui contient la prise en charge ATL. Vous pouvez utiliser [l’Assistant Projet ATL](../../atl/reference/atl-project-wizard.md) pour créer une application ATL ou [ajouter un objet ATL à votre application MFC](../../mfc/reference/adding-atl-support-to-your-mfc-project.md) pour implémenter la prise en charge ATL dans une application MFC.

Vous pouvez définir des interfaces COM pour votre nouvel objet ATL lors de la création ou les ajouter ultérieurement à l’aide de la [implémenter l’Interface](../../ide/implement-interface-wizard.md) commande dans le menu contextuel de vue de la classe.

### <a name="to-add-an-atl-simple-object-to-your-atl-com-project"></a>Pour ajouter un objet simple ATL à votre projet ATL COM

1. Dans le **l’Explorateur de solutions** ou [affichage de classes](/visualstudio/ide/viewing-the-structure-of-code), cliquez sur le nom du projet auquel vous souhaitez ajouter l’objet simple ATL.

2. Dans le menu contextuel, cliquez sur **Ajouter**, puis sur **Ajouter une classe**.

3. Dans le [ajouter une classe](../../ide/add-class-dialog-box.md) boîte de dialogue, dans le volet Modèles, cliquez sur **objet Simple ATL**, puis cliquez sur **Open** pour afficher le [Assistant objet Simple ATL](../../atl/reference/atl-simple-object-wizard.md).

4. Définir des options supplémentaires pour votre projet sur le [Options](../../atl/reference/options-atl-simple-object-wizard.md) page de l’Assistant objet Simple ATL.

5. Cliquez sur **Terminer** pour ajouter l’objet à votre projet.

## <a name="see-also"></a>Voir aussi

[Ajout d’une classe](../../ide/adding-a-class-visual-cpp.md)<br/>
[Ajout d’une nouvelle interface à un projet ATL](../../atl/reference/adding-a-new-interface-in-an-atl-project.md)<br/>
[Ajout de points de connexion à un objet](../../atl/adding-connection-points-to-an-object.md)<br/>
[Ajout d’une méthode](../../ide/adding-a-method-visual-cpp.md)<br/>
[Classe MFC](../../mfc/reference/adding-an-mfc-class.md)<br/>
[Ajout d’une classe C++ générique](../../ide/adding-a-generic-cpp-class.md)

