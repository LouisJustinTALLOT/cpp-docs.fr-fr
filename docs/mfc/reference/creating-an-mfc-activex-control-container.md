---
title: Création d'un conteneur de contrôles ActiveX MFC
ms.date: 09/12/2018
f1_keywords:
- vc.appwiz.activex.container
helpviewer_keywords:
- MFC ActiveX controls [MFC], containers
- ActiveX control containers [MFC], creating
- containers [MFC], creating
- OLE controls [MFC], containers
ms.assetid: ec70e137-7c14-4940-bd0e-fd4edcc63ea5
ms.openlocfilehash: 27f229a23595d4842a77409a3cedc7a57aa43e6c
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80079438"
---
# <a name="creating-an-mfc-activex-control-container"></a>Création d'un conteneur de contrôles ActiveX MFC

Un conteneur de contrôles ActiveX est un programme parent qui fournit l’environnement d’exécution d’un contrôle ActiveX (anciennement OLE). Vous pouvez créer une application capable de contenir des contrôles ActiveX avec ou sans MFC, mais il est beaucoup plus facile de le faire avec MFC.

>[!IMPORTANT]
> ActiveX est une technologie héritée qui ne doit pas être utilisée pour un nouveau développement. Pour plus d’informations sur les technologies modernes qui remplacent ActiveX, consultez [contrôles ActiveX](../activex-controls.md).

La création d’un programme de conteneur MFC à l’aide de l' [Assistant Application MFC](../../mfc/reference/mfc-application-wizard.md) vous permet d’accéder aux nombreuses fonctionnalités des contrôles ActiveX et de l’automatisation implémentées par les classes MFC et ActiveX. Ces fonctionnalités incluent la modification visuelle, l’automatisation, la création de fichiers composés et la prise en charge des contrôles. Les options d’édition visuelle de l’Assistant Application MFC que votre programme parent prendra en charge incluent la création d’un conteneur, d’un mini-serveur, d’un serveur complet et d’un programme qui est à la fois un conteneur et un serveur.

- **Nouvelle application MFC**. Pour créer un nouveau programme MFC qui comprend l’automatisation, l’édition visuelle, les fichiers composés ou la prise en charge des contrôles, utilisez l’Assistant Application MFC et choisissez les options d’automatisation appropriées.

- **Application MFC existante**. Si vous ajoutez une relation contenant-contenu de contrôle à une application MFC existante, consultez [conteneurs de contrôles OLE : activation manuelle de la relation contenant-contenu de contrôle OLE](../../mfc/activex-control-containers-manually-enabling-activex-control-containment.md).

### <a name="to-create-an-activex-container-for-any-of-the-following-types-of-applications"></a>Pour créer un conteneur ActiveX pour l’un des types d’applications suivants

1. [Containers](../../mfc/containers.md)

1. [Modification visuelle](../../mfc/ole-mfc.md)

1. [Contrôles ActiveX MFC](../../mfc/mfc-activex-controls.md)

## <a name="see-also"></a>Voir aussi

[Types de projets C++ dans Visual Studio](../../build/reference/visual-cpp-project-types.md)
