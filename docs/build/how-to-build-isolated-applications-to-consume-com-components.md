---
description: 'En savoir plus sur : Comment : générer des applications isolées pour consommer des composants COM'
title: 'Comment : générer des applications isolées pour consommer des composants COM'
ms.date: 11/04/2016
helpviewer_keywords:
- isolated applications [C++]
ms.assetid: 04587547-1174-44ab-bd99-1292358fba20
ms.openlocfilehash: 31a54683974b8539724ecee24aa45917674a6e82
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97156383"
---
# <a name="how-to-build-isolated-applications-to-consume-com-components"></a>Comment : générer des applications isolées pour consommer des composants COM

Les applications isolées sont des applications qui ont des manifestes intégrés au programme. Vous pouvez créer des applications isolées pour consommer des composants COM.

### <a name="to-add-com-references-to-manifests-of-isolated-applications"></a>Pour ajouter des références COM aux manifestes d’applications isolées

1. Ouvrez les pages de propriétés du projet pour l’application isolée.

1. Développez le nœud **Propriétés de configuration** , puis développez le nœud **outil manifeste** .

1. Sélectionnez la page de propriétés **com isolé** , puis définissez la propriété **nom de fichier du composant** sur le nom du composant COM que vous souhaitez que l’application isolée consomme.

1. Cliquez sur **OK**.

### <a name="to-build-manifests-into-isolated-applications"></a>Pour générer des manifestes dans des applications isolées

1. Ouvrez les pages de propriétés du projet pour l’application isolée.

1. Développez le nœud **Propriétés de configuration** , puis développez le nœud **outil manifeste** .

1. Sélectionnez la page de propriétés **entrée et sortie** , puis affectez à la propriété **incorporer le manifeste** la valeur **Oui**.

1. Cliquez sur **OK**.

1. Générez la solution.

## <a name="see-also"></a>Voir aussi

[Applications isolées](/windows/win32/SbsCs/isolated-applications)<br/>
[À propos des assemblys côte à côte](/windows/win32/SbsCs/about-side-by-side-assemblies-)
