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
ms.openlocfilehash: 7591b3ed84c1703a201e4e62f699df877de36058
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65220190"
---
# <a name="creating-an-mfc-activex-control-container"></a>Création d'un conteneur de contrôles ActiveX MFC

Un conteneur de contrôles ActiveX est un programme parent qui fournit l’environnement pour un contrôle ActiveX (anciennement appelés OLE) à exécuter. Vous pouvez créer une application capable de contenir des contrôles ActiveX avec ou sans MFC, mais il est beaucoup plus facile à voir avec MFC.

>[!IMPORTANT]
> ActiveX est une technologie héritée qui ne doit pas être utilisée pour tout nouveau développement. Pour plus d’informations sur les technologies modernes qui remplacent ActiveX, consultez [contrôles ActiveX](../activex-controls.md).

Création d’un programme MFC conteneur à l’aide du [Assistant Application MFC](../../mfc/reference/mfc-application-wizard.md) vous permet d’accéder aux nombreuses fonctionnalités de contrôles ActiveX et d’automatisation qui sont implémentées par les classes MFC et ActiveX. Ces fonctionnalités incluent la modification visuelle, Automation, création de fichiers composés et prendre en charge pour les contrôles. Les options d’édition visuelle Assistant Application MFC qui prend en charge votre programme parent incluent la création d’un conteneur, un mini-serveur, un serveur complet et un programme qui est un conteneur et un serveur.

- **Nouvelle Application MFC**. Pour créer un nouveau programme MFC qui inclut l’automatisation, modification visuelle, composée de fichiers, ou contrôle prennent en charge, utiliser l’Assistant Application MFC et choisissez les options Automation appropriées.

- **Application MFC existante**. Si vous ajoutez la contenance de contrôles à une application MFC existante, consultez [conteneurs de contrôles OLE : Activation manuelle de la contenance de contrôles OLE](../../mfc/activex-control-containers-manually-enabling-activex-control-containment.md).

### <a name="to-create-an-activex-container-for-any-of-the-following-types-of-applications"></a>Pour créer un conteneur ActiveX pour un des types suivants d’applications

1. [Conteneurs](../../mfc/containers.md)

1. [Édition visuelle](../../mfc/ole-mfc.md)

1. [Contrôles ActiveX MFC](../../mfc/mfc-activex-controls.md)

## <a name="see-also"></a>Voir aussi

[C++types de projets dans Visual Studio](../../build/reference/visual-cpp-project-types.md)

