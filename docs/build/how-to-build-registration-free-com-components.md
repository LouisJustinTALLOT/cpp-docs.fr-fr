---
title: 'Comment : générer des composants COM sans inscription | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- COM components, registration-free
ms.assetid: 7e585d6a-0314-45b2-8f1b-cae9ac4df037
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1eaf9417f4d2b3b825933589556055772b84e057
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2018
ms.locfileid: "43197411"
---
# <a name="how-to-build-registration-free-com-components"></a>Comment : générer des composants COM sans inscription
Les composants COM sans inscription sont des composants COM qui ont des manifestes générés dans les DLL.  
  
### <a name="to-build-manifests-into-com-components"></a>Pour générer des manifestes dans les composants COM  
  
1.  Ouvrez les pages de propriétés de projet pour le composant COM.  
  
2.  Développez le **propriétés de Configuration** nœud, puis développez le **outil manifeste** nœud.  
  
3.  Sélectionnez le **d’entrée et sortie** page de propriétés, puis définissez le **incorporer le manifeste** propriété égale à **Oui**.  
  
4.  Cliquez sur **OK**.  
  
5.  Générez la solution.  
  
## <a name="see-also"></a>Voir aussi  
 [Applications isolées](/windows/desktop/SbsCs/isolated-applications)   
 [Sur les assemblys côte à côte](/windows/desktop/SbsCs/about-side-by-side-assemblies-)   
 [Guide pratique pour générer des applications isolées pour consommer des composants COM](../build/how-to-build-isolated-applications-to-consume-com-components.md)